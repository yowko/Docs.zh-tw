---
title: "建立簡單資料驅動 CRUD 微服務"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 建立簡單資料驅動 CRUD 微服務"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: be8644e45be8db88c99332476e74c5c968764c74
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>建立簡單資料驅動 CRUD 微服務

本節描述了如何建立可針對資料來源執行建立、讀取、更新及刪除 (CRUD) 作業的簡單微服務。

## <a name="designing-a-simple-crud-microservice"></a>設計簡單的 CRUD 微服務

從設計觀點來看，這種類型的容器化微服務非常簡單。 可能是要解決的問題相當簡單，或者可能其實作僅只是一種概念的證明。

![](./media/image4.png)

**圖 8-4**。 簡單 CRUD 微服務的內部設計

eShopOnContainers 應用程式範例的目錄微服務即為這種簡單資料驅動服務的範例。 這種類型的服務會在單一 ASP.NET Core Web API 專案中實作所有自身的功能，包括其資料模型的類別、商務邏輯，以及資料存取程式碼。 它也會將相關資料儲存在執行於 SQL Server 的資料庫中 (作為開發/測試用途的另一個容器)，但也可以是任何一般的 SQL Server 主機，如圖 8-5 所示。

![](./media/image5.png)

**圖 8-5**。 簡單資料驅動/CRUD 微服務設計

當您開發這種服務時，您只需要 [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) 及一個資料存取 API 或 ORM，像是 [Entity Framework Core](https://docs.microsoft.com/ef/core/index)。 您也可以透過 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) 自動產生 [Swagger](http://swagger.io/) 中繼資料來提供您服務提供之內容的描述，如下一節中所解釋的。

請注意，在 Docker 容器中執行像是 SQL Server 這種資料庫伺服器對開發環境來說是非常適合的，因為您可以設定所有的相依性並使其順利執行，而無須在雲端或內部部署環境佈建資料庫。 這在執行整合測試時會非常方便。 然而，針對生產環境，我們不建議在容器內執行資料庫伺服器，因為使用此方法，您通常無法取得高度的可用性。 針對 Azure 中的生產環境，通常建議您使用 Azure SQL DB 或任何其他可提供高度可用性及延展性的資料庫技術。 例如，若要採用 NoSQL，您可能會選擇 DocumentDB。

最後，藉由編輯 Dockerfile 和 docker-compose.yml 中繼檔案，您可以設定此容器映像建立的方式—使用的基底映像，以及設計設定例如內部及外部名稱和 TCP 連接埠。 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>使用 ASP.NET Core 實作簡單 CRUD 微服務

若要使用 .NET Core 及 Visual Studio 實作簡單 CRUD 微服務，您可以從建立簡單的 ASP.NET Core Web API 專案 (於 .NET Core 上執行，以便能在 Linux Docker 主機上執行) 開始，如圖 8-6 所示。

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**圖 8-6**。 在 Visual Studio 中建立 ASP.NET Core Web API 專案

建立專案之後，您可以使用 Entity Framework API 或其他 API，利用您在任何其他 Web API 專案上相同的方式，實作您的 MVC 控制器。 在新的 Web API 專案中，您可以看到該微服務的唯一相依性即是 ASP.NET Core 本身。 於內部裡，在 `Microsoft.AspNetCore.All` 相依性中，它會參考 Entity Framework 和許多其他的 .NET Core Nuget 套件，如圖 8-7 所示。

![](./media/image8.PNG)

**圖 8-7**。 簡單 CRUD Web API 微服務的相依性

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>使用 Entity Framework Core 實作 CRUD Web API 微服務

Entity Framework (EF) Core 是常見 Entity Framework 資料存取技術的輕量型、可擴充且跨平台版本。 EF Core 是一種物件關聯式對應程式 (ORM)，可讓 .NET 開發人員使用 .NET 物件來處理資料庫。

目錄微服務使用了 EF 和 SQL Server 提供者，因為其資料庫是執行於一個帶有適用於 Linux Docker 之 SQL Server 映像的容器。 然而，資料庫也可以部署到任何 SQL Server，例如 Windows 內部部署環境或 Azure SQL DB。 您唯一需要變更的只有 ASP.NET Web API 微服務中的連接字串。


#### <a name="the-data-model"></a>資料模型

運用 EF Core，使用模型來執行資料存取。 模型包含多個實體類別以及一個代表含資料庫之工作階段的衍生內容，可讓您查詢和儲存資料。 您可以從現有資料庫產生模型、手動撰寫符合您資料庫的模型程式碼，或使用 EF 移轉從您的模型建立資料庫 (並在您的模型隨著時間變更時進行修改)。 針對目錄微服務，我們會使用最後一個方法。 您可以在下列程式碼範例中看到 CatalogItem 實體類別的範例。該實體類別為一個簡單的純舊 CLR 物件 ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) 實體類別。

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

