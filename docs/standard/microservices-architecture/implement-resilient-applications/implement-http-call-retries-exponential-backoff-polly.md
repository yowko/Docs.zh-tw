---
title: "利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 122f617874188d3bffe689d6b3cf7d7249c59c3b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="3a32c-104">利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試</span><span class="sxs-lookup"><span data-stu-id="3a32c-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="3a32c-105">使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly](https://github.com/App-vNext/Polly) 程式庫。</span><span class="sxs-lookup"><span data-stu-id="3a32c-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="3a32c-106">Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="3a32c-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="3a32c-107">您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，輕鬆地實作這些功能。</span><span class="sxs-lookup"><span data-stu-id="3a32c-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="3a32c-108">Polly 以 .NET 4.x 和 .NET Standard 1.0 版 (其支援 .NET Core) 為目標。</span><span class="sxs-lookup"><span data-stu-id="3a32c-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="3a32c-109">Polly 中的重試原則是實作 HTTP 重試時，在 eShopOnContainers 中所使用的方法。</span><span class="sxs-lookup"><span data-stu-id="3a32c-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="3a32c-110">您可以實作介面，以便使用 Polly 來插入標準 HttpClient 功能或具有恢復功能的 HttpClient 版本 (視您要使用的重試原則組態而定)。</span><span class="sxs-lookup"><span data-stu-id="3a32c-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="3a32c-111">下列範例會顯示在 eShopOnContainers 中實作的介面。</span><span class="sxs-lookup"><span data-stu-id="3a32c-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="3a32c-112">如果您不想要使用具有恢復功能的機制，您可以使用標準實作，就像是在開發或測試更簡單的方法一樣。</span><span class="sxs-lookup"><span data-stu-id="3a32c-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="3a32c-113">下列程式碼會顯示標準 HttpClient 實作，可選擇允許使用驗證權杖的要求。</span><span class="sxs-lookup"><span data-stu-id="3a32c-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="3a32c-114">撰寫另一個類似的類別會是有趣的實作，但使用 Polly 可實作您要使用之具有恢復功能的機制 (在下列範例中，就是使用指數輪詢重試)。</span><span class="sxs-lookup"><span data-stu-id="3a32c-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="3a32c-115">透過 Polly，您可以定義重試原則，其中包含重試次數、指數輪詢組態，以及發生 HTTP 例外狀況時所要採取的動作，例如記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="3a32c-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="3a32c-116">在本例中，會設定原則，以便在 IoC 容器中註冊類型時嘗試指定的次數。</span><span class="sxs-lookup"><span data-stu-id="3a32c-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="3a32c-117">由於指數輪詢組態，每當程式碼偵測到 HttpRequest 例外狀況時，都會在等候一段時間之後重試 Http 要求，而且此等候時間會根據原則的設定方式呈指數增加。</span><span class="sxs-lookup"><span data-stu-id="3a32c-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="3a32c-118">HttpInvoker 是很重要的方法，也是這整個公用程式類別中啟動 HTTP 要求的程式。</span><span class="sxs-lookup"><span data-stu-id="3a32c-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="3a32c-119">該方法會在內部使用 \_policyWrapper.ExecuteAsync 來執行 HTTP 要求，這會將重試原則列入考量。</span><span class="sxs-lookup"><span data-stu-id="3a32c-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="3a32c-120">在 eShopOnContainers 中，您可以在 IoC container 註冊類型時指定 Polly 原則，如 [startup.cs 的 MVC Web 應用程式](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)類別中的下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="3a32c-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="3a32c-121">請注意，IHttpClient 物件會具現化為單一子句 (而不是暫時性)，以便服務可有效率地使用 TCP 連線，而且不會發生[通訊端問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。</span><span class="sxs-lookup"><span data-stu-id="3a32c-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="3a32c-122">但復原的重點是您會在 CreateResilientHttpClient 方法的 ResilientHttpClientFactory 中套用 Polly WaitAndRetryAsync 原則，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="3a32c-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="3a32c-123">[上一個] (implement-custom-http-call-retries-exponential-backoff.md) [下一個] (implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="3a32c-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
