---
title: 實作斷路器模式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作斷路器模式
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.openlocfilehash: 2c89992c4c60ca7f1085050e6fed4922ecd4d8cc
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106121"
---
# <a name="implementing-the-circuit-breaker-pattern"></a>實作斷路器模式

如稍早所述，您應該處理復原所需的時間可能不確定的錯誤，當您嘗試連接到遠端服務或資源時，可能會發生此錯誤。 處理這種類型的錯誤可改善應用程式的穩定性和復原。

在分散式環境中，呼叫遠端資源和服務可能會由於暫時性錯誤 (例如網路連線太慢和逾時)，或是資源變慢或暫時無法使用而失敗。 這些錯誤通常會在很短的時間內自我修正，而且強大的雲端應用程式應該能夠使用重試模式之類的策略來處理錯誤。

不過有時候，錯誤是由於非預期的事件所致，可能需要更長時間來修正。 這些錯誤的嚴重性可能從失去部分連線到服務完全失敗。 在這些情況下，讓應用程式持續重試不太可能會成功的作業可能毫無意義。 相反地，應用程式應該設計成接受作業失敗並據以處理失敗。

斷路器模式的目的與重試模式不同。 重試模式可讓應用程式重試作業，期望該作業最終會成功。 斷路器模式可防止應用程式執行可能失敗的作業。 應用程式可以結合這兩種模式，使用重試模式透過斷路器來叫用作業。 不過，重試邏輯應該會受到斷路器所傳回之任何例外狀況的影響，而且如果斷路器指出錯誤不是暫時的，就應該放棄重試嘗試。

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>使用 Polly 實作斷路器模式

實作重試時，斷路器的建議方法是利用經過實證的 .NET 程式庫，例如 Polly。

實作 HTTP 重試時，eShopOnContainers 應用程式會使用 Polly 斷路器原則。 事實上，應用程式會將這兩個原則套用至 ResilientHttpClient 公用程式類別。 只要您針對 HTTP 要求 (來自 eShopOnContainers) 使用 ResilientHttpClient 類型的物件，就都會套用這兩個原則，但您也可以新增其他原則。

此處用於 HTTP 呼叫重試之程式碼的唯一新增項目，就是用來將斷路器原則新增至所要使用之原則清單的程式碼，如下列程式碼結尾所示：

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

此程式碼會將原則新增至 HTTP 包裝函式。 該原則會定義斷路器在程式碼偵測到指定的連續例外狀況 (一連串例外狀況) 數目時開啟，如同 exceptionsAllowedBeforeBreaking 參數中傳入的數目所指定 (在本例中為 5)。 當網路開啟時，HTTP 要求沒有作用，而是會引發例外狀況。

如果您部署在與執行 HTTP 呼叫的用戶端應用程式或服務不同之環境中的特定資源發生問題，也應該使用斷路器將要求重新導向至後援基礎結構。 這樣一來，如果資料中心的中斷只會影響您的後端微服務，但不會影響您的用戶端應用程式，用戶端應用程式就可以重新導向至後援服務。 Polly 正在規劃新的原則來自動化此[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。

當然，相對於由 Azure 為您自動管理，上述所有功能適用於從 .NET 程式碼管理容錯移轉的情況，並提供位置透明度。

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>從 eShopOnContainers 使用 ResilientHttpClient 公用程式類別

您可以透過類似 .NET HttpClient 類別的使用方式，來使用 ResilientHttpClient 公用程式類別。 在下列 eShopOnContainers MVC Web 應用程式範例中 (OrderController 所使用的 OrderingService 代理程式類別)，會透過建構函式的 httpClient 參數來插入 ResilientHttpClient 物件。 然後使用此物件來執行 HTTP 要求。

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

只要使用 \_apiClient 成員物件，它就會在內部搭配使用包裝函式類別與 Polly 原則：重試原則、斷路器原則，以及您想要從 Polly 原則集合套用的任何其他原則。

## <a name="testing-retries-in-eshoponcontainers"></a>在 eShopOnContainers 中測試重試

只要您在 Docker 主機中啟動 eShopOnContainers 解決方案，就需要啟動多個容器。 某些容器的啟動和初始化速度會比較慢，例如 SQL Server 容器。 特別是當您第一次將 eShopOnContainers 應用程式部署至 Docker 時，因為需要設定映像和資料庫。 某些容器的啟動速度會比其他容器慢，而導致其餘服務一開始擲回 HTTP 例外狀況，即使在 docker-compose 層級設定容器之間的相依性亦然，如先前章節所述。 容器之間的這些 docker-compose 相依性只會在處理序層。 容器的進入點處理序可能已啟動，但 SQL Server 可能尚未就緒而無法查詢。 結果可能是一連串的錯誤，而且嘗試取用該特定容器時，應用程式可能會收到例外狀況。

當應用程式正在部署至雲端時，您也可能會在啟動時看到這種錯誤類型。 在此情況下，平衡叢集節點之間的容器數目時，協調器可能會將容器從一個節點或 VM 移至另一個 (也就是啟動新的執行個體)。

eShopOnContainers 解決這個問題的方法是使用稍早所述的重試模式。 它也是為什麼在啟動解決方案時，您可能會收到類似如下的記錄追蹤或警告：

> **已使用 Polly 的重試原則實作重試 1**，原因如下：System.Net.Http.HttpRequestException：傳送要求時發生錯誤。 ---&gt; System.Net.Http.CurlException：無法連接到伺服器\\n 於 System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode 錯誤)\\n 於 \[...\]。

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>在 eShopOnContainers 中測試斷路器

