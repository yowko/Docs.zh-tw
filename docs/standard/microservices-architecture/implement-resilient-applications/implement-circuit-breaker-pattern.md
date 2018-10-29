---
title: 實作斷路器模式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作斷路器模式作為 Http 重試的互補系統
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
ms.openlocfilehash: b961ebd186953e614658915c7246e1c83c40e7e9
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453147"
---
# <a name="implement-the-circuit-breaker-pattern"></a><span data-ttu-id="25806-103">實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="25806-103">Implement the Circuit Breaker pattern</span></span>

<span data-ttu-id="25806-104">如稍早所述，您應該處理復原所需的時間可能不確定的錯誤，當您嘗試連接到遠端服務或資源時，可能會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="25806-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="25806-105">處理這種類型的錯誤可改善應用程式的穩定性和復原。</span><span class="sxs-lookup"><span data-stu-id="25806-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="25806-106">在分散式環境中，呼叫遠端資源和服務可能會由於暫時性錯誤 (例如網路連線太慢和逾時)，或是資源回應緩慢或暫時無法使用而失敗。</span><span class="sxs-lookup"><span data-stu-id="25806-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are responding slowly or are temporarily unavailable.</span></span> <span data-ttu-id="25806-107">這些錯誤通常會在很短的時間內自我修正，而且強大的雲端應用程式應該能夠使用「重試模式」之類的策略來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="25806-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the "Retry pattern".</span></span> 

<span data-ttu-id="25806-108">不過有時候，錯誤是由於非預期的事件所致，可能需要更長時間來修正。</span><span class="sxs-lookup"><span data-stu-id="25806-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="25806-109">這些錯誤的嚴重性可能從失去部分連線到服務完全失敗。</span><span class="sxs-lookup"><span data-stu-id="25806-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="25806-110">在這些情況下，讓應用程式持續重試不太可能會成功的作業可能毫無意義。</span><span class="sxs-lookup"><span data-stu-id="25806-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> 

<span data-ttu-id="25806-111">相反地，應用程式應該設計成接受作業失敗並據以處理失敗。</span><span class="sxs-lookup"><span data-stu-id="25806-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="25806-112">隨意使用 Http 重試可能會導致在您自己的軟體內產生拒絕服務 ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) 的攻擊。</span><span class="sxs-lookup"><span data-stu-id="25806-112">Using Http retries carelessly could result in creating a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack within your own software.</span></span> <span data-ttu-id="25806-113">由於微服務失敗或執行緩慢，因此多個用戶端可能會重複重試失敗的要求。</span><span class="sxs-lookup"><span data-stu-id="25806-113">As a microservice fails or performs slowly, multiple clients might repeatedly retry failed requests.</span></span> <span data-ttu-id="25806-114">這會帶來以失敗服務為目標的流量呈指數增加的危險風險。</span><span class="sxs-lookup"><span data-stu-id="25806-114">That creates a dangerous risk of exponentially increasing traffic targeted at the failing service.</span></span>

<span data-ttu-id="25806-115">因此，您需要某種形式的防禦屏障，在不值得繼續嘗試時停止多餘的要求。</span><span class="sxs-lookup"><span data-stu-id="25806-115">Therefore, you need some kind of defense barrier so that excessive requests stop when it is not worth keeping trying.</span></span> <span data-ttu-id="25806-116">該防禦屏障正是斷路器。</span><span class="sxs-lookup"><span data-stu-id="25806-116">That defense barrier is precisely the circuit breaker.</span></span>

<span data-ttu-id="25806-117">斷路器模式的目的與「重試模式」不同。</span><span class="sxs-lookup"><span data-stu-id="25806-117">The Circuit Breaker pattern has a different purpose than the "Retry pattern".</span></span> <span data-ttu-id="25806-118">「重試模式」可讓應用程式重試作業，期望該作業最終會成功。</span><span class="sxs-lookup"><span data-stu-id="25806-118">The "Retry pattern" enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="25806-119">斷路器模式可防止應用程式執行可能失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="25806-119">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="25806-120">應用程式可以結合這兩種模式。</span><span class="sxs-lookup"><span data-stu-id="25806-120">An application can combine these two patterns.</span></span> <span data-ttu-id="25806-121">不過，重試邏輯應該會受到斷路器所傳回之任何例外狀況的影響，而且如果斷路器指出錯誤不是暫時的，就應該放棄重試嘗試。</span><span class="sxs-lookup"><span data-stu-id="25806-121">However, the retry logic should be sensitive to any exception returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implement-circuit-breaker-pattern-with-httpclientfactory-and-polly"></a><span data-ttu-id="25806-122">使用 HttpClientFactory 和 Polly 實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="25806-122">Implement Circuit Breaker pattern with HttpClientFactory and Polly</span></span>

