---
title: 使用 ASP.NET Core 應用程式中的資料
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 使用 ASP 中的資料
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 89df46c8e04e1826c84058e5d2a92d089eb96098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="2e111-103">使用 ASP.NET Core 應用程式中的資料</span><span class="sxs-lookup"><span data-stu-id="2e111-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="2e111-104">「資料是非常寶貴的資產，而且比系統本身擁有更長久的價值。」</span><span class="sxs-lookup"><span data-stu-id="2e111-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="2e111-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="2e111-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="2e111-106">總結</span><span class="sxs-lookup"><span data-stu-id="2e111-106">Summary</span></span>

<span data-ttu-id="2e111-107">對所有軟體應用程式來說，資料存取都是非常重要的一部分。</span><span class="sxs-lookup"><span data-stu-id="2e111-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="2e111-108">ASP.NET Core 支援各種不同的資料存取選項，包括 Entity Framework Core (和 Entity Framework 6)，並可使用任何 .NET 資料存取架構。</span><span class="sxs-lookup"><span data-stu-id="2e111-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="2e111-109">至於要選擇使用哪種資料存取架構，則取決於應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="2e111-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="2e111-110">您可以將這些選項從 ApplicationCore 和 UI 專案中抽離出來，並將實作詳細資料封裝到基礎結構中，以協助產生相依性低的可測試軟體。</span><span class="sxs-lookup"><span data-stu-id="2e111-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="2e111-111">Entity Framework Core (適用於關聯式資料庫)</span><span class="sxs-lookup"><span data-stu-id="2e111-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="2e111-112">如果您要撰寫的新 ASP.NET Core 應用程式需要使用關聯式資料，建議您讓應用程式使用 Entity Framework Core (EF Core) 來存取資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="2e111-113">EF Core 是一種物件關聯式對應程式 (O/RM)，可讓 .NET 開發人員保存要進出資料來源的物件。</span><span class="sxs-lookup"><span data-stu-id="2e111-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="2e111-114">它可以讓開發人員免除一般需要撰寫的大多數資料存取程式碼。</span><span class="sxs-lookup"><span data-stu-id="2e111-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="2e111-115">EF Core 和 ASP.NET Core 一樣，已經過從頭改寫以支援模組化跨平台應用程式。</span><span class="sxs-lookup"><span data-stu-id="2e111-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="2e111-116">您可以將它以 NuGet 套件形式新增至應用程式，並於 啟動時進行設定，再視需要透過相依性插入對其提出要求。</span><span class="sxs-lookup"><span data-stu-id="2e111-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="2e111-117">若要搭配使用 EF Core 與 SQL Server 資料庫，請執行下列 dotnet CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="2e111-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="2e111-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="2e111-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="2e111-119">若要新增對 InMemory 資料來源的支援以進行測試：</span><span class="sxs-lookup"><span data-stu-id="2e111-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="2e111-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="2e111-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="2e111-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="2e111-121">The DbContext</span></span>

<span data-ttu-id="2e111-122">若要使用 EF Core，您需要 DbContext 的子類別。</span><span class="sxs-lookup"><span data-stu-id="2e111-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="2e111-123">這個類別包含的屬性代表應用程式會用到的實體集合。</span><span class="sxs-lookup"><span data-stu-id="2e111-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="2e111-124">eShopOnWeb 範例包括 CatalogContext 以及項目、品牌和類型的集合：</span><span class="sxs-lookup"><span data-stu-id="2e111-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="2e111-125">您的 DbContext 必須具備可接受 DbContextOptions 的建構函式，並將此引數傳遞給基底 DbContext 建構函式。</span><span class="sxs-lookup"><span data-stu-id="2e111-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="2e111-126">請注意，如果您的應用程式中只有一個 DbContext，即可傳遞 DbContextOptions 的執行個體，但如果不只一個，您就必須使用泛型 DbContextOptions<T> 類型，並將其作為泛型參數傳遞至 DbContext 類型中。</span><span class="sxs-lookup"><span data-stu-id="2e111-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="2e111-127">設定 EF Core</span><span class="sxs-lookup"><span data-stu-id="2e111-127">Configuring EF Core</span></span>

