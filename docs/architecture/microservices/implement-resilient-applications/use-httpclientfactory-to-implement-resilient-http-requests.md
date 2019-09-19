---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 了解如何使用 HttpClientFactory，自 .NET Core 2.1 開始提供，可用來建立 `HttpClient` 執行個體，方便您在應用程式中使用。
ms.date: 08/08/2019
ms.openlocfilehash: 6c862171ee6b5eda6f95694878bfa43518a9bdfa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039967"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="7da4b-103">使用 HttpClientFactory 實作復原 HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="7da4b-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="7da4b-104">`HttpClientFactory` 是意向明確的處理站，自 .NET Core 2.1 開始提供，可用來建立要在您應用程式中使用的 <xref:System.Net.Http.HttpClient> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7da4b-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="7da4b-105">.NET Core 中原始 HttpClient 類別的問題</span><span class="sxs-lookup"><span data-stu-id="7da4b-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="7da4b-106">您可以輕鬆地使用原始<xref:System.Net.Http.HttpClient>和知名的類別，但是在某些情況下，許多開發人員並不會正確地使用它。</span><span class="sxs-lookup"><span data-stu-id="7da4b-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="7da4b-107">第一個問題是，這個類別是可處置項目，將它與 `using` 陳述式搭配使用不是最好的選擇，因為即使您處置 `HttpClient` 物件，底層通訊端也不會立即釋出，而且可能會導致所謂「通訊端耗盡」的嚴重問題。</span><span class="sxs-lookup"><span data-stu-id="7da4b-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="7da4b-108">如需有關此問題的詳細資訊，請參閱[您使用 HttpClient 的方法錯誤而導致軟體不穩定](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) 部落格文章 (英文)。</span><span class="sxs-lookup"><span data-stu-id="7da4b-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="7da4b-109">因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。</span><span class="sxs-lookup"><span data-stu-id="7da4b-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="7da4b-110">為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。</span><span class="sxs-lookup"><span data-stu-id="7da4b-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="7da4b-111">該問題會導致 `SocketException` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7da4b-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="7da4b-112">解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="7da4b-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span>

