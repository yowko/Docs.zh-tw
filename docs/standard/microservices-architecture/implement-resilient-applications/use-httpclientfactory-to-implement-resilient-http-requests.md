---
title: 使用 HttpClientFactory 實作復原 HTTP 要求
description: 了解如何使用 HttpClientFactory，自 .NET Core 2.1 開始提供，可用來建立 `HttpClient` 執行個體，方便您在應用程式中使用。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 6af30ae3b5111e026be6ec89d266338b88cf22b2
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362637"
---
# <a name="use-httpclientfactory-to-implement-resilient-http-requests"></a>使用 HttpClientFactory 實作復原 HTTP 要求

`HttpClientFactory` 是意向明確的處理站，自 .NET Core 2.1 開始提供，可用來建立要在您應用程式中使用的 <xref:System.Net.Http.HttpClient> 執行個體。

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a>.NET Core 中原始 HttpClient 類別的問題

已知的原始 [HttpClient](/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) 類別使用方式簡單，但在某些情況下，許多開發人員都沒有正確地使用它。 

第一個問題是，這個類別是可處置項目，將它與 `using` 陳述式搭配使用不是最好的選擇，因為即使您處置 `HttpClient` 物件，底層通訊端也不會立即釋出，而且可能會導致所謂「通訊端耗盡」的嚴重問題。 如需有關此問題的詳細資訊，請參閱[您使用 HttpClient 的方法錯誤而導致軟體不穩定](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) 部落格文章 (英文)。

因此，您應該將 `HttpClient` 具現化一次，然後在整個應用程式生命週期中重複使用。 為每個要求具現化 `HttpClient` 類別將會在負載過重時耗盡可用的通訊端數目。 該問題會導致 `SocketException` 錯誤。 解決該問題的可能方法為建立 `HttpClient` 物件做為單一物件或靜態物件，如 [Microsoft 關於 HttpClient 用法的文章](/dotnet/csharp/tutorials/console-webapiclient)中所述。 

