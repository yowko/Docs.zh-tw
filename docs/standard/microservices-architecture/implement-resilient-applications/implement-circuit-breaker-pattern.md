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
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="aec7b-104">實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="aec7b-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="aec7b-105">如前文所述，您應該處理可能需要在變數一段時間復原，因為當您嘗試連接到遠端服務或資源時可能會發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="aec7b-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="aec7b-106">處理這種類型的錯誤，可以改進的穩定性和恢復功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="aec7b-107">在分散式環境中，呼叫遠端資源和服務可以因為暫時性錯誤，例如低速網路連線和逾時、 失敗或如果資源正在緩慢或暫時無法使用。</span><span class="sxs-lookup"><span data-stu-id="aec7b-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="aec7b-108">這些錯誤通常可以修正本身一段時間之後, 和強大的雲端應用程式應該準備好處理它們使用的策略，例如重試模式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="aec7b-109">不過，有也可以因為非預期的事件，可能需要更長時間來修正錯誤的情況。</span><span class="sxs-lookup"><span data-stu-id="aec7b-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="aec7b-110">這些錯誤的範圍部分連線中斷服務的完整錯誤的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="aec7b-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="aec7b-111">在這些情況下，可能毫無意義的應用程式持續重試不太可能會成功的作業。</span><span class="sxs-lookup"><span data-stu-id="aec7b-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="aec7b-112">相反地，應用程式碼設計應接受作業失敗，並據以處理失敗。</span><span class="sxs-lookup"><span data-stu-id="aec7b-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="aec7b-113">斷路器模式有不同的用途比重試模式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="aec7b-114">重試模式可讓應用程式重試此作業最終會成功且預期的作業。</span><span class="sxs-lookup"><span data-stu-id="aec7b-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="aec7b-115">斷路器模式會防止應用程式執行的作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="aec7b-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="aec7b-116">應用程式可以結合這兩種模式來叫用作業，斷路器透過使用重試模式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="aec7b-117">不過，重試邏輯應該格外斷路器，所傳回的任何例外狀況，而且如果斷路器會指出錯誤並非暫時性，它應該放棄重試次數。</span><span class="sxs-lookup"><span data-stu-id="aec7b-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="aec7b-118">使用 Polly 實作斷路器模式</span><span class="sxs-lookup"><span data-stu-id="aec7b-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="aec7b-119">為實作重試次數，斷路器的建議的方法時，若要善用像 Polly 經過證實的.NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="aec7b-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="aec7b-120">EShopOnContainers 應用程式實作 HTTP 重試時，會使用 Polly 斷路器原則。</span><span class="sxs-lookup"><span data-stu-id="aec7b-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="aec7b-121">事實上，應用程式會將這兩個原則套 ResilientHttpClient 公用程式類別。</span><span class="sxs-lookup"><span data-stu-id="aec7b-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="aec7b-122">每當 ResilientHttpClient 類型的物件使用的 HTTP 要求 （來自 eShopOnContainers) 時，您將會套用這兩個這些原則，但是您無法太加入額外的原則。</span><span class="sxs-lookup"><span data-stu-id="aec7b-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="aec7b-123">唯一新增這裡使用 HTTP 呼叫重試程式碼是程式碼，其中您加入斷路器原則的原則，以使用時，清單結尾的下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="aec7b-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="aec7b-124">程式碼會將原則加入至 HTTP 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="aec7b-125">原則會定義為當程式碼偵測到指定的數目的連續例外狀況 （資料列中例外狀況），會開啟斷路器會傳入 exceptionsAllowedBeforeBreaking 參數 (在本例中為 5)。</span><span class="sxs-lookup"><span data-stu-id="aec7b-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="aec7b-126">循環開啟時，HTTP 要求沒有作用，但是在引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aec7b-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="aec7b-127">斷路器應該也可用來要求重新導向至後援的基礎結構可能發生問題時於用戶端應用程式在不同環境中部署的特定資源或執行 HTTP 呼叫的服務中。</span><span class="sxs-lookup"><span data-stu-id="aec7b-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="aec7b-128">這樣一來，只有您的後端 microservices 但未用戶端應用程式，將會影響在資料中心中斷時用戶端應用程式可以重新導向至後援的服務。</span><span class="sxs-lookup"><span data-stu-id="aec7b-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="aec7b-129">新的原則，來自動化此計劃 Polly[容錯移轉原則](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)案例。</span><span class="sxs-lookup"><span data-stu-id="aec7b-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="aec7b-130">當然，所有這些功能便會管理.NET 程式碼，而不需要它會自動為您管理 azure，與位置透明度內的容錯移轉的情況下。</span><span class="sxs-lookup"><span data-stu-id="aec7b-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="aec7b-131">使用從 eShopOnContainers ResilientHttpClient 公用程式類別</span><span class="sxs-lookup"><span data-stu-id="aec7b-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="aec7b-132">您可以使用 ResilientHttpClient 公用程式類別中的方式類似於您如何使用.NET HttpClient 類別。</span><span class="sxs-lookup"><span data-stu-id="aec7b-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="aec7b-133">在下列範例從 eShopOnContainers MVC web 應用程式 （使用 OrderController OrderingService 代理程式類別） 中，是透過 httpClient 參數的建構函式插入 ResilientHttpClient 物件。</span><span class="sxs-lookup"><span data-stu-id="aec7b-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="aec7b-134">然後此物件用來執行 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="aec7b-134">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="aec7b-135">每當\_apiClient 成員物件，則會在內部使用包裝函式類別和 Polly policiesؙ-重試原則，斷路器原則和任何其他您可能想要從 Polly 原則集合套用的原則。</span><span class="sxs-lookup"><span data-stu-id="aec7b-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="aec7b-136">在 eShopOnContainers 測試重試次數</span><span class="sxs-lookup"><span data-stu-id="aec7b-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="aec7b-137">每當您在 Docker 主機啟動 eShopOnContainers 解決方案，它需要啟動多個容器。</span><span class="sxs-lookup"><span data-stu-id="aec7b-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="aec7b-138">容器的某些較慢啟動並初始化，例如 SQL Server 容器。</span><span class="sxs-lookup"><span data-stu-id="aec7b-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="aec7b-139">特別是第一次部署 eShopOnContainers 應用程式進入 Docker，因為它必須設定映像和資料庫。</span><span class="sxs-lookup"><span data-stu-id="aec7b-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="aec7b-140">某些容器的開始速度比其他人可能會造成其他的服務，一開始擲回 HTTP 例外狀況，即使您將在容器之間的相依性的事實 docker-撰寫層級上, 一節所述。</span><span class="sxs-lookup"><span data-stu-id="aec7b-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="aec7b-141">這些 docker-撰寫容器之間的相依性都只在處理序層級。</span><span class="sxs-lookup"><span data-stu-id="aec7b-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="aec7b-142">容器的進入點程序可能會啟動，但 SQL Server 可能無法供查詢。</span><span class="sxs-lookup"><span data-stu-id="aec7b-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="aec7b-143">此結果會串聯的錯誤，並嘗試使用該特定容器時，應用程式可以取得例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aec7b-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="aec7b-144">您也可能會看到這種類型的錯誤在啟動時應用程式部署到雲端。</span><span class="sxs-lookup"><span data-stu-id="aec7b-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="aec7b-145">在此情況下，orchestrators 可能容器從一個節點或 VM 之間移動 （也就，開始新執行個體） 時的容器數目平衡叢集的節點。</span><span class="sxs-lookup"><span data-stu-id="aec7b-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="aec7b-146">EShopOnContainers 可以解決此問題的方式是使用我們稍早所述的重試模式。</span><span class="sxs-lookup"><span data-stu-id="aec7b-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="aec7b-147">它也是為何，當啟動方案，您可能會發生記錄追蹤或警告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aec7b-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="aec7b-148">「**Polly 的 RetryPolicy 實作重試 1**，由於： System.Net.Http.HttpRequestException： 正在傳送的要求時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="aec7b-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="aec7b-149"> ---&gt;System.Net.Http.CurlException： 無法連接到伺服器\\System.Net.Http.CurlHandler.ThrowIfCURLEError （CURLcode 錯誤） 在 n\\在 n \[...\].</span><span class="sxs-lookup"><span data-stu-id="aec7b-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="aec7b-150">測試 eShopOnContainers 斷路器</span><span class="sxs-lookup"><span data-stu-id="aec7b-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="aec7b-151">有幾個方法，您可以開啟電路，eShopOnContainers 進行測試。</span><span class="sxs-lookup"><span data-stu-id="aec7b-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="aec7b-152">其中一個選項是降低的重試次數為 1，斷路器原則中允許的數目，並重新部署整個方案到 Docker。</span><span class="sxs-lookup"><span data-stu-id="aec7b-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="aec7b-153">單一重試 」，以在部署期間將會失敗的 HTTP 要求的機會，斷路器就會開啟，而且您收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="aec7b-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="aec7b-154">另一個選項是使用排序的微服務中實作自訂的中介軟體。</span><span class="sxs-lookup"><span data-stu-id="aec7b-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="aec7b-155">啟用此中介軟體時，它會攔截所有的 HTTP 要求，並會傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="aec7b-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="aec7b-156">您可以藉由發生失敗的 GET 要求來啟用中介軟體的 URI，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aec7b-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="aec7b-157">取得/失敗</span><span class="sxs-lookup"><span data-stu-id="aec7b-157">GET /failing</span></span>