<span data-ttu-id="25806-123">實作重試時，斷路器的建議方法是利用經過實證的 .NET 程式庫，例如 Polly 及其與 HttpClientFactory 的原生整合。</span><span class="sxs-lookup"><span data-stu-id="25806-123">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly and its native integration with HttpClientFactory.</span></span>

<span data-ttu-id="25806-124">將斷路器原則新增至您的 HttpClientFactory 傳出中介軟體管線，就像是將單一程式碼片段增量新增至使用 HttpClientFactory 時已有的程式碼一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="25806-124">Adding a circuit breaker policy into your HttpClientFactory outgoing middleware pipeline is as simple as adding a single incremental piece of code to what you already have when using HttpClientFactory.</span></span>

<span data-ttu-id="25806-125">此處用於 HTTP 呼叫重試之程式碼的唯一新增項目，就是用來將斷路器原則新增至所要使用之原則清單的程式碼，如下列程式碼增量所示 (屬於 ConfigureServices() 方法一部分)。</span><span class="sxs-lookup"><span data-stu-id="25806-125">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown in the following incremental code, part of the ConfigureServices() method.</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to 5 minutes
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="25806-126">`AddPolicyHandler()` 方法會將原則新增至您將使用的 HttpClient 物件。</span><span class="sxs-lookup"><span data-stu-id="25806-126">The `AddPolicyHandler()`method is what adds policies to the HttpClient objects you will use.</span></span> <span data-ttu-id="25806-127">在本例中，它會為斷路器新增 Polly 原則。</span><span class="sxs-lookup"><span data-stu-id="25806-127">In this case, it is adding a Polly policy for a circuit breaker.</span></span>

<span data-ttu-id="25806-128">為了有更模組化的方法，可在名為 GetCircuitBreakerPolicy() 的個別方法中定義斷路器原則，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="25806-128">In order to have a more modular approach, the Circuit Breaker Policy is defined in a separate method named GetCircuitBreakerPolicy(), as the following code.</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