<span data-ttu-id="7da4b-113">但是將 `HttpClient` 做為單一物件或靜態物件時會出現第二個問題。</span><span class="sxs-lookup"><span data-stu-id="7da4b-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="7da4b-114">在此情況下，單一或靜態`HttpClient`不會遵守 DNS 變更，如 dotnet/corefx GitHub 存放庫中的[問題](https://github.com/dotnet/corefx/issues/11224)中所述。</span><span class="sxs-lookup"><span data-stu-id="7da4b-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue](https://github.com/dotnet/corefx/issues/11224) at the dotnet/corefx GitHub repository.</span></span> 

<span data-ttu-id="7da4b-115">為解決所述的那些問題並更輕鬆地管理 `HttpClient` 執行個體，.NET Core 2.1 引進了一個新的 `HttpClientFactory`，它也可與 Polly 整合來實作復原 HTTP 呼叫。</span><span class="sxs-lookup"><span data-stu-id="7da4b-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>

<span data-ttu-id="7da4b-116">[Polly](http://www.thepollyproject.org/)是暫時性錯誤處理程式庫，可協助開發人員以流暢且安全線程的方式使用一些預先定義的原則，來為應用程式新增復原功能。</span><span class="sxs-lookup"><span data-stu-id="7da4b-116">[Polly](http://www.thepollyproject.org/) is transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="7da4b-117">什麼是 HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="7da4b-117">What is HttpClientFactory</span></span>

<span data-ttu-id="7da4b-118">`HttpClientFactory` 的設計宗旨是：</span><span class="sxs-lookup"><span data-stu-id="7da4b-118">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="7da4b-119">提供用來命名和設定邏輯`HttpClient`物件的中央位置。</span><span class="sxs-lookup"><span data-stu-id="7da4b-119">Provide a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="7da4b-120">例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="7da4b-120">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="7da4b-121">透過委派 `HttpClient` 中的處理常式和實作 Polly 型中介軟體以利用 Polly 原則用於復原，來編纂連出中介軟體的概念。</span><span class="sxs-lookup"><span data-stu-id="7da4b-121">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="7da4b-122">`HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。</span><span class="sxs-lookup"><span data-stu-id="7da4b-122">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="7da4b-123">您會將 HTTP 用戶端註冊到處理站，而且您可以使用 Polly 處理常式將 Polly 原則用於重試、斷路器等等。</span><span class="sxs-lookup"><span data-stu-id="7da4b-123">You register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="7da4b-124">管理的存留期`HttpClientMessageHandlers` ，以避免所提及的問題/在自行管理`HttpClient`生命週期時可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="7da4b-124">Manage the lifetime of `HttpClientMessageHandlers` to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="7da4b-125">使用 HttpClientFactory 的多種方式</span><span class="sxs-lookup"><span data-stu-id="7da4b-125">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="7da4b-126">有多種方式可在您的應用程式中使用 `HttpClientFactory`：</span><span class="sxs-lookup"><span data-stu-id="7da4b-126">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="7da4b-127">直接使用 `HttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="7da4b-127">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="7da4b-128">使用具名用戶端</span><span class="sxs-lookup"><span data-stu-id="7da4b-128">Use Named Clients</span></span>
- <span data-ttu-id="7da4b-129">使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="7da4b-129">Use Typed Clients</span></span>
- <span data-ttu-id="7da4b-130">使用產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="7da4b-130">Use Generated Clients</span></span>

<span data-ttu-id="7da4b-131">為了簡潔起見，本指南說明最具結構化的使用`HttpClientFactory`方式，也就是使用型別用戶端（服務代理程式模式）。</span><span class="sxs-lookup"><span data-stu-id="7da4b-131">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="7da4b-132">不過，所有選項都已記載，而且目前列于本文中，[涵蓋 HttpClientFactory 的使用](/aspnet/core/fundamentals/http-requests#consumption-patterns)方式。</span><span class="sxs-lookup"><span data-stu-id="7da4b-132">However, all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="7da4b-133">如何搭配 HttpClientFactory 使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="7da4b-133">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="7da4b-134">那麼，什麼是「具型別用戶端」？</span><span class="sxs-lookup"><span data-stu-id="7da4b-134">So, what's a "Typed Client"?</span></span> <span data-ttu-id="7da4b-135">它只是 `DefaultHttpClientFactory` 插入時所設定的一個 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="7da4b-135">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="7da4b-136">下圖顯示具型別用戶端如何搭配 `HttpClientFactory` 使用：</span><span class="sxs-lookup"><span data-stu-id="7da4b-136">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService (控制器或用戶端程式碼所使用) 會使用由已註冊的 IHttpClientFactory 所建立的 HttpClient。](./media/image3.5.png)

<span data-ttu-id="7da4b-140">**圖 8-4**。</span><span class="sxs-lookup"><span data-stu-id="7da4b-140">**Figure 8-4**.</span></span> <span data-ttu-id="7da4b-141">搭配具型別用戶端類別使用 HttpClientFactory。</span><span class="sxs-lookup"><span data-stu-id="7da4b-141">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="7da4b-142">首先， `HttpClientFactory` `AddHttpClient()`安裝包含之擴充方法的`Microsoft.Extensions.Http` NuGet 套件，以在您的應用程式中設定。 `IServiceCollection`</span><span class="sxs-lookup"><span data-stu-id="7da4b-142">First, setup `HttpClientFactory` in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="7da4b-143">這個擴充方法註冊將用來做為介面 `IHttpClientFactory` 之單一物件的 `DefaultHttpClientFactory`。</span><span class="sxs-lookup"><span data-stu-id="7da4b-143">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="7da4b-144">它為 `HttpMessageHandlerBuilder` 定義暫時性設定。</span><span class="sxs-lookup"><span data-stu-id="7da4b-144">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="7da4b-145">此訊息處理常式 (`HttpMessageHandler` 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。</span><span class="sxs-lookup"><span data-stu-id="7da4b-145">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="7da4b-146">在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="7da4b-146">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="7da4b-147">如先前的程式碼所示註冊用戶端服務，會`DefaultClientFactory`使每個`HttpClient`服務的建立一個標準。</span><span class="sxs-lookup"><span data-stu-id="7da4b-147">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="7da4b-148">您也可以在註冊中新增實例特定設定，例如設定基底位址，然後新增一些復原原則，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7da4b-148">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"])
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="7da4b-149">就此範例而言，您可以在下一個程式碼中看到上述其中一個原則：</span><span class="sxs-lookup"><span data-stu-id="7da4b-149">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="7da4b-150">您可以在[下一篇文章](implement-http-call-retries-exponential-backoff-polly.md)中找到更多有關使用 Polly 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7da4b-150">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="7da4b-151">HttpClient 存留期</span><span class="sxs-lookup"><span data-stu-id="7da4b-151">HttpClient lifetimes</span></span>

<span data-ttu-id="7da4b-152">每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7da4b-152">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="7da4b-153">但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。</span><span class="sxs-lookup"><span data-stu-id="7da4b-153">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="7da4b-154">處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。</span><span class="sxs-lookup"><span data-stu-id="7da4b-154">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="7da4b-155">有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。</span><span class="sxs-lookup"><span data-stu-id="7da4b-155">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="7da4b-156">集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。</span><span class="sxs-lookup"><span data-stu-id="7da4b-156">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="7da4b-157">預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。</span><span class="sxs-lookup"><span data-stu-id="7da4b-157">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="7da4b-158">若要覆寫它，請在建立用戶端時所傳回的 `IHttpClientBuilder` 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7da4b-158">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="7da4b-159">每個具型別用戶端都可以設定自己的處理常式存留期值。</span><span class="sxs-lookup"><span data-stu-id="7da4b-159">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="7da4b-160">將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。</span><span class="sxs-lookup"><span data-stu-id="7da4b-160">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="7da4b-161">實作使用已插入和已設定之 HttpClient 的具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="7da4b-161">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="7da4b-162">在上一個步驟中，您必須先定義具型別用戶端類別，例如範例程式碼中的類別，像是 'BasketService'、'CatalogService'、'OrderingService' 等等，具型別用戶端是接受 `HttpClient` 物件 (透過建構函式插入) 並使用該物件來呼叫某些遠端 HTTP 服務的類別。</span><span class="sxs-lookup"><span data-stu-id="7da4b-162">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="7da4b-163">例如：</span><span class="sxs-lookup"><span data-stu-id="7da4b-163">For example:</span></span>

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

<span data-ttu-id="7da4b-164">具型別用戶端 (範例中的 CatalogService) 由 DI (相依性插入) 啟用，這表示除了 HttpClient 之外，它可以接受其建構函式中任何已註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="7da4b-164">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="7da4b-165">具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7da4b-165">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="7da4b-166">不過，集區中的 HttpMessageHandler 物件是可讓多個 Http 要求重複使用的物件。</span><span class="sxs-lookup"><span data-stu-id="7da4b-166">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="7da4b-167">使用具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="7da4b-167">Use your Typed Client classes</span></span>

<span data-ttu-id="7da4b-168">最後，一旦您將具`AddHttpClient()`類型的類別實作為，並將它們註冊之後，您就可以在任何可使用 DI 插入服務的地方使用它們。</span><span class="sxs-lookup"><span data-stu-id="7da4b-168">Finally, once you have your typed classes implemented and have them registered with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="7da4b-169">例如，在 Razor 頁面程式碼或 MVC web 應用程式的控制器中，如下列 eShopOnContainers 程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="7da4b-169">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

<span data-ttu-id="7da4b-170">到目前為止，顯示的程式碼只是執行一般 Http 要求，但下面幾節才是神奇的地方，只需新增原則及委派處理常式到已註冊的具型別用戶端，將由 `HttpClient` 完成的所有 HTTP 要求，在運作時會考慮使用帳戶復原原則 (例如利用指數輪詢和斷路器來重試)，或是任何其他自訂委派處理常式來實作其他安全性功能 (例如使用驗證權杖) 或任何其他自訂功能。</span><span class="sxs-lookup"><span data-stu-id="7da4b-170">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7da4b-171">其他資源</span><span class="sxs-lookup"><span data-stu-id="7da4b-171">Additional resources</span></span>

- <span data-ttu-id="7da4b-172">**使用 .NET Core 中的 HttpClientFactory** </span><span class="sxs-lookup"><span data-stu-id="7da4b-172">**Using HttpClientFactory in .NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="7da4b-173">**HttpClientFactory GitHub 存放庫** </span><span class="sxs-lookup"><span data-stu-id="7da4b-173">**HttpClientFactory GitHub repo** </span></span>\
  <https://github.com/aspnet/Extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="7da4b-174">**Polly (.NET 復原和暫時性錯誤處理程式庫)**  </span><span class="sxs-lookup"><span data-stu-id="7da4b-174">**Polly (.NET resilience and transient-fault-handling library)** </span></span>\
  <http://www.thepollyproject.org/>

>[!div class="step-by-step"]
><span data-ttu-id="7da4b-175">[上一頁](explore-custom-http-call-retries-exponential-backoff.md)
>[下一頁](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="7da4b-175">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
