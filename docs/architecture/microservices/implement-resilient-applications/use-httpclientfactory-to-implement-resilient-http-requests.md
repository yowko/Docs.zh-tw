---
title: 使用 IHttpClientFactory 實現彈性 HTTP 要求
description: 瞭解如何使用自 .NET Core 2.1 以來可用的 IHttpClientFactory`HttpClient`創建實例，從而便於您在應用程式中使用它。
ms.date: 03/03/2020
ms.openlocfilehash: 088fb6c7e10ad656247ee4065da5c13d383b2cf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847215"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="12e1f-103">使用 IHttpClientFactory 實現彈性 HTTP 要求</span><span class="sxs-lookup"><span data-stu-id="12e1f-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="12e1f-104"><xref:System.Net.Http.IHttpClientFactory>是由 、`DefaultHttpClientFactory`自 .NET Core 2.1 起提供的具有意見性的工廠實施的合同，<xref:System.Net.Http.HttpClient>用於創建要在應用程式中使用的實例。</span><span class="sxs-lookup"><span data-stu-id="12e1f-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="12e1f-105">.NET Core 中原始 HttpClient 類別的問題</span><span class="sxs-lookup"><span data-stu-id="12e1f-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="12e1f-106">原始類和已知<xref:System.Net.Http.HttpClient>類可以很容易地使用，但在某些情況下，許多開發人員沒有正確使用它。</span><span class="sxs-lookup"><span data-stu-id="12e1f-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="12e1f-107">雖然`IDisposable`類實現 ，但不傾向于`using`在語句中聲明和具現化它，因為當`HttpClient`物件被釋放時，不會立即釋放基礎通訊端，這可能導致_通訊端耗盡_問題。</span><span class="sxs-lookup"><span data-stu-id="12e1f-107">While this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="12e1f-108">有關此問題的詳細資訊，請參閱您[使用的 HttpClient 錯誤的博客文章，它破壞了您的軟體](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。</span><span class="sxs-lookup"><span data-stu-id="12e1f-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="12e1f-109">因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。</span><span class="sxs-lookup"><span data-stu-id="12e1f-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="12e1f-110">為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。</span><span class="sxs-lookup"><span data-stu-id="12e1f-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="12e1f-111">該問題會導致 `SocketException` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="12e1f-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="12e1f-112">解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="12e1f-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="12e1f-113">對於每天運行幾次的短壽命主控台應用或類似應用，這可能是一個很好的解決方案。</span><span class="sxs-lookup"><span data-stu-id="12e1f-113">This can be a good solution for short-lived console apps or similar that are run a few times a day.</span></span>

<span data-ttu-id="12e1f-114">開發人員遇到的另一個問題是，在長時間運行的進程中使用`HttpClient`共用實例時。</span><span class="sxs-lookup"><span data-stu-id="12e1f-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long running processes.</span></span> <span data-ttu-id="12e1f-115">在 HttpClient 具現化為單例或靜態物件的情況下，它無法處理 dotnet/corefx GitHub 存儲庫[本期](https://github.com/dotnet/corefx/issues/11224)中描述的 DNS 更改。</span><span class="sxs-lookup"><span data-stu-id="12e1f-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/corefx/issues/11224) of the dotnet/corefx GitHub repository.</span></span>

