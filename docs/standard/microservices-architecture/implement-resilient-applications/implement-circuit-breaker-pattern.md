---
title: "實作斷路器模式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作斷路器模式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>實作斷路器模式

如前文所述，您應該處理可能需要在變數一段時間復原，因為當您嘗試連接到遠端服務或資源時可能會發生的錯誤。 處理這種類型的錯誤，可以改進的穩定性和恢復功能的應用程式。

在分散式環境中，呼叫遠端資源和服務可以因為暫時性錯誤，例如低速網路連線和逾時、 失敗或如果資源正在緩慢或暫時無法使用。 這些錯誤通常可以修正本身一段時間之後, 和強大的雲端應用程式應該準備好處理它們使用的策略，例如重試模式。

不過，有也可以因為非預期的事件，可能需要更長時間來修正錯誤的情況。 這些錯誤的範圍部分連線中斷服務的完整錯誤的嚴重性。 在這些情況下，可能毫無意義的應用程式持續重試不太可能會成功的作業。 相反地，應用程式碼設計應接受作業失敗，並據以處理失敗。

斷路器模式有不同的用途比重試模式。 重試模式可讓應用程式重試此作業最終會成功且預期的作業。 斷路器模式會防止應用程式執行的作業可能會失敗。 應用程式可以結合這兩種模式來叫用作業，斷路器透過使用重試模式。 不過，重試邏輯應該格外斷路器，所傳回的任何例外狀況，而且如果斷路器會指出錯誤並非暫時性，它應該放棄重試次數。

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>使用 Polly 實作斷路器模式

為實作重試次數，斷路器的建議的方法時，若要善用像 Polly 經過證實的.NET 程式庫。

EShopOnContainers 應用程式實作 HTTP 重試時，會使用 Polly 斷路器原則。 事實上，應用程式會將這兩個原則套 ResilientHttpClient 公用程式類別。 每當 ResilientHttpClient 類型的物件使用的 HTTP 要求 （來自 eShopOnContainers) 時，您將會套用這兩個這些原則，但是您無法太加入額外的原則。

唯一新增這裡使用 HTTP 呼叫重試程式碼是程式碼，其中您加入斷路器原則的原則，以使用時，清單結尾的下列程式碼所示：

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

程式碼會將原則加入至 HTTP 包裝函式。 原則會定義為當程式碼偵測到指定的數目的連續例外狀況 （資料列中例外狀況），會開啟斷路器會傳入 exceptionsAllowedBeforeBreaking 參數 (在本例中為 5)。 循環開啟時，HTTP 要求沒有作用，但是在引發例外狀況。

