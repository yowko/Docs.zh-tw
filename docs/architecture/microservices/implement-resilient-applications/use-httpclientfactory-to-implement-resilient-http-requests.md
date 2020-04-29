---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 瞭解如何使用 .NET Core 2.1 之後提供的 IHttpClientFactory 來建立`HttpClient`實例，讓您輕鬆地在應用程式中使用它。
ms.date: 03/03/2020
ms.openlocfilehash: ade26208a931faa456c8e267def2caef7a3f32de
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507295"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>使用 HttpClientFactory 實作復原 HTTP 要求

<xref:System.Net.Http.IHttpClientFactory>是由`DefaultHttpClientFactory`.net Core 2.1 開始提供的合約，可用於建立<xref:System.Net.Http.HttpClient>要在您的應用程式中使用的實例。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 中原始 HttpClient 類別的問題

您可以輕鬆地使用原始<xref:System.Net.Http.HttpClient>和知名的類別，但是在某些情況下，許多開發人員並不會正確地使用它。

雖然這個類別會`IDisposable`執行`using` ，但不建議在語句內宣告並具現化， `HttpClient`因為當物件被處置時，不會立即釋放基礎通訊端，這可能會導致_通訊端耗盡_的問題。 如需有關此問題的詳細資訊，請參閱[使用 HttpClient 錯誤](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)的 blog 文章，並不穩定您的軟體。

因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。 為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。 該問題會導致 `SocketException` 錯誤。 解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。 對於短期的主控台應用程式而言，這可能是很好的解決方案，或一天執行幾次的類似。

