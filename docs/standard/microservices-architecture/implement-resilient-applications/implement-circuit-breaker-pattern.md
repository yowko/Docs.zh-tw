---
title: 實作斷路器模式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作斷路器模式作為 Http 重試的互補系統
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: 8cd3564e5240ec5a8783edb336957549be27ea6a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44193233"
---
# <a name="implement-the-circuit-breaker-pattern"></a>實作斷路器模式

如稍早所述，您應該處理復原所需的時間可能不確定的錯誤，當您嘗試連接到遠端服務或資源時，可能會發生此錯誤。 處理這種類型的錯誤可改善應用程式的穩定性和復原。

在分散式環境中，呼叫遠端資源和服務可能會由於暫時性錯誤 (例如網路連線太慢和逾時)，或是資源回應緩慢或暫時無法使用而失敗。 這些錯誤通常會在很短的時間內自我修正，而且強大的雲端應用程式應該能夠使用「重試模式」之類的策略來處理錯誤。 

不過有時候，錯誤是由於非預期的事件所致，可能需要更長時間來修正。 這些錯誤的嚴重性可能從失去部分連線到服務完全失敗。 在這些情況下，讓應用程式持續重試不太可能會成功的作業可能毫無意義。 

相反地，應用程式應該設計成接受作業失敗並據以處理失敗。

隨意使用 Http 重試可能會導致在您自己的軟體內產生拒絕服務 ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) 的攻擊。 由於微服務失敗或執行緩慢，因此多個用戶端可能會重複重試失敗的要求。 這會帶來以失敗服務為目標的流量呈指數增加的危險風險。

因此，您需要某種形式的防禦屏障，在不值得繼續嘗試時停止多餘的要求。 該防禦屏障正是斷路器。

斷路器模式的目的與「重試模式」不同。 「重試模式」可讓應用程式重試作業，期望該作業最終會成功。 斷路器模式可防止應用程式執行可能失敗的作業。 應用程式可以結合這兩種模式。 不過，重試邏輯應該會受到斷路器所傳回之任何例外狀況的影響，而且如果斷路器指出錯誤不是暫時的，就應該放棄重試嘗試。

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a>使用 HttpClientFactory 和 Polly 實作斷路器模式

實作重試時，斷路器的建議方法是利用經過實證的 .NET 程式庫，例如 Polly 及其與 HttpClientFactory 的原生整合。

將斷路器原則新增至您的 HttpClientFactory 傳出中介軟體管線，就像是將單一程式碼片段增量新增至使用 HttpClientFactory 時已有的程式碼一樣簡單。

此處用於 HTTP 呼叫重試之程式碼的唯一新增項目，就是用來將斷路器原則新增至所要使用之原則清單的程式碼，如下列程式碼增量所示 (屬於 ConfigureServices() 方法一部分)。

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

`AddPolicyHandler()` 方法會將原則新增至您將使用的 HttpClient 物件。 在本例中，它會為斷路器新增 Polly 原則。

為了有更模組化的方法，可在名為 GetCircuitBreakerPolicy() 的個別方法中定義斷路器原則，如下列程式碼所示。

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

在上述程式碼範例中，斷路器原則設定為在重試 Http 要求時，若連續五次失敗，則會中斷或開啟網路。 發生此情況時，網路會中斷 30 秒：在這段期間，斷路器會立即使呼叫失敗，而不是實際發出。  原則會自動將[相關的例外狀況和 HTTP 狀態碼](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults)解釋為錯誤。  