斷路器應該也可用來要求重新導向至後援的基礎結構可能發生問題時於用戶端應用程式在不同環境中部署的特定資源或執行 HTTP 呼叫的服務中。 這樣一來，只有您的後端 microservices 但未用戶端應用程式，將會影響在資料中心中斷時用戶端應用程式可以重新導向至後援的服務。 新的原則，來自動化此計劃 Polly[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。

當然，所有這些功能便會管理.NET 程式碼，而不需要它會自動為您管理 azure，與位置透明度內的容錯移轉的情況下。

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>使用從 eShopOnContainers ResilientHttpClient 公用程式類別

您可以使用 ResilientHttpClient 公用程式類別中的方式類似於您如何使用.NET HttpClient 類別。 在下列範例從 eShopOnContainers MVC web 應用程式 （使用 OrderController OrderingService 代理程式類別） 中，是透過 httpClient 參數的建構函式插入 ResilientHttpClient 物件。 然後此物件用來執行 HTTP 要求。

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

每當\_apiClient 成員物件，則會在內部使用包裝函式類別和 Polly policiesؙ-重試原則，斷路器原則和任何其他您可能想要從 Polly 原則集合套用的原則。

## <a name="testing-retries-in-eshoponcontainers"></a>在 eShopOnContainers 測試重試次數

每當您在 Docker 主機啟動 eShopOnContainers 解決方案，它需要啟動多個容器。 容器的某些較慢啟動並初始化，例如 SQL Server 容器。 特別是第一次部署 eShopOnContainers 應用程式進入 Docker，因為它必須設定映像和資料庫。 某些容器的開始速度比其他人可能會造成其他的服務，一開始擲回 HTTP 例外狀況，即使您將在容器之間的相依性的事實 docker-撰寫層級上, 一節所述。 這些 docker-撰寫容器之間的相依性都只在處理序層級。 容器的進入點程序可能會啟動，但 SQL Server 可能無法供查詢。 此結果會串聯的錯誤，並嘗試使用該特定容器時，應用程式可以取得例外狀況。

您也可能會看到這種類型的錯誤在啟動時應用程式部署到雲端。 在此情況下，orchestrators 可能容器從一個節點或 VM 之間移動 （也就，開始新執行個體） 時的容器數目平衡叢集的節點。

EShopOnContainers 可以解決此問題的方式是使用我們稍早所述的重試模式。 它也是為何，當啟動方案，您可能會發生記錄追蹤或警告，如下所示：

> 「**Polly 的 RetryPolicy 實作重試 1**，由於： System.Net.Http.HttpRequestException： 正在傳送的要求時發生錯誤。 ---&gt;System.Net.Http.CurlException： 無法連接到伺服器\\System.Net.Http.CurlHandler.ThrowIfCURLEError （CURLcode 錯誤） 在 n\\在 n \[...\].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>測試 eShopOnContainers 斷路器

有幾個方法，您可以開啟電路，eShopOnContainers 進行測試。

其中一個選項是降低的重試次數為 1，斷路器原則中允許的數目，並重新部署整個方案到 Docker。 單一重試 」，以在部署期間將會失敗的 HTTP 要求的機會，斷路器就會開啟，而且您收到錯誤。

另一個選項是使用排序的微服務中實作自訂的中介軟體。 啟用此中介軟體時，它會攔截所有的 HTTP 要求，並會傳回狀態碼 500。 您可以藉由發生失敗的 GET 要求來啟用中介軟體的 URI，如下所示：

-   取得/失敗

此要求會傳回目前中介軟體的狀態。 如果已啟用中, 介軟體，則要求會傳回狀態碼 500。 如果已停用中介軟體，但沒有回應。

-   取得/失敗？ 啟用

此要求可讓中介軟體。

-   取得/失敗？ 停用

此要求會停用中介軟體。

比方說，應用程式開始執行之後，您就可以提出任何瀏覽器中使用下列 URI 要求啟用的中介軟體。 請注意，排序的微服務會使用連接埠 5102。

http://localhost:5102 / 失敗？ 啟用

然後，您可以檢查的狀態，使用 URI [http://localhost:5102 / 失敗](http://localhost:5100/failing)，如圖 10-4 所示。

![](./media/image4.png)

**圖 10-4**。 模擬與 ASP.NET 中介軟體的失敗

此時，順序微服務回應，狀態碼為 500，每當您呼叫叫用它。

中介軟體開始執行之後，您可以嘗試讓 MVC web 應用程式向下的訂單。 要求失敗，因為此電路會開啟。

在下列範例中，您可以看到 MVC web 應用程式有 catch 區塊中的邏輯下訂單。 如果程式碼攔截開啟電路例外狀況，它會顯示使用者易記訊息，告知等待。

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

此為摘要。 重試原則會嘗試對 HTTP 要求和取得 HTTP 錯誤數次。 當嘗試次數達到設定的最大數目 （在此情況下，5） 的斷路器原則時，應用程式會擲回 BrokenCircuitException。 結果是易記的訊息，如圖 10-5 所示。

![](./media/image5.png)

**圖 10-5**。 斷路器 ui 傳回錯誤

您可以實作不同的邏輯時開啟電路。 或如果沒有後援資料中心或多餘的後端系統，您可以嘗試對不同的後端微服務的 HTTP 要求。

最後，CircuitBreakerPolicy 另一個可能性是使用隔離 （這樣會強制開啟並保持開啟循環） 和重設 （這會關閉它一次）。 這些可以用來建立原則會隔離和重設直接叫用的公用程式 HTTP 端點。 HTTP 端點也可以使用，適當地保護暫時隔離的下游系統，例如當您想要將它升級生產環境中。 或其無法成為以手動方式來保護您懷疑被判定為失敗的下游系統循環。

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>抖動策略加入重試原則

規則的重試原則可能會影響您的系統在高並行存取，以及延展性，並在高度競爭的情況下。 若要克服類似來自部分的中斷發生的許多用戶端重試次數的尖峰，良好的因應措施是抖動策略加入重試演算法/原則。 這可以改善整體系統效能的端對端加入指數型輪詢的隨機性。 這向外擴散如果看到爆增情形發生問題時。 當您使用 Polly 時，程式碼來實作抖動可能看起來像下列的範例：

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

-   **連接恢復功能**(Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** （.NET 恢復功能和暫時性錯誤處理程式庫） [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker。抖動： 讓事情更加具有隨機性**https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[上一個](implement-http-call-retries-exponential-backoff-polly.md) [下一步] (監視的應用程式-health.md)