開發人員執行的另一個問題是`HttpClient`在長時間執行的進程中使用的共用實例。 在 HttpClient 具現化為單一或靜態物件的情況下，它無法處理 DNS 變更，如此 dotnet/執行時間 GitHub 存放庫[問題](https://github.com/dotnet/runtime/issues/18348)中所述。

不過，此問題並不是`HttpClient`因為每個 se，而是使用[HttpClient 的預設](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)函式，因為它會建立的<xref:System.Net.Http.HttpMessageHandler>新實體實例，這是具有*通訊端耗盡*和 DNS 變更的問題。

為了解決上述問題並讓`HttpClient`實例可供管理，.net Core 2.1 引進了<xref:System.Net.Http.IHttpClientFactory>介面，可用來透過相依性插入（DI `HttpClient` ）在應用程式中設定和建立實例。 它也提供 Polly 為基礎中介軟體的延伸模組，以利用 HttpClient 中的委派處理常式。

[Polly](http://www.thepollyproject.org/)是暫時性錯誤處理程式庫，可協助開發人員以流暢且安全線程的方式使用一些預先定義的原則，來為應用程式新增復原功能。

## <a name="benefits-of-using-ihttpclientfactory"></a>使用 IHttpClientFactory 的優點

目前的執行<xref:System.Net.Http.IHttpClientFactory>（也就是<xref:System.Net.Http.IHttpMessageHandlerFactory>）會提供下列優點：

- 提供用來命名和設定邏輯`HttpClient`物件的中央位置。 例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。
- 藉由委派中`HttpClient`的處理常式並執行以 Polly 為基礎的中介軟體，來編寫外寄中介軟體的概念，以利用 Polly 的復原原則。
- `HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。 您可以將 HTTP 用戶端註冊到處理站，而且您可以使用 Polly 處理常式，將 Polly 原則用於重試、斷路器等等。
- 管理的存留期<xref:System.Net.Http.HttpMessageHandler> ，以避免所提及的問題/在自行管理`HttpClient`生命週期時可能發生的問題。

> [!TIP]
> DI `HttpClient`所插入的實例可以安全地處置，因為相關聯`HttpMessageHandler`的是由處理站所管理。 事實上，插入`HttpClient`的實例的*範圍*是從 DI 觀點來看。

> [!NOTE]
> （）的執行會緊密地系結至`Microsoft.Extensions.DependencyInjection` NuGet 套件中的 DI 實作為關聯。`DefaultHttpClientFactory` `IHttpClientFactory` 如需使用其他 DI 容器的詳細資訊，請參閱此[GitHub 討論](https://github.com/dotnet/extensions/issues/1345)。

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>使用 IHttpClientFactory 的多種方式

有多種方式可在您的應用程式中使用 `IHttpClientFactory`：

- 基本使用方式
- 使用具名用戶端
- 使用具型別用戶端
- 使用產生的用戶端

為了簡潔起見，本指南說明最具結構化的使用`IHttpClientFactory`方式，也就是使用型別用戶端（服務代理程式模式）。 不過，所有選項都已記載，而且目前已列在本文中，[涵蓋`IHttpClientFactory`使用](/aspnet/core/fundamentals/http-requests#consumption-patterns)方式。

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>如何搭配 IHttpClientFactory 使用具類型的用戶端

那麼，什麼是「具型別用戶端」？ 這只`HttpClient`是針對某些特定用途預先設定的。 此設定可以包含特定的值，例如基礎伺服器、HTTP 標頭或時間輸出。

下圖顯示具型別用戶端如何搭配 `IHttpClientFactory` 使用：

![顯示型別用戶端如何搭配 IHttpClientFactory 使用的圖表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**圖 8-4**。 搭配`IHttpClientFactory`具型別用戶端類別使用。

在上圖中， `ClientService` （由控制器或用戶端程式代碼使用）會使用`HttpClient`已註冊`IHttpClientFactory`的所建立的。 這個 factory 會將`HttpMessageHandler`從集區指派至`HttpClient`。 使用`HttpClient`擴充方法`IHttpClientFactory` <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>在 DI 容器中註冊時，可以使用 Polly 的原則來設定。

若要設定上述結構，請<xref:System.Net.Http.IHttpClientFactory>安裝包含之`Microsoft.Extensions.Http` <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>擴充方法的 NuGet 套件，以在您的應用<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>程式中新增。 這個擴充方法會註冊內部`DefaultHttpClientFactory`類別，以作為介面`IHttpClientFactory`的 singleton 使用。 它為 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 定義暫時性設定。 此訊息處理常式 (<xref:System.Net.Http.HttpMessageHandler> 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。

在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

如先前的程式碼所示註冊用戶端服務，會`DefaultClientFactory`使每個`HttpClient`服務的建立一個標準。

您也可以在註冊中新增實例特定設定，例如設定基底位址，然後新增一些復原原則，如下列程式碼所示：

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

您可以在[下一篇文章](implement-http-call-retries-exponential-backoff-polly.md)中找到更多有關使用 Polly 的詳細資料。

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

在上一個步驟中，您必須定義具型別用戶端類別，例如範例程式碼中的類別，像是 ' BasketService '、' CatalogService '、' Orderingservice 等等 ' 等等。–具型別用戶端是接受`HttpClient`物件的類別（透過其函式插入），並使用它來呼叫一些遠端 HTTP 服務。 例如：

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

型別用戶端`CatalogService` （在此範例中為）會由 DI （相依性插入）啟動，這表示除了之外，它也可以接受其所有`HttpClient`在其函式中的已註冊服務。

具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。 不過，集`HttpMessageHandler`區中的物件是由多個`HttpClient`實例重複使用的物件。

### <a name="use-your-typed-client-classes"></a>使用具型別用戶端類別

最後，一旦您將具型`AddHttpClient()`別類別實作為，並使用進行登錄和設定之後，您就可以在任何可透過 DI 插入服務的地方使用它們。 例如，在 Razor 頁面程式碼或 MVC web 應用程式的控制器中，如下列 eShopOnContainers 程式碼所示：

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

到目前為止，顯示的程式碼只是執行一般的 Http 要求，但 ' 魔術 ' 出現在下列各節中，您只需新增原則並將處理常式委派給您已註冊的型別用戶端，完成`HttpClient`的所有 Http 要求都會進入復原原則，例如使用指數輪詢、斷路器重試，或任何其他自訂委派處理常式來執行額外的安全性功能，例如使用驗證權杖或任何其他自訂功能。

## <a name="additional-resources"></a>其他資源

- **使用 .NET Core 中的 HttpClientFactory**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **GitHub 存放庫中的`dotnet/extensions` HttpClientFactory 原始程式碼**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**  
  <http://www.thepollyproject.org/>
  
- **使用不具相依性插入的 IHttpClientFactory （GitHub 問題）**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[上一頁](implement-resilient-entity-framework-core-sql-connections.md)
>[下一頁](implement-http-call-retries-exponential-backoff-polly.md)