<span data-ttu-id="25806-129">在上述程式碼範例中，斷路器原則設定為在重試 Http 要求時，若連續五次失敗，則會中斷或開啟網路。</span><span class="sxs-lookup"><span data-stu-id="25806-129">In the code example above, the circuit breaker policy is configured so it breaks or opens the circuit when there have been five consecutive faults when retrying the Http requests.</span></span> <span data-ttu-id="25806-130">發生此情況時，網路會中斷 30 秒：在這段期間，斷路器會立即使呼叫失敗，而不是實際發出。</span><span class="sxs-lookup"><span data-stu-id="25806-130">When that happens, the circuit will break for 30 seconds: in that period, calls will be failed immediately by the circuit-breaker rather than actually be placed.</span></span>  <span data-ttu-id="25806-131">原則會自動將[相關的例外狀況和 HTTP 狀態碼](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults)解釋為錯誤。</span><span class="sxs-lookup"><span data-stu-id="25806-131">The policy automatically interprets [relevant exceptions and HTTP status codes](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1#handle-transient-faults) as faults.</span></span>  

<span data-ttu-id="25806-132">如果您部署在與執行 HTTP 呼叫的用戶端應用程式或服務不同之環境中的特定資源發生問題，也應該使用斷路器將要求重新導向至後援基礎結構。</span><span class="sxs-lookup"><span data-stu-id="25806-132">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you had issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="25806-133">這樣一來，如果資料中心的中斷只會影響您的後端微服務，但不會影響您的用戶端應用程式，用戶端應用程式就可以重新導向至後援服務。</span><span class="sxs-lookup"><span data-stu-id="25806-133">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="25806-134">Polly 正在規劃新的原則來自動化此[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。</span><span class="sxs-lookup"><span data-stu-id="25806-134">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span> 

<span data-ttu-id="25806-135">相對於由 Azure 為您自動管理，上述所有功能適用於從 .NET 程式碼管理容錯移轉的情況，並提供位置透明度。</span><span class="sxs-lookup"><span data-stu-id="25806-135">All those features are for cases where you're managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span> 

<span data-ttu-id="25806-136">從使用觀點來看，使用 HttpClient 時，不需要在此新增任何項目，因為使用 HttpClient 時的程式碼與 HttpClientFactory 相同，如先前章節所示。</span><span class="sxs-lookup"><span data-stu-id="25806-136">From a usage point of view, when using HttpClient, there’s no need to add anything new here because the code is the same than when using HttpClient with HttpClientFactory, as shown in previous sections.</span></span> 

## <a name="testing-http-retries-and-circuit-breakers-in-eshoponcontainers"></a><span data-ttu-id="25806-137">在 eShopOnContainers 中測試 Http 重試和斷路器</span><span class="sxs-lookup"><span data-stu-id="25806-137">Testing Http retries and circuit breakers in eShopOnContainers</span></span>

<span data-ttu-id="25806-138">只要您在 Docker 主機中啟動 eShopOnContainers 解決方案，就需要啟動多個容器。</span><span class="sxs-lookup"><span data-stu-id="25806-138">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="25806-139">某些容器的啟動和初始化速度會比較慢，例如 SQL Server 容器。</span><span class="sxs-lookup"><span data-stu-id="25806-139">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="25806-140">特別是當您第一次將 eShopOnContainers 應用程式部署至 Docker 時，因為需要設定映像和資料庫。</span><span class="sxs-lookup"><span data-stu-id="25806-140">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="25806-141">某些容器的啟動速度會比其他容器慢，而導致其餘服務一開始擲回 HTTP 例外狀況，即使在 docker-compose 層級設定容器之間的相依性亦然，如先前章節所述。</span><span class="sxs-lookup"><span data-stu-id="25806-141">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="25806-142">容器之間的這些 docker-compose 相依性只會在處理序層。</span><span class="sxs-lookup"><span data-stu-id="25806-142">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="25806-143">容器的進入點處理序可能已啟動，但 SQL Server 可能尚未就緒而無法查詢。</span><span class="sxs-lookup"><span data-stu-id="25806-143">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="25806-144">結果可能是一連串的錯誤，而且嘗試取用該特定容器時，應用程式可能會收到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="25806-144">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span> 

<span data-ttu-id="25806-145">當應用程式正在部署至雲端時，您也可能會在啟動時看到這種錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="25806-145">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="25806-146">在此情況下，平衡叢集節點之間的容器數目時，協調器可能會將容器從一個節點或 VM 移至另一個 (也就是啟動新的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="25806-146">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="25806-147">啟動所有容器時，'eShopOnContainers' 解決這些問題的方法是使用稍早所述的重試模式。</span><span class="sxs-lookup"><span data-stu-id="25806-147">The way 'eShopOnContainers' solves those issues when starting all the containers is by using the Retry pattern illustrated earlier.</span></span> 

### <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="25806-148">在 eShopOnContainers 中測試斷路器</span><span class="sxs-lookup"><span data-stu-id="25806-148">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="25806-149">您可以透過幾個方法來中斷/開啟網路，並使用 eShopOnContainers 進行測試。</span><span class="sxs-lookup"><span data-stu-id="25806-149">There are a few ways you can break/open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="25806-150">一個選項是將斷路器原則中允許的重試次數減少為 1，然後將整個解決方案重新部署至 Docker。</span><span class="sxs-lookup"><span data-stu-id="25806-150">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="25806-151">使用單一重試，HTTP 要求很有可能會在部署期間失敗，此時斷路器會開啟，而且您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="25806-151">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="25806-152">另一個選項是使用在購物籃微服務中實作的自訂中介軟體。</span><span class="sxs-lookup"><span data-stu-id="25806-152">Another option is to use custom middleware that is implemented in the Basket microservice.</span></span> <span data-ttu-id="25806-153">啟用此中介軟體時，它會攔截所有的 HTTP 要求並傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="25806-153">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="25806-154">您可以藉由提出失敗 URI 的 GET 要求來啟用中介軟體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="25806-154">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

- `GET http://localhost:5103/failing`

<span data-ttu-id="25806-155">此要求會傳回中介軟體的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="25806-155">This request returns the current state of the middleware.</span></span> <span data-ttu-id="25806-156">如果啟用中介軟體，要求會傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="25806-156">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="25806-157">如果停用中介軟體，則沒有回應。</span><span class="sxs-lookup"><span data-stu-id="25806-157">If the middleware is disabled, there is no response.</span></span> 

- `GET http://localhost:5103/failing?enable`

<span data-ttu-id="25806-158">此要求會啟用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="25806-158">This request enables the middleware.</span></span> 

- `GET http://localhost:5103/failing?disable`

<span data-ttu-id="25806-159">此要求會停用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="25806-159">This request disables the middleware.</span></span> 

<span data-ttu-id="25806-160">例如，應用程式開始執行之後，您可以在任何瀏覽器中使用下列 URI 提出要求，來啟用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="25806-160">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="25806-161">請注意，訂購微服務會使用連接埠 5103。</span><span class="sxs-lookup"><span data-stu-id="25806-161">Note that the ordering microservice uses port 5103.</span></span>

`http://localhost:5103/failing?enable` 

<span data-ttu-id="25806-162">您可以接著使用 URI `http://localhost:5103/failing` 來檢查狀態，如圖 10-4 所示。</span><span class="sxs-lookup"><span data-stu-id="25806-162">You can then check the status using the URI `http://localhost:5103/failing`, as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="25806-163">**圖 10-4**：</span><span class="sxs-lookup"><span data-stu-id="25806-163">**Figure 10-4**.</span></span> <span data-ttu-id="25806-164">檢查「失敗」的 ASP.NET 中介軟體狀態 (在本例中已停用)</span><span class="sxs-lookup"><span data-stu-id="25806-164">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="25806-165">此時，只要您呼叫/叫用它，購物籃微服務就會以狀態碼 500 回應。</span><span class="sxs-lookup"><span data-stu-id="25806-165">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="25806-166">中介軟體開始執行之後，您可以嘗試從 MVC Web 應用程式下訂單。</span><span class="sxs-lookup"><span data-stu-id="25806-166">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="25806-167">由於要求失敗，因此會開啟網路。</span><span class="sxs-lookup"><span data-stu-id="25806-167">Because the requests fail, the circuit will open.</span></span> 

<span data-ttu-id="25806-168">在下列範例中，您可以看到 MVC Web 應用程式在下訂單的邏輯中有一個 catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="25806-168">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span>  <span data-ttu-id="25806-169">如果程式碼攔截到開路例外狀況，它會向使用者顯示易懂訊息以通知他們等候。</span><span class="sxs-lookup"><span data-stu-id="25806-169">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="25806-170">以下摘要說明。</span><span class="sxs-lookup"><span data-stu-id="25806-170">Here’s a summary.</span></span> <span data-ttu-id="25806-171">重試原則嘗試提出 HTTP 要求幾次，並收到 HTTP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="25806-171">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="25806-172">當重試次數達到針對斷路器原則設定的最大數目時 (在本例中為 5)，應用程式會擲回 BrokenCircuitException。</span><span class="sxs-lookup"><span data-stu-id="25806-172">When the number of retries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="25806-173">結果是易懂訊息，如圖 10-5 所示。</span><span class="sxs-lookup"><span data-stu-id="25806-173">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="25806-174">**圖 10-5**：</span><span class="sxs-lookup"><span data-stu-id="25806-174">**Figure 10-5**.</span></span> <span data-ttu-id="25806-175">斷路器傳回錯誤至 UI</span><span class="sxs-lookup"><span data-stu-id="25806-175">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="25806-176">您可以實作何時開啟/中斷網路的不同邏輯。</span><span class="sxs-lookup"><span data-stu-id="25806-176">You can implement different logic for when to open/break the circuit.</span></span> <span data-ttu-id="25806-177">或者，如有後援資料中心或備援後端系統，您可以嘗試對不同後端微服務提出 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="25806-177">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span> 

<span data-ttu-id="25806-178">最後，`CircuitBreakerPolicy` 的另一個可能性是使用 `Isolate` (這會強制開啟並保持開啟網路) 和 `Reset` (這會再次將它關閉)。</span><span class="sxs-lookup"><span data-stu-id="25806-178">Finally, another possibility for the `CircuitBreakerPolicy` is to use `Isolate` (which forces open and holds open the circuit) and `Reset` (which closes it again).</span></span> <span data-ttu-id="25806-179">這些可用來建置公用程式 HTTP 端點，以直接在原則上叫用 Isolate 和 Reset。</span><span class="sxs-lookup"><span data-stu-id="25806-179">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span>  <span data-ttu-id="25806-180">您也可以在生產環境中使用這類 HTTP 端點 (經過適當保護)，來暫時隔離下游系統，例如當您想要將它升級時。</span><span class="sxs-lookup"><span data-stu-id="25806-180">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="25806-181">或者，它可以手動啟動網路，來保護疑似故障的下游系統。</span><span class="sxs-lookup"><span data-stu-id="25806-181">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>


## <a name="additional-resources"></a><span data-ttu-id="25806-182">其他資源</span><span class="sxs-lookup"><span data-stu-id="25806-182">Additional resources</span></span>


-   <span data-ttu-id="25806-183">**斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="25806-183">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="25806-184">[上一頁](implement-http-call-retries-exponential-backoff-polly.md)
[下一頁](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="25806-184">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