<span data-ttu-id="12e1f-116">但是，問題本身`HttpClient`並不是真正的問題，而是[HttpClient 的預設建構函式](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)，因為它創建了一個新的具體實例<xref:System.Net.Http.HttpMessageHandler>，該實例具有*通訊端耗盡*和上面提到的 DNS 更改問題。</span><span class="sxs-lookup"><span data-stu-id="12e1f-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="12e1f-117">為了解決上述問題並使`HttpClient`實例易於管理，.NET Core 2.1 引入了<xref:System.Net.Http.IHttpClientFactory>可用於通過依賴項注入 （DI） 在應用中配置`HttpClient`和創建實例的介面。</span><span class="sxs-lookup"><span data-stu-id="12e1f-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="12e1f-118">它還為基於 Polly 的中介軟體提供了擴展，以利用 HttpClient 中委派處理常式。</span><span class="sxs-lookup"><span data-stu-id="12e1f-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="12e1f-119">[Polly](http://www.thepollyproject.org/)是一個瞬態故障處理庫，通過流暢且執行緒安全的方式使用某些預定義的策略，可説明開發人員為其應用程式增加恢復能力。</span><span class="sxs-lookup"><span data-stu-id="12e1f-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="12e1f-120">使用 IHttpClientFactory 的好處</span><span class="sxs-lookup"><span data-stu-id="12e1f-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="12e1f-121">當前實現的 還<xref:System.Net.Http.IHttpClientFactory>實現了<xref:System.Net.Http.IHttpMessageHandlerFactory>，提供了以下好處：</span><span class="sxs-lookup"><span data-stu-id="12e1f-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="12e1f-122">提供用於命名和配置邏輯`HttpClient`物件的中心位置。</span><span class="sxs-lookup"><span data-stu-id="12e1f-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="12e1f-123">例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="12e1f-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="12e1f-124">通過授權處理常式`HttpClient`和實現基於 Polly 的中介軟體來利用 Polly 的彈性策略，將傳出中介軟體的概念編纂成。</span><span class="sxs-lookup"><span data-stu-id="12e1f-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="12e1f-125">`HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。</span><span class="sxs-lookup"><span data-stu-id="12e1f-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="12e1f-126">您可以將 HTTP 用戶端註冊到工廠，也可以使用 Polly 處理常式對重試、斷路器等使用 Polly 策略。</span><span class="sxs-lookup"><span data-stu-id="12e1f-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="12e1f-127">管理的生存<xref:System.Net.Http.HttpMessageHandler>期，以避免自己管理`HttpClient`存留期時可能出現的上述問題。</span><span class="sxs-lookup"><span data-stu-id="12e1f-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="12e1f-128">DI`HttpClient`注入的實例可以安全地釋放，因為關聯的`HttpMessageHandler`實例由工廠管理。</span><span class="sxs-lookup"><span data-stu-id="12e1f-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="12e1f-129">事實上，從 DI 的角度來看`HttpClient`，注入的實例*是範圍*的。</span><span class="sxs-lookup"><span data-stu-id="12e1f-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="12e1f-130">（ `IHttpClientFactory` `DefaultHttpClientFactory`） 的實現與`Microsoft.Extensions.DependencyInjection`NuGet 包中的 DI 實現緊密關聯。</span><span class="sxs-lookup"><span data-stu-id="12e1f-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="12e1f-131">有關使用其他 DI 容器的詳細資訊，請參閱此[GitHub 討論](https://github.com/dotnet/extensions/issues/1345)。</span><span class="sxs-lookup"><span data-stu-id="12e1f-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="12e1f-132">使用 IHttpClientFactory 的多種方法</span><span class="sxs-lookup"><span data-stu-id="12e1f-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="12e1f-133">有多種方式可在您的應用程式中使用 `IHttpClientFactory`：</span><span class="sxs-lookup"><span data-stu-id="12e1f-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="12e1f-134">基本使用方式</span><span class="sxs-lookup"><span data-stu-id="12e1f-134">Basic usage</span></span>
- <span data-ttu-id="12e1f-135">使用具名用戶端</span><span class="sxs-lookup"><span data-stu-id="12e1f-135">Use Named Clients</span></span>
- <span data-ttu-id="12e1f-136">使用具型別用戶端</span><span class="sxs-lookup"><span data-stu-id="12e1f-136">Use Typed Clients</span></span>
- <span data-ttu-id="12e1f-137">使用產生的用戶端</span><span class="sxs-lookup"><span data-stu-id="12e1f-137">Use Generated Clients</span></span>