如果您部署在與執行 HTTP 呼叫的用戶端應用程式或服務不同之環境中的特定資源發生問題，也應該使用斷路器將要求重新導向至後援基礎結構。 這樣一來，如果資料中心的中斷只會影響您的後端微服務，但不會影響您的用戶端應用程式，用戶端應用程式就可以重新導向至後援服務。 Polly 正在規劃新的原則來自動化此[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。 

相對於由 Azure 為您自動管理，上述所有功能適用於從 .NET 程式碼管理容錯移轉的情況，並提供位置透明度。 

從使用觀點來看，使用 HttpClient 時，不需要在此新增任何項目，因為使用 HttpClient 時的程式碼與 HttpClientFactory 相同，如先前章節所示。 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>在 eShopOnContainers 中測試 Http 重試和斷路器

只要您在 Docker 主機中啟動 eShopOnContainers 解決方案，就需要啟動多個容器。 某些容器的啟動和初始化速度會比較慢，例如 SQL Server 容器。 特別是當您第一次將 eShopOnContainers 應用程式部署至 Docker 時，因為需要設定映像和資料庫。 某些容器的啟動速度會比其他容器慢，而導致其餘服務一開始擲回 HTTP 例外狀況，即使在 docker-compose 層級設定容器之間的相依性亦然，如先前章節所述。 容器之間的這些 docker-compose 相依性只會在處理序層。 容器的進入點處理序可能已啟動，但 SQL Server 可能尚未就緒而無法查詢。 結果可能是一連串的錯誤，而且嘗試取用該特定容器時，應用程式可能會收到例外狀況。 

當應用程式正在部署至雲端時，您也可能會在啟動時看到這種錯誤類型。 在此情況下，平衡叢集節點之間的容器數目時，協調器可能會將容器從一個節點或 VM 移至另一個 (也就是啟動新的執行個體)。

啟動所有容器時，'eShopOnContainers' 解決這些問題的方法是使用稍早所述的重試模式。 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>在 eShopOnContainers 中測試斷路器

您可以透過幾個方法來中斷/開啟網路，並使用 eShopOnContainers 進行測試。

一個選項是將斷路器原則中允許的重試次數減少為 1，然後將整個解決方案重新部署至 Docker。 使用單一重試，HTTP 要求很有可能會在部署期間失敗，此時斷路器會開啟，而且您會收到錯誤。

另一個選項是使用在購物籃微服務中實作的自訂中介軟體。 啟用此中介軟體時，它會攔截所有的 HTTP 要求並傳回狀態碼 500。 您可以藉由提出失敗 URI 的 GET 要求來啟用中介軟體，如下所示：

- `GET http://localhost:5103/failing`

此要求會傳回中介軟體的目前狀態。 如果啟用中介軟體，要求會傳回狀態碼 500。 如果停用中介軟體，則沒有回應。 

- `GET http://localhost:5103/failing?enable`

此要求會啟用中介軟體。 

- `GET http://localhost:5103/failing?disable`

此要求會停用中介軟體。 

例如，應用程式開始執行之後，您可以在任何瀏覽器中使用下列 URI 提出要求，來啟用中介軟體。 請注意，訂購微服務會使用連接埠 5103。

`http://localhost:5103/failing?enable` 

您可以接著使用 URI http://localhost:5103/failing 來檢查狀態，如圖 10-4 所示。

![](./media/image4.png)

**圖 10-4**： 檢查「失敗」的 ASP.NET 中介軟體狀態 (在本例中已停用) 

此時，只要您呼叫/叫用它，購物籃微服務就會以狀態碼 500 回應。

中介軟體開始執行之後，您可以嘗試從 MVC Web 應用程式下訂單。 由於要求失敗，因此會開啟網路。 

在下列範例中，您可以看到 MVC Web 應用程式在下訂單的邏輯中有一個 catch 區塊。  如果程式碼攔截到開路例外狀況，它會向使用者顯示易懂訊息以通知他們等候。

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {          
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
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

以下摘要說明。 重試原則嘗試提出 HTTP 要求幾次，並收到 HTTP 錯誤。 當重試次數達到針對斷路器原則設定的最大數目時 (在本例中為 5)，應用程式會擲回 BrokenCircuitException。 結果是易懂訊息，如圖 10-5 所示。

![](./media/image5.png)

**圖 10-5**： 斷路器傳回錯誤至 UI

您可以實作何時開啟/中斷網路的不同邏輯。 或者，如有後援資料中心或備援後端系統，您可以嘗試對不同後端微服務提出 HTTP 要求。 

最後，`CircuitBreakerPolicy` 的另一個可能性是使用 `Isolate` (這會強制開啟並保持開啟網路) 和 `Reset` (這會再次將它關閉)。 這些可用來建置公用程式 HTTP 端點，以直接在原則上叫用 Isolate 和 Reset。  您也可以在生產環境中使用這類 HTTP 端點 (經過適當保護)，來暫時隔離下游系統，例如當您想要將它升級時。 或者，它可以手動啟動網路，來保護疑似故障的下游系統。


## <a name="additional-resources"></a>其他資源


-   **斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)


>[!div class="step-by-step"]
[上一頁](implement-http-call-retries-exponential-backoff-polly.md)
[下一頁](monitor-app-health.md)
