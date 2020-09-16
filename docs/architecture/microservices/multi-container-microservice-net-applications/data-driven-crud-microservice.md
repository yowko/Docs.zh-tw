---
title: 建立簡單資料驅動 CRUD 微服務
description: 容器化 .NET 應用程式的 .NET 微服務架構 |瞭解如何在微服務應用程式的內容中建立簡單的 CRUD (資料驅動) 微服務。
ms.date: 08/14/2020
ms.openlocfilehash: 46654b9e6283d913910b62621d056e034c18870e
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679145"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="d4fa4-103">建立簡單資料驅動 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="d4fa4-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="d4fa4-104">本節描述了如何建立可針對資料來源執行建立、讀取、更新及刪除 (CRUD) 作業的簡單微服務。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="d4fa4-105">設計簡單的 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="d4fa4-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="d4fa4-106">從設計觀點來看，這種類型的容器化微服務非常簡單。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="d4fa4-107">可能是要解決的問題相當簡單，或者可能其實作僅只是一種概念的證明。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![此圖顯示簡單的 CRUD 微服務內部設計模式。](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="d4fa4-109">**圖 6-4**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-109">**Figure 6-4**.</span></span> <span data-ttu-id="d4fa4-110">簡單 CRUD 微服務的內部設計</span><span class="sxs-lookup"><span data-stu-id="d4fa4-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="d4fa4-111">eShopOnContainers 應用程式範例的目錄微服務即為這種簡單資料驅動服務的範例。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="d4fa4-112">這種類型的服務會在單一 ASP.NET Core Web API 專案中實作所有自身的功能，包括其資料模型的類別、商務邏輯，以及資料存取程式碼。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="d4fa4-113">它也會將相關資料儲存於在 SQL Server 中執行的資料庫中 (當作開發/測試用途的另一個容器)，但也可當作任何一般 SQL Server 主機，如圖 6-5 所示。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![顯示資料驅動/CRUD 微服務容器的圖表。](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="d4fa4-115">**圖 6-5**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-115">**Figure 6-5**.</span></span> <span data-ttu-id="d4fa4-116">簡單資料驅動/CRUD 微服務設計</span><span class="sxs-lookup"><span data-stu-id="d4fa4-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="d4fa4-117">上圖顯示邏輯目錄微服務，其中包含其目錄資料庫（可以是或不在相同的 Docker 主機中）。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="d4fa4-118">在相同的 Docker 主機中擁有資料庫可能適合開發，但不適用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="d4fa4-119">當您開發這種服務時，您只需要 [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) 及一個資料存取 API 或 ORM，像是 [Entity Framework Core](https://docs.microsoft.com/ef/core/index)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="d4fa4-120">您也可以透過 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) 自動產生 [Swagger](https://swagger.io/) 中繼資料來提供您服務提供之內容的描述，如下一節中所解釋的。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="d4fa4-121">請注意，在 Docker 容器中執行像是 SQL Server 這種資料庫伺服器對開發環境來說是非常適合的，因為您可以設定所有的相依性並使其順利執行，而無須在雲端或內部部署環境佈建資料庫。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="d4fa4-122">這在執行整合測試時會非常方便。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="d4fa4-123">然而，針對生產環境，我們不建議在容器內執行資料庫伺服器，因為使用此方法，您通常無法取得高度的可用性。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="d4fa4-124">針對 Azure 中的生產環境，通常建議您使用 Azure SQL DB 或任何其他可提供高度可用性及延展性的資料庫技術。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="d4fa4-125">舉例來說，若要採用 NoSQL 方法，您可能會選擇 CosmosDB。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="d4fa4-126">最後，藉由編輯 Dockerfile 和 docker-compose.yml 中繼檔案，您可以設定此容器映像建立的方式—使用的基底映像，以及設計設定例如內部及外部名稱和 TCP 連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="d4fa4-127">使用 ASP.NET Core 實作簡單 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="d4fa4-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="d4fa4-128">若要使用 .NET Core 及 Visual Studio 實作簡單 CRUD 微服務，就從建立簡單 ASP.NET Core Web API 專案 (要在 .NET Core 上執行才能於 Linux Docker 主機上執行) 開始，如圖 6-6 所示。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Visual studio 的螢幕擷取畫面，其中顯示專案的設定。](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="d4fa4-130">**圖 6-6**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-130">**Figure 6-6**.</span></span> <span data-ttu-id="d4fa4-131">在 Visual Studio 2019 中建立 ASP.NET Core Web API 專案</span><span class="sxs-lookup"><span data-stu-id="d4fa4-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="d4fa4-132">若要建立 ASP.NET Core Web API 專案，首先要選取一個 ASP.NET Core Web 應用程式，然後選取 API 類型。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="d4fa4-133">建立專案之後，您可以使用 Entity Framework API 或其他 API，利用您在任何其他 Web API 專案上相同的方式，實作您的 MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="d4fa4-134">在新的 Web API 專案中，您可以看到該微服務的唯一相依性即是 ASP.NET Core 本身。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="d4fa4-135">在內部，AspNetCore 中的 *所有* 相依性都會參考 Entity Framework 以及許多其他的 .Net Core NuGet 套件，如圖6-7 所示。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![VS 的螢幕擷取畫面，其中顯示 Catalog 的 NuGet 相依性。](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="d4fa4-137">**圖 6-7**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-137">**Figure 6-7**.</span></span> <span data-ttu-id="d4fa4-138">簡單 CRUD Web API 微服務的相依性</span><span class="sxs-lookup"><span data-stu-id="d4fa4-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="d4fa4-139">API 專案包含 AspNetCore 的參考，其中包含所有基本封裝的參考。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-139">The API project includes references to Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="d4fa4-140">這也可能包含某些其他套件。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="d4fa4-141">使用 Entity Framework Core 實作 CRUD Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="d4fa4-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="d4fa4-142">Entity Framework (EF) Core 是常見 Entity Framework 資料存取技術的輕量型、可擴充且跨平台版本。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="d4fa4-143">EF Core 是一種物件關聯式對應程式 (ORM)，可讓 .NET 開發人員使用 .NET 物件來處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="d4fa4-144">目錄微服務使用了 EF 和 SQL Server 提供者，因為其資料庫是執行於一個帶有適用於 Linux Docker 之 SQL Server 映像的容器。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="d4fa4-145">然而，資料庫也可以部署到任何 SQL Server，例如 Windows 內部部署環境或 Azure SQL DB。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="d4fa4-146">您唯一需要變更的只有 ASP.NET Web API 微服務中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="d4fa4-147">資料模型</span><span class="sxs-lookup"><span data-stu-id="d4fa4-147">The data model</span></span>

<span data-ttu-id="d4fa4-148">運用 EF Core，使用模型來執行資料存取。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="d4fa4-149">模型由 (領域模型) 實體類別及代表資料庫中一個工作階段的衍生內容 (DbContext) 組成，可讓您查詢及儲存資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="d4fa4-150">您可以從現有的資料庫產生模型、手動撰寫模型的程式碼以符合您的資料庫，或使用 EF 遷移技術從您的模型建立資料庫，並使用程式碼優先方法 (，讓您可以在模型隨時間變化的模型變更) 時，輕鬆地將資料庫演進。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations technique to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="d4fa4-151">針對目錄微服務，已使用最後一種方法。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-151">For the catalog microservice, the last approach has been used.</span></span> <span data-ttu-id="d4fa4-152">您可以在下列程式碼範例中看到 CatalogItem 實體類別的範例。該實體類別為一個簡單的簡單的 CLR 物件 ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) 實體類別。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="d4fa4-153">您也需要一個能夠代表資料庫工作階段的 DbContext。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="d4fa4-154">針對目錄微服務，CatalogContext 類別衍生自 DbContext 基底類別，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

<span data-ttu-id="d4fa4-155">您可以有其他 `DbContext` 實作。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="d4fa4-156">例如，在範例 Catalog API 微服務中，有一個名為 `CatalogContextSeed` 的第二個 `DbContext`，其會在第一次嘗試存取資料庫時自動填入範例資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="d4fa4-157">這個方法對示範資料及自動化測試案例來說也非常有用。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="d4fa4-158">在 `DbContext` 內，您會使用 `OnModelCreating` 方法來自訂物件/資料庫實體對應及其他 [EF 擴充點](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="d4fa4-159">從 Web API 控制器查詢資料</span><span class="sxs-lookup"><span data-stu-id="d4fa4-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="d4fa4-160">您的實體類別執行個體通常會使用 Language Integrated Query (LINQ) 來從資料庫擷取，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

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

##### <a name="saving-data"></a><span data-ttu-id="d4fa4-161">儲存資料</span><span class="sxs-lookup"><span data-stu-id="d4fa4-161">Saving data</span></span>

<span data-ttu-id="d4fa4-162">使用您實體類別的執行個體，建立、刪除和修改資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="d4fa4-163">您可以將像是下列硬式編碼範例 (在此案例中為模擬資料) 的程式碼新增至您的 Web API 控制器。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="d4fa4-164">ASP.NET Core 和 Web API 控制器中的相依性插入</span><span class="sxs-lookup"><span data-stu-id="d4fa4-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="d4fa4-165">在 ASP.NET Core 中，您可以直接使用相依性插入 (DI)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="d4fa4-166">您不需要設定協力廠商的控制反轉 (IoC) 容器，雖然您可以將您偏好的 IoC 容器插入 ASP.NET Core 基礎結構 (若您想要的話)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="d4fa4-167">在此案例下，這表示您可以透過控制器的建構函式直接插入必要的 EF DbContext 或其他存放庫。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="d4fa4-168">在稍 `CatalogController` 早所述的類別中， `CatalogContext` 繼承自 `DbContext`) 類型的 (會與函式中的其他必要物件一起插入 `CatalogController()` 。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-168">In the `CatalogController` class mentioned earlier, `CatalogContext` (which inherits from `DbContext`) type is injected along with the other required objects in the `CatalogController()` constructor.</span></span>

<span data-ttu-id="d4fa4-169">要在 Web API 專案中設定的一項重要組態，是將 DbContext 類別註冊至服務的 IoC 容器內。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="d4fa4-170">一般來說，您可以在方法中呼叫方法來執行此動作 `Startup` `services.AddDbContext<CatalogContext>()` `ConfigureServices()` ，如下列 **簡化** 範例所示：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<CatalogContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

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

### <a name="additional-resources"></a><span data-ttu-id="d4fa4-171">其他資源</span><span class="sxs-lookup"><span data-stu-id="d4fa4-171">Additional resources</span></span>

- <span data-ttu-id="d4fa4-172">**查詢資料** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="d4fa4-173">**儲存資料** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="d4fa4-174">Docker 容器所使用的 DB 連接字串及環境變數</span><span class="sxs-lookup"><span data-stu-id="d4fa4-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="d4fa4-175">您可以使用 ASP.NET Core 設定並將 ConnectionString 屬性新增至您的 settings.json 檔案，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
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

<span data-ttu-id="d4fa4-176">settings.json 檔案可具有 ConnectionString 屬性及其他任何屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="d4fa4-177">然而，在使用 Docker 時，您在 docker-compose.override.yml 檔案中指定的環境變數值會覆寫那些屬性。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="d4fa4-178">您可以從您的 docker-compose.yml 檔案或 docker-compose.override.yml 檔案將那些環境變數初始化，如此一來 Docker 便會替您將其設定為 OS 環境變數，如下列 docker-compose.override.yml 檔案所示 (此範例中會有連接字串及其他自動換行，但在您個人的檔案中不會換行)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="d4fa4-179">位於解決方案層級的 docker-compose.yml 檔案不僅比位於專案或微服務層級的組態檔更有彈性，當您使用在部署工具 (例如 Azure DevOps Services Docker 部署工作) 中設定的值來覆寫 docker-compose 檔案中宣告的環境變數時，還會更安全。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="d4fa4-180">最後，您可以使用 Configuration\["ConnectionString"\] 來在您的程式碼中取得該值，如先前程式碼範例中的 ConfigurationServices 方法所示。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="d4fa4-181">然而，針對生產環境，建議您探索其他儲存像是連接字串這種機密資料的方式。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="d4fa4-182">管理應用程式秘密的絕佳方式是使用 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="d4fa4-183">Azure Key Vault 可協助儲存及保護您雲端應用程式及服務所使用的密碼編譯金鑰及祕密。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="d4fa4-184">任何您想要嚴格控管的項目都是祕密，例如 API 金鑰、連接字串、密碼等，而嚴格控管的方法包括使用方式記錄、設定到期日、管理存取權*等等*。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="d4fa4-185">Azure Key Vault 提供非常細微的應用程式祕密使用控制層級，且不須讓任何人知悉。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="d4fa4-186">祕密甚至可以在不中斷開發或營運的狀況下輪替，以加強安全性。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="d4fa4-187">應用程式必須在組織的 Active Directory 註冊，才能使用 Key Vault。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="d4fa4-188">如需詳細資料，請查看 *Key Vault 概念文件*。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="d4fa4-189">在 ASP.NET Web API 中實作版本控制</span><span class="sxs-lookup"><span data-stu-id="d4fa4-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="d4fa4-190">隨著商務需求的變更，可能會新增新的資源集合，資源之間的關聯性可能會變更，而資源中的資料結構也可能會修改。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="d4fa4-191">更新 Web API 以處理新的需求是一段相對直接的過程，但您必須考量到該變更會為取用 Web API 之用戶端應用程式帶來的影響。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="d4fa4-192">雖然設計和實行 Web API 的開發人員可以完全掌控該 API，但開發人員並沒有與用戶端應用程式相同的控制權，而這些應用程式可能是由遠端操作的協力廠商組織所建立。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third-party organizations operating remotely.</span></span>

<span data-ttu-id="d4fa4-193">版本控制可讓 Web API 指出其公開的功能和資源。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="d4fa4-194">用戶端應用程式便能將要求提交至特定版本的功能或資源。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="d4fa4-195">有幾種方式可以實作版本控制：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="d4fa4-196">URI 版本控制</span><span class="sxs-lookup"><span data-stu-id="d4fa4-196">URI versioning</span></span>

- <span data-ttu-id="d4fa4-197">查詢字串版本控制</span><span class="sxs-lookup"><span data-stu-id="d4fa4-197">Query string versioning</span></span>

- <span data-ttu-id="d4fa4-198">標頭版本控制</span><span class="sxs-lookup"><span data-stu-id="d4fa4-198">Header versioning</span></span>

<span data-ttu-id="d4fa4-199">查詢字串及 URI 版本控制是實作最為簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="d4fa4-200">標頭版本控制是一種不錯的方法。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-200">Header versioning is a good approach.</span></span> <span data-ttu-id="d4fa4-201">不過，標頭版本設定不像 URI 版本控制一樣明確且直接。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-201">However, header versioning is not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="d4fa4-202">因為 URL 版本控制是最簡單也最為明確的，eShopOnContainers 應用程式範例便使用了 URI 版本控制。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="d4fa4-203">如 eShopOnContainers 應用程式範例中使用 URI 版本控制，每次您修改 Web API 或變更資源的結構描述時，您便會將版本號碼新增至每個資源的 URI。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="d4fa4-204">現有的 URI 會跟之前一樣繼續作業，傳回符合與請求版本相符之資料結構的資源。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="d4fa4-205">如下列程式碼範例所示，您可在 Web API 控制器中使用 Route 屬性來設定版本，這會讓版本在 URI 中明確顯示 (在此案例中為 v1)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="d4fa4-206">此版本控制機制很簡單，相依於伺服器將請求路由至適當的端點。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="d4fa4-207">然而，若需要更複雜的版本控制及使用 REST 時最佳的方法，建議您使用超媒體並實作 [HATEOAS (超文字作為應用程式狀態之引擎)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d4fa4-208">其他資源</span><span class="sxs-lookup"><span data-stu-id="d4fa4-208">Additional resources</span></span>

- <span data-ttu-id="d4fa4-209">**Scott Hanselman。ASP.NET Core RESTful Web API 版本設定變得更簡單** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="d4fa4-210">**RESTful web API 的版本控制** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="d4fa4-211">**Roy版本控制、超媒體和 REST** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="d4fa4-212">從您的 ASP.NET Core Web API 產生 Swagger 描述中繼資料</span><span class="sxs-lookup"><span data-stu-id="d4fa4-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="d4fa4-213">[Swagger](https://swagger.io/) 是一種常用的開放原始碼架構，由可協助您設計、建置、記錄文件及取用您 RESTful API 的龐大工具生態系統所支援。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="d4fa4-214">它已逐漸成為 API 描述中繼資料領域的標準。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="d4fa4-215">您應該在任何種類的微服務（資料驅動微服務或更高階的網域導向微服務 (）中包含 Swagger 描述中繼資料，如) 的下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in the following section).</span></span>

<span data-ttu-id="d4fa4-216">Swagger 的核心是 Swagger 規格，即儲存於 JSON 或 YAML 檔案中的 API 描述中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="d4fa4-217">規格會為您的 API 建立 RESTful 合約，以人類易懂及電腦可讀取的格式詳述其所有的資源和作業，以進行簡單的部署、探索及整合。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="d4fa4-218">規格是 OpenAPI 規格 (OAS) 的基礎，並且是在開放、透明且共同作業的社群開發的，以標準化定義 RESTful 介面的方式。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="d4fa4-219">規格定義了可探索到服務的結構，以及理解其功能的方式。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="d4fa4-220">如需詳細資訊，包含 Web 編輯器及來自像是 Spotify、Uber、Slack 及 Microsoft 等公司 Swagger 規格的範例，請參閱 Swagger 網站 (<https://swagger.io>)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="d4fa4-221">為何要使用 Swagger？</span><span class="sxs-lookup"><span data-stu-id="d4fa4-221">Why use Swagger?</span></span>

<span data-ttu-id="d4fa4-222">為您的 API 產生 Swagger 中繼資料的主要理由如下。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="d4fa4-223">**讓其他產品可自動取用及與您的 API 整合**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="d4fa4-224">有數十種產品及[商業工具](https://swagger.io/commercial-tools/)和許多[程式庫和架構](https://swagger.io/open-source-integrations/)支援 Swagger。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="d4fa4-225">Microsoft 具有能自動取用 Swagger 式 API 的高階產品和工具，例如：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="d4fa4-226">[AutoRest](https://github.com/Azure/AutoRest)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="d4fa4-227">您可以為呼叫 Swagger 自動產生 .NET 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="d4fa4-228">此工具可於 CLI 中使用，也可以與 Visual Studio 整合以讓使用者透過 GUI 簡單的進行操作。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="d4fa4-229">[Microsoft Flow](https://flow.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="d4fa4-230">您可以自動[使用及將您的 API 整合](https://flow.microsoft.com/blog/integrating-custom-api/)至高階 Microsoft Flow 工作流程，而無須任何程式設計技能。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="d4fa4-231">[Microsoft PowerApps](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="d4fa4-232">您可以自動從使用 [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/) 建置的 [PowerApps 行動應用程式](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) 取用您的 API，而無須任何程式設計技能。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="d4fa4-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="d4fa4-234">您可以自動[使用並將您的 API 整合至 Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)，而無須任何程式設計技能。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="d4fa4-235">**自動產生 API 文件**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="d4fa4-236">當您建立大型的 RESTful API，例如複雜的微服務式應用程式時，您需要在要求及回應裝載中使用不同的資料模型來處理許多端點。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="d4fa4-237">透過 Swagger 取得適當的文件及牢靠的 API 總管，是讓您的 API 得以成功並讓開發人員採用的關鍵。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="d4fa4-238">Microsoft Flow、PowerApps 及 Azure Logic Apps 都使用 Swagger 的中繼資料來了解如何使用及連線至 API。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="d4fa4-239">有許多選項可用來依據 *swagger-ui*，以功能 API 說明頁面的形式為 ASP.NET Core REST API 應用程式自動產生 Swagger 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="d4fa4-240">最好是 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) ，它目前是在 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 中使用，我們將在本指南中討論一些詳細資料，但也可以選擇使用 [NSwag](https://github.com/RSuter/NSwag)，也就是 \# 從 Swagger 或 OpenAPI 規格產生 Typescript 和 c API 用戶端，以及 c \# 控制器，甚至是使用 [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio)掃描包含控制器的 .dll。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="d4fa4-241">如何使用 Swashbuckle NuGet 套件來自動化產生 API Swagger 中繼資料</span><span class="sxs-lookup"><span data-stu-id="d4fa4-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="d4fa4-242">手動產生 Swagger 中繼資料 (JSON 或 YAML 檔案) 是一件冗長的工作。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="d4fa4-243">然而，您可以藉由使用 [Swashbuckle NuGet 套件](https://aka.ms/swashbuckledotnetcore)動態產生 Swagger API 中繼資料，來自動化 ASP.NET Web API 服務的 API 探索。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="d4fa4-244">Swashbuckle 會為您的 ASP.NET Web API 專案自動產生 Swagger 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="d4fa4-245">它支援 ASP.NET Core Web API 專案及傳統式 ASP.NET Web API 和任何其他類別，例如 Azure API 應用程式、Azure 行動應用程式及基於 ASP.NET 的 Azure Service Fabric 微服務。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="d4fa4-246">它也支援部署在容器上的單純 Web API，如同在參考應用程式中的情況。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="d4fa4-247">Swashbuckle 會結合 API 總管及 Swagger 或 [swagger-ui](https://github.com/swagger-api/swagger-ui) 來為您的 API 取用者提供豐富探索及文件體驗。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="d4fa4-248">除了其 Swagger 中繼資料產生器引擎之外，Swashbuckle 也包含了內嵌版本的 swagger-ui，會在安裝 Swashbuckle 之後自動提供。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="d4fa4-249">這表示您可以使用可協助開發人員使用您 API 的良好探索 UI，來補充您的 API。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="d4fa4-250">由於它是自動產生的，它只需要非常少量的程式碼及維護，讓您可以專注於建置您的 API。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="d4fa4-251">API 總管的結果會如圖 6-8 所示。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![顯示 eShopOContainers API 的 Swagger API Explorer 螢幕擷取畫面。](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="d4fa4-253">**圖 6-8**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-253">**Figure 6-8**.</span></span> <span data-ttu-id="d4fa4-254">基於 Swagger 中繼資料的 Swashbuckle API—eShopOnContainers 目錄微服務</span><span class="sxs-lookup"><span data-stu-id="d4fa4-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="d4fa4-255">Swashbuckle 產生的 Swagger UI API 文件包含所有已發佈的動作。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="d4fa4-256">API 總管此時並不是最重要的。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="d4fa4-257">當您有了可在 Swagger 中繼資料中描述自身的 Web API 後，您的 API 便可從 Swagger 式工具隨選即用，包含可瞄準許多平台的用戶端 Proxy 類別產生器。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="d4fa4-258">例如，如前所述，[AutoRest](https://github.com/Azure/AutoRest) 會自動產生 .NET 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="d4fa4-259">但其他像是 [swagger-codegen](https://github.com/swagger-api/swagger-codegen) 的工具也可供使用，自動允許 API 用戶端程式庫、伺服器 Stub 及文件的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="d4fa4-260">目前，Swashbuckle 是由高階中繼套件 [Swashbuckle](https://www.nuget.org/packages/Swashbuckle.AspNetCore) 的五個內部 NuGet 套件組成 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level metapackage [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="d4fa4-261">在您的 Web API 專案中安裝這些 NuGet 套件之後，您需要在 Startup 類別中設定 Swagger，如下列 **簡化** 的程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

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
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
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

<span data-ttu-id="d4fa4-262">完成之後，您便可以啟動您的應用程式，並使用像是這些 URL 來瀏覽下列 Swagger JSON 和 UI 端點：</span><span class="sxs-lookup"><span data-stu-id="d4fa4-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="d4fa4-263">您先前曾看過 Swashbuckle 為 URL 產生的 UI，像是 `http://<your-root-url>/swagger`。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="d4fa4-264">在圖 6-9 中，您也可以看到該如何測試任一 API 方法。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Swagger UI 的螢幕擷取畫面，其中顯示可用的測試控管。](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="d4fa4-266">**圖 6-9**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-266">**Figure 6-9**.</span></span> <span data-ttu-id="d4fa4-267">Swashbuckle UI 測試目錄/項目 API 方法</span><span class="sxs-lookup"><span data-stu-id="d4fa4-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="d4fa4-268">Swagger UI API 詳細資料會顯示回應的範例，並可用於執行實際 API，對於開發人員探索很有助益。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="d4fa4-269">圖 6-10 顯示了當您使用 [Postman](https://www.getpostman.com/) \(英文\) 要求 `http://<your-root-url>/swagger/v1/swagger.json` 時，從 eShopOnContainers 微服務 (即於幕後使用的工具) 產生的 Swagger JSON 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![顯示 Swagger JSON 中繼資料的範例 Postman UI 螢幕擷取畫面。](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="d4fa4-271">**圖 6-10**。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-271">**Figure 6-10**.</span></span> <span data-ttu-id="d4fa4-272">Swagger JSON 中繼資料</span><span class="sxs-lookup"><span data-stu-id="d4fa4-272">Swagger JSON metadata</span></span>

<span data-ttu-id="d4fa4-273">就是這麼簡單。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-273">It is that simple.</span></span> <span data-ttu-id="d4fa4-274">由於它是自動產生的，當您將更多功能新增至您的 API 時，Swagger 中繼資料也會持續成長。</span><span class="sxs-lookup"><span data-stu-id="d4fa4-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d4fa4-275">其他資源</span><span class="sxs-lookup"><span data-stu-id="d4fa4-275">Additional resources</span></span>

- <span data-ttu-id="d4fa4-276">**使用 Swagger ASP.NET Web API 說明頁面** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="d4fa4-277">**開始使用 Swashbuckle 和 ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="d4fa4-278">**開始使用 NSwag 和 ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="d4fa4-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="d4fa4-279">[上一個](microservice-application-design.md) 
> [下一步](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="d4fa4-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