<span data-ttu-id="12e1f-138">為了簡潔起見，本指南顯示了最結構化的使用`IHttpClientFactory`方式，即使用類型用戶端（服務代理模式）。</span><span class="sxs-lookup"><span data-stu-id="12e1f-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="12e1f-139">但是，所有選項都記錄在案，並且當前在[本文中列出了有關`IHttpClientFactory`用法](/aspnet/core/fundamentals/http-requests#consumption-patterns)。</span><span class="sxs-lookup"><span data-stu-id="12e1f-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="12e1f-140">如何使用 IHttpClientFactory 的鍵入用戶端</span><span class="sxs-lookup"><span data-stu-id="12e1f-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="12e1f-141">那麼，什麼是「具型別用戶端」？</span><span class="sxs-lookup"><span data-stu-id="12e1f-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="12e1f-142">它只是一個`HttpClient`預配置用於特定用途。</span><span class="sxs-lookup"><span data-stu-id="12e1f-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="12e1f-143">此配置可以包括特定值，如基本伺服器、HTTP 標頭或超時。</span><span class="sxs-lookup"><span data-stu-id="12e1f-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="12e1f-144">下圖顯示具型別用戶端如何搭配 `IHttpClientFactory` 使用：</span><span class="sxs-lookup"><span data-stu-id="12e1f-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![顯示類型用戶端如何與 IHttpClientFactory 一起使用的圖表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="12e1f-146">**圖 8-4**。</span><span class="sxs-lookup"><span data-stu-id="12e1f-146">**Figure 8-4**.</span></span> <span data-ttu-id="12e1f-147">與`IHttpClientFactory`類型用戶端類一起使用。</span><span class="sxs-lookup"><span data-stu-id="12e1f-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="12e1f-148">在上圖中，（`ClientService`由控制器或用戶端代碼使用）使用由註冊的`HttpClient``IHttpClientFactory`創建的 。</span><span class="sxs-lookup"><span data-stu-id="12e1f-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="12e1f-149">這家工廠將 從`HttpMessageHandler`池分配 到`HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="12e1f-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="12e1f-150">在`HttpClient`使用擴充方法`IHttpClientFactory`<xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>註冊 DI 容器中 時，可以使用 Polly 的策略配置 。</span><span class="sxs-lookup"><span data-stu-id="12e1f-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>.</span></span>

<span data-ttu-id="12e1f-151">要配置上述結構，請通過<xref:System.Net.Http.IHttpClientFactory>安裝包含<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>的擴充方法`Microsoft.Extensions.Http`的<xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>NuGet 包在應用程式中添加。</span><span class="sxs-lookup"><span data-stu-id="12e1f-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="12e1f-152">此擴充方法註冊內部`DefaultHttpClientFactory`類，以用作介面`IHttpClientFactory`的單例。</span><span class="sxs-lookup"><span data-stu-id="12e1f-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="12e1f-153">它為 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 定義暫時性設定。</span><span class="sxs-lookup"><span data-stu-id="12e1f-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="12e1f-154">此訊息處理常式 (<xref:System.Net.Http.HttpMessageHandler> 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。</span><span class="sxs-lookup"><span data-stu-id="12e1f-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="12e1f-155">在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。</span><span class="sxs-lookup"><span data-stu-id="12e1f-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="12e1f-156">註冊以前代碼所示的用戶端服務，使為每個服務`DefaultClientFactory`創建標準。 `HttpClient`</span><span class="sxs-lookup"><span data-stu-id="12e1f-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="12e1f-157">您還可以在註冊中添加特定于實例的配置，例如配置基本位址，並添加一些恢復性策略，如以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="12e1f-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="12e1f-158">僅出於示例，您可以在下一個代碼中看到上述策略之一：</span><span class="sxs-lookup"><span data-stu-id="12e1f-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="12e1f-159">您可以在[下一篇文章中](implement-http-call-retries-exponential-backoff-polly.md)找到有關使用 Polly 的更多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="12e1f-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="12e1f-160">HttpClient 存留期</span><span class="sxs-lookup"><span data-stu-id="12e1f-160">HttpClient lifetimes</span></span>

