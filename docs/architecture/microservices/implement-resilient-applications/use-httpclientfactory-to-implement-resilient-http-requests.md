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
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a>使用 IHttpClientFactory 實現彈性 HTTP 要求

<xref:System.Net.Http.IHttpClientFactory>是由 、`DefaultHttpClientFactory`自 .NET Core 2.1 起提供的具有意見性的工廠實施的合同，<xref:System.Net.Http.HttpClient>用於創建要在應用程式中使用的實例。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 中原始 HttpClient 類別的問題

原始類和已知<xref:System.Net.Http.HttpClient>類可以很容易地使用，但在某些情況下，許多開發人員沒有正確使用它。

雖然`IDisposable`類實現 ，但不傾向于`using`在語句中聲明和具現化它，因為當`HttpClient`物件被釋放時，不會立即釋放基礎通訊端，這可能導致_通訊端耗盡_問題。 有關此問題的詳細資訊，請參閱您[使用的 HttpClient 錯誤的博客文章，它破壞了您的軟體](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)。

因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。 為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。 該問題會導致 `SocketException` 錯誤。 解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](../../../csharp/tutorials/console-webapiclient.md)中所述。 對於每天運行幾次的短壽命主控台應用或類似應用，這可能是一個很好的解決方案。

開發人員遇到的另一個問題是，在長時間運行的進程中使用`HttpClient`共用實例時。 在 HttpClient 具現化為單例或靜態物件的情況下，它無法處理 dotnet/corefx GitHub 存儲庫[本期](https://github.com/dotnet/corefx/issues/11224)中描述的 DNS 更改。

但是，問題本身`HttpClient`並不是真正的問題，而是[HttpClient 的預設建構函式](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)，因為它創建了一個新的具體實例<xref:System.Net.Http.HttpMessageHandler>，該實例具有*通訊端耗盡*和上面提到的 DNS 更改問題。

為了解決上述問題並使`HttpClient`實例易於管理，.NET Core 2.1 引入了<xref:System.Net.Http.IHttpClientFactory>可用於通過依賴項注入 （DI） 在應用中配置`HttpClient`和創建實例的介面。 它還為基於 Polly 的中介軟體提供了擴展，以利用 HttpClient 中委派處理常式。

[Polly](http://www.thepollyproject.org/)是一個瞬態故障處理庫，通過流暢且執行緒安全的方式使用某些預定義的策略，可説明開發人員為其應用程式增加恢復能力。

## <a name="benefits-of-using-ihttpclientfactory"></a>使用 IHttpClientFactory 的好處

當前實現的 還<xref:System.Net.Http.IHttpClientFactory>實現了<xref:System.Net.Http.IHttpMessageHandlerFactory>，提供了以下好處：

- 提供用於命名和配置邏輯`HttpClient`物件的中心位置。 例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。
- 通過授權處理常式`HttpClient`和實現基於 Polly 的中介軟體來利用 Polly 的彈性策略，將傳出中介軟體的概念編纂成。
- `HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。 您可以將 HTTP 用戶端註冊到工廠，也可以使用 Polly 處理常式對重試、斷路器等使用 Polly 策略。
- 管理的生存<xref:System.Net.Http.HttpMessageHandler>期，以避免自己管理`HttpClient`存留期時可能出現的上述問題。

> [!TIP]
> DI`HttpClient`注入的實例可以安全地釋放，因為關聯的`HttpMessageHandler`實例由工廠管理。 事實上，從 DI 的角度來看`HttpClient`，注入的實例*是範圍*的。

> [!NOTE]
> （ `IHttpClientFactory` `DefaultHttpClientFactory`） 的實現與`Microsoft.Extensions.DependencyInjection`NuGet 包中的 DI 實現緊密關聯。 有關使用其他 DI 容器的詳細資訊，請參閱此[GitHub 討論](https://github.com/dotnet/extensions/issues/1345)。

## <a name="multiple-ways-to-use-ihttpclientfactory"></a>使用 IHttpClientFactory 的多種方法

有多種方式可在您的應用程式中使用 `IHttpClientFactory`：

- 基本使用方式
- 使用具名用戶端
- 使用具型別用戶端
- 使用產生的用戶端

為了簡潔起見，本指南顯示了最結構化的使用`IHttpClientFactory`方式，即使用類型用戶端（服務代理模式）。 但是，所有選項都記錄在案，並且當前在[本文中列出了有關`IHttpClientFactory`用法](/aspnet/core/fundamentals/http-requests#consumption-patterns)。

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a>如何使用 IHttpClientFactory 的鍵入用戶端

那麼，什麼是「具型別用戶端」？ 它只是一個`HttpClient`預配置用於特定用途。 此配置可以包括特定值，如基本伺服器、HTTP 標頭或超時。

下圖顯示具型別用戶端如何搭配 `IHttpClientFactory` 使用：

![顯示類型用戶端如何與 IHttpClientFactory 一起使用的圖表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

**圖 8-4**。 與`IHttpClientFactory`類型用戶端類一起使用。

在上圖中，（`ClientService`由控制器或用戶端代碼使用）使用由註冊的`HttpClient``IHttpClientFactory`創建的 。 這家工廠將 從`HttpMessageHandler`池分配 到`HttpClient`。 在`HttpClient`使用擴充方法`IHttpClientFactory`<xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>註冊 DI 容器中 時，可以使用 Polly 的策略配置 。

要配置上述結構，請通過<xref:System.Net.Http.IHttpClientFactory>安裝包含<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>的擴充方法`Microsoft.Extensions.Http`的<xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient*>NuGet 包在應用程式中添加。 此擴充方法註冊內部`DefaultHttpClientFactory`類，以用作介面`IHttpClientFactory`的單例。 它為 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 定義暫時性設定。 此訊息處理常式 (<xref:System.Net.Http.HttpMessageHandler> 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。

在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

註冊以前代碼所示的用戶端服務，使為每個服務`DefaultClientFactory`創建標準。 `HttpClient`

您還可以在註冊中添加特定于實例的配置，例如配置基本位址，並添加一些恢復性策略，如以下代碼所示：

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

僅出於示例，您可以在下一個代碼中看到上述策略之一：

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

您可以在[下一篇文章中](implement-http-call-retries-exponential-backoff-polly.md)找到有關使用 Polly 的更多詳細資訊。

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

作為前面的步驟，您需要定義類型用戶端類，例如示例代碼中的類，如"購物服務"、"目錄服務"、"訂購服務"等 — 類型用戶端是一個接受`HttpClient`物件（通過其建構函式注入）並用它來調用某些遠端 HTTP 服務的類。 例如：

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

鍵入的用戶端（`CatalogService`在示例中）由 DI（依賴注入）啟動，這意味著除了`HttpClient`之外，它可以接受其建構函式中的任何註冊服務。

具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。 但是，`HttpMessageHandler`池中的物件是多個`HttpClient`實例重用的物件。

### <a name="use-your-typed-client-classes"></a>使用具型別用戶端類別

最後，一旦實現了類型化類並註冊並配置了它們`AddHttpClient()`，就可以在 DI 注入服務的任何位置使用它們。 例如，在 MVC Web 應用的 Razor 頁面代碼或控制器中，如 eShopOn 容器中的以下代碼所示：

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

至此，顯示的代碼只是執行常規 Http 請求，但"神奇"出現在以下各節中，其中，只需將策略和處理常式委派到已註冊的 Typed 用戶端，所有要執行的`HttpClient`HTTP 要求都會考慮彈性策略，例如使用指數回退、斷路器或任何其他自訂委派處理常式來實現其他安全功能，例如使用身份驗證權杖或任何其他自訂功能。

## <a name="additional-resources"></a>其他資源

- **使用 .NET Core 中的 HttpClientFactory**  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- **GitHub 存儲庫中的`dotnet/extensions`HttpClientFactory 原始程式碼**  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- **Polly (.NET 復原和暫時性錯誤處理程式庫)**  
  <http://www.thepollyproject.org/>
  
- **使用 IHttpClientFactory 而不注入依賴項（GitHub 問題）**  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
>[上一個](implement-resilient-entity-framework-core-sql-connections.md)
>[下一個](implement-http-call-retries-exponential-backoff-polly.md)
