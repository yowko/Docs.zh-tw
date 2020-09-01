---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 瞭解如何使用 .NET Core 2.1 之後提供的 IHttpClientFactory 來建立 `HttpClient` 實例，讓您輕鬆地在應用程式中使用。
ms.date: 08/31/2020
ms.openlocfilehash: 1df5432f215371b60722212cf706c28a4a5bb5f6
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271824"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="85f2e-103">使用 HttpClientFactory 實作復原 HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="85f2e-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="85f2e-104"><xref:System.Net.Http.IHttpClientFactory> 是 `DefaultHttpClientFactory` 實作為固定 factory （自 .Net Core 2.1 起提供）的合約，可用來建立 <xref:System.Net.Http.HttpClient> 要在應用程式中使用的實例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="85f2e-105">.NET Core 中原始 HttpClient 類別的問題</span><span class="sxs-lookup"><span data-stu-id="85f2e-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="85f2e-106">您 <xref:System.Net.Http.HttpClient> 可以輕鬆地使用原始和知名的類別，但在某些情況下，許多開發人員都沒有正確使用它。</span><span class="sxs-lookup"><span data-stu-id="85f2e-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="85f2e-107">雖然此類別 `IDisposable` 會在語句中執行、宣告和具現化，但不建議您這樣做， `using` 因為當 `HttpClient` 物件被處置時，不會立即釋放基礎通訊端，這可能會導致 _通訊端耗盡_ 問題。</span><span class="sxs-lookup"><span data-stu-id="85f2e-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="85f2e-108">如需有關此問題的詳細資訊，請參閱 [使用 HttpClient 錯誤的 blog 文章，並不穩定您的軟體](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。</span><span class="sxs-lookup"><span data-stu-id="85f2e-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="85f2e-109">因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。</span><span class="sxs-lookup"><span data-stu-id="85f2e-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="85f2e-110">為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。</span><span class="sxs-lookup"><span data-stu-id="85f2e-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="85f2e-111">該問題會導致 `SocketException` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="85f2e-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="85f2e-112">解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="85f2e-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="85f2e-113">這是適用于短期的主控台應用程式或類似的解決方案，其會在一天內執行數次。</span><span class="sxs-lookup"><span data-stu-id="85f2e-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="85f2e-114">開發人員遇到的另一個問題，就是在長時間執行的進程中使用的共用實例 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="85f2e-115">在 HttpClient 具現化為單一或靜態物件的情況下，它無法處理 DNS 變更，如此 dotnet/runtime GitHub 存放庫的 [問題](https://github.com/dotnet/runtime/issues/18348) 所述。</span><span class="sxs-lookup"><span data-stu-id="85f2e-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="85f2e-116">不過，這個問題並不是 `HttpClient` 每個 se 都有問題，而是使用 [預設的 HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)函式，因為它會建立一個新的具體實例 <xref:System.Net.Http.HttpMessageHandler> ，也就是有 *通訊端耗盡* 和 DNS 變更上述問題的實例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="85f2e-117">為了解決上述問題，並讓實例可供 `HttpClient` 管理，.Net Core 2.1 引進了 <xref:System.Net.Http.IHttpClientFactory> 介面，可透過相依性 `HttpClient` 插入 (DI) ，在應用程式中設定和建立實例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="85f2e-118">它也提供 Polly 型中介軟體的延伸模組，以利用 HttpClient 中委派的處理常式。</span><span class="sxs-lookup"><span data-stu-id="85f2e-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="85f2e-119">[Polly](http://www.thepollyproject.org/) 是暫時性錯誤處理程式庫，可協助開發人員以流暢且安全線程的方式使用一些預先定義的原則，來為應用程式新增復原功能。</span><span class="sxs-lookup"><span data-stu-id="85f2e-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="85f2e-120">使用 IHttpClientFactory 的優點</span><span class="sxs-lookup"><span data-stu-id="85f2e-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="85f2e-121">目前執行的 <xref:System.Net.Http.IHttpClientFactory> 也會 <xref:System.Net.Http.IHttpMessageHandlerFactory> 提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="85f2e-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="85f2e-122">提供命名和設定邏輯物件的集中位置 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="85f2e-123">例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="85f2e-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="85f2e-124">透過在中委派處理常式 `HttpClient` ，並執行以 Polly 為基礎的中介軟體，以利用 Polly 的原則來復原，以編寫傳出中介軟體的概念。</span><span class="sxs-lookup"><span data-stu-id="85f2e-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="85f2e-125">`HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。</span><span class="sxs-lookup"><span data-stu-id="85f2e-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="85f2e-126">您可以將 HTTP 用戶端註冊至 factory，而且可以使用 Polly 處理常式來使用 Polly 原則來重試、CircuitBreakers 等等。</span><span class="sxs-lookup"><span data-stu-id="85f2e-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="85f2e-127">管理的存留期， <xref:System.Net.Http.HttpMessageHandler> 以避免在自行管理存留期時可能發生的問題/問題 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="85f2e-128">`HttpClient`DI 插入的實例可以安全地處置，因為相關聯的 `HttpMessageHandler` 是由 factory 管理。</span><span class="sxs-lookup"><span data-stu-id="85f2e-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="85f2e-129">事實上，插入 `HttpClient` 的實例的 *範圍* 是從 DI 的觀點來看。</span><span class="sxs-lookup"><span data-stu-id="85f2e-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="85f2e-130">`IHttpClientFactory` () 的執行 `DefaultHttpClientFactory` 會緊密地系結至 NuGet 套件中的 DI 實作為 `Microsoft.Extensions.DependencyInjection` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="85f2e-131">如需使用其他 DI 容器的詳細資訊，請參閱此 [GitHub 討論](https://github.com/dotnet/extensions/issues/1345)。</span><span class="sxs-lookup"><span data-stu-id="85f2e-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="85f2e-132">使用 IHttpClientFactory 的多種方式</span><span class="sxs-lookup"><span data-stu-id="85f2e-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="85f2e-133">有多種方式可在您的應用程式中使用 `IHttpClientFactory`：</span><span class="sxs-lookup"><span data-stu-id="85f2e-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="85f2e-134">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="85f2e-134">Basic usage</span></span>
- <span data-ttu-id="85f2e-135">使用具名用戶端</span><span class="sxs-lookup"><span data-stu-id="85f2e-135">Use Named Clients</span></span>
- <span data-ttu-id="85f2e-136">使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="85f2e-136">Use Typed Clients</span></span>
- <span data-ttu-id="85f2e-137">使用產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="85f2e-137">Use Generated Clients</span></span>

<span data-ttu-id="85f2e-138">為了簡潔起見，本指南說明最具結構化的使用方式 `IHttpClientFactory` ，也就是使用具型別用戶端 (Service Agent 模式) 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="85f2e-139">不過，所有選項都記載于本文中，並且目前列在 [涵蓋 `IHttpClientFactory` 使用](/aspnet/core/fundamentals/http-requests#consumption-patterns)方式的本文中。</span><span class="sxs-lookup"><span data-stu-id="85f2e-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="85f2e-140">如何搭配使用具類型的用戶端與 IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="85f2e-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="85f2e-141">那麼，什麼是「具型別用戶端」？</span><span class="sxs-lookup"><span data-stu-id="85f2e-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="85f2e-142">這只是 `HttpClient` 針對某些特定用途預先設定的。</span><span class="sxs-lookup"><span data-stu-id="85f2e-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="85f2e-143">這種設定可以包含特定值，例如基礎伺服器、HTTP 標頭或超時時間。</span><span class="sxs-lookup"><span data-stu-id="85f2e-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="85f2e-144">下圖顯示具型別用戶端如何搭配 `IHttpClientFactory` 使用：</span><span class="sxs-lookup"><span data-stu-id="85f2e-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![顯示如何搭配使用具型別用戶端與 IHttpClientFactory 的圖表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="85f2e-146">**圖 8-4**。</span><span class="sxs-lookup"><span data-stu-id="85f2e-146">**Figure 8-4**.</span></span> <span data-ttu-id="85f2e-147">搭配 `IHttpClientFactory` 具型別用戶端類別使用。</span><span class="sxs-lookup"><span data-stu-id="85f2e-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="85f2e-148">在上圖中， `ClientService` 控制器或用戶端程式代碼所使用的 () 使用 `HttpClient` 已註冊的所建立的 `IHttpClientFactory` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="85f2e-149">此 factory 會將 `HttpMessageHandler` 從集區指派給 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="85f2e-150">`HttpClient` `IHttpClientFactory` 使用擴充方法在 DI 容器中註冊時，可以使用 Polly 的原則來設定 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="85f2e-151">若要設定上述結構，請 <xref:System.Net.Http.IHttpClientFactory> 安裝 `Microsoft.Extensions.Http` 包含擴充方法的 NuGet 套件，以新增您的應用程式 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="85f2e-152">這個擴充方法會註冊內部 `DefaultHttpClientFactory` 類別，作為介面的 singleton `IHttpClientFactory` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="85f2e-153">它為 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 定義暫時性設定。</span><span class="sxs-lookup"><span data-stu-id="85f2e-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="85f2e-154">此訊息處理常式 (<xref:System.Net.Http.HttpMessageHandler> 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。</span><span class="sxs-lookup"><span data-stu-id="85f2e-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="85f2e-155">在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="85f2e-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="85f2e-156">如先前的程式碼所示，註冊用戶端服務會讓 `DefaultClientFactory` 建立 `HttpClient` 每個服務的標準。</span><span class="sxs-lookup"><span data-stu-id="85f2e-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="85f2e-157">您也可以在註冊中新增實例專屬設定（例如，設定基底位址），並新增一些復原原則，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="85f2e-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="85f2e-158">就此範例而言，您可以在下一個程式碼中看到上述其中一個原則：</span><span class="sxs-lookup"><span data-stu-id="85f2e-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="85f2e-159">您可以在 [下一篇文章](implement-http-call-retries-exponential-backoff-polly.md)中找到更多有關使用 Polly 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="85f2e-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="85f2e-160">HttpClient 存留期</span><span class="sxs-lookup"><span data-stu-id="85f2e-160">HttpClient lifetimes</span></span>

<span data-ttu-id="85f2e-161">每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="85f2e-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="85f2e-162">但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。</span><span class="sxs-lookup"><span data-stu-id="85f2e-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="85f2e-163">處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。</span><span class="sxs-lookup"><span data-stu-id="85f2e-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="85f2e-164">有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。</span><span class="sxs-lookup"><span data-stu-id="85f2e-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="85f2e-165">集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。</span><span class="sxs-lookup"><span data-stu-id="85f2e-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="85f2e-166">預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。</span><span class="sxs-lookup"><span data-stu-id="85f2e-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="85f2e-167">若要覆寫它，請在建立用戶端時所傳回的 <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="85f2e-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="85f2e-168">每個具型別用戶端都可以設定自己的處理常式存留期值。</span><span class="sxs-lookup"><span data-stu-id="85f2e-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="85f2e-169">將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。</span><span class="sxs-lookup"><span data-stu-id="85f2e-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="85f2e-170">實作使用已插入和已設定之 HttpClient 的具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="85f2e-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="85f2e-171">在上一個步驟中，您必須定義您的型別用戶端類別，例如範例程式碼中的類別，例如 ' BasketService '、' CatalogService '、' Orderingservice 等等 ' 等等。-具型別用戶端是可接受 `HttpClient` 透過) 其函式插入之物件 (的類別，並使用它來呼叫某些遠端 HTTP 服務。</span><span class="sxs-lookup"><span data-stu-id="85f2e-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="85f2e-172">例如：</span><span class="sxs-lookup"><span data-stu-id="85f2e-172">For example:</span></span>

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

<span data-ttu-id="85f2e-173">範例) 中的具型別用戶端 (`CatalogService` 是由 DI (相依性插入) 所啟動，這表示除了之外，它也可以接受其函式中任何已註冊的服務 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="85f2e-174">具型別用戶端實際上是暫時性物件，這表示每次需要一個新的實例時，就會建立一個新的實例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="85f2e-175">它會在每次建立新的實例時收到新的 `HttpClient` 實例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="85f2e-176">不過， `HttpMessageHandler` 集區中的物件是由多個實例重複使用的物件 `HttpClient` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="85f2e-177">使用具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="85f2e-177">Use your Typed Client classes</span></span>

<span data-ttu-id="85f2e-178">最後，一旦實作為型別類別之後，您就可以將它們註冊並設定為 `AddHttpClient()` 。</span><span class="sxs-lookup"><span data-stu-id="85f2e-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="85f2e-179">之後，您可以使用它們，無論是透過 DI 插入服務。</span><span class="sxs-lookup"><span data-stu-id="85f2e-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="85f2e-180">例如，在 Razor 頁面程式碼或 MVC web 應用程式的控制器中，如下列 eShopOnContainers 程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="85f2e-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="85f2e-181">到目前為止，上述程式碼片段僅顯示執行一般 HTTP 要求的範例。</span><span class="sxs-lookup"><span data-stu-id="85f2e-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="85f2e-182">但是，在下列各節中，「魔術」會顯示所有由提出的 HTTP 要求如何 `HttpClient` 具有復原性原則，例如以指數輪詢、斷路器、使用驗證權杖的安全性功能，甚至是其他任何自訂功能的重試。</span><span class="sxs-lookup"><span data-stu-id="85f2e-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="85f2e-183">而且所有這些都可以藉由新增原則，並將處理常式委派給已註冊的型別用戶端來完成。</span><span class="sxs-lookup"><span data-stu-id="85f2e-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="85f2e-184">其他資源</span><span class="sxs-lookup"><span data-stu-id="85f2e-184">Additional resources</span></span>

- <span data-ttu-id="85f2e-185">**使用 .NET Core 中的 HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="85f2e-185">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="85f2e-186">**HttpClientFactory GitHub 存放庫中的原始程式碼 `dotnet/extensions`**</span><span class="sxs-lookup"><span data-stu-id="85f2e-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="85f2e-187">**Polly (.NET 復原和暫時性錯誤處理程式庫)**</span><span class="sxs-lookup"><span data-stu-id="85f2e-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="85f2e-188">\*\*使用 IHttpClientFactory 而不使用相依性插入 (GitHub 問題) \*\*</span><span class="sxs-lookup"><span data-stu-id="85f2e-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="85f2e-189">[上一個](implement-resilient-entity-framework-core-sql-connections.md) 
>[下一步](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="85f2e-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