<span data-ttu-id="12e1f-161">每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="12e1f-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="12e1f-162">但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。</span><span class="sxs-lookup"><span data-stu-id="12e1f-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="12e1f-163">處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。</span><span class="sxs-lookup"><span data-stu-id="12e1f-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="12e1f-164">有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。</span><span class="sxs-lookup"><span data-stu-id="12e1f-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="12e1f-165">集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。</span><span class="sxs-lookup"><span data-stu-id="12e1f-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="12e1f-166">預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。</span><span class="sxs-lookup"><span data-stu-id="12e1f-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="12e1f-167">若要覆寫它，請在建立用戶端時所傳回的 <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="12e1f-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="12e1f-168">每個具型別用戶端都可以設定自己的處理常式存留期值。</span><span class="sxs-lookup"><span data-stu-id="12e1f-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="12e1f-169">將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。</span><span class="sxs-lookup"><span data-stu-id="12e1f-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="12e1f-170">實作使用已插入和已設定之 HttpClient 的具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="12e1f-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="12e1f-171">作為前面的步驟，您需要定義類型用戶端類，例如示例代碼中的類，如"購物服務"、"目錄服務"、"訂購服務"等 — 類型用戶端是一個接受`HttpClient`物件（通過其建構函式注入）並用它來調用某些遠端 HTTP 服務的類。</span><span class="sxs-lookup"><span data-stu-id="12e1f-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="12e1f-172">例如：</span><span class="sxs-lookup"><span data-stu-id="12e1f-172">For example:</span></span>

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

<span data-ttu-id="12e1f-173">鍵入的用戶端（`CatalogService`在示例中）由 DI（依賴注入）啟動，這意味著除了`HttpClient`之外，它可以接受其建構函式中的任何註冊服務。</span><span class="sxs-lookup"><span data-stu-id="12e1f-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="12e1f-174">具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="12e1f-174">A Typed Client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="12e1f-175">但是，`HttpMessageHandler`池中的物件是多個`HttpClient`實例重用的物件。</span><span class="sxs-lookup"><span data-stu-id="12e1f-175">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="12e1f-176">使用具型別用戶端類別</span><span class="sxs-lookup"><span data-stu-id="12e1f-176">Use your Typed Client classes</span></span>

<span data-ttu-id="12e1f-177">最後，一旦實現了類型化類並註冊並配置了它們`AddHttpClient()`，就可以在 DI 注入服務的任何位置使用它們。</span><span class="sxs-lookup"><span data-stu-id="12e1f-177">Finally, once you have your typed classes implemented and have them registered and configured with `AddHttpClient()`, you can use them wherever you can have services injected by DI.</span></span> <span data-ttu-id="12e1f-178">例如，在 MVC Web 應用的 Razor 頁面代碼或控制器中，如 eShopOn 容器中的以下代碼所示：</span><span class="sxs-lookup"><span data-stu-id="12e1f-178">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

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

<span data-ttu-id="12e1f-179">至此，顯示的代碼只是執行常規 Http 請求，但"神奇"出現在以下各節中，其中，只需將策略和處理常式委派到已註冊的 Typed 用戶端，所有要執行的`HttpClient`HTTP 要求都會考慮彈性策略，例如使用指數回退、斷路器或任何其他自訂委派處理常式來實現其他安全功能，例如使用身份驗證權杖或任何其他自訂功能。</span><span class="sxs-lookup"><span data-stu-id="12e1f-179">Up to this point, the code shown is just performing regular Http requests, but the 'magic' comes in the following sections where, just by adding policies and delegating handlers to your registered Typed Clients, all the HTTP requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="12e1f-180">其他資源</span><span class="sxs-lookup"><span data-stu-id="12e1f-180">Additional resources</span></span>

- <span data-ttu-id="12e1f-181">**使用 .NET Core 中的 HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="12e1f-181">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="12e1f-182">**GitHub 存儲庫中的`dotnet/extensions`HttpClientFactory 原始程式碼**</span><span class="sxs-lookup"><span data-stu-id="12e1f-182">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="12e1f-183">**Polly (.NET 復原和暫時性錯誤處理程式庫)**</span><span class="sxs-lookup"><span data-stu-id="12e1f-183">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="12e1f-184">**使用 IHttpClientFactory 而不注入依賴項（GitHub 問題）**</span><span class="sxs-lookup"><span data-stu-id="12e1f-184">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="12e1f-185">[上一個](implement-resilient-entity-framework-core-sql-connections.md)
>[下一個](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="12e1f-185">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
