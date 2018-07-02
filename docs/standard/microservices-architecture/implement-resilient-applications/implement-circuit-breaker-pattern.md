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
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="7766e-103">實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="7766e-103">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="7766e-104">如稍早所述，您應該處理復原所需的時間可能不確定的錯誤，當您嘗試連接到遠端服務或資源時，可能會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="7766e-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="7766e-105">處理這種類型的錯誤可改善應用程式的穩定性和復原。</span><span class="sxs-lookup"><span data-stu-id="7766e-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="7766e-106">在分散式環境中，呼叫遠端資源和服務可能會由於暫時性錯誤 (例如網路連線太慢和逾時)，或是資源變慢或暫時無法使用而失敗。</span><span class="sxs-lookup"><span data-stu-id="7766e-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="7766e-107">這些錯誤通常會在很短的時間內自我修正，而且強大的雲端應用程式應該能夠使用重試模式之類的策略來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="7766e-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="7766e-108">不過有時候，錯誤是由於非預期的事件所致，可能需要更長時間來修正。</span><span class="sxs-lookup"><span data-stu-id="7766e-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="7766e-109">這些錯誤的嚴重性可能從失去部分連線到服務完全失敗。</span><span class="sxs-lookup"><span data-stu-id="7766e-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="7766e-110">在這些情況下，讓應用程式持續重試不太可能會成功的作業可能毫無意義。</span><span class="sxs-lookup"><span data-stu-id="7766e-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="7766e-111">相反地，應用程式應該設計成接受作業失敗並據以處理失敗。</span><span class="sxs-lookup"><span data-stu-id="7766e-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="7766e-112">斷路器模式的目的與重試模式不同。</span><span class="sxs-lookup"><span data-stu-id="7766e-112">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="7766e-113">重試模式可讓應用程式重試作業，期望該作業最終會成功。</span><span class="sxs-lookup"><span data-stu-id="7766e-113">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="7766e-114">斷路器模式可防止應用程式執行可能失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="7766e-114">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="7766e-115">應用程式可以結合這兩種模式，使用重試模式透過斷路器來叫用作業。</span><span class="sxs-lookup"><span data-stu-id="7766e-115">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="7766e-116">不過，重試邏輯應該會受到斷路器所傳回之任何例外狀況的影響，而且如果斷路器指出錯誤不是暫時的，就應該放棄重試嘗試。</span><span class="sxs-lookup"><span data-stu-id="7766e-116">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="7766e-117">使用 Polly 實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="7766e-117">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="7766e-118">實作重試時，斷路器的建議方法是利用經過實證的 .NET 程式庫，例如 Polly。</span><span class="sxs-lookup"><span data-stu-id="7766e-118">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="7766e-119">實作 HTTP 重試時，eShopOnContainers 應用程式會使用 Polly 斷路器原則。</span><span class="sxs-lookup"><span data-stu-id="7766e-119">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="7766e-120">事實上，應用程式會將這兩個原則套用至 ResilientHttpClient 公用程式類別。</span><span class="sxs-lookup"><span data-stu-id="7766e-120">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="7766e-121">只要您針對 HTTP 要求 (來自 eShopOnContainers) 使用 ResilientHttpClient 類型的物件，就都會套用這兩個原則，但您也可以新增其他原則。</span><span class="sxs-lookup"><span data-stu-id="7766e-121">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="7766e-122">此處用於 HTTP 呼叫重試之程式碼的唯一新增項目，就是用來將斷路器原則新增至所要使用之原則清單的程式碼，如下列程式碼結尾所示：</span><span class="sxs-lookup"><span data-stu-id="7766e-122">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="7766e-123">此程式碼會將原則新增至 HTTP 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="7766e-123">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="7766e-124">該原則會定義斷路器在程式碼偵測到指定的連續例外狀況 (一連串例外狀況) 數目時開啟，如同 exceptionsAllowedBeforeBreaking 參數中傳入的數目所指定 (在本例中為 5)。</span><span class="sxs-lookup"><span data-stu-id="7766e-124">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="7766e-125">當網路開啟時，HTTP 要求沒有作用，而是會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7766e-125">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="7766e-126">如果您部署在與執行 HTTP 呼叫的用戶端應用程式或服務不同之環境中的特定資源發生問題，也應該使用斷路器將要求重新導向至後援基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7766e-126">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="7766e-127">這樣一來，如果資料中心的中斷只會影響您的後端微服務，但不會影響您的用戶端應用程式，用戶端應用程式就可以重新導向至後援服務。</span><span class="sxs-lookup"><span data-stu-id="7766e-127">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="7766e-128">Polly 正在規劃新的原則來自動化此[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。</span><span class="sxs-lookup"><span data-stu-id="7766e-128">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="7766e-129">當然，相對於由 Azure 為您自動管理，上述所有功能適用於從 .NET 程式碼管理容錯移轉的情況，並提供位置透明度。</span><span class="sxs-lookup"><span data-stu-id="7766e-129">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="7766e-130">從 eShopOnContainers 使用 ResilientHttpClient 公用程式類別</span><span class="sxs-lookup"><span data-stu-id="7766e-130">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="7766e-131">您可以透過類似 .NET HttpClient 類別的使用方式，來使用 ResilientHttpClient 公用程式類別。</span><span class="sxs-lookup"><span data-stu-id="7766e-131">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="7766e-132">在下列 eShopOnContainers MVC Web 應用程式範例中 (OrderController 所使用的 OrderingService 代理程式類別)，會透過建構函式的 httpClient 參數來插入 ResilientHttpClient 物件。</span><span class="sxs-lookup"><span data-stu-id="7766e-132">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="7766e-133">然後使用此物件來執行 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="7766e-133">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="7766e-134">只要使用 \_apiClient 成員物件，它就會在內部搭配使用包裝函式類別與 Polly 原則：重試原則、斷路器原則，以及您想要從 Polly 原則集合套用的任何其他原則。</span><span class="sxs-lookup"><span data-stu-id="7766e-134">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="7766e-135">在 eShopOnContainers 中測試重試</span><span class="sxs-lookup"><span data-stu-id="7766e-135">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="7766e-136">只要您在 Docker 主機中啟動 eShopOnContainers 解決方案，就需要啟動多個容器。</span><span class="sxs-lookup"><span data-stu-id="7766e-136">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="7766e-137">某些容器的啟動和初始化速度會比較慢，例如 SQL Server 容器。</span><span class="sxs-lookup"><span data-stu-id="7766e-137">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="7766e-138">特別是當您第一次將 eShopOnContainers 應用程式部署至 Docker 時，因為需要設定映像和資料庫。</span><span class="sxs-lookup"><span data-stu-id="7766e-138">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="7766e-139">某些容器的啟動速度會比其他容器慢，而導致其餘服務一開始擲回 HTTP 例外狀況，即使在 docker-compose 層級設定容器之間的相依性亦然，如先前章節所述。</span><span class="sxs-lookup"><span data-stu-id="7766e-139">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="7766e-140">容器之間的這些 docker-compose 相依性只會在處理序層。</span><span class="sxs-lookup"><span data-stu-id="7766e-140">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="7766e-141">容器的進入點處理序可能已啟動，但 SQL Server 可能尚未就緒而無法查詢。</span><span class="sxs-lookup"><span data-stu-id="7766e-141">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="7766e-142">結果可能是一連串的錯誤，而且嘗試取用該特定容器時，應用程式可能會收到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7766e-142">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="7766e-143">當應用程式正在部署至雲端時，您也可能會在啟動時看到這種錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="7766e-143">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="7766e-144">在此情況下，平衡叢集節點之間的容器數目時，協調器可能會將容器從一個節點或 VM 移至另一個 (也就是啟動新的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="7766e-144">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="7766e-145">eShopOnContainers 解決這個問題的方法是使用稍早所述的重試模式。</span><span class="sxs-lookup"><span data-stu-id="7766e-145">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="7766e-146">它也是為什麼在啟動解決方案時，您可能會收到類似如下的記錄追蹤或警告：</span><span class="sxs-lookup"><span data-stu-id="7766e-146">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="7766e-147">**已使用 Polly 的重試原則實作重試 1**，原因如下：System.Net.Http.HttpRequestException：傳送要求時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7766e-147">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="7766e-148"> ---&gt; System.Net.Http.CurlException：無法連接到伺服器\\n 於 System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode 錯誤)\\n 於 \[...\]。</span><span class="sxs-lookup"><span data-stu-id="7766e-148"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="7766e-149">在 eShopOnContainers 中測試斷路器</span><span class="sxs-lookup"><span data-stu-id="7766e-149">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="7766e-150">您可以透過幾個方法來開啟網路，並使用 eShopOnContainers 進行測試。</span><span class="sxs-lookup"><span data-stu-id="7766e-150">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="7766e-151">一個選項是將斷路器原則中允許的重試次數減少為 1，然後將整個解決方案重新部署至 Docker。</span><span class="sxs-lookup"><span data-stu-id="7766e-151">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="7766e-152">使用單一重試，HTTP 要求很有可能會在部署期間失敗，此時斷路器會開啟，而且您會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="7766e-152">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="7766e-153">另一個選項是使用在 `Basket` 微服務中實作的自訂中介軟體。</span><span class="sxs-lookup"><span data-stu-id="7766e-153">Another option is to use custom middleware that is implemented in the `Basket` microservice.</span></span> <span data-ttu-id="7766e-154">啟用此中介軟體時，它會攔截所有的 HTTP 要求並傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="7766e-154">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="7766e-155">您可以藉由提出失敗 URI 的 GET 要求來啟用中介軟體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7766e-155">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="7766e-156">GET /failing</span><span class="sxs-lookup"><span data-stu-id="7766e-156">GET /failing</span></span>

