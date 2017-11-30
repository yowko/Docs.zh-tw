---
title: "建立簡單的資料導向 CRUD 微服務"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |建立簡單的資料導向 CRUD 微服務"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>建立簡單的資料導向 CRUD 微服務

此章節所述方式來建立簡單執行的微服務建立時，讀取、 更新和刪除 (CRUD) 作業的資料來源。

## <a name="designing-a-simple-crud-microservice"></a>設計簡單的 CRUD 微服務

從設計觀點來看，這種類型的容器化的微服務就非常簡單。 若要解決此問題可能是簡單，或可能是實作的概念性驗證。

![](./media/image4.png)

**圖 8-4**。 內部設計簡單的 CRUD microservices

這種簡單的資料磁碟機服務的範例是來自 eShopOnContainers 範例應用程式類別目錄微服務。 這種類型的服務在單一 ASP.NET Core Web API 專案，包括其資料模型、 其商務邏輯和其資料存取程式碼的類別中實作它的功能。 也在 SQL Server 中執行 （做為另一個容器基於開發/測試），在資料庫中儲存相關的資料，但如圖 8-5 所示，則也可能是任何規則的 SQL Server 主機。

![](./media/image5.png)

**圖 8-5**。 簡單的資料驅動/CRUD 微服務設計

當您開發這種服務時，您只需要[ASP.NET Core](https://docs.microsoft.com/aspnet/core/)和資料存取應用程式開發介面或 ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index)。 您也可以產生[Swagger](http://swagger.io/)中繼資料會自動透過[Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)以提供您服務的提供，描述在下一節所述。

請注意，執行像 Docker 容器中的 SQL Server 最適合用於開發環境，因為您最多可以有您所有的相依性的資料庫伺服器，而不需要佈建資料庫中的雲端或內部部署執行。 執行整合測試時，這是很方便。 不過，實際執行環境，在容器中執行的資料庫伺服器不是建議，因為通常不會使用該方法的高可用性。 在 Azure 中的生產環境，建議您使用 Azure SQL DB 或任何其他可提供高可用性和高擴充性的資料庫技術。 例如，如 NoSQL 方法，您可以選擇 DocumentDB。

最後，藉由編輯的 Dockerfile 並 docker compose.yml 中繼資料檔案，您可以設定此容器映像建立的方式，它會使用，加上設計等內部和外部名稱及 TCP 通訊埠設定哪些基底映像。 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>使用 ASP.NET Core 實作簡單的 CRUD 微服務

若要實作簡單的 CRUD 微服務，使用.NET Core 和 Visual Studio，您開始建立簡單的 ASP.NET Core Web API 專案 （執行.NET Core 讓它可以執行 Linux Docker 主機上），做為顯示圖 8-6。

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**圖 8-6**。 Visual Studio 中建立 ASP.NET Core Web API 專案

建立專案之後，您可以實作 MVC 控制器，您可以按照任何其他 Web API 專案使用 Entity Framework 應用程式開發介面或其他應用程式開發介面。 在 eShopOnContainers.Catalog.API 專案中，您可以看到該微服務的主要相依性都只 ASP.NET Core 本身、 Entity Framework 和 Swashbuckle，如圖 8-7 所示。

![](./media/image8.PNG)

**圖 8-7**。 簡單的 CRUD Web API 微服務中的相依性

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>實作與 Entity Framework Core CRUD Web API 服務

Entity Framework (EF) 核心的輕量型可擴充的並跨平台版本常見的 Entity Framework 資料存取技術。 EF 核心是可讓.NET 開發人員使用.NET 物件的資料庫與物件關聯式對應 (ORM)。

目錄微服務會使用 EF 和 SQL Server 提供者，因為它的資料庫在與 Linux Docker 映像的 SQL Server 容器中執行。 不過，資料庫無法部署至任何 SQL Server，例如 Windows 內部部署或 Azure SQL DB。 唯一您需要變更的是 ASP.NET Web API 的微服務中的連接字串。

#### <a name="add-entity-framework-core-to-your-dependencies"></a>Entity Framework Core 加入相依性

您可以針對您想要使用，在此情況下 SQL Server，從 Visual Studio IDE 中或使用 NuGet 主控台資料庫提供者安裝 NuGet 封裝。 請使用以下命令：

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a>資料模型

使用 EF 核心會使用模型執行資料存取。 模型是由實體類別和衍生的內容，表示與資料庫，可以讓您查詢及儲存資料的工作階段所組成。 您可以從現有的資料庫產生模型、 手動撰寫程式碼模式，以符合您的資料庫，或從您的模型建立的資料庫 （及您的模型變更後經過一段時間不同時） 使用 EF 移轉。 目錄微服務會使用最後一個的方法。 您可以看到 CatalogItem 實體類別，在下列的程式碼範例簡單純舊 CLR 物件的範例 ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) 實體類別。

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

