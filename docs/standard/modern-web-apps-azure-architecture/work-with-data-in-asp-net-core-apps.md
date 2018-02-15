---
title: "使用 ASP.NET Core 應用程式中的資料"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |使用 asp 中的資料"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="0f2f2-103">在 ASP.NET Core 應用程式中使用資料</span><span class="sxs-lookup"><span data-stu-id="0f2f2-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="0f2f2-104">「 資料是非常寶貴的功能和將持續時間超過本身的系統。 」</span><span class="sxs-lookup"><span data-stu-id="0f2f2-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="0f2f2-105">Tim Berners-lee</span><span class="sxs-lookup"><span data-stu-id="0f2f2-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="0f2f2-106">總結</span><span class="sxs-lookup"><span data-stu-id="0f2f2-106">Summary</span></span>

<span data-ttu-id="0f2f2-107">資料存取是幾乎任何的軟體應用程式中很重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="0f2f2-108">ASP.NET Core 支援各種不同的資料存取選項，包括 Entity Framework Core （和 Entity Framework 6），而且可以使用任何.NET 資料存取架構。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="0f2f2-109">其中的資料存取架構使用的選擇取決於應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="0f2f2-110">抽象化 ApplicationCore 和 UI 專案，這些選項和封裝的基礎結構的實作詳細資料有助於產生鬆散偶合、 可測試的軟體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="0f2f2-111">Entity Framework Core （適用於關聯式資料庫）</span><span class="sxs-lookup"><span data-stu-id="0f2f2-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="0f2f2-112">如果您要撰寫新的 ASP.NET Core 應用程式需要處理關聯式資料，Entity Framework Core （EF 核心） 是您的應用程式存取其資料的建議的方式。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="0f2f2-113">EF 核心是物件關聯式對應工具 (O/RM)，可讓.NET 開發人員，以保存資料來源的物件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="0f2f2-114">它不必將大部分的開發通常需要撰寫資料存取程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="0f2f2-115">ASP.NET Core 像已經改寫 EF 核心模組支援跨平台應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="0f2f2-116">您將它加入至您的應用程式以 NuGet 套件、 將它設定在啟動時，和要求透過相依性插入，每當您需要它。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="0f2f2-117">若要使用 SQL Server 資料庫的 EF 核心，執行下列 dotnet CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="0f2f2-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="0f2f2-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="0f2f2-119">若要新增為 InMemory 資料來源，進行測試的支援：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="0f2f2-120">dotnet 新增封裝 Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="0f2f2-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="0f2f2-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="0f2f2-121">The DbContext</span></span>

<span data-ttu-id="0f2f2-122">若要使用 EF 核心，您需要 DbContext 子的類別。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="0f2f2-123">這個類別包含代表您的應用程式將會使用實體集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="0f2f2-124">EShopOnWeb 範例包括 CatalogContext 與項目、 品牌、 和類型的集合：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="0f2f2-125">您 DbContext 必須有接受 DbContextOptions 建構函式，並將此引數傳遞給基底的 DbContext 建構函式。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="0f2f2-126">請注意，如果應用程式中有一個 DbContext，您可以傳遞 DbContextOptions，執行個體，但如果您有多個您必須使用泛型 DbContextOptions<T> DbContext 類型做為泛型參數中傳遞的類型。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="0f2f2-127">設定 EF 核心</span><span class="sxs-lookup"><span data-stu-id="0f2f2-127">Configuring EF Core</span></span>

