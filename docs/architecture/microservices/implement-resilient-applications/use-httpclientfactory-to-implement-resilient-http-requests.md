---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 瞭解如何使用 .NET Core 2.1 之後提供的 IHttpClientFactory 來建立 `HttpClient` 實例，讓您輕鬆地在應用程式中使用。
ms.date: 08/31/2020
ms.openlocfilehash: c54965a9bbb700cfb1f14150773c2df45d109c39
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678812"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>使用 HttpClientFactory 實作復原 HTTP 要求

<xref:System.Net.Http.IHttpClientFactory> 是 `DefaultHttpClientFactory` 實作為固定 factory （自 .Net Core 2.1 起提供）的合約，可用來建立 <xref:System.Net.Http.HttpClient> 要在應用程式中使用的實例。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 中原始 HttpClient 類別的問題

您 <xref:System.Net.Http.HttpClient> 可以輕鬆地使用原始和知名的類別，但在某些情況下，許多開發人員都沒有正確使用它。

雖然此類別 `IDisposable` 會在語句中執行、宣告和具現化，但不建議您這樣做， `using` 因為當 `HttpClient` 物件被處置時，不會立即釋放基礎通訊端，這可能會導致 _通訊端耗盡_ 問題。 如需有關此問題的詳細資訊，請參閱 [使用 HttpClient 錯誤的 blog 文章，並不穩定您的軟體](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。

因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。 為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。 該問題會導致 `SocketException` 錯誤。 解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。 這是適用于短期的主控台應用程式或類似的解決方案，其會在一天內執行數次。

開發人員遇到的另一個問題，就是在長時間執行的進程中使用的共用實例 `HttpClient` 。 在 HttpClient 具現化為單一或靜態物件的情況下，它無法處理 DNS 變更，如此 dotnet/runtime GitHub 存放庫的 [問題](https://github.com/dotnet/runtime/issues/18348) 所述。

不過，這個問題並不是 `HttpClient` 每個 se 都有問題，而是使用 [預設的 HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)函式，因為它會建立一個新的具體實例 <xref:System.Net.Http.HttpMessageHandler> ，也就是有 *通訊端耗盡* 和 DNS 變更上述問題的實例。

為了解決上述問題，並讓實例可供 `HttpClient` 管理，.Net Core 2.1 引進了 <xref:System.Net.Http.IHttpClientFactory> 介面，可透過相依性 `HttpClient` 插入 (DI) ，在應用程式中設定和建立實例。 它也提供 Polly 型中介軟體的延伸模組，以利用 HttpClient 中委派的處理常式。

[Polly](http://www.thepollyproject.org/) 是暫時性錯誤處理程式庫，可協助開發人員以流暢且安全線程的方式使用一些預先定義的原則，來為應用程式新增復原功能。

## <a name="benefits-of-using-ihttpclientfactory"></a>使用 IHttpClientFactory 的優點

目前執行的 <xref:System.Net.Http.IHttpClientFactory> 也會 <xref:System.Net.Http.IHttpMessageHandlerFactory> 提供下列優點：

- 提供命名和設定邏輯物件的集中位置 `HttpClient` 。 例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。
- 透過在中委派處理常式 `HttpClient` ，並執行以 Polly 為基礎的中介軟體，以利用 Polly 的原則來復原，以編寫傳出中介軟體的概念。
- `HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。 您可以將 HTTP 用戶端註冊至 factory，而且可以使用 Polly 處理常式來使用 Polly 原則來重試、CircuitBreakers 等等。
- 管理的存留期， <xref:System.Net.Http.HttpMessageHandler> 以避免在自行管理存留期時可能發生的問題/問題 `HttpClient` 。

> [!TIP]
> `HttpClient`DI 插入的實例可以安全地處置，因為相關聯的 `HttpMessageHandler` 是由 factory 管理。 事實上，插入 `HttpClient` 的實例的 *範圍* 是從 DI 的觀點來看。

> [!NOTE]
> `IHttpClientFactory` () 的執行 `DefaultHttpClientFactory` 會緊密地系結至 NuGet 套件中的 DI 實作為 `Microsoft.Extensions.DependencyInjection` 。 如需使用其他 DI 容器的詳細資訊，請參閱此 [GitHub 討論](https://github.com/dotnet/extensions/issues/1345)。

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>使用 IHttpClientFactory 的多種方式

有多種方式可在您的應用程式中使用 `IHttpClientFactory`：

- 基本使用方式
- 使用具名用戶端
- 使用具型別用戶端
- 使用產生的用戶端

為了簡潔起見，本指南說明最具結構化的使用方式 `IHttpClientFactory` ，也就是使用具型別用戶端 (Service Agent 模式) 。 不過，所有選項都記載于本文中，並且目前列在 [涵蓋 `IHttpClientFactory` 使用](/aspnet/core/fundamentals/http-requests#consumption-patterns)方式的本文中。

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>如何搭配使用具類型的用戶端與 IHttpClientFactory

那麼，什麼是「具型別用戶端」？ 這只是 `HttpClient` 針對某些特定用途預先設定的。 這種設定可以包含特定值，例如基礎伺服器、HTTP 標頭或超時時間。

下圖顯示具型別用戶端如何搭配 `IHttpClientFactory` 使用：

![顯示如何搭配使用具型別用戶端與 IHttpClientFactory 的圖表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**圖 8-4**。 搭配 `IHttpClientFactory` 具型別用戶端類別使用。

在上圖中， `ClientService` 控制器或用戶端程式代碼所使用的 () 使用 `HttpClient` 已註冊的所建立的 `IHttpClientFactory` 。 此 factory 會將 `HttpMessageHandler` 從集區指派給 `HttpClient` 。 `HttpClient` `IHttpClientFactory` 使用擴充方法在 DI 容器中註冊時，可以使用 Polly 的原則來設定 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> 。

若要設定上述結構，請 <xref:System.Net.Http.IHttpClientFactory> 安裝 `Microsoft.Extensions.Http` 包含擴充方法的 NuGet 套件，以新增您的應用程式 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 。 這個擴充方法會註冊內部 `DefaultHttpClientFactory` 類別，作為介面的 singleton `IHttpClientFactory` 。 它為 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 定義暫時性設定。 此訊息處理常式 (<xref:System.Net.Http.HttpMessageHandler> 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。

在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

如先前的程式碼所示，註冊用戶端服務會讓 `DefaultClientFactory` 建立 `HttpClient` 每個服務的標準。

您也可以在註冊中新增實例專屬設定（例如，設定基底位址），並新增一些復原原則，如下列程式碼所示：

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

就此範例而言，您可以在下一個程式碼中看到上述其中一個原則：

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

您可以在 [下一篇文章](implement-http-call-retries-exponential-backoff-polly.md)中找到更多有關使用 Polly 的詳細資料。

### <a name="httpclient-lifetimes"></a>HttpClient 存留期

每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。 但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。

處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。 有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。

集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。 預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。 若要覆寫它，請在建立用戶端時所傳回的 <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

每個具型別用戶端都可以設定自己的處理常式存留期值。 將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>實作使用已插入和已設定之 HttpClient 的具型別用戶端類別

在上一個步驟中，您必須定義您的型別用戶端類別，例如範例程式碼中的類別，例如 ' BasketService '、' CatalogService '、' Orderingservice 等等 ' 等等。-具型別用戶端是可接受 `HttpClient` 透過) 其函式插入之物件 (的類別，並使用它來呼叫某些遠端 HTTP 服務。 例如：

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

範例) 中的具型別用戶端 (`CatalogService` 是由 DI (相依性插入) 所啟動，這表示除了之外，它也可以接受其函式中任何已註冊的服務 `HttpClient` 。

具型別用戶端實際上是暫時性物件，這表示每次需要一個新的實例時，就會建立一個新的實例。 它會在每次建立新的實例時收到新的 `HttpClient` 實例。 不過， `HttpMessageHandler` 集區中的物件是由多個實例重複使用的物件 `HttpClient` 。

### <a name="use-your-typed-client-classes"></a>使用具型別用戶端類別

最後，一旦實作為型別類別之後，您就可以將它們註冊並設定為 `AddHttpClient()` 。 之後，您可以使用它們，無論是透過 DI 插入服務。 例如，在 Razor 頁面程式碼或 MVC web 應用程式的控制器中，如下列 eShopOnContainers 程式碼所示：

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

到目前為止，上述程式碼片段僅顯示執行一般 HTTP 要求的範例。 但是，在下列各節中，「魔術」會顯示所有由提出的 HTTP 要求如何 `HttpClient` 具有復原性原則，例如以指數輪詢、斷路器、使用驗證權杖的安全性功能，甚至是其他任何自訂功能的重試。 而且所有這些都可以藉由新增原則，並將處理常式委派給已註冊的型別用戶端來完成。

## <a name="additional-resources"></a>其他資源

- **使用 .NET Core 中的 HttpClientFactory**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **HttpClientFactory GitHub 存放庫中的原始程式碼 `dotnet/extensions`**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**  
  <http://www.thepollyproject.org/>
  
- **使用 IHttpClientFactory 而不使用相依性插入 (GitHub 問題) **  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[上一個](implement-resilient-entity-framework-core-sql-connections.md) 
>[下一步](implement-http-call-retries-exponential-backoff-polly.md)