<span data-ttu-id="aec7b-158">此要求會傳回目前中介軟體的狀態。</span><span class="sxs-lookup"><span data-stu-id="aec7b-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="aec7b-159">如果已啟用中, 介軟體，則要求會傳回狀態碼 500。</span><span class="sxs-lookup"><span data-stu-id="aec7b-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="aec7b-160">如果已停用中介軟體，但沒有回應。</span><span class="sxs-lookup"><span data-stu-id="aec7b-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="aec7b-161">取得/失敗？ 啟用</span><span class="sxs-lookup"><span data-stu-id="aec7b-161">GET /failing?enable</span></span>

<span data-ttu-id="aec7b-162">此要求可讓中介軟體。</span><span class="sxs-lookup"><span data-stu-id="aec7b-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="aec7b-163">取得/失敗？ 停用</span><span class="sxs-lookup"><span data-stu-id="aec7b-163">GET /failing?disable</span></span>

<span data-ttu-id="aec7b-164">此要求會停用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="aec7b-164">This request disables the middleware.</span></span>

<span data-ttu-id="aec7b-165">比方說，應用程式開始執行之後，您就可以提出任何瀏覽器中使用下列 URI 要求啟用的中介軟體。</span><span class="sxs-lookup"><span data-stu-id="aec7b-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="aec7b-166">請注意，排序的微服務會使用連接埠 5102。</span><span class="sxs-lookup"><span data-stu-id="aec7b-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="aec7b-167">http://localhost:5102 / 失敗？ 啟用</span><span class="sxs-lookup"><span data-stu-id="aec7b-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="aec7b-168">然後，您可以檢查的狀態，使用 URI [http://localhost:5102 / 失敗](http://localhost:5100/failing)，如圖 10-4 所示。</span><span class="sxs-lookup"><span data-stu-id="aec7b-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="aec7b-169">**圖 10-4**。</span><span class="sxs-lookup"><span data-stu-id="aec7b-169">**Figure 10-4**.</span></span> <span data-ttu-id="aec7b-170">模擬與 ASP.NET 中介軟體的失敗</span><span class="sxs-lookup"><span data-stu-id="aec7b-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="aec7b-171">此時，順序微服務回應，狀態碼為 500，每當您呼叫叫用它。</span><span class="sxs-lookup"><span data-stu-id="aec7b-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="aec7b-172">中介軟體開始執行之後，您可以嘗試讓 MVC web 應用程式向下的訂單。</span><span class="sxs-lookup"><span data-stu-id="aec7b-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="aec7b-173">要求失敗，因為此電路會開啟。</span><span class="sxs-lookup"><span data-stu-id="aec7b-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="aec7b-174">在下列範例中，您可以看到 MVC web 應用程式有 catch 區塊中的邏輯下訂單。</span><span class="sxs-lookup"><span data-stu-id="aec7b-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="aec7b-175">如果程式碼攔截開啟電路例外狀況，它會顯示使用者易記訊息，告知等待。</span><span class="sxs-lookup"><span data-stu-id="aec7b-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="aec7b-176">此為摘要。</span><span class="sxs-lookup"><span data-stu-id="aec7b-176">Here’s a summary.</span></span> <span data-ttu-id="aec7b-177">重試原則會嘗試對 HTTP 要求和取得 HTTP 錯誤數次。</span><span class="sxs-lookup"><span data-stu-id="aec7b-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="aec7b-178">當嘗試次數達到設定的最大數目 （在此情況下，5） 的斷路器原則時，應用程式會擲回 BrokenCircuitException。</span><span class="sxs-lookup"><span data-stu-id="aec7b-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="aec7b-179">結果是易記的訊息，如圖 10-5 所示。</span><span class="sxs-lookup"><span data-stu-id="aec7b-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="aec7b-180">**圖 10-5**。</span><span class="sxs-lookup"><span data-stu-id="aec7b-180">**Figure 10-5**.</span></span> <span data-ttu-id="aec7b-181">斷路器 ui 傳回錯誤</span><span class="sxs-lookup"><span data-stu-id="aec7b-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="aec7b-182">您可以實作不同的邏輯時開啟電路。</span><span class="sxs-lookup"><span data-stu-id="aec7b-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="aec7b-183">或如果沒有後援資料中心或多餘的後端系統，您可以嘗試對不同的後端微服務的 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="aec7b-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="aec7b-184">最後，CircuitBreakerPolicy 另一個可能性是使用隔離 （這樣會強制開啟並保持開啟循環） 和重設 （這會關閉它一次）。</span><span class="sxs-lookup"><span data-stu-id="aec7b-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="aec7b-185">這些可以用來建立原則會隔離和重設直接叫用的公用程式 HTTP 端點。</span><span class="sxs-lookup"><span data-stu-id="aec7b-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="aec7b-186">HTTP 端點也可以使用，適當地保護暫時隔離的下游系統，例如當您想要將它升級生產環境中。</span><span class="sxs-lookup"><span data-stu-id="aec7b-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="aec7b-187">或其無法成為以手動方式來保護您懷疑被判定為失敗的下游系統循環。</span><span class="sxs-lookup"><span data-stu-id="aec7b-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="aec7b-188">抖動策略加入重試原則</span><span class="sxs-lookup"><span data-stu-id="aec7b-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="aec7b-189">規則的重試原則可能會影響您的系統在高並行存取，以及延展性，並在高度競爭的情況下。</span><span class="sxs-lookup"><span data-stu-id="aec7b-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="aec7b-190">若要克服類似來自部分的中斷發生的許多用戶端重試次數的尖峰，良好的因應措施是抖動策略加入重試演算法/原則。</span><span class="sxs-lookup"><span data-stu-id="aec7b-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="aec7b-191">這可以改善整體系統效能的端對端加入指數型輪詢的隨機性。</span><span class="sxs-lookup"><span data-stu-id="aec7b-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="aec7b-192">這向外擴散如果看到爆增情形發生問題時。</span><span class="sxs-lookup"><span data-stu-id="aec7b-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="aec7b-193">當您使用 Polly 時，程式碼來實作抖動可能看起來像下列的範例：</span><span class="sxs-lookup"><span data-stu-id="aec7b-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="aec7b-194">其他資源</span><span class="sxs-lookup"><span data-stu-id="aec7b-194">Additional resources</span></span>

-   <span data-ttu-id="aec7b-195">**重試模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="aec7b-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="aec7b-196">**連接恢復功能**(Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="aec7b-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="aec7b-197">**Polly** （.NET 恢復功能和暫時性錯誤處理程式庫） [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="aec7b-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="aec7b-198">**斷路器模式**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="aec7b-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="aec7b-199">**Marc Brooker。抖動： 讓事情更加具有隨機性**https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="aec7b-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="aec7b-200">[上一個](implement-http-call-retries-exponential-backoff-polly.md) [下一步] (監視的應用程式-health.md)</span><span class="sxs-lookup"><span data-stu-id="aec7b-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>