<span data-ttu-id="2e111-128">一般來說，您需要在 ASP.NET Core 應用程式的 ConfigureServices 方法中設定 EF Core。</span><span class="sxs-lookup"><span data-stu-id="2e111-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="2e111-129">EF Core 使用的 DbContextOptionsBuilder 可支援幾項實用的擴充方法，以簡化其組態。</span><span class="sxs-lookup"><span data-stu-id="2e111-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="2e111-130">若要將 CatalogContext 設定為搭配使用 SQL Server 資料庫與 [組態] 中定義的連接字串，您可以將下列程式碼新增至 ConfigureServices：</span><span class="sxs-lookup"><span data-stu-id="2e111-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="2e111-131">若要使用記憶體內部資料庫：</span><span class="sxs-lookup"><span data-stu-id="2e111-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="2e111-132">一旦您安裝好 EF Core、建立 DbContext 子類型，並在 ConfigureServices 中進行設定，即可使用 EF Core。</span><span class="sxs-lookup"><span data-stu-id="2e111-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="2e111-133">您可以在任何需要 DbContext 類型執行個體的服務中，對其提出要求，並透過 LINQ 來使用您保存的實體，如同它們就在集合中一般。</span><span class="sxs-lookup"><span data-stu-id="2e111-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="2e111-134">EF Core 會將您的 LINQ 運算式轉譯為 SQL 查詢以儲存和擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="2e111-135">EF Core 會設定記錄器，並確保其層級至少設定為「資訊」以執行查詢，如圖 8-1 所示。</span><span class="sxs-lookup"><span data-stu-id="2e111-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="2e111-136">圖 8-1 將 EF Core 查詢記錄到主控台</span><span class="sxs-lookup"><span data-stu-id="2e111-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="2e111-137">擷取與儲存資料</span><span class="sxs-lookup"><span data-stu-id="2e111-137">Fetching and Storing Data</span></span>

<span data-ttu-id="2e111-138">若要從 EF Core 擷取資料，您可以存取適當的屬性，並使用 LINQ 篩選結果。</span><span class="sxs-lookup"><span data-stu-id="2e111-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="2e111-139">您也可以使用 LINQ 來執行投影，將某種類的結果轉換到另一種類型。</span><span class="sxs-lookup"><span data-stu-id="2e111-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="2e111-140">下列範例會擷取 CatalogBrands，並依名稱排序、依 Enabled 屬性篩選，然後投射到 SelectListItem 類型：</span><span class="sxs-lookup"><span data-stu-id="2e111-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="2e111-141">請務必在上述範例中新增 ToListAsync 呼叫，以立即執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2e111-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="2e111-142">否則，陳述式會指派 IQueryable<SelectListItem> 給 brandItem，直到系統列舉它時才執行。</span><span class="sxs-lookup"><span data-stu-id="2e111-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="2e111-143">從方法傳回 IQueryable 結果時，也有其優缺點。</span><span class="sxs-lookup"><span data-stu-id="2e111-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="2e111-144">它可讓您進一步修改 EF Core 建構的查詢，但如果您將作業新增至 EF Core 不能轉譯的查詢時，也可能會出現只在執行階段發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e111-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="2e111-145">一般來說，比較安全的做法是將任何篩選條件傳遞給執行資料存取的方法，並傳回記憶體內部的集合 (例如，List<T>) 作為結果。</span><span class="sxs-lookup"><span data-stu-id="2e111-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="2e111-146">EF Core 會追蹤其從持續性儲存區擷取的實體變更。</span><span class="sxs-lookup"><span data-stu-id="2e111-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="2e111-147">若要儲存追蹤實體的變更，您只需要在 DbContext 上呼叫 SaveChanges 方法，並確定它是用來擷取實體的相同 DbContext 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e111-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="2e111-148">您可以直接在適當的 DbSet 屬性中新增和移除實體，並再次使用 SaveChanges 呼叫，以執行資料庫命令。</span><span class="sxs-lookup"><span data-stu-id="2e111-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="2e111-149">下列範例示範如何新增、更新和移除持續性儲存區的實體。</span><span class="sxs-lookup"><span data-stu-id="2e111-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="2e111-150">EF Core 支援擷取和儲存的同步與非同步的方法。</span><span class="sxs-lookup"><span data-stu-id="2e111-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="2e111-151">若是 Web 應用程式，建議搭配使用非同步方法與非同步/等候模式，Web 伺服器執行緒才不會在等候資料存取作業完成期間受到封鎖。</span><span class="sxs-lookup"><span data-stu-id="2e111-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="2e111-152">擷取相關資料</span><span class="sxs-lookup"><span data-stu-id="2e111-152">Fetching Related Data</span></span>