<span data-ttu-id="0f2f2-128">在您的 ASP.NET Core 應用程式，您通常需要設定 EF 核心 ConfigureServices 方法中。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="0f2f2-129">EF 核心使用 DbContextOptionsBuilder，可支援幾個很有幫助的擴充方法，以簡化其組態。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="0f2f2-130">若要設定 CatalogContext 組態中定義的連接字串中使用 SQL Server 資料庫，您可以加入下列程式碼以 ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="0f2f2-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="0f2f2-131">若要使用的記憶體中資料庫：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="0f2f2-132">一旦您安裝 EF 核心，建立 DbContext 子型別，並設定 ConfigureServices 中，您已準備好使用 EF 核心。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="0f2f2-133">您可以要求您在需要它，任何服務中的 DbContext 類型的執行個體，並開始使用您保存使用 LINQ，如同它們是直接在集合中的實體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="0f2f2-134">EF 核心運作的程式來儲存和擷取資料的 SQL 查詢的 LINQ 運算式轉譯。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="0f2f2-135">您可以看到 EF 核心藉由設定記錄器和確保至少其層級設定為執行的查詢資訊，如圖 8-1 所示。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="0f2f2-136">圖 8-1 到主控台的記錄 EF 核心查詢</span><span class="sxs-lookup"><span data-stu-id="0f2f2-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="0f2f2-137">正在擷取及儲存資料</span><span class="sxs-lookup"><span data-stu-id="0f2f2-137">Fetching and Storing Data</span></span>

<span data-ttu-id="0f2f2-138">若要從 EF 核心擷取資料，您可以存取適當的屬性，並使用 LINQ 篩選結果。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="0f2f2-139">您也可以使用 LINQ 來執行投影，轉換到另一種類型的結果。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="0f2f2-140">下列範例會擷取 CatalogBrands，依名稱排序，它們已啟用的屬性，以進行篩選和投射到 SelectListItem 類型：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="0f2f2-141">請務必在上述範例中新增至 ToListAsync 呼叫，以立即執行查詢。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="0f2f2-142">否則，陳述式將會指派 IQueryable<SelectListItem>至 brandItems，這不會執行直到經過列舉。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="0f2f2-143">有優缺點，若要從方法傳回 IQueryable 結果。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="0f2f2-144">它可讓的查詢 EF 核心會建構來進一步修改，但是如果，也可以只在執行階段，就會發生的錯誤導致作業會加入至 EF 核心不能轉譯的查詢。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="0f2f2-145">將任何篩選至執行資料存取，方法通常比較安全，並傳回回記憶體中集合 (例如，列出<T>) 做為結果。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="0f2f2-146">EF 核心提取從持續性的實體上追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="0f2f2-147">若要儲存變更追蹤的實體，您只需要呼叫 SaveChanges 方法 DbContext，並確定它是用來擷取實體的相同 DbContext 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="0f2f2-148">加入和移除項目是直接在適當的 DbSet 屬性中使用 SaveChanges 呼叫，以執行資料庫命令，然後再次上。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="0f2f2-149">下列範例示範如何加入、 更新和移除從持續性的實體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="0f2f2-150">EF 核心支援同步和非同步方法，擷取和儲存。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="0f2f2-151">在 web 應用程式，則建議使用非同步/等候模式，與非同步方法，使 web 伺服器執行緒不會封鎖在等候資料存取作業完成時。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="0f2f2-152">擷取相關的資料</span><span class="sxs-lookup"><span data-stu-id="0f2f2-152">Fetching Related Data</span></span>

<span data-ttu-id="0f2f2-153">當 EF 核心擷取實體時，它會填入所有直接與該實體資料庫中儲存的內容。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="0f2f2-154">未填入導覽屬性，例如相關實體的清單，且可能有其值設定為 null。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="0f2f2-155">這可確保 EF 核心未擷取超過所需的資料所在的 web 應用程式，它們必須快速處理要求並傳回回應，以有效率的方式特別重要。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="0f2f2-156">若要包含與實體使用的關聯性*積極式載入*，您指定在查詢中，使用包含擴充方法的屬性所示：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="0f2f2-157">您可以包含多個關聯性，而且您也可以包含子關聯性使用 ThenInclude。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="0f2f2-158">EF 核心會執行單一查詢來擷取結果集的實體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="0f2f2-159">用於載入相關的資料的另一個選項是使用*明確載入*。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="0f2f2-160">明確式載入可讓您將額外的資料載入已擷取的實體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="0f2f2-161">由於這牽涉到資料庫的個別要求，不建議的 web 應用程式應該減少資料庫的每個要求所做的往返。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="0f2f2-162">*消極式載入*是會自動載入相關的資料，因為它參考應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="0f2f2-163">EF 核心目前不支援，但做為具有明確載入它通常必須停用 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="0f2f2-164">具有恢復功能的連線</span><span class="sxs-lookup"><span data-stu-id="0f2f2-164">Resilient Connections</span></span>

