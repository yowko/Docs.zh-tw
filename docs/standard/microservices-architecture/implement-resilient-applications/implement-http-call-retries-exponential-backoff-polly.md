---
title: "使用 Polly 實作 HTTP 呼叫使用指數型輪詢的重試次數"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用 Polly 實作 HTTP 呼叫使用指數型輪詢的重試次數"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="f328d-104">使用 Polly 實作 HTTP 呼叫使用指數型輪詢的重試次數</span><span class="sxs-lookup"><span data-stu-id="f328d-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="f328d-105">指數型輪詢的重試次數的建議的方法是利用更進階的.NET 程式庫像開放原始碼[Polly](https://github.com/App-vNext/Polly)程式庫。</span><span class="sxs-lookup"><span data-stu-id="f328d-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="f328d-106">Polly 是.NET 程式庫提供恢復功能和暫時性錯誤處理功能。</span><span class="sxs-lookup"><span data-stu-id="f328d-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="f328d-107">您可以輕鬆地實作這些功能，藉由套用 Polly 原則，例如重試，斷路器、 艙隔離、 逾時，以及後援。</span><span class="sxs-lookup"><span data-stu-id="f328d-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="f328d-108">Polly 以.NET 為目標 4.x 和.NET 標準 1.0 版 （可支援.NET Core）。</span><span class="sxs-lookup"><span data-stu-id="f328d-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="f328d-109">Polly 中的重試原則是實作 HTTP 重試時，eShopOnContainers 中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="f328d-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="f328d-110">您可以實作介面，讓您可以將插入標準 HttpClient 功能或 HttpClient 使用 Polly，根據您想要使用何種重試原則設定的恢復功能版本。</span><span class="sxs-lookup"><span data-stu-id="f328d-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="f328d-111">下列範例會示範 eShopOnContainers 中實作的介面。</span><span class="sxs-lookup"><span data-stu-id="f328d-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

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

<span data-ttu-id="f328d-112">如果您不要做為有彈性的機制，當您正在開發或測試更簡單的方法，您可以使用標準的實作。</span><span class="sxs-lookup"><span data-stu-id="f328d-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="f328d-113">下列程式碼會顯示標準 HttpClient 實作允許要求驗證語彙基元為選擇性的案例。</span><span class="sxs-lookup"><span data-stu-id="f328d-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

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

<span data-ttu-id="f328d-114">有趣的實作會撰寫程式碼，另一個，類似的類別，但使用 Polly 實作您想要使用的彈性機制，在下列範例中，重試使用指數型輪詢。</span><span class="sxs-lookup"><span data-stu-id="f328d-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

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

<span data-ttu-id="f328d-115">您可以使用 Polly，定義的重試、 指數型輪詢組態，以及一個 HTTP 例外狀況，例如記錄錯誤時應採取的動作數目的重試原則。</span><span class="sxs-lookup"><span data-stu-id="f328d-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="f328d-116">在此情況下，原則設定，將會嘗試註冊 IoC 容器中的類型時指定的次數。</span><span class="sxs-lookup"><span data-stu-id="f328d-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="f328d-117">指數型輪詢組態，因為每當程式碼偵測到 HttpRequest 例外狀況，會重試 Http 要求之後等候一段時間，會根據原則設定的方式以等比級數增加。</span><span class="sxs-lookup"><span data-stu-id="f328d-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="f328d-118">重要的方法是 HttpInvoker，這就是在此公用程式類別的 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="f328d-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="f328d-119">方法會在內部執行的 HTTP 要求\_policyWrapper.ExecuteAsync，列入考量的重試原則。</span><span class="sxs-lookup"><span data-stu-id="f328d-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="f328d-120">在 eShopOnContainers 您指定 Polly 原則註冊 IoC 容器，例如下列程式碼，從在型別時[MVC web 應用程式，在 startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)類別。</span><span class="sxs-lookup"><span data-stu-id="f328d-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

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

<span data-ttu-id="f328d-121">請注意，IHttpClient 物件具現化為 singleton 而不是為暫時性以便有效率地服務所使用的 TCP 連線的和[通訊端的問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)將不會發生。</span><span class="sxs-lookup"><span data-stu-id="f328d-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="f328d-122">但是有關復原很重要的一點是您套用 Polly WaitAndRetryAsync 原則內 ResilientHttpClientFactory 在 CreateResilientHttpClient 方法中，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="f328d-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

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
<span data-ttu-id="f328d-123">[上一個](implement-custom-http-call-retries-exponential-backoff.md) [下一步] (實作-循環-分隔-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="f328d-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>