<span data-ttu-id="2e111-153">當 EF Core 擷取實體時，它會填入與資料庫中的這個實體一起儲存的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="2e111-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="2e111-154">EF Core 不會填入相關實體清單這類導覽屬性，且可能會將其值設為 Null。</span><span class="sxs-lookup"><span data-stu-id="2e111-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="2e111-155">這可確保 EF Core 不會擷取超過實際所需的資料，這對 Web 應用程式來說尤其重要，因為這類應用程式必須快速處理要求，並以有效率的方式傳回回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="2e111-156">若要使用「積極式載入」來包含實體的關聯性，您可以在查詢中使用 Include 擴充方法以指定屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e111-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="2e111-157">您可以包含多個關聯性，也可以使用 ThenInclude 來包含子關聯性。</span><span class="sxs-lookup"><span data-stu-id="2e111-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="2e111-158">EF Core 會執行單一查詢來擷取產生的實體集。</span><span class="sxs-lookup"><span data-stu-id="2e111-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="2e111-159">另一個用來載入相關資料的選項是使用「明確式載入」。</span><span class="sxs-lookup"><span data-stu-id="2e111-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="2e111-160">明確式載入可讓您將其他資料載入已擷取的實體中。</span><span class="sxs-lookup"><span data-stu-id="2e111-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="2e111-161">由於這牽涉到資料庫的個別要求，因此不建議用於 Web 應用程式，而應該將每項要求的資料庫往返次數降至最低。</span><span class="sxs-lookup"><span data-stu-id="2e111-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="2e111-162">「消極式載入」功能會自動載入應用程式參考的相關資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="2e111-163">EF Core 目前不支援這項功能，但和明確式載入相同，通常建議您為 Web 應用程式停用此功能。</span><span class="sxs-lookup"><span data-stu-id="2e111-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="2e111-164">具復原功能的連線</span><span class="sxs-lookup"><span data-stu-id="2e111-164">Resilient Connections</span></span>