您也需要一個能夠代表資料庫工作階段的 DbContext。 針對目錄微服務，CatalogContext 類別衍生自 DbContext 基底類別，如下列範例中所示：

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

您可以有其他 `DbContext` 實作。 例如，在範例 Catalog API 微服務中，有一個名為 `CatalogContextSeed` 的第二個 `DbContext`，其會在第一次嘗試存取資料庫時自動填入範例資料。 這個方法對示範資料及自動化測試案例來說也非常有用。 在 `DbContext` 中，您會使用 `OnModelCreating` 方法來自訂物件/資料庫實體對應和其他 [EF 擴充點](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)。

##### <a name="querying-data-from-web-api-controllers"></a>從 Web API 控制器查詢資料

您的實體類別執行個體通常會使用 Language Integrated Query (LINQ) 來從資料庫擷取，如下列範例中所示：

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context, 
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10, 
                                           [FromQuery]int pageIndex = 0)

    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    } 
    //...
}
```

##### <a name="saving-data"></a>儲存資料

使用您實體類別的執行個體，建立、刪除和修改資料庫中的資料。 您可以將像是下列硬式編碼範例 (在此案例中為模擬資料) 的程式碼新增至您的 Web API 控制器。

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>ASP.NET Core 和 Web API 控制器中的相依性插入

在 ASP.NET Core 中，您可以直接使用相依性插入 (DI)。 您不需要設定協力廠商的控制反轉 (IoC) 容器，雖然您可以將您偏好的 IoC 容器插入 ASP.NET Core 基礎結構 (若您想要的話)。 在此案例下，這表示您可以透過控制器的建構函式直接插入必要的 EF DbContext 或其他存放庫。 在上述 `CatalogController` 類別的範例中，我們透過 `CatalogController()` 建構函式插入了 `CatalogContext` 類型的物件及其他物件。

在 Web API 專案中要設定的一項重要組態便是將 DbContext 類別註冊到服務的 IoC 容器。 您通常會藉由在 `Startup` 類別中的 `ConfigureServices()` 方法內呼叫 `services.AddDbContext<DbContext>()` 來執行此動作，如下列範例所示：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a>其他資源

-   **Querying Data (查詢資料)**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Saving Data (儲存資料)**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Docker 容器所使用的 DB 連接字串及環境變數

您可以使用 ASP.NET Core 設定並將 ConnectionString 屬性新增至您的 settings.json 檔案，如下列範例所示：

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

settings.json 檔案可具有 ConnectionString 屬性及其他任何屬性的預設值。 然而，在使用 Docker 時，您在 docker-compose.override.yml 檔案中指定的環境變數值會覆寫那些屬性。

從您的 docker-compose.yml 或 docker-compose.override.yml 檔案，您可以初始化那些屬性，讓 Docker 為您將他們設定為 OS 環境變數，如下列 docker-compose.override.yml 檔案中所示 (此範例中的連接字串和其他行會換行，但在您擁有的程式碼檔案中將不會換行)。

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

位於方案層級的 docker-compose.yml 檔案不僅比位於專案或微服務層級的組態檔更有彈性，當您使用在您的部署工具 (例如 VSTS Docker 部署工作) 中設定的值來覆寫 docker-compose 檔案中宣告的環境變數時，還會更安全。 

最後，您可以使用 Configuration\["ConnectionString"\] 來在您的程式碼中取得該值，如先前程式碼範例中的 ConfigurationServices 方法所示。

然而，針對生產環境，建議您探索其他儲存像是連接字串這種機密資料的方式。 通常會由您選擇的協調器管理，如同您針對 [Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/) (群集機密資料管理) 可使用的方式。

### <a name="implementing-versioning-in-aspnet-web-apis"></a>在 ASP.NET Web API 中實作版本控制

隨著商務需求的變更，可能會新增新的資源集合，資源之間的關聯性可能會變更，而資源中的資料結構也可能會修改。 更新 Web API 以處理新的需求是一段相對直接的過程，但您必須考量到該變更會為取用 Web API 之用戶端應用程式帶來的影響。 雖然設計及實作 Web API 的開發人員能夠完全控制該 API，但開發人員針對可能由遠端作業之協力廠商組織建置的用戶端應用程式無法擁有相同程度的控制。

版本控制可讓 Web API 指出其公開的功能和資源。 用戶端應用程式便能將要求提交至特定版本的功能或資源。 有幾種方式可以實作版本控制：

-   URI 版本控制

-   查詢字串版本控制

-   標頭版本控制

查詢字串及 URI 版本控制是實作最為簡單的方式。 標頭版本控制是一種不錯的方法。 然而，相較於 URI 版本控制，標頭版本控制沒有那麼明確及直接。 因為 URL 版本控制是最簡單也最為明確的，eShopOnContainers 應用程式範例便使用了 URI 版本控制。

如 eShopOnContainers 應用程式範例中使用 URI 版本控制，每次您修改 Web API 或變更資源的結構描述時，您便會將版本號碼新增至每個資源的 URI。 現有的 URI 會跟之前一樣繼續作業，傳回符合與請求版本相符之資料結構的資源。

如下列程式碼範例所示，您可以在 Web API 中使用 Route 屬性來設定版本。此舉會讓版本在 URI 中明確顯示 (在此案例中為 v1)。

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

此版本控制機制很簡單，相依於伺服器將請求路由至適當的端點。 然而，若需要更複雜的版本控制及使用 REST 時最佳的方法，建議您使用超媒體並實作 [HATEOAS (超文字作為應用程式狀態之引擎)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources)。

### <a name="additional-resources"></a>其他資源

-   **Scott Hanselman。ASP.NET Core RESTful Web API versioning made easy (ASP.NET Core RESTful Web API 輕鬆進行版本控制)**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Versioning a RESTful web API (符合 REST 限制的 Web API 版本控制)**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding。Versioning, Hypermedia, and REST (版本控制、超媒體、以及 REST)**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>從您的 ASP.NET Core Web API 產生 Swagger 描述中繼資料 

[Swagger](http://swagger.io/) 是一種常用的開放原始碼架構，由可協助您設計、建置、記錄文件及取用您 RESTful API 的龐大工具生態系統所支援。 它已逐漸成為 API 描述中繼資料領域的標準。 您應在任何形式的微服務中包含 Swagger 描述中繼資料，無論是資料驅動微服務，或是更進階的網域驅動微服務 (如下一節所述)。

Swagger 的核心是 Swagger 規格，即儲存於 JSON 或 YAML 檔案中的 API 描述中繼資料。 規格會為您的 API 建立 RESTful 合約，以人類易懂及電腦可讀取的格式詳述其所有的資源和作業，以進行簡單的部署、探索及整合。

規格是 OpenAPI 規格 (OAS) 的基礎，並且是在開放、透明且共同作業的社群開發的，以標準化定義 RESTful 介面的方式。

規格定義了可探索到服務的結構，以及理解其功能的方式。 如需詳細資訊，包含 Web 編輯器及來自像是 Spotify、Uber、Slack 及 Microsoft 等公司 Swagger 規格的範例，請參閱 Swagger 網站 (<http://swagger.io>)。

### <a name="why-use-swagger"></a>為何要使用 Swagger？

為您的 API 產生 Swagger 中繼資料的主要理由如下。

**讓其他產品可自動取用及與您的 API 整合**。 有數十種產品及[商業工具](http://swagger.io/commercial-tools/)和許多[程式庫和架構](http://swagger.io/open-source-integrations/)支援 Swagger。 Microsoft 具有能自動取用 Swagger 式 API 的高階產品和工具，例如：

-   [AutoRest](https://github.com/Azure/AutoRest)。 您可以為呼叫 Swagger 自動產生 .NET 用戶端類別。 此工具可於 CLI 中使用，也可以與 Visual Studio 整合以讓使用者透過 GUI 簡單的進行操作。

-   [Microsoft Flow](https://flow.microsoft.com/en-us/)。 您可以自動[使用及將您的 API 整合](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)至高階 Microsoft Flow 工作流程，而無須任何程式設計技能。

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)。 您可以自動從使用 [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/) 建置的 [PowerApps 行動應用程式](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) 取用您的 API，而無須任何程式設計技能。

-   [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。 您可以自動[使用並將您的 API 整合至 Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)，而無須任何程式設計技能。

**自動產生 API 文件**。 當您建立大型的 RESTful API，例如複雜的微服務式應用程式時，您需要在要求及回應裝載中使用不同的資料模型來處理許多端點。 透過 Swagger 取得適當的文件及牢靠的 API 總管，是讓您的 API 得以成功並讓開發人員採用的關鍵。

Microsoft Flow、PowerApps 及 Azure Logic Apps 會使用 Swagger 中繼資料來了解 API 的使用及連線方式。

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>如何使用 Swashbuckle NuGet 套件來自動化產生 API Swagger 中繼資料

手動產生 Swagger 中繼資料 (JSON 或 YAML 檔案) 是一件冗長的工作。 然而，您可以藉由使用 [Swashbuckle NuGet 套件](http://aka.ms/swashbuckledotnetcore)動態產生 Swagger API 中繼資料，來自動化 ASP.NET Web API 服務的 API 探索。

Swashbuckle 會為您的 ASP.NET Web API 專案自動產生 Swagger 中繼資料。 它支援 ASP.NET Core Web API 專案及傳統式 ASP.NET Web API 和任何其他類別，例如 Azure API 應用程式、Azure 行動應用程式及基於 ASP.NET 的 Azure Service Fabric 微服務。 它也支援部署在容器上的單純 Web API，如同在參考應用程式中的情況。

Swashbuckle 會結合 API 總管及 Swagger 或 [swagger-ui](https://github.com/swagger-api/swagger-ui) 來為您的 API 取用者提供豐富探索及文件體驗。 除了其 Swagger 中繼資料產生器引擎之外，Swashbuckle 也包含了內嵌版本的 swagger-ui，會在安裝 Swashbuckle 之後自動提供。

這表示您可以使用可協助開發人員使用您 API 的良好探索 UI，來補充您的 API。 由於它是自動產生的，它只需要非常少量的程式碼及維護，讓您可以專注於建置您的 API。 API 總管的結果如圖 8-8 所示。

![](./media/image9.png)

**圖 8-8**。 基於 Swagger 中繼資料的 Swashbuckle API—eShopOnContainers 目錄微服務

API 總管此時並不是最重要的。 當您有了可在 Swagger 中繼資料中描述自身的 Web API 後，您的 API 便可從 Swagger 式工具隨選即用，包含可瞄準許多平台的用戶端 Proxy 類別產生器。 例如，如前所述，[AutoRest](https://github.com/Azure/AutoRest) 會自動產生 .NET 用戶端類別。 但其他像是 [swagger-codegen](https://github.com/swagger-api/swagger-codegen) 的工具也可供使用，自動允許 API 用戶端程式庫、伺服器 Stub 及文件的程式碼產生。

目前，Swashbuckle 由兩個位於適用於 ASP.NET Core 應用程式之 [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) 版本 1.0.0 或更新版本之下的幾個內部 NuGet 套件組成。

在您將這些 NuGet 套件安裝在您的 Web API 專案中之後，您需要在 Startup 類別中設定 Swagger，如下列程式碼所示：

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

完成之後，您便可以啟動您的應用程式，並使用像是這些 URL 來瀏覽下列 Swagger JSON 和 UI 端點：

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

您先前曾看過 Swashbuckle 為 URL 產生的 UI，像是 http://&lt;your-root-url&gt;/swagger/ui。 在圖 8-9 中，您也可以看到如何測試任何 API 方法。

![](./media/image10.png)

**圖 8-9**。 Swashbuckle UI 測試目錄/項目 API 方法

圖 8-10 顯示了當您使用 [Postman](https://www.getpostman.com/) 向 &lt;your-root-url&gt;/swagger/v1/swagger.json 發出請求時，從 eShopOnContainers 微服務 (即工具在下方使用的) 產生的 Swagger JSON 中繼資料。

![](./media/image11.png)

**圖 8-10**。 Swagger JSON 中繼資料

就是這麼簡單。 由於它是自動產生的，當您將更多功能新增至您的 API 時，Swagger 中繼資料也會持續成長。

### <a name="additional-resources"></a>其他資源

-   **ASP.NET Web API Help Pages using Swagger (使用 Swagger 的 ASP.NET Core Web API 說明頁面)**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[上一頁] (microservice-application-design.md) [下一頁] (multi-container-applications-docker-compose.md)