<span data-ttu-id="0f2f2-165">外部資源，例如 SQL 資料庫有時可能會無法使用。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="0f2f2-166">在暫時無法使用的情況下，應用程式可以使用重試邏輯，以避免引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="0f2f2-167">這項技術通常稱為*連接恢復功能*。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="0f2f2-168">您可以實作您[指數型輪詢使用自己的重試](https://docs.microsoft.com/azure/architecture/patterns/retry)技術，藉由嘗試重試以指數遞增的等候時間，直到達到重試次數上限為止。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="0f2f2-169">這項技術採用雲端資源可能間歇會無法使用短的時間，導致失敗的某些要求的事實。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="0f2f2-170">Azure SQL DB、 針對 Entity Framework Core 已經提供內部資料庫連接恢復功能和重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="0f2f2-171">但是，您必須啟用 Entity Framework 的執行策略，針對每個 DbContext 連線，如果您想要有彈性的 EF 核心連線。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="0f2f2-172">比方說，下列程式碼在 EF 核心連接層級可讓具有恢復功能的 SQL 連線的連線失敗時重試。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="0f2f2-173">執行策略和使用 BeginTransaction 和多個 DbContexts 的明確交易</span><span class="sxs-lookup"><span data-stu-id="0f2f2-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="0f2f2-174">在 EF 核心連線啟用重試時，您使用 EF 核心執行每項作業會變成可重試作業。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="0f2f2-175">每個查詢和 SaveChanges 每次呼叫將會重試做為一個單位發生暫時性失敗時。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="0f2f2-176">不過，如果您的程式碼啟動使用 BeginTransaction 的交易，您要定義您自己的作業需要被視為一個單位的群組，如果失敗，就會發生已復原在交易內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="0f2f2-177">如果您嘗試使用的 EF 執行策略 （重試原則） 時執行該交易，並在其中包含多個 DbContexts 從數個 SaveChanges，您會看到像下列的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="0f2f2-178">System.InvalidOperationException： 設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的交易。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="0f2f2-179">在做為可重試單位的交易中執行所有作業中使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="0f2f2-180">解決方法是手動叫用的委派代表的所有項目需要執行的 EF 執行策略。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="0f2f2-181">如果發生暫時性中斷，執行策略會叫用委派一次。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="0f2f2-182">下列程式碼會示範如何實作這個方法：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-182">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="0f2f2-183">First DbContext 是\_內，第二個 catalogContext 是 DbContext \_integrationEventLogService 物件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="0f2f2-184">最後，動作會認可所執行的多個 DbContexts，並使用 EF 執行策略。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="0f2f2-185">參考 – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="0f2f2-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="0f2f2-186">**EF 核心文件**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-186">**EF Core Docs**</span></span>  
> <span data-ttu-id="0f2f2-187"><https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="0f2f2-187"><https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="0f2f2-188">**EF Core： 相關的資料**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-188">**EF Core: Related Data**</span></span>  
> <span data-ttu-id="0f2f2-189"><https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="0f2f2-189"><https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="0f2f2-190">**避免在 ASPNET 應用程式中的延遲載入實體**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-190">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <span data-ttu-id="0f2f2-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="0f2f2-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="0f2f2-192">EF 核心或 MICRO-ORM 嗎？</span><span class="sxs-lookup"><span data-stu-id="0f2f2-192">EF Core or micro-ORM?</span></span>

<span data-ttu-id="0f2f2-193">在 EF 核心是絕佳的選擇，可用於管理持續性，並在大部分情況封裝資料庫的詳細資訊，從應用程式開發人員時，不是唯一的選擇。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-193">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="0f2f2-194">另一個熱門的開放原始碼的替代方式是[Dapper](https://github.com/StackExchange/Dapper)，所謂 MICRO-ORM。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-194">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="0f2f2-195">MICRO-ORM 是輕量型、 較完整的工具，將物件對應至資料結構。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-195">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="0f2f2-196">Dapper，在它的設計目標專注於效能、 而非完整封裝的基本查詢會使用以擷取和更新資料。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-196">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="0f2f2-197">因為它不會從開發人員抽象 SQL Dapper"接近金屬 」，並可讓開發人員撰寫的確切查詢他們想要使用指定的資料存取作業。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-197">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="0f2f2-198">EF 核心有兩個重要的功能，它會提供將它與 Dapper 但也新增至它的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-198">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="0f2f2-199">第一個是從 SQL 將 LINQ 運算式轉譯。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-199">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="0f2f2-200">這些翻譯會快取，但即使如此負擔中沒有執行它們第一次。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-200">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="0f2f2-201">第二個是 （以便可以產生有效的 update 陳述式），變更追蹤實體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-201">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="0f2f2-202">此行為可以關閉特定的查詢使用 AsNotTracking 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-202">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="0f2f2-203">EF 核心也會產生 SQL 查詢，通常是非常有效率，因此在任何情況下完全可接受效能的觀點而言，但如果您需要精密控制要執行精確的查詢，您可以在自訂的 SQL 中傳遞 （或執行預存程序） 使用 EF核心，太。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-203">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="0f2f2-204">Dapper 仍在此情況下，勝過 EF 核心，但只會稍微。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-204">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="0f2f2-205">在她的一些效能資料可能 2016 MSDN 文章 Julie Lerman 顯示[Dapper、 Entity Framework 和混合式應用程式](https://msdn.microsoft.com/magazine/mt703432.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-205">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="0f2f2-206">可找到各種不同的資料存取方法的其他效能基準資料[Dapper 網站](https://github.com/StackExchange/Dapper)。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-206">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="0f2f2-207">若要查看如何 Dapper 的語法變化從 EF 核心，請考慮下列兩個版本的相同方法來擷取項目清單：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-207">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="0f2f2-208">如果您需要建立與 Dapper 更複雜的物件圖形，您需要自行撰寫相關的查詢，（而不是正在將 Include 加入在 EF 核心中一樣）。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-208">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="0f2f2-209">這是透過各種不同的語法，包括名為多重對應，可讓您將個別資料列對應到多個對應物件的功能支援。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-209">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="0f2f2-210">例如，給定類型的類別張貼的內容擁有者之使用者，下列 SQL 就會傳回所有必要的資料：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-210">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="0f2f2-211">每個傳回的資料列包含使用者和 Post 資料。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-211">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="0f2f2-212">因為使用者資料應該附加至張貼資料透過其擁有者屬性，所以會使用下列函數：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-212">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="0f2f2-213">會傳回其擁有者 屬性會填入相關聯的使用者資料的文章集合的完整程式碼清單：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-213">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="0f2f2-214">因為它可以提供較少的封裝，Dapper 需要開發人員深入了解如何儲存資料，如何有效率地進行查詢，並撰寫更多的程式碼來加以擷取。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-214">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="0f2f2-215">模型的變更，而不是只建立新的移轉 （另一個 EF 核心功能），及/或更新中，建立的 DbContext 的一個位置的對應資訊會受到影響的每一個查詢都必須更新。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-215">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="0f2f2-216">這些查詢有未編譯時間保證，因此它們可能會中斷在執行階段以回應變更模型或資料庫，以更難快速偵測的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-216">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="0f2f2-217">這些權衡問題，出具 Dapper 提供極快速的效能。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-217">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="0f2f2-218">對於大部分應用程式，以及大多數的部分幾乎所有應用程式，EF 核心會提供可接受的效能。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-218">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="0f2f2-219">因此，其開發人員的生產力優勢是可能遠大於它的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-219">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="0f2f2-220">對於可以從快取獲益的查詢，實際的查詢可能只會執行很小的百分比表示的時間，使相對較小的查詢效能差異加以改善。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-220">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="0f2f2-221">SQL 或 NoSQL</span><span class="sxs-lookup"><span data-stu-id="0f2f2-221">SQL or NoSQL</span></span>

<span data-ttu-id="0f2f2-222">傳統上，例如 SQL Server 關聯式資料庫已大幅影響 marketplace 以取得永續性資料儲存，但不是唯一可用的解決方案。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-222">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="0f2f2-223">NoSQL 資料庫喜歡[MongoDB](https://www.mongodb.com/what-is-mongodb)提供了不同的方式，以儲存物件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-223">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="0f2f2-224">而不是將物件對應至資料表和資料列，另一個選項是序列化整個物件圖形中，並且將結果儲存。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-224">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="0f2f2-225">這個方法時，優點至少一開始會簡化和效能。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-225">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="0f2f2-226">當然簡單比來將物件分解成許多資料表關聯性的索引鍵使用儲存單一序列化的物件，並從資料庫擷取的更新和自上次物件可能已變更的資料列。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-226">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="0f2f2-227">同樣地，擷取和還原序列化金鑰為基礎的存放區中的單一物件通常是更為快速而且更為複雜的聯結或完整撰寫相同的物件，從關聯式資料庫所需的多個資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-227">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="0f2f2-228">缺少鎖定或交易或固定的結構描述也可讓 NoSQL 資料庫非常適合在許多機器，支援極大型資料集調整。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-228">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="0f2f2-229">相反地，NoSQL 資料庫 （通常稱為） 會有其缺點。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-229">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="0f2f2-230">關聯式資料庫使用正規化，以強制一致性並避免出現重複的資料。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-230">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="0f2f2-231">這可減少資料庫的大小總計，並可確保對共用資料的更新可立即在整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-231">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="0f2f2-232">在關聯式資料庫中，國家/地區的名稱已變更，如果位址記錄獲益更新而不需要更新本身的位址表格時，可能會參考國家 （地區） 資料表的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-232">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="0f2f2-233">不過，在 NoSQL 資料庫中，地址和其相關聯的國家/地區可能會序列化為許多預存物件的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-233">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="0f2f2-234">國家/地區名稱的更新需要更新，而不是單一資料列的所有此類物件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-234">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="0f2f2-235">關聯式資料庫也可以確保關聯式完整性，藉由強制執行規則，例如外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-235">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="0f2f2-236">NoSQL 資料庫通常不會提供其資料這類條件約束。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-236">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="0f2f2-237">其他複雜性 NoSQL 資料庫必須處理為版本設定。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-237">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="0f2f2-238">當物件的屬性變更時，它可能無法從已儲存的過去版本還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-238">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="0f2f2-239">因此，必須更新所有現有物件的物件序列化 （舊版），才能符合新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-239">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="0f2f2-240">這不是在概念上不同的關聯式資料庫，其中結構描述變更有時需要更新指令碼，或對應更新。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-240">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="0f2f2-241">不過，您必須修改的項目數通常會大於在 NoSQL 方法中，因為沒有多個出現重複的資料。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-241">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="0f2f2-242">在 NoSQL 資料庫來儲存物件的多個版本是可行的是固定的結構描述關聯式資料庫通常不支援。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-242">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="0f2f2-243">不過，在此情況下您的應用程式程式碼必須帳戶存在的先前版本的物件、 將新增額外的複雜性。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-243">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="0f2f2-244">NoSQL 資料庫通常不會強制執行[ACID](http://en.wikipedia.org/wiki/ACID)，這表示他們對關聯式資料庫的效能和延展性好處。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-244">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="0f2f2-245">它們適用於極大型資料集並不適合在正規化的資料表結構中的儲存體的物件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-245">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="0f2f2-246">沒有的理由為何單一應用程式無法利用兩者的關聯式和 NoSQL 資料庫時，使用每個最佳適合。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-246">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="0f2f2-247">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="0f2f2-247">Azure DocumentDB</span></span>

<span data-ttu-id="0f2f2-248">Azure DocumentDB 是完全受管理的 NoSQL 資料庫服務，提供以雲端為基礎的無結構描述的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-248">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="0f2f2-249">DocumentDB 是建置快速且可預測的效能、 高可用性、 彈性調整和全域發佈。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-249">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="0f2f2-250">儘管 NoSQL 資料庫，開發人員可以使用 JSON 資料的豐富且熟悉的 SQL 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-250">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="0f2f2-251">DocumentDB 中的所有資源會都儲存成 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-251">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="0f2f2-252">資源管理做為*項目*，它會包含中繼資料文件和*摘要*，而這是集合的項目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-252">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="0f2f2-253">圖 8-2 會顯示不同的 DocumentDB 資源之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-253">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![DocumentDB 的 NoSQL JSON 資料庫中的資源之間的階層式關聯性](./media/image8-2.png)

<span data-ttu-id="0f2f2-255">**圖 8-2。**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-255">**Figure 8-2.**</span></span> <span data-ttu-id="0f2f2-256">DocumentDB 資源的組織。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-256">DocumentDB resource organization.</span></span>

<span data-ttu-id="0f2f2-257">DocumentDB 查詢語言是簡單但功能強大的介面，來查詢 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-257">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="0f2f2-258">語言支援的 ANSI SQL 文法子集，並將 JavaScript 物件、 陣列、 物件建構和函式引動過程的深度整合。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-258">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="0f2f2-259">**參考 – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-259">**References – DocumentDB**</span></span>

-   <span data-ttu-id="0f2f2-260">DocumentDB Introduction\\</span><span class="sxs-lookup"><span data-stu-id="0f2f2-260">DocumentDB Introduction\\</span></span>
    <span data-ttu-id="0f2f2-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span><span class="sxs-lookup"><span data-stu-id="0f2f2-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="0f2f2-262">其他持續性選項</span><span class="sxs-lookup"><span data-stu-id="0f2f2-262">Other Persistence Options</span></span>

<span data-ttu-id="0f2f2-263">在加法關聯式和 NoSQL 存放裝置選項，ASP.NET Core 應用程式可以使用 Azure 儲存體來儲存各種不同的資料格式和檔案以雲端為基礎且可擴充的方式。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="0f2f2-264">您可以一開始儲存資料和最多儲存數百或 tb，如果您的應用程式需要的小數位數的資訊量很少，所以可大幅擴充，azure 儲存體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="0f2f2-265">Azure 儲存體支援四種資料類型：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-265">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="0f2f2-266">針對非結構化的文字或二進位存放裝置，也稱為物件儲存體的 blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="0f2f2-267">結構化資料集，可透過資料列索引鍵存取的資料表儲存體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-267">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="0f2f2-268">可靠的佇列架構傳訊佇列儲存體。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-268">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="0f2f2-269">適用於 Azure 虛擬機器與內部部署應用程式之間共用的檔案存取的檔案存放裝置。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="0f2f2-270">**參考 – Azure 儲存體**</span><span class="sxs-lookup"><span data-stu-id="0f2f2-270">**References – Azure Storage**</span></span>

-   <span data-ttu-id="0f2f2-271">Azure 儲存體 Introduction\\</span><span class="sxs-lookup"><span data-stu-id="0f2f2-271">Azure Storage Introduction\\</span></span>
    <span data-ttu-id="0f2f2-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="0f2f2-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="0f2f2-273">快取</span><span class="sxs-lookup"><span data-stu-id="0f2f2-273">Caching</span></span>

<span data-ttu-id="0f2f2-274">在 web 應用程式，每個 web 要求應該可能的最短時間內完成。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-274">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="0f2f2-275">為了達成此目的的方法之一是限制外部伺服器必須對完成要求的呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-275">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="0f2f2-276">快取牽涉到在伺服器上儲存資料的複本 （或另一個資料存放區也就是更輕鬆地查詢資料來源）。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-276">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="0f2f2-277">Web 應用程式，以及特別是非 SPA 傳統 web 應用程式，需要建立每個要求的整個使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-277">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="0f2f2-278">這通常牽涉到進行許多到下一個使用者要求中重複相同資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-278">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="0f2f2-279">在大部分情況下，此變更資料很少，因此沒有什麼道理不斷向資料庫要求。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-279">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="0f2f2-280">ASP.NET Core 支援快取回應，快取整個頁面和資料快取，可支援更細微的快取行為。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-280">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="0f2f2-281">當實作快取時，它是特別注意的重要性分離。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-281">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="0f2f2-282">避免在資料存取邏輯，或您的使用者介面中實作快取邏輯。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-282">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="0f2f2-283">相反地，封裝在其自己的類別中，快取，並使用設定管理其行為。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-283">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="0f2f2-284">這會遵循開啟/關閉和單一責任原則，並讓您更輕鬆地管理您如何使用快取應用程式中的成長。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-284">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="0f2f2-285">ASP.NET Core 回應快取</span><span class="sxs-lookup"><span data-stu-id="0f2f2-285">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="0f2f2-286">ASP.NET Core 支援快取回應的兩個層的級。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-286">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="0f2f2-287">第一個層級並不會快取伺服器上的任何項目，但會增加指示用戶端和 proxy 伺服器來快取回應的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-287">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="0f2f2-288">這被藉由將 ResponseCache 屬性加入個別的控制器或動作：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-288">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="0f2f2-289">回應快取中介軟體會自動快取根據一組條件，您可以自訂的回應。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-289">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="0f2f2-290">根據預設，透過 GET 或 HEAD 方法要求只能使用 「 200 （確定） 回應會快取。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-290">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="0f2f2-291">此外，要求必須有與快取控制項的回應： 公用標頭，而且不能包含授權或設定 Cookie 的標頭。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-291">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="0f2f2-292">請參閱[回應快取中介軟體所使用的快取條件的完整清單](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-292">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="0f2f2-293">資料快取</span><span class="sxs-lookup"><span data-stu-id="0f2f2-293">Data Caching</span></span>

<span data-ttu-id="0f2f2-294">而非 （或其他） 快取完整的 web 回應，您可以快取的個別資料查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-294">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="0f2f2-295">這麼做，您可以使用中記憶體內部快取的 web 伺服器上，或使用[分散式快取](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-295">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="0f2f2-296">本節將示範如何實作記憶體內部快取中。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-296">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="0f2f2-297">新增記憶體的支援 （或分散式） ConfigureServices 中的快取：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-297">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="0f2f2-298">請務必新增的 Microsoft.Extensions.Caching.Memory NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-298">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="0f2f2-299">加入服務之後, 您要求 IMemoryCache 透過相依性插入每當您需要存取快取。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-299">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="0f2f2-300">在此範例中，CachedCatalogService 使用 Proxy （或裝飾項目） 設計模式中，藉由提供替代的實作 ICatalogService 控制存取權 （或新增至行為） 的基礎 CatalogService 實作。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-300">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="0f2f2-301">若要設定要使用服務的快取的版本，但仍然可讓服務取得的 CatalogService 它需要其建構函式中的執行個體的應用程式，您可以加入下列 ConfigureServices 中：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-301">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="0f2f2-302">這位置，每分鐘一次，而不是在每次要求只會對擷取目錄資料的資料庫呼叫。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-302">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="0f2f2-303">根據網站的流量，這可能會影響非常重要的資料庫，以及平均頁面載入時間，首頁目前相依於此服務所公開之查詢的這三個的查詢數目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-303">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="0f2f2-304">實作快取時，就會發生一個問題就*過時的資料*– 也就是在來源但過期的版本已變更的資料會保留在快取。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-304">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="0f2f2-305">簡單的方式來減輕這個問題是使用小型的快取持續時間，因為忙碌的應用程式沒有有限的另一個好處，來擴充快取資料的長度。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-305">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="0f2f2-306">例如，考慮一個頁面，可讓單一資料庫查詢，而且會要求每秒 10 倍。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-306">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="0f2f2-307">如果此頁面會快取一分鐘，將會導致每分鐘做為 1，99.8%降低從 600 卸除的資料庫查詢的數目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-307">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="0f2f2-308">如果改為快取持續時間所做的一小時整體縮減 99.997%，而現在的可能性和潛在的存在時間的過時資料會同時大幅增加。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-308">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="0f2f2-309">另一個方法是更新本身包含的資料時，主動移除快取項目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-309">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="0f2f2-310">如果已知其索引鍵，則可以移除任何個別的項目：</span><span class="sxs-lookup"><span data-stu-id="0f2f2-310">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="0f2f2-311">如果您的應用程式公開功能的更新，它會快取項目，您可以在執行更新程式碼中移除對應的快取項目。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-311">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="0f2f2-312">有時可能會有許多不同的項目相依於特定的資料集。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-312">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="0f2f2-313">在此情況下，可用來建立快取項目，使用 CancellationChangeToken 之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-313">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="0f2f2-314">與 CancellationChangeToken，您可以終止多個快取項目一次取消語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0f2f2-314">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
<span data-ttu-id="0f2f2-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="0f2f2-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