<span data-ttu-id="2e111-165">有時您可能會無法使用 SQL 資料庫等外部資源。</span><span class="sxs-lookup"><span data-stu-id="2e111-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="2e111-166">在暫時無法使用的情況下，應用程式可以使用重試邏輯，以避免引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e111-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="2e111-167">這項技術通常稱為「連線復原能力」。</span><span class="sxs-lookup"><span data-stu-id="2e111-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="2e111-168">您可以重試某項作業，並以指數方式增加等候時間，直到已達重試計數上限為止，藉此實作[使用指數輪詢重試](https://docs.microsoft.com/azure/architecture/patterns/retry)技術。</span><span class="sxs-lookup"><span data-stu-id="2e111-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="2e111-169">這項技術是為了因應雲端資源可能會在短時間內斷斷續續無法使用，而導致某些要求失敗的問題。</span><span class="sxs-lookup"><span data-stu-id="2e111-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="2e111-170">在 Azure SQL DB 中，Entity Framework Core 已提供內部資料庫恢復連接功能和重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="2e111-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="2e111-171">如果您想要使用具復原功能的 EF Core 連線，則必須為每個 DbContext 連線啟用 Entity Framework 執行策略。</span><span class="sxs-lookup"><span data-stu-id="2e111-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="2e111-172">例如，EF Core 連接層級的下列程式碼可在連接失敗時重試具有恢復功能的 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="2e111-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="2e111-173">使用 BeginTransaction 和多個 DbContext 的執行策略和明確異動</span><span class="sxs-lookup"><span data-stu-id="2e111-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="2e111-174">在 EF Core 連接中啟用重試時，您使用 EF Core 執行的每項作業都會變成其本身可重試的作業。</span><span class="sxs-lookup"><span data-stu-id="2e111-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="2e111-175">如果發生暫時性失敗，SaveChanges 的每個查詢和每個呼叫會當做一個單位來重試。</span><span class="sxs-lookup"><span data-stu-id="2e111-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="2e111-176">不過，如果您的程式碼使用 BeginTransaction 起始異動，您將定義需視為一個單位的專屬作業群組，如果發生失敗，必須復原異動內的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2e111-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="2e111-177">如果您在使用 EF 執行策略 (重試原則) 時嘗試執行該交易，並在交易中包含來自多個 DbContext 的數個 SaveChanges，則會看到類似如下的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e111-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="2e111-178">System.InvalidOperationException：已設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的異動。</span><span class="sxs-lookup"><span data-stu-id="2e111-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="2e111-179">使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略，將異動中的所有作業當做一個可重試的單位來執行。</span><span class="sxs-lookup"><span data-stu-id="2e111-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="2e111-180">解決方法是使用代表必須執行之所有項目的委派，來手動叫用 EF 執行策略。</span><span class="sxs-lookup"><span data-stu-id="2e111-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="2e111-181">如果發生暫時性失敗，執行策略會再叫用委派一次。</span><span class="sxs-lookup"><span data-stu-id="2e111-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="2e111-182">下列程式碼會示範如何實作這個方法：</span><span class="sxs-lookup"><span data-stu-id="2e111-182">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="2e111-183">第一個 DbContext 是 \_catalogContext，第二個 DbContext 則位於 \_integrationEventLogService 物件內。</span><span class="sxs-lookup"><span data-stu-id="2e111-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="2e111-184">最後，系統會使用 EF 執行策略執行多個 DbContext 的認可動作。</span><span class="sxs-lookup"><span data-stu-id="2e111-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="2e111-185">參考資料 – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2e111-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="2e111-186">**EF Core 文件**</span><span class="sxs-lookup"><span data-stu-id="2e111-186">**EF Core Docs**</span></span>  
> <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="2e111-187">**EF Core：相關資料**</span><span class="sxs-lookup"><span data-stu-id="2e111-187">**EF Core: Related Data**</span></span>  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="2e111-188">**避免在 ASPNET 應用程式中消極載入實體**</span><span class="sxs-lookup"><span data-stu-id="2e111-188">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="2e111-189">該使用 EF Core 或微型 ORM？</span><span class="sxs-lookup"><span data-stu-id="2e111-189">EF Core or micro-ORM?</span></span>

<span data-ttu-id="2e111-190">雖然 EF Core 是管理持續性的絕佳選擇，甚至能封裝應用程式開發人員提供的資料庫詳細資料，但它並不是唯一的選擇。</span><span class="sxs-lookup"><span data-stu-id="2e111-190">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="2e111-191">另一個熱門的開放原始碼替代方法是 [Dapper](https://github.com/StackExchange/Dapper)，也就是所謂的微型 ORM。</span><span class="sxs-lookup"><span data-stu-id="2e111-191">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="2e111-192">微型 ORM 是一種功能較簡單的輕量型工具，可將物件對應至資料結構。</span><span class="sxs-lookup"><span data-stu-id="2e111-192">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="2e111-193">舉 Dapper 為例，其設計目標著重在效能，而非完整封裝用來擷取和更新資料的基礎查詢。</span><span class="sxs-lookup"><span data-stu-id="2e111-193">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="2e111-194">因為 Dapper 不需要開發人員完全抽離 SQL，所以是比較單純的「試用版」，可讓開發人員撰寫想用於指定資料存取作業的確切查詢。</span><span class="sxs-lookup"><span data-stu-id="2e111-194">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="2e111-195">EF Core 與 Dapper 的主要差異是前者提供下列兩個重要的功能，但這也會對效能產生額外負荷。</span><span class="sxs-lookup"><span data-stu-id="2e111-195">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="2e111-196">第一個是它會將 LINQ 運算式轉譯為 SQL。</span><span class="sxs-lookup"><span data-stu-id="2e111-196">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="2e111-197">雖然系統會快取這些轉譯，第一次執行時仍會產生額外負荷。</span><span class="sxs-lookup"><span data-stu-id="2e111-197">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="2e111-198">第二個是追蹤實體的變更 (以便產生有效的 UPDATE 陳述式)。</span><span class="sxs-lookup"><span data-stu-id="2e111-198">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="2e111-199">您可以使用 AsNotTracking 延伸模組，將特定查詢的這項行為關閉。</span><span class="sxs-lookup"><span data-stu-id="2e111-199">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="2e111-200">EF Core 也會產生非常有效率的 SQL 查詢，而且在任何情況下，效能都是完全可以接受的等級；但如果您需要妥善控制要執行的精確查詢，您也可以使用 EF Core 傳入自訂的 SQL (或執行預存程序)。</span><span class="sxs-lookup"><span data-stu-id="2e111-200">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="2e111-201">在這種情況下，Dapper 就略勝於 EF Core。</span><span class="sxs-lookup"><span data-stu-id="2e111-201">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="2e111-202">Julie Lerman 在 2016 年 5 月的 [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx) (Dapper、Entity Framework 和混合式應用程式) MSDN 文章中提供了一些效能資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-202">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="2e111-203">如需各種不同資料存取方法的其他效能基準測試資料，請參閱 [Dapper 網站](https://github.com/StackExchange/Dapper)。</span><span class="sxs-lookup"><span data-stu-id="2e111-203">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="2e111-204">若要查看 Dapper 和 EF Core 的語法差異，請參考下列用來擷取項目清單之相同方法的兩個版本：</span><span class="sxs-lookup"><span data-stu-id="2e111-204">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="2e111-205">如果您需要使用 Dapper 建立更複雜的物件圖形，則必須自行撰寫相關的查詢 (反之，在 EF Core 中是要新增 Include)。</span><span class="sxs-lookup"><span data-stu-id="2e111-205">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="2e111-206">上述作業是透過各種語法來支援，包括「多重對應」這項功能，可讓您將個別資料列對應到多個對應物件。</span><span class="sxs-lookup"><span data-stu-id="2e111-206">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="2e111-207">例如，假設 Post 類別具有 User 類型的 Owner 屬性 ，下列 SQL 就會傳回所有必要的資料：</span><span class="sxs-lookup"><span data-stu-id="2e111-207">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="2e111-208">每個傳回的資料列都包含 User 和 Post 資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-208">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="2e111-209">因為 User 資料應該透過其 Owner 屬性附加至 Post 資料，所以會使用下列函式：</span><span class="sxs-lookup"><span data-stu-id="2e111-209">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="2e111-210">下列為完整的程式碼清單，其會傳回文章集合，並以相關聯的使用者資料填入 Owner 屬性：</span><span class="sxs-lookup"><span data-stu-id="2e111-210">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="2e111-211">因為 Dapper 提供較少的封裝，所以開發人員必須進一步了解如何儲存資料、如何有效率地查詢資料，並撰寫更多程式碼來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-211">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="2e111-212">當模型變更時，您不只要建立新的移轉 (另一個 EF Core 功能)，及/或逐一更新 DbContext 中每個位置的對應資訊，還要更新會受到影響的每一個查詢。</span><span class="sxs-lookup"><span data-stu-id="2e111-212">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="2e111-213">這些查詢的編譯時間無法保證，因此為了回應模型或資料庫的變更，查詢可能會在執行階段中斷，導致更難快速偵測錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e111-213">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="2e111-214">Dapper 折衷了上述情況，以提供極快速的效能。</span><span class="sxs-lookup"><span data-stu-id="2e111-214">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="2e111-215">對於大部分應用程式以及幾乎所有主要的應用程式來說，EF Core 可提供還不錯的效能。</span><span class="sxs-lookup"><span data-stu-id="2e111-215">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="2e111-216">因此，其開發人員的生產力優勢可能遠大於它的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="2e111-216">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="2e111-217">如果查詢可受益於快取，實際的查詢可能只會執行很短的時間，這時查詢效能之間的微小差異就無傷大雅了。</span><span class="sxs-lookup"><span data-stu-id="2e111-217">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="2e111-218">SQL 或 NoSQL</span><span class="sxs-lookup"><span data-stu-id="2e111-218">SQL or NoSQL</span></span>

<span data-ttu-id="2e111-219">傳統上來看，SQL Server 這類關聯式資料庫主導了永續性資料儲存的市場，但它們並不是唯一可用的解決方案。</span><span class="sxs-lookup"><span data-stu-id="2e111-219">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="2e111-220">[MongoDB](https://www.mongodb.com/what-is-mongodb) 這類 NoSQL 資料庫提供儲存物件的不同方式。</span><span class="sxs-lookup"><span data-stu-id="2e111-220">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="2e111-221">這個選項不會將物件對應至資料表和資料列，而是序列化整個物件圖形，並且將結果儲存。</span><span class="sxs-lookup"><span data-stu-id="2e111-221">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="2e111-222">初步來講，這個方法的優點是簡潔和效能。</span><span class="sxs-lookup"><span data-stu-id="2e111-222">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="2e111-223">比起將物件分解成許多關聯性資料表，並更新自上次從資料庫擷取物件之後可能已變更的資料列，使用索引鍵儲存單一序列化的物件，當然更加簡單。</span><span class="sxs-lookup"><span data-stu-id="2e111-223">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="2e111-224">同樣地，相較於從關聯式資料庫完整撰寫相同物件所需的複雜聯結或多個資料庫查詢，從以索引鍵為基礎的存放區中擷取和還原序列化單一物件通常更為快速、簡單。</span><span class="sxs-lookup"><span data-stu-id="2e111-224">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="2e111-225">NoSQL 資料庫不具鎖定、異動或固定結構描述的特質，也非常適合跨多部機器調整規模，同時支援大型資料集。</span><span class="sxs-lookup"><span data-stu-id="2e111-225">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="2e111-226">另一方面來看，NoSQL 資料庫 (如字面通稱) 也有其缺點。</span><span class="sxs-lookup"><span data-stu-id="2e111-226">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="2e111-227">關聯式資料庫使用正規化功能，強制執行一致性並避免出現重複的資料。</span><span class="sxs-lookup"><span data-stu-id="2e111-227">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="2e111-228">這可減少資料庫的大小總計，並確保對共用資料所做的更新可在整個資料庫中立即生效。</span><span class="sxs-lookup"><span data-stu-id="2e111-228">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="2e111-229">在關聯式資料庫中，假設「地址」資料表參考了「國家/地區」資料表中的識別碼，如果國家/地區的名稱已變更，地址記錄就會隨之更新，您不需要另行更新地址記錄。</span><span class="sxs-lookup"><span data-stu-id="2e111-229">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="2e111-230">不過，在 NoSQL 資料庫中，「地址」和其相關聯的「國家/地區」可能會序列化為許多預存物件的一部分。</span><span class="sxs-lookup"><span data-stu-id="2e111-230">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="2e111-231">更新國家/地區名稱時，也必須更新所有相關物件，而不是單一資料列。</span><span class="sxs-lookup"><span data-stu-id="2e111-231">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="2e111-232">關聯式資料庫也可以強制執行規則 (例如外部索引鍵)，以確保關聯的完整性。</span><span class="sxs-lookup"><span data-stu-id="2e111-232">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="2e111-233">NoSQL 資料庫通常不會對其資料提供這類條件約束。</span><span class="sxs-lookup"><span data-stu-id="2e111-233">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="2e111-234">NoSQL 資料庫還有一個必須處理的複雜問題是版本設定。</span><span class="sxs-lookup"><span data-stu-id="2e111-234">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="2e111-235">當物件的屬性變更時，您可能無法從過去已儲存的版本將它還原序列化。</span><span class="sxs-lookup"><span data-stu-id="2e111-235">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="2e111-236">因此，所有含序列化版本 (舊版) 物件的現有物件，都必須更新以符合新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2e111-236">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="2e111-237">而在關聯式資料庫中，當結構描述變更時，有時需要更新指令碼或對應更新，因此兩者已不只是概念上的差異。</span><span class="sxs-lookup"><span data-stu-id="2e111-237">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="2e111-238">不過，使用 NoSQL 方法時，您必須修改的項目數通常非常多，因為重複的資料比較多。</span><span class="sxs-lookup"><span data-stu-id="2e111-238">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="2e111-239">您可以在 NoSQL 資料庫中儲存物件的多個版本，而固定結構描述的關聯式資料庫通常不支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="2e111-239">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="2e111-240">不過，在這種情況下，應用程式的程式碼必須找出存在的舊版本物件，這增加了其額外的複雜性。</span><span class="sxs-lookup"><span data-stu-id="2e111-240">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="2e111-241">NoSQL 資料庫通常不會強制執行 [ACID](https://en.wikipedia.org/wiki/ACID)，因此在效能和延展性方面比關聯式資料庫更有優勢。</span><span class="sxs-lookup"><span data-stu-id="2e111-241">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="2e111-242">因此針對不適用於正規化資料表結構儲存區的極大型資料集以及物件，就非常適合使用這種資料庫。</span><span class="sxs-lookup"><span data-stu-id="2e111-242">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="2e111-243">單一應用程式也可以同時利用關聯式和 NoSQL 資料庫，只要依據最適合的情況來選擇即可。</span><span class="sxs-lookup"><span data-stu-id="2e111-243">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="2e111-244">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="2e111-244">Azure DocumentDB</span></span>

<span data-ttu-id="2e111-245">Azure DocumentDB 是全受控的 NoSQL 資料庫服務，可提供以雲端為基礎的無結構描述資料儲存區。</span><span class="sxs-lookup"><span data-stu-id="2e111-245">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="2e111-246">DocumentDB 是專為滿足快速及可預測的效能、高可用性、彈性調整和全域發佈需求所建置。</span><span class="sxs-lookup"><span data-stu-id="2e111-246">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="2e111-247">即使在 NoSQL 資料庫中，開發人員仍可以對 JSON 資料使用豐富且熟悉的 SQL 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="2e111-247">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="2e111-248">DocumentDB 中的所有資源都會儲存為 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="2e111-248">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="2e111-249">系統會以「項目」形式來管理資源；也就是說，資源是包含中繼資料和「摘要」的文件，也是項目的集合。</span><span class="sxs-lookup"><span data-stu-id="2e111-249">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="2e111-250">圖 8-2 顯示不同 DocumentDB 資源之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="2e111-250">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![DocumentDB (其為 NoSQL JSON 資料庫) 資源之間的階層式關聯性](./media/image8-2.png)

<span data-ttu-id="2e111-252">**圖 8-2**：</span><span class="sxs-lookup"><span data-stu-id="2e111-252">**Figure 8-2.**</span></span> <span data-ttu-id="2e111-253">DocumentDB 資源的組織。</span><span class="sxs-lookup"><span data-stu-id="2e111-253">DocumentDB resource organization.</span></span>

<span data-ttu-id="2e111-254">DocumentDB 查詢語言是一種簡單但功能強大的介面，適用於查詢 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="2e111-254">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="2e111-255">該語言支援 ANSI SQL 文法子集，並深度整合 JavaScript 物件、陣列、物件建構和函式引動過程。</span><span class="sxs-lookup"><span data-stu-id="2e111-255">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="2e111-256">**參考資料 – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="2e111-256">**References – DocumentDB**</span></span>

-   <span data-ttu-id="2e111-257">DocumentDB 簡介</span><span class="sxs-lookup"><span data-stu-id="2e111-257">DocumentDB Introduction\\</span></span>
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="2e111-258">其他持續性儲存區選項</span><span class="sxs-lookup"><span data-stu-id="2e111-258">Other Persistence Options</span></span>

<span data-ttu-id="2e111-259">除了關聯式和 NoSQL 儲存區選項，ASP.NET Core 應用程式也可以使用 Azure 儲存體，透過以雲端為基礎且可擴充的方式，來儲存各種不同的資料格式和檔案。</span><span class="sxs-lookup"><span data-stu-id="2e111-259">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="2e111-260">Azure 儲存體可大幅進行調整，因此您可以一開始先儲存少量資料，之後再視應用程式的需要，擴充儲存至數百 GB 或 TB。</span><span class="sxs-lookup"><span data-stu-id="2e111-260">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="2e111-261">Azure 儲存體支援下列四種資料類型：</span><span class="sxs-lookup"><span data-stu-id="2e111-261">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="2e111-262">Blob 儲存體，也稱為物件儲存體，適用於非結構化的文字或二進位儲存。</span><span class="sxs-lookup"><span data-stu-id="2e111-262">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="2e111-263">資料表儲存體，可透過資料列索引鍵存取，適用於結構化資料集。</span><span class="sxs-lookup"><span data-stu-id="2e111-263">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="2e111-264">佇列儲存體，適合用來進行以佇列為主的通訊。</span><span class="sxs-lookup"><span data-stu-id="2e111-264">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="2e111-265">檔案儲存體，適合用來存取 Azure 虛擬機器和內部部署應用程式之間的共用檔案。</span><span class="sxs-lookup"><span data-stu-id="2e111-265">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="2e111-266">**參考資料 – Azure 儲存體**</span><span class="sxs-lookup"><span data-stu-id="2e111-266">**References – Azure Storage**</span></span>

-   <span data-ttu-id="2e111-267">Azure 儲存體簡介</span><span class="sxs-lookup"><span data-stu-id="2e111-267">Azure Storage Introduction\\</span></span>
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="2e111-268">快取</span><span class="sxs-lookup"><span data-stu-id="2e111-268">Caching</span></span>

<span data-ttu-id="2e111-269">在 Web 應用程式中，每個 Web 要求都應盡量在最短時間內完成。</span><span class="sxs-lookup"><span data-stu-id="2e111-269">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="2e111-270">為了達成上述目的，其中一個方法是限制伺服器為完成要求必須發出的外部呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="2e111-270">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="2e111-271">快取功能會將資料的複本儲存到伺服器 (或比資料來源更容易查詢的其他資料存放區)。</span><span class="sxs-lookup"><span data-stu-id="2e111-271">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="2e111-272">Web 應用程式 (特別是非 SPA 的傳統 Web 應用程式) 必須使用每個要求來建置完整的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="2e111-272">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="2e111-273">若要這麼做，通常要從某個使用者要求到下一個使用者要求不斷重複進行許多相同的資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="2e111-273">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="2e111-274">在大部分情況下，這些資料很少變更，因此實在沒有必要不斷向資料庫提出要求。</span><span class="sxs-lookup"><span data-stu-id="2e111-274">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="2e111-275">ASP.NET Core 支援可快取整個頁面的回應快取，以及可支援更細微快取行為的資料快取。</span><span class="sxs-lookup"><span data-stu-id="2e111-275">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="2e111-276">當實作快取時，應特別注意關注點分離原則。</span><span class="sxs-lookup"><span data-stu-id="2e111-276">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="2e111-277">避免在資料存取邏輯或使用者介面中，實作快取邏輯。</span><span class="sxs-lookup"><span data-stu-id="2e111-277">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="2e111-278">相反地，請將快取封裝在其自身的類別中，並使用組態來管理它的行為。</span><span class="sxs-lookup"><span data-stu-id="2e111-278">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="2e111-279">這會遵循開啟/關閉準則 (Open/Closed Principle) 和單一責任準則 (Single Responsibility Principle)，並可讓您更輕鬆管理應用程式增長時的快取使用方式。</span><span class="sxs-lookup"><span data-stu-id="2e111-279">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="2e111-280">ASP.NET Core 回應快取</span><span class="sxs-lookup"><span data-stu-id="2e111-280">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="2e111-281">ASP.NET Core 支援兩個層級的快取回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-281">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="2e111-282">第一個層級不會快取伺服器上的任何項目，但會新增 HTTP 標頭以指示用戶端和 Proxy 伺服器來快取回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-282">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="2e111-283">上述作業的實作方式為將 ResponseCache 屬性新增至個別的控制器或動作：</span><span class="sxs-lookup"><span data-stu-id="2e111-283">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

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

<span data-ttu-id="2e111-284">回應快取中介軟體會根據一組可自訂的條件來自動快取回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-284">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="2e111-285">根據預設，只會快取透過 GET 或 HEAD 方法要求的 200 (沒問題) 回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-285">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="2e111-286">此外，要求的回應必須具備 Cache-Control: public 標頭，而且不能包含 Authorization 或 Set-Cookie 的標頭。</span><span class="sxs-lookup"><span data-stu-id="2e111-286">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="2e111-287">請參閱[回應快取中介軟體所使用的快取條件完整清單](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)。</span><span class="sxs-lookup"><span data-stu-id="2e111-287">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="2e111-288">資料快取</span><span class="sxs-lookup"><span data-stu-id="2e111-288">Data Caching</span></span>

<span data-ttu-id="2e111-289">您可以只快取個別的資料查詢結果，或同時快取完整的 Web 回應。</span><span class="sxs-lookup"><span data-stu-id="2e111-289">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="2e111-290">若要這麼做，您可以在 Web 伺服器上使用記憶體內部快取，或使用[分散式快取](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)。</span><span class="sxs-lookup"><span data-stu-id="2e111-290">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="2e111-291">本節將示範如何實作記憶體內部快取。</span><span class="sxs-lookup"><span data-stu-id="2e111-291">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="2e111-292">在 ConfigureServices 中，新增對記憶體 (或分散式) 快取的支援：</span><span class="sxs-lookup"><span data-stu-id="2e111-292">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="2e111-293">請務必一併新增 Microsoft.Extensions.Caching.Memory NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2e111-293">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="2e111-294">新增服務之後，每當您需要存取快取時，即可透過相依性插入要求 IMemoryCache。</span><span class="sxs-lookup"><span data-stu-id="2e111-294">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="2e111-295">在此範例中，CachedCatalogService 會提供 ICatalogService 的替代實作來使用 Proxy (或裝飾項目) 設計模式，以控制基礎 CatalogService 實作的存取權 (或新增行為至基礎 CatalogService 實作)。</span><span class="sxs-lookup"><span data-stu-id="2e111-295">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="2e111-296">若要將應用程式設定為使用服務的快取版本，但仍然允許服務取得其建構函式中所需的 CatalogService 執行個體，您可以在 ConfigureServices 中新增下列項目：</span><span class="sxs-lookup"><span data-stu-id="2e111-296">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="2e111-297">完成上述作業時，系統只會每分鐘呼叫一次資料庫以擷取目錄資料，而不會在每次要求時都呼叫。</span><span class="sxs-lookup"><span data-stu-id="2e111-297">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="2e111-298">根據網站的流量而定，這可能會大幅影響資料庫的查詢數目以及首頁 (目前相依於此服務所公開的所有三個查詢) 的平均頁面載入時間。</span><span class="sxs-lookup"><span data-stu-id="2e111-298">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="2e111-299">實作快取時會引發「過時資料」的問題 – 亦即，來源的資料已變更，但快取中仍保留過期的版本。</span><span class="sxs-lookup"><span data-stu-id="2e111-299">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="2e111-300">若要緩和這個問題，一個簡單的方式是將快取持續時間縮短，因為對忙碌的應用程式來說，延長快取資料的時間長度意義不大。</span><span class="sxs-lookup"><span data-stu-id="2e111-300">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="2e111-301">例如，假設某個頁面會進行單一資料庫查詢，且每秒要求 10 次。</span><span class="sxs-lookup"><span data-stu-id="2e111-301">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="2e111-302">如果將這個頁面快取一分鐘，則資料庫每分鐘查詢的數目可從 600 降到 1，減少了 99.8%。</span><span class="sxs-lookup"><span data-stu-id="2e111-302">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="2e111-303">如果快取持續時間設為一小時，整體可以減少 99.997%；不過，這樣一來，過時資料的可能性和存在時間都會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="2e111-303">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="2e111-304">另一個方法是當快取項目包含的資料有所更新時，就主動移除快取項目。</span><span class="sxs-lookup"><span data-stu-id="2e111-304">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="2e111-305">只要知道索引鍵，就可以移除任何個別的項目：</span><span class="sxs-lookup"><span data-stu-id="2e111-305">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="2e111-306">如果應用程式會公開功能以更新它的快取項目，您可以在執行更新的程式碼中移除對應的快取項目。</span><span class="sxs-lookup"><span data-stu-id="2e111-306">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="2e111-307">有時候，可能會有許多不同的項目相依於特定的資料集。</span><span class="sxs-lookup"><span data-stu-id="2e111-307">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="2e111-308">在此情況下，您可以使用 CancellationChangeToken 來建立快取項目之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="2e111-308">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="2e111-309">使用 CancellationChangeToken 時，您只要取消權杖即可一次讓多個快取項目到期。</span><span class="sxs-lookup"><span data-stu-id="2e111-309">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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
<span data-ttu-id="2e111-310">[上一頁] (develop-asp-net-core-mvc-apps.md) [上一頁] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="2e111-310">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