您也需要表示與資料庫的工作階段的 DbContext。 針對類別目錄微服務 CatalogContext 類別衍生自 DbContext 的基底類別，如下列範例所示：

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

您可以在 DbContext 實作額外的程式碼。 例如，在範例應用程式中，我們有 OnModelCreating 方法 CatalogContext 類別會自動填入範例資料第一次嘗試存取資料庫中。 這個方法是用於示範的資料。 您也可以使用 OnModelCreating 方法來自訂物件/資料庫與許多其他的實體對應[EF 擴充性點](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)。

您可以查看進一步的詳細資料中 OnModelCreating[實作持續性的基礎結構層與 Entity Framework Core](#implementing_infrastructure_persistence)稍後在這個活頁簿中的區段。

##### <a name="querying-data-from-web-api-controllers"></a>從 Web API 控制器查詢資料

實體類別的執行個體通常會使用 Language Integrated Query (LINQ)，從資料庫擷取，如下列範例所示：

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
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
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

建立、 刪除，並在使用實體類別的執行個體的資料庫中修改資料。 您可以加入程式碼，如下列硬式編碼範例 （在此情況下，模擬資料） 至您的 Web API 控制器。

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>在 ASP.NET Core 及 Web API 控制器的相依性插入

在 ASP.NET Core 中，您可以使用相依性插入 (DI) 立即可用的。 您不需要設定協力廠商的逆轉控制 (IoC) 容器，但如果您想，您可以在 ASP.NET Core 基礎結構中插入您慣用的 IoC 容器。 在此情況下，這表示您可以直接插入必要的 EF DBContext 或其他儲存機制，透過控制器建構函式。 在上面的 CatalogController 類別的範例，我們會插入 CatalogContext 型別的物件加上透過 CatalogController 建構函式的其他物件。

設定 Web API 專案中的重要組態是 DbContext 類別註冊到服務的 IoC 容器。 通常，您在啟動類別藉由呼叫服務。AddDbContext 方法內 ConfigureServices 方法，如下列範例所示：

```csharp
public void ConfigureServices(IServiceCollection services)
{
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

-   **查詢資料**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **將資料儲存**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>資料庫連接字串和環境變數使用 Docker 容器

您可以使用的 ASP.NET 核心設定，並將 ConnectionString 屬性加入至您 settings.json 檔案，如下列範例所示：

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

Settings.json 檔案可以有預設值為 ConnectionString 屬性或任何其他內容。 不過，這些屬性將會覆寫您在 docker compose.override.yml 檔案中指定的環境變數的值。

從您的 docker compose.yml 或 docker compose.override.yml 檔，您可以初始化這些環境變數的 Docker 將它們做為作業系統的環境變數為您設定，因此下列 docker compose.override.yml 檔案 （此連線中所示字串和其他行包裝在此範例中，但它不會包裝在自己的檔案）。

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

在解決方案層級 docker compose.yml 檔案不只會比在專案 」 或 「 微服務層級的組態檔更有彈性，但是也更安全的。 請考慮您建置每微服務的 Docker 映像不包含 docker compose.yml 檔案，只有二進位檔案和每個微服務，包括 Dockerfile 的組態檔。 但 docker compose.yml 檔案尚未部署應用程式; 以及它只在部署期間使用。 因此，將環境變數值放入這些 docker compose.yml 檔案中 （即使未加密的值） 是比放置這些值會隨著您的程式碼部署的一般.NET 組態檔中更安全。

最後，使用組態從程式碼取得該值\["ConnectionString"\]ConfigureServices 方法，在先前的程式碼範例所示。

不過，實際執行環境，您可能要如何儲存機密資料的連接字串類似總管 中的其他方法。 通常，將受您所選擇的 orchestrator，像是您如何使用[Docker Swarm 密碼管理](https://docs.docker.com/engine/swarm/secrets/)。

### <a name="implementing-versioning-in-aspnet-web-apis"></a>在 ASP.NET Web 應用程式開發介面中實作版本控制

當商務需求變更時，可能會加入新的資源集合、 資源之間的關聯性可能會變更，和可能修改的資源中的資料結構。 更新 Web 應用程式開發介面來處理新的需求是相當簡單的程序，但您必須考慮這類變更對於會耗用 Web API 的用戶端應用程式的影響。 雖然開發人員設計和實作 Web API 的應用程式開發介面的完整控制權，開發人員不需要用戶端應用程式可能會建立第三方組織操作遠端控制的程度。

版本設定可讓 Web API，以表示它會公開的資源的功能。 用戶端應用程式就可以提交要求至特定版本的功能或資源。 有數種方法來實作版本設定：

-   URI 的版本控制

-   查詢字串的版本控制

-   標頭版本控制

查詢字串和 URI 版本設定是最簡單的方式實作。 標頭版本設定是很好的方法。 不過，不為明確和那樣 URI 版本設定標頭版本。 因為 URL 版本是最簡單且最明確，eShopOnContainers 範例應用程式會使用 URI 版本設定。

使用 URI 版本設定，如同 eShopOnContainers 範例應用程式中，每次修改 Web 應用程式開發介面，或變更結構描述的資源，您將版本號碼加入每個資源的 URI。 現有的 Uri 應繼續操作之前一樣，傳回符合的資源結構描述符合要求的版本。

下列程式碼範例所示，可以將版本設定在 Web API 中，讓版本在 URI 中明確使用路由屬性 (在此情況下 v1)。

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

此版本設定機制很簡單，而且相依於伺服器要求路由至適當的端點。 不過，對於更複雜的版本設定和使用 REST 時的最佳方法，您應該使用超及實作[HATEOAS （超文字做為應用程式狀態的引擎）](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources)。

### <a name="additional-resources"></a>其他資源

-   **Scott Hanselman。ASP.NET Core RESTful Web API 版本設定輕鬆**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **版本控制 RESTful web API**

    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **伊 Fielding。版本控制、 超和 REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>從您的 ASP.NET Core Web API 產生 Swagger 描述中繼資料 

[Swagger](http://swagger.io/)是常用的開放原始碼架構支援大型生態系統的工具，可協助您設計、 建置、 文件，並使用您的 RESTful Api。 得 Api 描述中繼資料網域的標準。 您應該包含 Swagger 描述中繼資料，與任何一種微服務，資料驅動 microservices 或更多進階網域導向 microservices （下一節所述）。

Swagger 的核心是 Swagger 規格，也就是 JSON 或 YAML 檔案中的 API 描述中繼資料。 規格會建立您的 API，詳述所有其資源和作業中這兩個的人們和 machine readable 格式的簡易的開發、 探索與整合的 RESTful 合約。

規格為基礎的 OpenAPI 規格 (OAS) 和開發開啟、 透明的且協同社群標準化 RESTful 介面定義的方式。

此規格會定義可探索服務的方式，和其功能的了解的結構。 如需詳細資訊，包括 web 編輯器和公司、 Spotify、 超級、 寬限時間和 Microsoft Swagger 規格的範例請參閱 Swagger 站台 (<http://swagger.io>)。

### <a name="why-use-swagger"></a>為何要使用 Swagger？

若要產生您的應用程式開發介面 Swagger 中繼資料的主要原因如下所示。

**其他產品來自動使用及整合您的應用程式開發介面的能力**。 數十個產品和[商業工具](http://swagger.io/commercial-tools/)和許多[程式庫和架構](http://swagger.io/open-source-integrations/)支援 Swagger。 Microsoft 具有高層級的產品與工具，可以自動耗用 Swagger 為基礎的 Api，如下所示：

-   [AutoRest](https://github.com/Azure/AutoRest)。 您可以自動產生的 Swagger 函式呼叫的.NET 用戶端類別。 這個

-   工具可從 CLI，它也會整合與 Visual Studio 以透過 GUI 的方便使用。

-   [Microsoft Flow](https://flow.microsoft.com/en-us/)。 您可以自動[使用並整合您的 API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)成高階 Microsoft Flow 工作流程，且沒有執行任何程式設計所需的技巧。

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)。 您可以自動使用您的 API，從[PowerApps 行動裝置應用程式](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/)建置[PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/)，與所需的任何程式設計技術。

-   [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。 您可以自動[使用，並將您的 API 整合到 Azure App Service 的邏輯應用程式](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)，與所需的任何程式設計技術。

**讓您自動產生應用程式開發介面文件**。 當您建立複雜的微服務為基礎應用程式，例如大型的 RESTful Api 時您需要在要求和回應裝載中使用不同的資料模型處理多個端點。 具有適當的文件，以及取得純色的 API 總管 中，當您使用 Swagger，為您的應用程式開發介面和開發人員所採用的成功與否的索引鍵。

Swagger 的中繼資料是 Microsoft Flow、 PowerApps 和 Azure 邏輯應用程式用來了解如何使用 Api 且與它們連線。

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>如何自動化 API Swagger 中繼資料的產生與 Swashbuckle NuGet 封裝

產生 Swagger 中繼資料，以手動方式 （以 JSON 或 YAML 檔案） 可以是冗長的工作。 不過，您可以使用自動執行的 ASP.NET Web API 服務的應用程式開發介面探索[Swashbuckle NuGet 封裝](http://aka.ms/swashbuckledotnetcore)動態產生 Swagger API 中繼資料。

Swashbuckle 會自動產生 ASP.NET Web API 專案的 Swagger 中繼資料。 它支援 ASP.NET Core Web API 專案與傳統的 ASP.NET Web API，以及任何其他類別，例如 Azure API 應用程式、 Azure 行動應用程式，以 ASP.NET 為基礎的 Azure Service Fabric microservices。 它也支援一般部署容器，而在參考應用程式的 Web API。

Swashbuckle 結合 API 總管和 Swagger 或[swagger ui](https://github.com/swagger-api/swagger-ui)來提供豐富的探索和文件的應用程式開發介面消費者的體驗。 除了 Swagger 中繼資料產生器引擎 Swashbuckle 也包含內嵌的 swagger ui，它會自動提供 Swashbuckle 安裝之後的版本。

這表示可以補充您的 API nice 探索可協助開發人員使用您的應用程式開發介面的 UI。 它需要非常少量的程式碼和維護，因為它自動產生，可讓您專注於建置您的 API。 API 總管 結果看起來像圖 8-8。

![](./media/image9.png)

**圖 8-8**。 Swagger 中繼資料為基礎的 Swashbuckle API 總管 — eShopOnContainers 目錄微服務

[總管] 中應用程式開發介面不是最重要的一點。 一旦您擁有可描述自己 Swagger 中繼資料中的 Web API，您的 API 可順暢地從 Swagger 為基礎的工具，包括用戶端 proxy 類別程式碼產生器可以在許多平台為目標。 例如，如所述， [AutoRest](https://github.com/Azure/AutoRest) .NET 用戶端類別會自動產生。 但其他工具想[swagger codegen](https://github.com/swagger-api/swagger-codegen)是也可以使用程式庫、 伺服器 stub 和文件會自動讓 API 用戶端的程式碼產生。

目前，Swashbuckle 包含兩個 NuGet 套件： Swashbuckle.SwaggerGen 和 Swashbuckle.SwaggerUi。 前者提供直接從您的應用程式開發介面實作產生一或多個 Swagger 文件，並將它們公開為 JSON 端點的功能。 後者提供 swagger ui 工具可以由您的應用程式和由產生的 Swagger 文件來描述您 API 所提供的內嵌的版本。 不過，最新版的 Swashbuckle 換行 Swashbuckle.AspNetCore metapackage 的。

請注意，.NET Core Web API 專案，您需要使用[Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) 1.0.0 版或更新版本。

這些 NuGet 封裝安裝在您的 Web API 專案之後，您需要設定 Swagger 中啟動類別，如下列程式碼所示：

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
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
            .UseSwaggerUi();
    }
}
```

完成之後，您可以啟動您的應用程式，並瀏覽下列 Swagger JSON 和 UI 端點使用這些 Url:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

您先前已看到的 URL，例如 http:// Swashbuckle 所建立的產生的 UI&lt;程式根 url &gt; /swagger/ui。 圖 8-9 您也可以查看如何測試任何應用程式開發介面的方法。

![](./media/image10.png)

**圖 8-9**。 Swashbuckle UI 測試的類別目錄/項目 API 方法

圖 8-10 顯示 eShopOnContainers 微服務產生的 Swagger JSON 中繼資料 （此為之下使用的工具） 在您要求的&lt;程式根 url&gt;/swagger/v1/swagger.json 使用[郵差](https://www.getpostman.com/).

![](./media/image11.png)

**圖 8-10**。 Swagger JSON 中繼資料

就這麼簡單。 和自動產生，因此當您將更多的功能加入您的 api，將會成長 Swagger 中繼資料。

### <a name="additional-resources"></a>其他資源

-   **ASP.NET Web API 說明頁面使用 Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[上一個](微服務-應用程式-design.md) [下一步] (多-container-應用程式-docker-compose.md)
