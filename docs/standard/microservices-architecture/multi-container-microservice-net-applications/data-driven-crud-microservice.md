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
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="82f65-104">建立簡單的資料導向 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="82f65-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="82f65-105">此章節所述方式來建立簡單執行的微服務建立時，讀取、 更新和刪除 (CRUD) 作業的資料來源。</span><span class="sxs-lookup"><span data-stu-id="82f65-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="82f65-106">設計簡單的 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="82f65-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="82f65-107">從設計觀點來看，這種類型的容器化的微服務就非常簡單。</span><span class="sxs-lookup"><span data-stu-id="82f65-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="82f65-108">若要解決此問題可能是簡單，或可能是實作的概念性驗證。</span><span class="sxs-lookup"><span data-stu-id="82f65-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="82f65-109">**圖 8-4**。</span><span class="sxs-lookup"><span data-stu-id="82f65-109">**Figure 8-4**.</span></span> <span data-ttu-id="82f65-110">內部設計簡單的 CRUD microservices</span><span class="sxs-lookup"><span data-stu-id="82f65-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="82f65-111">這種簡單的資料磁碟機服務的範例是來自 eShopOnContainers 範例應用程式類別目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="82f65-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="82f65-112">這種類型的服務在單一 ASP.NET Core Web API 專案，包括其資料模型、 其商務邏輯和其資料存取程式碼的類別中實作它的功能。</span><span class="sxs-lookup"><span data-stu-id="82f65-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="82f65-113">也在 SQL Server 中執行 （做為另一個容器基於開發/測試），在資料庫中儲存相關的資料，但如圖 8-5 所示，則也可能是任何規則的 SQL Server 主機。</span><span class="sxs-lookup"><span data-stu-id="82f65-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="82f65-114">**圖 8-5**。</span><span class="sxs-lookup"><span data-stu-id="82f65-114">**Figure 8-5**.</span></span> <span data-ttu-id="82f65-115">簡單的資料驅動/CRUD 微服務設計</span><span class="sxs-lookup"><span data-stu-id="82f65-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="82f65-116">當您開發這種服務時，您只需要[ASP.NET Core](https://docs.microsoft.com/aspnet/core/)和資料存取應用程式開發介面或 ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index)。</span><span class="sxs-lookup"><span data-stu-id="82f65-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="82f65-117">您也可以產生[Swagger](http://swagger.io/)中繼資料會自動透過[Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)以提供您服務的提供，描述在下一節所述。</span><span class="sxs-lookup"><span data-stu-id="82f65-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="82f65-118">請注意，執行像 Docker 容器中的 SQL Server 最適合用於開發環境，因為您最多可以有您所有的相依性的資料庫伺服器，而不需要佈建資料庫中的雲端或內部部署執行。</span><span class="sxs-lookup"><span data-stu-id="82f65-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="82f65-119">執行整合測試時，這是很方便。</span><span class="sxs-lookup"><span data-stu-id="82f65-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="82f65-120">不過，實際執行環境，在容器中執行的資料庫伺服器不是建議，因為通常不會使用該方法的高可用性。</span><span class="sxs-lookup"><span data-stu-id="82f65-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="82f65-121">在 Azure 中的生產環境，建議您使用 Azure SQL DB 或任何其他可提供高可用性和高擴充性的資料庫技術。</span><span class="sxs-lookup"><span data-stu-id="82f65-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="82f65-122">例如，如 NoSQL 方法，您可以選擇 DocumentDB。</span><span class="sxs-lookup"><span data-stu-id="82f65-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="82f65-123">最後，藉由編輯的 Dockerfile 並 docker compose.yml 中繼資料檔案，您可以設定此容器映像建立的方式，它會使用，加上設計等內部和外部名稱及 TCP 通訊埠設定哪些基底映像。</span><span class="sxs-lookup"><span data-stu-id="82f65-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="82f65-124">使用 ASP.NET Core 實作簡單的 CRUD 微服務</span><span class="sxs-lookup"><span data-stu-id="82f65-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="82f65-125">若要實作簡單的 CRUD 微服務，使用.NET Core 和 Visual Studio，您開始建立簡單的 ASP.NET Core Web API 專案 （執行.NET Core 讓它可以執行 Linux Docker 主機上），做為顯示圖 8-6。</span><span class="sxs-lookup"><span data-stu-id="82f65-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="82f65-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="82f65-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="82f65-127">**圖 8-6**。</span><span class="sxs-lookup"><span data-stu-id="82f65-127">**Figure 8-6**.</span></span> <span data-ttu-id="82f65-128">Visual Studio 中建立 ASP.NET Core Web API 專案</span><span class="sxs-lookup"><span data-stu-id="82f65-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="82f65-129">建立專案之後，您可以實作 MVC 控制器，您可以按照任何其他 Web API 專案使用 Entity Framework 應用程式開發介面或其他應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="82f65-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="82f65-130">在 eShopOnContainers.Catalog.API 專案中，您可以看到該微服務的主要相依性都只 ASP.NET Core 本身、 Entity Framework 和 Swashbuckle，如圖 8-7 所示。</span><span class="sxs-lookup"><span data-stu-id="82f65-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="82f65-131">**圖 8-7**。</span><span class="sxs-lookup"><span data-stu-id="82f65-131">**Figure 8-7**.</span></span> <span data-ttu-id="82f65-132">簡單的 CRUD Web API 微服務中的相依性</span><span class="sxs-lookup"><span data-stu-id="82f65-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="82f65-133">實作與 Entity Framework Core CRUD Web API 服務</span><span class="sxs-lookup"><span data-stu-id="82f65-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="82f65-134">Entity Framework (EF) 核心的輕量型可擴充的並跨平台版本常見的 Entity Framework 資料存取技術。</span><span class="sxs-lookup"><span data-stu-id="82f65-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="82f65-135">EF 核心是可讓.NET 開發人員使用.NET 物件的資料庫與物件關聯式對應 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="82f65-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="82f65-136">目錄微服務會使用 EF 和 SQL Server 提供者，因為它的資料庫在與 Linux Docker 映像的 SQL Server 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="82f65-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="82f65-137">不過，資料庫無法部署至任何 SQL Server，例如 Windows 內部部署或 Azure SQL DB。</span><span class="sxs-lookup"><span data-stu-id="82f65-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="82f65-138">唯一您需要變更的是 ASP.NET Web API 的微服務中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="82f65-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="82f65-139">Entity Framework Core 加入相依性</span><span class="sxs-lookup"><span data-stu-id="82f65-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="82f65-140">您可以針對您想要使用，在此情況下 SQL Server，從 Visual Studio IDE 中或使用 NuGet 主控台資料庫提供者安裝 NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="82f65-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="82f65-141">請使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="82f65-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="82f65-142">資料模型</span><span class="sxs-lookup"><span data-stu-id="82f65-142">The data model</span></span>

<span data-ttu-id="82f65-143">使用 EF 核心會使用模型執行資料存取。</span><span class="sxs-lookup"><span data-stu-id="82f65-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="82f65-144">模型是由實體類別和衍生的內容，表示與資料庫，可以讓您查詢及儲存資料的工作階段所組成。</span><span class="sxs-lookup"><span data-stu-id="82f65-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="82f65-145">您可以從現有的資料庫產生模型、 手動撰寫程式碼模式，以符合您的資料庫，或從您的模型建立的資料庫 （及您的模型變更後經過一段時間不同時） 使用 EF 移轉。</span><span class="sxs-lookup"><span data-stu-id="82f65-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="82f65-146">目錄微服務會使用最後一個的方法。</span><span class="sxs-lookup"><span data-stu-id="82f65-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="82f65-147">您可以看到 CatalogItem 實體類別，在下列的程式碼範例簡單純舊 CLR 物件的範例 ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) 實體類別。</span><span class="sxs-lookup"><span data-stu-id="82f65-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="82f65-148">您也需要表示與資料庫的工作階段的 DbContext。</span><span class="sxs-lookup"><span data-stu-id="82f65-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="82f65-149">針對類別目錄微服務 CatalogContext 類別衍生自 DbContext 的基底類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="82f65-150">您可以在 DbContext 實作額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="82f65-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="82f65-151">例如，在範例應用程式中，我們有 OnModelCreating 方法 CatalogContext 類別會自動填入範例資料第一次嘗試存取資料庫中。</span><span class="sxs-lookup"><span data-stu-id="82f65-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="82f65-152">這個方法是用於示範的資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-152">This method is useful for demo data.</span></span> <span data-ttu-id="82f65-153">您也可以使用 OnModelCreating 方法來自訂物件/資料庫與許多其他的實體對應[EF 擴充性點](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)。</span><span class="sxs-lookup"><span data-stu-id="82f65-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="82f65-154">您可以查看進一步的詳細資料中 OnModelCreating[實作持續性的基礎結構層與 Entity Framework Core](#implementing_infrastructure_persistence)稍後在這個活頁簿中的區段。</span><span class="sxs-lookup"><span data-stu-id="82f65-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="82f65-155">從 Web API 控制器查詢資料</span><span class="sxs-lookup"><span data-stu-id="82f65-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="82f65-156">實體類別的執行個體通常會使用 Language Integrated Query (LINQ)，從資料庫擷取，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="82f65-157">儲存資料</span><span class="sxs-lookup"><span data-stu-id="82f65-157">Saving data</span></span>

<span data-ttu-id="82f65-158">建立、 刪除，並在使用實體類別的執行個體的資料庫中修改資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="82f65-159">您可以加入程式碼，如下列硬式編碼範例 （在此情況下，模擬資料） 至您的 Web API 控制器。</span><span class="sxs-lookup"><span data-stu-id="82f65-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="82f65-160">在 ASP.NET Core 及 Web API 控制器的相依性插入</span><span class="sxs-lookup"><span data-stu-id="82f65-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="82f65-161">在 ASP.NET Core 中，您可以使用相依性插入 (DI) 立即可用的。</span><span class="sxs-lookup"><span data-stu-id="82f65-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="82f65-162">您不需要設定協力廠商的逆轉控制 (IoC) 容器，但如果您想，您可以在 ASP.NET Core 基礎結構中插入您慣用的 IoC 容器。</span><span class="sxs-lookup"><span data-stu-id="82f65-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="82f65-163">在此情況下，這表示您可以直接插入必要的 EF DBContext 或其他儲存機制，透過控制器建構函式。</span><span class="sxs-lookup"><span data-stu-id="82f65-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="82f65-164">在上面的 CatalogController 類別的範例，我們會插入 CatalogContext 型別的物件加上透過 CatalogController 建構函式的其他物件。</span><span class="sxs-lookup"><span data-stu-id="82f65-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="82f65-165">設定 Web API 專案中的重要組態是 DbContext 類別註冊到服務的 IoC 容器。</span><span class="sxs-lookup"><span data-stu-id="82f65-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="82f65-166">通常，您在啟動類別藉由呼叫服務。AddDbContext 方法內 ConfigureServices 方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="82f65-167">其他資源</span><span class="sxs-lookup"><span data-stu-id="82f65-167">Additional resources</span></span>

-   <span data-ttu-id="82f65-168">**查詢資料**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="82f65-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="82f65-169">**將資料儲存**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="82f65-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="82f65-170">資料庫連接字串和環境變數使用 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="82f65-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="82f65-171">您可以使用的 ASP.NET 核心設定，並將 ConnectionString 屬性加入至您 settings.json 檔案，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="82f65-172">Settings.json 檔案可以有預設值為 ConnectionString 屬性或任何其他內容。</span><span class="sxs-lookup"><span data-stu-id="82f65-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="82f65-173">不過，這些屬性將會覆寫您在 docker compose.override.yml 檔案中指定的環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="82f65-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="82f65-174">從您的 docker compose.yml 或 docker compose.override.yml 檔，您可以初始化這些環境變數的 Docker 將它們做為作業系統的環境變數為您設定，因此下列 docker compose.override.yml 檔案 （此連線中所示字串和其他行包裝在此範例中，但它不會包裝在自己的檔案）。</span><span class="sxs-lookup"><span data-stu-id="82f65-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="82f65-175">在解決方案層級 docker compose.yml 檔案不只會比在專案 」 或 「 微服務層級的組態檔更有彈性，但是也更安全的。</span><span class="sxs-lookup"><span data-stu-id="82f65-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="82f65-176">請考慮您建置每微服務的 Docker 映像不包含 docker compose.yml 檔案，只有二進位檔案和每個微服務，包括 Dockerfile 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="82f65-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="82f65-177">但 docker compose.yml 檔案尚未部署應用程式; 以及它只在部署期間使用。</span><span class="sxs-lookup"><span data-stu-id="82f65-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="82f65-178">因此，將環境變數值放入這些 docker compose.yml 檔案中 （即使未加密的值） 是比放置這些值會隨著您的程式碼部署的一般.NET 組態檔中更安全。</span><span class="sxs-lookup"><span data-stu-id="82f65-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="82f65-179">最後，使用組態從程式碼取得該值\["ConnectionString"\]ConfigureServices 方法，在先前的程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="82f65-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="82f65-180">不過，實際執行環境，您可能要如何儲存機密資料的連接字串類似總管 中的其他方法。</span><span class="sxs-lookup"><span data-stu-id="82f65-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="82f65-181">通常，將受您所選擇的 orchestrator，像是您如何使用[Docker Swarm 密碼管理](https://docs.docker.com/engine/swarm/secrets/)。</span><span class="sxs-lookup"><span data-stu-id="82f65-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="82f65-182">在 ASP.NET Web 應用程式開發介面中實作版本控制</span><span class="sxs-lookup"><span data-stu-id="82f65-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="82f65-183">當商務需求變更時，可能會加入新的資源集合、 資源之間的關聯性可能會變更，和可能修改的資源中的資料結構。</span><span class="sxs-lookup"><span data-stu-id="82f65-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="82f65-184">更新 Web 應用程式開發介面來處理新的需求是相當簡單的程序，但您必須考慮這類變更對於會耗用 Web API 的用戶端應用程式的影響。</span><span class="sxs-lookup"><span data-stu-id="82f65-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="82f65-185">雖然開發人員設計和實作 Web API 的應用程式開發介面的完整控制權，開發人員不需要用戶端應用程式可能會建立第三方組織操作遠端控制的程度。</span><span class="sxs-lookup"><span data-stu-id="82f65-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="82f65-186">版本設定可讓 Web API，以表示它會公開的資源的功能。</span><span class="sxs-lookup"><span data-stu-id="82f65-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="82f65-187">用戶端應用程式就可以提交要求至特定版本的功能或資源。</span><span class="sxs-lookup"><span data-stu-id="82f65-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="82f65-188">有數種方法來實作版本設定：</span><span class="sxs-lookup"><span data-stu-id="82f65-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="82f65-189">URI 的版本控制</span><span class="sxs-lookup"><span data-stu-id="82f65-189">URI versioning</span></span>

-   <span data-ttu-id="82f65-190">查詢字串的版本控制</span><span class="sxs-lookup"><span data-stu-id="82f65-190">Query string versioning</span></span>

-   <span data-ttu-id="82f65-191">標頭版本控制</span><span class="sxs-lookup"><span data-stu-id="82f65-191">Header versioning</span></span>

<span data-ttu-id="82f65-192">查詢字串和 URI 版本設定是最簡單的方式實作。</span><span class="sxs-lookup"><span data-stu-id="82f65-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="82f65-193">標頭版本設定是很好的方法。</span><span class="sxs-lookup"><span data-stu-id="82f65-193">Header versioning is a good approach.</span></span> <span data-ttu-id="82f65-194">不過，不為明確和那樣 URI 版本設定標頭版本。</span><span class="sxs-lookup"><span data-stu-id="82f65-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="82f65-195">因為 URL 版本是最簡單且最明確，eShopOnContainers 範例應用程式會使用 URI 版本設定。</span><span class="sxs-lookup"><span data-stu-id="82f65-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="82f65-196">使用 URI 版本設定，如同 eShopOnContainers 範例應用程式中，每次修改 Web 應用程式開發介面，或變更結構描述的資源，您將版本號碼加入每個資源的 URI。</span><span class="sxs-lookup"><span data-stu-id="82f65-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="82f65-197">現有的 Uri 應繼續操作之前一樣，傳回符合的資源結構描述符合要求的版本。</span><span class="sxs-lookup"><span data-stu-id="82f65-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="82f65-198">下列程式碼範例所示，可以將版本設定在 Web API 中，讓版本在 URI 中明確使用路由屬性 (在此情況下 v1)。</span><span class="sxs-lookup"><span data-stu-id="82f65-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="82f65-199">此版本設定機制很簡單，而且相依於伺服器要求路由至適當的端點。</span><span class="sxs-lookup"><span data-stu-id="82f65-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="82f65-200">不過，對於更複雜的版本設定和使用 REST 時的最佳方法，您應該使用超及實作[HATEOAS （超文字做為應用程式狀態的引擎）](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources)。</span><span class="sxs-lookup"><span data-stu-id="82f65-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="82f65-201">其他資源</span><span class="sxs-lookup"><span data-stu-id="82f65-201">Additional resources</span></span>

-   <span data-ttu-id="82f65-202">**Scott Hanselman。ASP.NET Core RESTful Web API 版本設定輕鬆**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="82f65-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="82f65-203">**版本控制 RESTful web API**</span><span class="sxs-lookup"><span data-stu-id="82f65-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="82f65-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span><span class="sxs-lookup"><span data-stu-id="82f65-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="82f65-205">**伊 Fielding。版本控制、 超和 REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="82f65-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="82f65-206">從您的 ASP.NET Core Web API 產生 Swagger 描述中繼資料</span><span class="sxs-lookup"><span data-stu-id="82f65-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="82f65-207">[Swagger](http://swagger.io/)是常用的開放原始碼架構支援大型生態系統的工具，可協助您設計、 建置、 文件，並使用您的 RESTful Api。</span><span class="sxs-lookup"><span data-stu-id="82f65-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="82f65-208">得 Api 描述中繼資料網域的標準。</span><span class="sxs-lookup"><span data-stu-id="82f65-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="82f65-209">您應該包含 Swagger 描述中繼資料，與任何一種微服務，資料驅動 microservices 或更多進階網域導向 microservices （下一節所述）。</span><span class="sxs-lookup"><span data-stu-id="82f65-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="82f65-210">Swagger 的核心是 Swagger 規格，也就是 JSON 或 YAML 檔案中的 API 描述中繼資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="82f65-211">規格會建立您的 API，詳述所有其資源和作業中這兩個的人們和 machine readable 格式的簡易的開發、 探索與整合的 RESTful 合約。</span><span class="sxs-lookup"><span data-stu-id="82f65-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="82f65-212">規格為基礎的 OpenAPI 規格 (OAS) 和開發開啟、 透明的且協同社群標準化 RESTful 介面定義的方式。</span><span class="sxs-lookup"><span data-stu-id="82f65-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="82f65-213">此規格會定義可探索服務的方式，和其功能的了解的結構。</span><span class="sxs-lookup"><span data-stu-id="82f65-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="82f65-214">如需詳細資訊，包括 web 編輯器和公司、 Spotify、 超級、 寬限時間和 Microsoft Swagger 規格的範例請參閱 Swagger 站台 (<http://swagger.io>)。</span><span class="sxs-lookup"><span data-stu-id="82f65-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="82f65-215">為何要使用 Swagger？</span><span class="sxs-lookup"><span data-stu-id="82f65-215">Why use Swagger?</span></span>

<span data-ttu-id="82f65-216">若要產生您的應用程式開發介面 Swagger 中繼資料的主要原因如下所示。</span><span class="sxs-lookup"><span data-stu-id="82f65-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="82f65-217">**其他產品來自動使用及整合您的應用程式開發介面的能力**。</span><span class="sxs-lookup"><span data-stu-id="82f65-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="82f65-218">數十個產品和[商業工具](http://swagger.io/commercial-tools/)和許多[程式庫和架構](http://swagger.io/open-source-integrations/)支援 Swagger。</span><span class="sxs-lookup"><span data-stu-id="82f65-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="82f65-219">Microsoft 具有高層級的產品與工具，可以自動耗用 Swagger 為基礎的 Api，如下所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="82f65-220">[AutoRest](https://github.com/Azure/AutoRest)。</span><span class="sxs-lookup"><span data-stu-id="82f65-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="82f65-221">您可以自動產生的 Swagger 函式呼叫的.NET 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="82f65-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="82f65-222">這個</span><span class="sxs-lookup"><span data-stu-id="82f65-222">This</span></span>

-   <span data-ttu-id="82f65-223">工具可從 CLI，它也會整合與 Visual Studio 以透過 GUI 的方便使用。</span><span class="sxs-lookup"><span data-stu-id="82f65-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="82f65-224">[Microsoft Flow](https://flow.microsoft.com/en-us/)。</span><span class="sxs-lookup"><span data-stu-id="82f65-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="82f65-225">您可以自動[使用並整合您的 API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)成高階 Microsoft Flow 工作流程，且沒有執行任何程式設計所需的技巧。</span><span class="sxs-lookup"><span data-stu-id="82f65-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="82f65-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)。</span><span class="sxs-lookup"><span data-stu-id="82f65-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="82f65-227">您可以自動使用您的 API，從[PowerApps 行動裝置應用程式](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/)建置[PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/)，與所需的任何程式設計技術。</span><span class="sxs-lookup"><span data-stu-id="82f65-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="82f65-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="82f65-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="82f65-229">您可以自動[使用，並將您的 API 整合到 Azure App Service 的邏輯應用程式](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)，與所需的任何程式設計技術。</span><span class="sxs-lookup"><span data-stu-id="82f65-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="82f65-230">**讓您自動產生應用程式開發介面文件**。</span><span class="sxs-lookup"><span data-stu-id="82f65-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="82f65-231">當您建立複雜的微服務為基礎應用程式，例如大型的 RESTful Api 時您需要在要求和回應裝載中使用不同的資料模型處理多個端點。</span><span class="sxs-lookup"><span data-stu-id="82f65-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="82f65-232">具有適當的文件，以及取得純色的 API 總管 中，當您使用 Swagger，為您的應用程式開發介面和開發人員所採用的成功與否的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="82f65-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="82f65-233">Swagger 的中繼資料是 Microsoft Flow、 PowerApps 和 Azure 邏輯應用程式用來了解如何使用 Api 且與它們連線。</span><span class="sxs-lookup"><span data-stu-id="82f65-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="82f65-234">如何自動化 API Swagger 中繼資料的產生與 Swashbuckle NuGet 封裝</span><span class="sxs-lookup"><span data-stu-id="82f65-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="82f65-235">產生 Swagger 中繼資料，以手動方式 （以 JSON 或 YAML 檔案） 可以是冗長的工作。</span><span class="sxs-lookup"><span data-stu-id="82f65-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="82f65-236">不過，您可以使用自動執行的 ASP.NET Web API 服務的應用程式開發介面探索[Swashbuckle NuGet 封裝](http://aka.ms/swashbuckledotnetcore)動態產生 Swagger API 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="82f65-237">Swashbuckle 會自動產生 ASP.NET Web API 專案的 Swagger 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="82f65-238">它支援 ASP.NET Core Web API 專案與傳統的 ASP.NET Web API，以及任何其他類別，例如 Azure API 應用程式、 Azure 行動應用程式，以 ASP.NET 為基礎的 Azure Service Fabric microservices。</span><span class="sxs-lookup"><span data-stu-id="82f65-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="82f65-239">它也支援一般部署容器，而在參考應用程式的 Web API。</span><span class="sxs-lookup"><span data-stu-id="82f65-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="82f65-240">Swashbuckle 結合 API 總管和 Swagger 或[swagger ui](https://github.com/swagger-api/swagger-ui)來提供豐富的探索和文件的應用程式開發介面消費者的體驗。</span><span class="sxs-lookup"><span data-stu-id="82f65-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="82f65-241">除了 Swagger 中繼資料產生器引擎 Swashbuckle 也包含內嵌的 swagger ui，它會自動提供 Swashbuckle 安裝之後的版本。</span><span class="sxs-lookup"><span data-stu-id="82f65-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="82f65-242">這表示可以補充您的 API nice 探索可協助開發人員使用您的應用程式開發介面的 UI。</span><span class="sxs-lookup"><span data-stu-id="82f65-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="82f65-243">它需要非常少量的程式碼和維護，因為它自動產生，可讓您專注於建置您的 API。</span><span class="sxs-lookup"><span data-stu-id="82f65-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="82f65-244">API 總管 結果看起來像圖 8-8。</span><span class="sxs-lookup"><span data-stu-id="82f65-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="82f65-245">**圖 8-8**。</span><span class="sxs-lookup"><span data-stu-id="82f65-245">**Figure 8-8**.</span></span> <span data-ttu-id="82f65-246">Swagger 中繼資料為基礎的 Swashbuckle API 總管 — eShopOnContainers 目錄微服務</span><span class="sxs-lookup"><span data-stu-id="82f65-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="82f65-247">[總管] 中應用程式開發介面不是最重要的一點。</span><span class="sxs-lookup"><span data-stu-id="82f65-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="82f65-248">一旦您擁有可描述自己 Swagger 中繼資料中的 Web API，您的 API 可順暢地從 Swagger 為基礎的工具，包括用戶端 proxy 類別程式碼產生器可以在許多平台為目標。</span><span class="sxs-lookup"><span data-stu-id="82f65-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="82f65-249">例如，如所述， [AutoRest](https://github.com/Azure/AutoRest) .NET 用戶端類別會自動產生。</span><span class="sxs-lookup"><span data-stu-id="82f65-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="82f65-250">但其他工具想[swagger codegen](https://github.com/swagger-api/swagger-codegen)是也可以使用程式庫、 伺服器 stub 和文件會自動讓 API 用戶端的程式碼產生。</span><span class="sxs-lookup"><span data-stu-id="82f65-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="82f65-251">目前，Swashbuckle 包含兩個 NuGet 套件： Swashbuckle.SwaggerGen 和 Swashbuckle.SwaggerUi。</span><span class="sxs-lookup"><span data-stu-id="82f65-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="82f65-252">前者提供直接從您的應用程式開發介面實作產生一或多個 Swagger 文件，並將它們公開為 JSON 端點的功能。</span><span class="sxs-lookup"><span data-stu-id="82f65-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="82f65-253">後者提供 swagger ui 工具可以由您的應用程式和由產生的 Swagger 文件來描述您 API 所提供的內嵌的版本。</span><span class="sxs-lookup"><span data-stu-id="82f65-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="82f65-254">不過，最新版的 Swashbuckle 換行 Swashbuckle.AspNetCore metapackage 的。</span><span class="sxs-lookup"><span data-stu-id="82f65-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="82f65-255">請注意，.NET Core Web API 專案，您需要使用[Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) 1.0.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="82f65-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="82f65-256">這些 NuGet 封裝安裝在您的 Web API 專案之後，您需要設定 Swagger 中啟動類別，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="82f65-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

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

<span data-ttu-id="82f65-257">完成之後，您可以啟動您的應用程式，並瀏覽下列 Swagger JSON 和 UI 端點使用這些 Url:</span><span class="sxs-lookup"><span data-stu-id="82f65-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="82f65-258">您先前已看到的 URL，例如 http:// Swashbuckle 所建立的產生的 UI&lt;程式根 url &gt; /swagger/ui。</span><span class="sxs-lookup"><span data-stu-id="82f65-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="82f65-259">圖 8-9 您也可以查看如何測試任何應用程式開發介面的方法。</span><span class="sxs-lookup"><span data-stu-id="82f65-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="82f65-260">**圖 8-9**。</span><span class="sxs-lookup"><span data-stu-id="82f65-260">**Figure 8-9**.</span></span> <span data-ttu-id="82f65-261">Swashbuckle UI 測試的類別目錄/項目 API 方法</span><span class="sxs-lookup"><span data-stu-id="82f65-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="82f65-262">圖 8-10 顯示 eShopOnContainers 微服務產生的 Swagger JSON 中繼資料 （此為之下使用的工具） 在您要求的&lt;程式根 url&gt;/swagger/v1/swagger.json 使用[郵差](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="82f65-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="82f65-263">**圖 8-10**。</span><span class="sxs-lookup"><span data-stu-id="82f65-263">**Figure 8-10**.</span></span> <span data-ttu-id="82f65-264">Swagger JSON 中繼資料</span><span class="sxs-lookup"><span data-stu-id="82f65-264">Swagger JSON metadata</span></span>

<span data-ttu-id="82f65-265">就這麼簡單。</span><span class="sxs-lookup"><span data-stu-id="82f65-265">It is that simple.</span></span> <span data-ttu-id="82f65-266">和自動產生，因此當您將更多的功能加入您的 api，將會成長 Swagger 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="82f65-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="82f65-267">其他資源</span><span class="sxs-lookup"><span data-stu-id="82f65-267">Additional resources</span></span>

-   <span data-ttu-id="82f65-268">**ASP.NET Web API 說明頁面使用 Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="82f65-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="82f65-269">[上一個](微服務-應用程式-design.md) [下一步] (多-container-應用程式-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="82f65-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