但是將 `HttpClient` 做為單一物件或靜態物件時會出現第二個問題。 在此案例中，單一或靜態 `HttpClient` 不會理會 DNS 變更，如 [.NET Core GitHub 存放庫提及的問題](https://github.com/dotnet/corefx/issues/11224)中所述。 

為解決所述的那些問題並更輕鬆地管理 `HttpClient` 執行個體，.NET Core 2.1 提供一個新的 `HttpClientFactory`，它也可與 Polly 整合來實作復原 HTTP 呼叫。   

## <a name="what-is-httpclientfactory"></a>什麼是 HttpClientFactory

`HttpClientFactory` 的設計宗旨是：

- 提供一個集中位置以便命名及設定邏輯 HttpClients。 例如，您可以設定一個已預先設定為存取特定微服務的用戶端 (服務代理程式)。
- 透過委派 `HttpClient` 中的處理常式和實作 Polly 型中介軟體以利用 Polly 原則用於復原，來編纂連出中介軟體的概念。
- `HttpClient` 已經有委派可針對傳出 HTTP 要求連結在一起之處理常式的概念。 您將 http 用戶端註冊到處理站，而且您可以使用允許 Polly 原則用於重試、斷路器等等的 Polly 處理常式。
- 管理 HttpClientMessageHandlers 存留期，以避免您自己管理 `HttpClient` 存留期時可能發生的上述問題。 

## <a name="multiple-ways-to-use-httpclientfactory"></a>使用 HttpClientFactory 的多種方式

有多種方式可在您的應用程式中使用 `HttpClientFactory`：

- 直接使用 `HttpClientFactory`
- 使用具名用戶端
- 使用具型別用戶端
- 使用產生的用戶端

為了簡潔起見，此指導方針展示如何以結構化程度最高的方式使用 `HttpClientFactory`，也就是使用具型別用戶端 (服務代理程式模式)，但是我們已記錄所有選項，而且目前已詳列在這篇[涵蓋 HttpClientFactory 用法的文章](/aspnet/core/fundamentals/http-requests?#consumption-patterns)中。  

## <a name="how-to-use-typed-clients-with-httpclientfactory"></a>如何搭配 HttpClientFactory 使用具型別用戶端

那麼，什麼是「具型別用戶端」？ 它只是 `DefaultHttpClientFactory` 插入時所設定的一個 `HttpClient`。

下圖顯示具型別用戶端如何搭配 `HttpClientFactory` 使用：

![ClientService (控制器或用戶端程式碼所使用) 會使用由已註冊的 IHttpClientFactory 所建立的 HttpClient。 此處理站會從它管理的集區指派一個 HttpMessageHandler 給 HttpClient。 使用擴充方法 AddHttpClient 在 DI 容器中註冊 IHttpClientFactory 時，可以使用 Polly 的原則設定 HttpClient。](./media/image3.5.png)

**圖 8-4**。 搭配具型別用戶端類別使用 HttpClientFactory。

首先，在應用程式中設定 `HttpClientFactory`，加入對 `Microsoft.Extensions.Http` 的參考，其中包括 `IServiceCollection` 的 `AddHttpClient()` 擴充方法。 這個擴充方法註冊將用來做為介面 `IHttpClientFactory` 之單一物件的 `DefaultHttpClientFactory`。 它為 `HttpMessageHandlerBuilder` 定義暫時性設定。 此訊息處理常式 (`HttpMessageHandler` 物件) 取自集區，供處理站傳回的 `HttpClient` 使用。

在下一個程式碼中，您可以看到如何使用 `AddHttpClient()` 來註冊需要使用 `HttpClient` 的具型別用戶端 (服務代理程式)。

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

如先前的程式碼所示，註冊用戶端服務，讓 `DefaultClientFactory` 建立特別針對每個服務設定的 `HttpClient`，我們將在下一個段落中說明。

只要透過 `AddHttpClient()` 註冊您的用戶端服務類別，將插入您類別中的 `HttpClient` 物件將使用註冊時所提供的設定和原則。 在以下各節中，您將會看到那些原則，如 Polly 的重試或斷路器。

### <a name="httpclient-lifetimes"></a>HttpClient 存留期

每次您從 `IHttpClientFactory` 取得 `HttpClient` 物件時，都會傳回一個新的執行個體。 但只要 `HttpMessageHandler` 的存留期間尚未過期，每個 `HttpClient` 就都會使用 `HttpMessageHandler`，它會由 `IHttpClientFactory` 組成集區並重複使用以減少資源耗用量。

處理常式的集合是需要的做法，因為每個處理常式通常會管理自己的基礎 HTTP 連線；建立比所需數目更多的處理常式可能會導致連線延遲。 有些處理常式也會保持連線無限期地開啟，這可能導致處理常式無法對 DNS 變更回應。

集區中的 `HttpMessageHandler` 物件有存留期，也就是集區中該 `HttpMessageHandler` 執行個體可重複使用的時間長度。 預設值為 2 分鐘，但是可針對各個具型別用戶端分別覆寫。 若要覆寫它，請在建立用戶端時所傳回的 `IHttpClientBuilder` 上呼叫 `SetHandlerLifetime()`，如下列程式碼所示：

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

每個具型別用戶端都可以設定自己的處理常式存留期值。 將存留期設定成 `InfiniteTimeSpan` 以停用處理常式到期時間。

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a>實作使用已插入和已設定之 HttpClient 的具型別用戶端類別

在上一個步驟中，您必須先定義具型別用戶端類別，例如範例程式碼中的類別，像是 'BasketService'、'CatalogService'、'OrderingService' 等等，具型別用戶端是接受 `HttpClient` 物件 (透過建構函式插入) 並使用該物件來呼叫某些遠端 HTTP 服務的類別。 例如：

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

具型別用戶端 (範例中的 CatalogService) 由 DI (相依性插入) 啟用，這表示除了 HttpClient 之外，它可以接受其建構函式中任何已註冊的服務。

具型別用戶端實際上是暫時性物件，也就是說只要需要就會建立新的執行個體，而且每次建構它時都會收到一個新的 `HttpClient` 執行個體。 不過，集區中的 HttpMessageHandler 物件是可讓多個 Http 要求重複使用的物件。

### <a name="use-your-typed-client-classes"></a>使用具型別用戶端類別

最後，實作類型類別並使用 AddHttpClient() 註冊之後，即可在 DI 插入的服務中隨意使用它，例如在任何 Razor 頁面程式碼或任何 MVC Web 應用程式控制器，就像來自 eShopOnContainers 的下列程式碼一樣。

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

到目前為止，顯示的程式碼只是執行一般 Http 要求，但下面幾節才是神奇的地方，只需新增原則及委派處理常式到已註冊的具型別用戶端，將由 `HttpClient` 完成的所有 HTTP 要求，在運作時會考慮使用帳戶復原原則 (例如利用指數輪詢和斷路器來重試)，或是任何其他自訂委派處理常式來實作其他安全性功能 (例如使用驗證權杖) 或任何其他自訂功能。 

## <a name="additional-resources"></a>其他資源

- **使用 .NET Core 2.1 中的 HttpClientFactory**\
  [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)

- **HttpClientFactory GitHub 存放庫**\
  [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)

>[!div class="step-by-step"]
>[上一頁](explore-custom-http-call-retries-exponential-backoff.md)
>[下一頁](implement-http-call-retries-exponential-backoff-polly.md)