<span data-ttu-id="7766e-157">此要求會傳回中介軟體的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="7766e-157">This request returns the current state of the middleware.</span></span> <span data-ttu-id="7766e-158">如果啟用中介軟體，要求會傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="7766e-158">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="7766e-159">如果停用中介軟體，則沒有回應。</span><span class="sxs-lookup"><span data-stu-id="7766e-159">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="7766e-160">GET /failing?enable</span><span class="sxs-lookup"><span data-stu-id="7766e-160">GET /failing?enable</span></span>

<span data-ttu-id="7766e-161">此要求會啟用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="7766e-161">This request enables the middleware.</span></span>

-   <span data-ttu-id="7766e-162">GET /failing?disable</span><span class="sxs-lookup"><span data-stu-id="7766e-162">GET /failing?disable</span></span>

<span data-ttu-id="7766e-163">此要求會停用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="7766e-163">This request disables the middleware.</span></span>

<span data-ttu-id="7766e-164">例如，應用程式開始執行之後，您可以在任何瀏覽器中使用下列 URI 提出要求，來啟用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="7766e-164">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="7766e-165">請注意，訂購微服務會使用連接埠 5103。</span><span class="sxs-lookup"><span data-stu-id="7766e-165">Note that the ordering microservice uses port 5103.</span></span>

