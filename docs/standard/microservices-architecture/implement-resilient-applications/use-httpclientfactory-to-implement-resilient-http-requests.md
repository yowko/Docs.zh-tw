---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 了解如何使用 HttpClientFactory，自 .NET Core 2.1 開始提供，可用來建立 `HttpClient` 執行個體，方便您在應用程式中使用。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 73faa847dae2f844784ae5d85ce905b7e1e64cd0
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479811"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="45c35-103">使用 HttpClientFactory 實作復原 HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="45c35-103">Use HttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="45c35-104">`HttpClientFactory` 是意向明確的處理站，自 .NET Core 2.1 開始提供，可用來建立要在您應用程式中使用的 <xref:System.Net.Http.HttpClient> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="45c35-104">`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="45c35-105">.NET Core 中原始 HttpClient 類別的問題</span><span class="sxs-lookup"><span data-stu-id="45c35-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="45c35-106">已知的原始 [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) 類別使用方式簡單，但在某些情況下，許多開發人員都沒有正確地使用它。</span><span class="sxs-lookup"><span data-stu-id="45c35-106">The original and well-known [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span> 

<span data-ttu-id="45c35-107">第一個問題是，這個類別是可處置項目，將它與 `using` 陳述式搭配使用不是最好的選擇，因為即使您處置 `HttpClient` 物件，底層通訊端也不會立即釋出，而且可能會導致所謂「通訊端耗盡」的嚴重問題。</span><span class="sxs-lookup"><span data-stu-id="45c35-107">As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’.</span></span> <span data-ttu-id="45c35-108">如需有關此問題的詳細資訊，請參閱[您使用 HttpClient 的方法錯誤而導致軟體不穩定](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) 部落格文章 (英文)。</span><span class="sxs-lookup"><span data-stu-id="45c35-108">For more information about this issue, see [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.</span></span>

<span data-ttu-id="45c35-109">因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。</span><span class="sxs-lookup"><span data-stu-id="45c35-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="45c35-110">為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。</span><span class="sxs-lookup"><span data-stu-id="45c35-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="45c35-111">該問題會導致 `SocketException` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="45c35-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="45c35-112">解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](/dotnet/csharp/tutorials/console-webapiclient)中所述。</span><span class="sxs-lookup"><span data-stu-id="45c35-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](/dotnet/csharp/tutorials/console-webapiclient).</span></span> 

<span data-ttu-id="45c35-113">但是將 `HttpClient` 做為單一物件或靜態物件時會出現第二個問題。</span><span class="sxs-lookup"><span data-stu-id="45c35-113">But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object.</span></span> <span data-ttu-id="45c35-114">在此案例中，單一或靜態 `HttpClient` 不會理會 DNS 變更，如 [.NET Core GitHub 存放庫提及的問題](https://github.com/dotnet/corefx/issues/11224)中所述。</span><span class="sxs-lookup"><span data-stu-id="45c35-114">In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224).</span></span> 

<span data-ttu-id="45c35-115">為解決所述的那些問題並更輕鬆地管理 `HttpClient` 執行個體，.NET Core 2.1 引進了一個新的 `HttpClientFactory`，它也可與 Polly 整合來實作復原 HTTP 呼叫。</span><span class="sxs-lookup"><span data-stu-id="45c35-115">To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 introduced a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.</span></span>   

## <a name="what-is-httpclientfactory"></a><span data-ttu-id="45c35-116">什麼是 HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="45c35-116">What is HttpClientFactory</span></span>

<span data-ttu-id="45c35-117">`HttpClientFactory` 的設計宗旨是：</span><span class="sxs-lookup"><span data-stu-id="45c35-117">`HttpClientFactory` is designed to:</span></span>

- <span data-ttu-id="45c35-118">提供一個集中位置以便命名及設定邏輯 HttpClients。</span><span class="sxs-lookup"><span data-stu-id="45c35-118">Provide a central location for naming and configuring logical HttpClients.</span></span> <span data-ttu-id="45c35-119">例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="45c35-119">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="45c35-120">透過委派 `HttpClient` 中的處理常式和實作 Polly 型中介軟體以利用 Polly 原則用於復原，來編纂連出中介軟體的概念。</span><span class="sxs-lookup"><span data-stu-id="45c35-120">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.</span></span>
- <span data-ttu-id="45c35-121">`HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。</span><span class="sxs-lookup"><span data-stu-id="45c35-121">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="45c35-122">您將 http 用戶端註冊到處理站，而且您可以使用允許 Polly 原則用於重試、斷路器等等的 Polly 處理常式。</span><span class="sxs-lookup"><span data-stu-id="45c35-122">You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.</span></span>
- <span data-ttu-id="45c35-123">管理 HttpClientMessageHandlers 存留期，以避免您自己管理 `HttpClient` 存留期時可能發生的上述問題。</span><span class="sxs-lookup"><span data-stu-id="45c35-123">Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span> 

## <a name="multiple-ways-to-use-httpclientfactory"></a><span data-ttu-id="45c35-124">使用 HttpClientFactory 的多種方式</span><span class="sxs-lookup"><span data-stu-id="45c35-124">Multiple ways to use HttpClientFactory</span></span>

<span data-ttu-id="45c35-125">有多種方式可在您的應用程式中使用 `HttpClientFactory`：</span><span class="sxs-lookup"><span data-stu-id="45c35-125">There are several ways that you can use `HttpClientFactory` in your application:</span></span>

- <span data-ttu-id="45c35-126">直接使用 `HttpClientFactory`</span><span class="sxs-lookup"><span data-stu-id="45c35-126">Use `HttpClientFactory` Directly</span></span>
- <span data-ttu-id="45c35-127">使用具名用戶端</span><span class="sxs-lookup"><span data-stu-id="45c35-127">Use Named Clients</span></span>
- <span data-ttu-id="45c35-128">使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="45c35-128">Use Typed Clients</span></span>
- <span data-ttu-id="45c35-129">使用產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="45c35-129">Use Generated Clients</span></span>

<span data-ttu-id="45c35-130">為了簡潔起見，此指導方針展示如何以結構化程度最高的方式使用 `HttpClientFactory`，也就是使用具型別用戶端 (服務代理程式模式)，但是我們已記錄所有選項，而且目前已詳列在這篇[涵蓋 HttpClientFactory 用法的文章](/aspnet/core/fundamentals/http-requests?#consumption-patterns)中。</span><span class="sxs-lookup"><span data-stu-id="45c35-130">For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that's to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](/aspnet/core/fundamentals/http-requests?#consumption-patterns).</span></span>  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a><span data-ttu-id="45c35-131">如何搭配 HttpClientFactory 使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="45c35-131">How to use Typed Clients with HttpClientFactory</span></span>

<span data-ttu-id="45c35-132">那麼，什麼是「具型別用戶端」？</span><span class="sxs-lookup"><span data-stu-id="45c35-132">So, what's a "Typed Client"?</span></span> <span data-ttu-id="45c35-133">它只是 `DefaultHttpClientFactory` 插入時所設定的一個 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="45c35-133">It's just an `HttpClient` that's configured upon injection by the `DefaultHttpClientFactory`.</span></span>

<span data-ttu-id="45c35-134">下圖顯示具型別用戶端如何搭配 `HttpClientFactory` 使用：</span><span class="sxs-lookup"><span data-stu-id="45c35-134">The following diagram shows how Typed Clients are used with `HttpClientFactory`:</span></span>

![ClientService (控制器或用戶端程式碼所使用) 會使用由已註冊的 IHttpClientFactory 所建立的 HttpClient。](./media/image3.5.png)

<span data-ttu-id="45c35-138">**圖 8-4**。</span><span class="sxs-lookup"><span data-stu-id="45c35-138">**Figure 8-4**.</span></span> <span data-ttu-id="45c35-139">搭配具型別用戶端類別使用 HttpClientFactory。</span><span class="sxs-lookup"><span data-stu-id="45c35-139">Using HttpClientFactory with Typed Client classes.</span></span>

<span data-ttu-id="45c35-140">首先，在應用程式中設定 `HttpClientFactory`，加入對 `Microsoft.Extensions.Http` 的參考，其中包括 `IServiceCollection` 的 `AddHttpClient()` 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="45c35-140">First, setup `HttpClientFactory` in your application, adding a reference to the `Microsoft.Extensions.Http` package that includes the `AddHttpClient()` extension method for `IServiceCollection`.</span></span> <span data-ttu-id="45c35-141">這個擴充方法註冊將用來做為介面 `IHttpClientFactory` 之單一物件的 `DefaultHttpClientFactory`。</span><span class="sxs-lookup"><span data-stu-id="45c35-141">This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="45c35-142">它為 `HttpMessageHandlerBuilder` 定義暫時性設定。</span><span class="sxs-lookup"><span data-stu-id="45c35-142">It defines a transient configuration for the `HttpMessageHandlerBuilder`.</span></span> <span data-ttu-id="45c35-143">此訊息處理常式 (`HttpMessageHandler` 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。</span><span class="sxs-lookup"><span data-stu-id="45c35-143">This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="45c35-144">在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="45c35-144">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="45c35-145">如先前的程式碼所示，註冊用戶端服務，讓 `DefaultClientFactory` 建立特別針對每個服務設定的 `HttpClient`，我們將在下一個段落中說明。</span><span class="sxs-lookup"><span data-stu-id="45c35-145">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create an `HttpClient` configured specifically for each service, as we'll explain in the next paragraph.</span></span>

<span data-ttu-id="45c35-146">只要透過 `AddHttpClient()` 註冊您的用戶端服務類別，將插入您類別中的 `HttpClient` 物件將使用註冊時所提供的設定和原則。</span><span class="sxs-lookup"><span data-stu-id="45c35-146">Just by registering your client service class with `AddHttpClient()`, the `HttpClient` object that will be injected into your class will use the configuration and policies provided upon registration.</span></span> <span data-ttu-id="45c35-147">在以下各節中，您將會看到那些原則，如 Polly 的重試或斷路器。</span><span class="sxs-lookup"><span data-stu-id="45c35-147">In the next sections, you'll see those policies like Polly’s retries or circuit-breakers.</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="45c35-148">HttpClient 存留期</span><span class="sxs-lookup"><span data-stu-id="45c35-148">HttpClient lifetimes</span></span>

<span data-ttu-id="45c35-149">每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="45c35-149">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="45c35-150">但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。</span><span class="sxs-lookup"><span data-stu-id="45c35-150">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="45c35-151">處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。</span><span class="sxs-lookup"><span data-stu-id="45c35-151">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="45c35-152">有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。</span><span class="sxs-lookup"><span data-stu-id="45c35-152">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="45c35-153">集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。</span><span class="sxs-lookup"><span data-stu-id="45c35-153">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="45c35-154">預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。</span><span class="sxs-lookup"><span data-stu-id="45c35-154">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="45c35-155">若要覆寫它，請在建立用戶端時所傳回的 `IHttpClientBuilder` 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="45c35-155">To override it, call `SetHandlerLifetime()` on the `IHttpClientBuilder` that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

<span data-ttu-id="45c35-156">每個具型別用戶端都可以設定自己的處理常式存留期值。</span><span class="sxs-lookup"><span data-stu-id="45c35-156">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="45c35-157">將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。</span><span class="sxs-lookup"><span data-stu-id="45c35-157">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="45c35-158">實作使用已插入和已設定之 HttpClient 的具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="45c35-158">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="45c35-159">在上一個步驟中，您必須先定義具型別用戶端類別，例如範例程式碼中的類別，像是 'BasketService'、'CatalogService'、'OrderingService' 等等，具型別用戶端是接受 `HttpClient` 物件 (透過建構函式插入) 並使用該物件來呼叫某些遠端 HTTP 服務的類別。</span><span class="sxs-lookup"><span data-stu-id="45c35-159">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="45c35-160">例如：</span><span class="sxs-lookup"><span data-stu-id="45c35-160">For example:</span></span>

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

<span data-ttu-id="45c35-161">具型別用戶端 (範例中的 CatalogService) 由 DI (相依性插入) 啟用，這表示除了 HttpClient 之外，它可以接受其建構函式中任何已註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="45c35-161">The Typed Client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.</span></span>

<span data-ttu-id="45c35-162">具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="45c35-162">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="45c35-163">不過，集區中的 HttpMessageHandler 物件是可讓多個 Http 要求重複使用的物件。</span><span class="sxs-lookup"><span data-stu-id="45c35-163">However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="45c35-164">使用具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="45c35-164">Use your Typed Client classes</span></span>

<span data-ttu-id="45c35-165">最後，實作類型類別並使用 AddHttpClient() 註冊之後，即可在 DI 插入的服務中隨意使用它，例如在任何 Razor 頁面程式碼或任何 MVC Web 應用程式控制器，就像來自 eShopOnContainers 的下列程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="45c35-165">Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.</span></span>

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

<span data-ttu-id="45c35-166">到目前為止，顯示的程式碼只是執行一般 Http 要求，但下面幾節才是神奇的地方，只需新增原則及委派處理常式到已註冊的具型別用戶端，將由 `HttpClient` 完成的所有 HTTP 要求，在運作時會考慮使用帳戶復原原則 (例如利用指數輪詢和斷路器來重試)，或是任何其他自訂委派處理常式來實作其他安全性功能 (例如使用驗證權杖) 或任何其他自訂功能。</span><span class="sxs-lookup"><span data-stu-id="45c35-166">Up to this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="45c35-167">其他資源</span><span class="sxs-lookup"><span data-stu-id="45c35-167">Additional resources</span></span>

- <span data-ttu-id="45c35-168">**使用 .NET Core 中的 HttpClientFactory**\\</span><span class="sxs-lookup"><span data-stu-id="45c35-168">**Using HttpClientFactory in .NET Core**\\</span></span>
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- <span data-ttu-id="45c35-169">**HttpClientFactory GitHub 存放庫**\\</span><span class="sxs-lookup"><span data-stu-id="45c35-169">**HttpClientFactory GitHub repo**\\</span></span>
  [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
><span data-ttu-id="45c35-170">[上一頁](explore-custom-http-call-retries-exponential-backoff.md)
>[下一頁](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="45c35-170">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>