---
title: 利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 66ac57fc824e01f96d6584ab86bb95ba1b0174a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576977"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>利用 Polly 使用指數輪詢來實作 HTTP 呼叫重試

使用指數輪詢重試的建議方法是利用更進階的 .NET 程式庫，例如開放原始碼 [Polly](https://github.com/App-vNext/Polly) 程式庫。

Polly 是 .NET 程式庫，提供恢復功能和暫時性錯誤處理功能。 您可以藉由套用重試、斷路器、艙壁隔離 (Bulkhead Isolation)、逾時和後援等 Polly 原則，輕鬆地實作這些功能。 Polly 以 .NET 4.x 和 .NET Standard 1.0 版 (其支援 .NET Core) 為目標。

Polly 中的重試原則是實作 HTTP 重試時，在 eShopOnContainers 中所使用的方法。 您可以實作介面，以便使用 Polly 來插入標準 HttpClient 功能或具有恢復功能的 HttpClient 版本 (視您要使用的重試原則組態而定)。

下列範例會顯示在 eShopOnContainers 中實作的介面。

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

如果您不想要使用具有恢復功能的機制，您可以使用標準實作，就像是在開發或測試更簡單的方法一樣。 下列程式碼會顯示標準 HttpClient 實作，可選擇允許使用驗證權杖的要求。

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

撰寫另一個類似的類別會是有趣的實作，但使用 Polly 可實作您要使用之具有恢復功能的機制 (在下列範例中，就是使用指數輪詢重試)。

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

透過 Polly，您可以定義重試原則，其中包含重試次數、指數輪詢組態，以及發生 HTTP 例外狀況時所要採取的動作，例如記錄錯誤。 在本例中，會設定原則，以便在 IoC 容器中註冊類型時嘗試指定的次數。 由於指數輪詢組態，每當程式碼偵測到 HttpRequest 例外狀況時，都會在等候一段時間之後重試 Http 要求，而且此等候時間會根據原則的設定方式呈指數增加。

HttpInvoker 是很重要的方法，也是這整個公用程式類別中啟動 HTTP 要求的程式。 該方法會在內部使用 \_policyWrapper.ExecuteAsync 來執行 HTTP 要求，這會將重試原則列入考量。

在 eShopOnContainers 中，您可以在 IoC container 註冊類型時指定 Polly 原則，如 [startup.cs 的 MVC Web 應用程式](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)類別中的下列程式碼所示。

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

請注意，IHttpClient 物件會具現化為單一子句 (而不是暫時性)，以便服務可有效率地使用 TCP 連線，而且不會發生[通訊端問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。

但復原的重點是您會在 CreateResilientHttpClient 方法的 ResilientHttpClientFactory 中套用 Polly WaitAndRetryAsync 原則，如下列程式碼所示：

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
[上一個] (implement-custom-http-call-retries-exponential-backoff.md) [下一個] (implement-circuit-breaker-pattern.md)