http://localhost:5103/failing?enable

<span data-ttu-id="7766e-166">您可以接著使用 URI [http://localhost:5103/failing](http://localhost:5103/failing) 來檢查狀態，如圖 10-4 所示。</span><span class="sxs-lookup"><span data-stu-id="7766e-166">You can then check the status using the URI [http://localhost:5103/failing](http://localhost:5103/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="7766e-167">**圖 10-4**：</span><span class="sxs-lookup"><span data-stu-id="7766e-167">**Figure 10-4**.</span></span> <span data-ttu-id="7766e-168">檢查「失敗」的 ASP.NET 中介軟體狀態 (在本例中已停用)</span><span class="sxs-lookup"><span data-stu-id="7766e-168">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="7766e-169">此時，只要您呼叫/叫用它，購物籃微服務就會以狀態碼 500 回應。</span><span class="sxs-lookup"><span data-stu-id="7766e-169">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="7766e-170">中介軟體開始執行之後，您可以嘗試從 MVC Web 應用程式下訂單。</span><span class="sxs-lookup"><span data-stu-id="7766e-170">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="7766e-171">由於要求失敗，因此會開啟網路。</span><span class="sxs-lookup"><span data-stu-id="7766e-171">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="7766e-172">在下列範例中，您可以看到 MVC Web 應用程式在下訂單的邏輯中有一個 catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="7766e-172">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="7766e-173">如果程式碼攔截到開路例外狀況，它會向使用者顯示易懂訊息以通知他們等候。</span><span class="sxs-lookup"><span data-stu-id="7766e-173">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="7766e-174">以下摘要說明。</span><span class="sxs-lookup"><span data-stu-id="7766e-174">Here’s a summary.</span></span> <span data-ttu-id="7766e-175">重試原則嘗試提出 HTTP 要求幾次，並收到 HTTP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7766e-175">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="7766e-176">當嘗試次數達到針對斷路器原則設定的最大數目時 (在本例中為 5)，應用程式會擲回 BrokenCircuitException。</span><span class="sxs-lookup"><span data-stu-id="7766e-176">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="7766e-177">結果是易懂訊息，如圖 10-5 所示。</span><span class="sxs-lookup"><span data-stu-id="7766e-177">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="7766e-178">**圖 10-5**：</span><span class="sxs-lookup"><span data-stu-id="7766e-178">**Figure 10-5**.</span></span> <span data-ttu-id="7766e-179">斷路器傳回錯誤至 UI</span><span class="sxs-lookup"><span data-stu-id="7766e-179">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="7766e-180">您可以實作何時開路的不同邏輯。</span><span class="sxs-lookup"><span data-stu-id="7766e-180">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="7766e-181">或者，如有後援資料中心或備援後端系統，您可以嘗試對不同後端微服務提出 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="7766e-181">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="7766e-182">最後，CircuitBreakerPolicy 的另一個可能性是使用 Isolate (這會強制開啟並保持開啟網路) 和 Reset (這會再次將它關閉)。</span><span class="sxs-lookup"><span data-stu-id="7766e-182">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="7766e-183">這些可用來建置公用程式 HTTP 端點，以直接在原則上叫用 Isolate 和 Reset。</span><span class="sxs-lookup"><span data-stu-id="7766e-183">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="7766e-184">您也可以在生產環境中使用這類 HTTP 端點 (經過適當保護)，來暫時隔離下游系統，例如當您想要將它升級時。</span><span class="sxs-lookup"><span data-stu-id="7766e-184">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="7766e-185">或者，它可以手動啟動網路，來保護疑似故障的下游系統。</span><span class="sxs-lookup"><span data-stu-id="7766e-185">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="7766e-186">將 Jitter 策略新增至重試原則</span><span class="sxs-lookup"><span data-stu-id="7766e-186">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="7766e-187">如果發生高並行和延展性以及高競爭的情況，定期重試原則可能會影響您的系統。</span><span class="sxs-lookup"><span data-stu-id="7766e-187">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="7766e-188">若要解決來自許多用戶端的類似重試因部分中斷而達到最高的問題，一個很好的解決方法是將 Jitter 策略新增至重試演算法/原則。</span><span class="sxs-lookup"><span data-stu-id="7766e-188">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="7766e-189">這可以透過將隨機性加入指數輪詢，來改善端對端系統的整體效能。</span><span class="sxs-lookup"><span data-stu-id="7766e-189">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="7766e-190">發生問題時，突然增加的情況會擴散。</span><span class="sxs-lookup"><span data-stu-id="7766e-190">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="7766e-191">使用 Polly 時，要實作 Jitter 的程式碼可能會如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7766e-191">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="7766e-192">其他資源</span><span class="sxs-lookup"><span data-stu-id="7766e-192">Additional resources</span></span>

-   <span data-ttu-id="7766e-193">**重試模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="7766e-193">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="7766e-194">**恢復連線** (Entity Framework Core)[*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="7766e-194">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="7766e-195">**Polly** (.NET 復原和暫時性錯誤處理程式庫) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="7766e-195">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="7766e-196">**斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="7766e-196">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="7766e-197">**Marc Brooker：Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="7766e-197">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7766e-198">[上一頁](implement-http-call-retries-exponential-backoff-polly.md)
[下一頁](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="7766e-198">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>