您可以透過幾個方法來開啟網路，並使用 eShopOnContainers 進行測試。

一個選項是將斷路器原則中允許的重試次數減少為 1，然後將整個解決方案重新部署至 Docker。 使用單一重試，HTTP 要求很有可能會在部署期間失敗，此時斷路器會開啟，而且您會收到錯誤。

另一個選項是使用在 `Basket` 微服務中實作的自訂中介軟體。 啟用此中介軟體時，它會攔截所有的 HTTP 要求並傳回狀態碼 500。 您可以藉由提出失敗 URI 的 GET 要求來啟用中介軟體，如下所示：

-   GET /failing

此要求會傳回中介軟體的目前狀態。 如果啟用中介軟體，要求會傳回狀態碼 500。 如果停用中介軟體，則沒有回應。

-   GET /failing?enable

此要求會啟用中介軟體。

-   GET /failing?disable

此要求會停用中介軟體。

例如，應用程式開始執行之後，您可以在任何瀏覽器中使用下列 URI 提出要求，來啟用中介軟體。 請注意，訂購微服務會使用連接埠 5103。

http://localhost:5103/failing?enable

您可以接著使用 URI [http://localhost:5103/failing](http://localhost:5103/failing) 來檢查狀態，如圖 10-4 所示。

![](./media/image4.png)

**圖 10-4**： 檢查「失敗」的 ASP.NET 中介軟體狀態 (在本例中已停用) 

此時，只要您呼叫/叫用它，購物籃微服務就會以狀態碼 500 回應。

中介軟體開始執行之後，您可以嘗試從 MVC Web 應用程式下訂單。 由於要求失敗，因此會開啟網路。

在下列範例中，您可以看到 MVC Web 應用程式在下訂單的邏輯中有一個 catch 區塊。 如果程式碼攔截到開路例外狀況，它會向使用者顯示易懂訊息以通知他們等候。

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode                 
            HandleBrokenCircuitException();
        }
        return View();
    }       

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

以下摘要說明。 重試原則嘗試提出 HTTP 要求幾次，並收到 HTTP 錯誤。 當嘗試次數達到針對斷路器原則設定的最大數目時 (在本例中為 5)，應用程式會擲回 BrokenCircuitException。 結果是易懂訊息，如圖 10-5 所示。

![](./media/image5.png)

**圖 10-5**： 斷路器傳回錯誤至 UI

您可以實作何時開路的不同邏輯。 或者，如有後援資料中心或備援後端系統，您可以嘗試對不同後端微服務提出 HTTP 要求。

最後，CircuitBreakerPolicy 的另一個可能性是使用 Isolate (這會強制開啟並保持開啟網路) 和 Reset (這會再次將它關閉)。 這些可用來建置公用程式 HTTP 端點，以直接在原則上叫用 Isolate 和 Reset。 您也可以在生產環境中使用這類 HTTP 端點 (經過適當保護)，來暫時隔離下游系統，例如當您想要將它升級時。 或者，它可以手動啟動網路，來保護疑似故障的下游系統。

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>將 Jitter 策略新增至重試原則

如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。 若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。 這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。 發生問題時，突然增加的情況會擴散。 使用 Polly 時，要實作 Jitter 的程式碼可能會如下列範例所示：

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>其他資源

-   **重試模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **恢復連線** (Entity Framework Core)[*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (.NET 復原和暫時性錯誤處理程式庫) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker：Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[上一頁](implement-http-call-retries-exponential-backoff-polly.md)
[下一頁](monitor-app-health.md)
