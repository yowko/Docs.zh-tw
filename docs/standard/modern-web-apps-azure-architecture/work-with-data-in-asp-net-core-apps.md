---
title: "使用 ASP.NET Core 應用程式中的資料"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |使用 asp 中的資料"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: bcb8f7bbfa83db9c86cd1278a89750b9f02061d9
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a>在 ASP.NET Core 應用程式中使用資料

> 「 資料是非常寶貴的功能和將持續時間超過本身的系統。 」

Tim Berners-lee

## <a name="summary"></a>總結

資料存取是幾乎任何的軟體應用程式中很重要的一部分。 ASP.NET Core 支援各種不同的資料存取選項，包括 Entity Framework Core （和 Entity Framework 6），而且可以使用任何.NET 資料存取架構。 其中的資料存取架構使用的選擇取決於應用程式的需求。 抽象化 ApplicationCore 和 UI 專案，這些選項和封裝的基礎結構的實作詳細資料有助於產生鬆散偶合、 可測試的軟體。

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core （適用於關聯式資料庫）

如果您要撰寫新的 ASP.NET Core 應用程式需要處理關聯式資料，Entity Framework Core （EF 核心） 是您的應用程式存取其資料的建議的方式。 EF 核心是物件關聯式對應工具 (O/RM)，可讓.NET 開發人員，以保存資料來源的物件。 它不必將大部分的開發通常需要撰寫資料存取程式碼。 ASP.NET Core 像已經改寫 EF 核心模組支援跨平台應用程式的基礎。 您將它加入至您的應用程式以 NuGet 套件、 將它設定在啟動時，和要求透過相依性插入，每當您需要它。

若要使用 SQL Server 資料庫的 EF 核心，執行下列 dotnet CLI 命令：

dotnet 新增封裝 Microsoft.EntityFrameworkCore.SqlServer

若要新增為 InMemory 資料來源，進行測試的支援：

dotnet 新增封裝 Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>DbContext

若要使用 EF 核心，您需要 DbContext 子的類別。 這個類別包含代表您的應用程式將會使用實體集合的屬性。 EShopOnWeb 範例包括 CatalogContext 與項目、 品牌、 和類型的集合：

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

您 DbContext 必須有接受 DbContextOptions 建構函式，並將此引數傳遞給基底的 DbContext 建構函式。 請注意，如果應用程式中有一個 DbContext，您可以傳遞 DbContextOptions，執行個體，但如果您有多個您必須使用泛型 DbContextOptions<T> DbContext 類型做為泛型參數中傳遞的類型。

### <a name="configuring-ef-core"></a>設定 EF 核心

在您的 ASP.NET Core 應用程式，您通常需要設定 EF 核心 ConfigureServices 方法中。 EF 核心使用 DbContextOptionsBuilder，可支援幾個很有幫助的擴充方法，以簡化其組態。 若要設定 CatalogContext 組態中定義的連接字串中使用 SQL Server 資料庫，您可以加入下列程式碼以 ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

若要使用的記憶體中資料庫：

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

一旦您安裝 EF 核心，建立 DbContext 子型別，並設定 ConfigureServices 中，您已準備好使用 EF 核心。 您可以要求您在需要它，任何服務中的 DbContext 類型的執行個體，並開始使用您保存使用 LINQ，如同它們是直接在集合中的實體。 EF 核心運作的程式來儲存和擷取資料的 SQL 查詢的 LINQ 運算式轉譯。

您可以看到 EF 核心藉由設定記錄器和確保至少其層級設定為執行的查詢資訊，如圖 8-1 所示。

![](./media/image8-1.png)

圖 8-1 到主控台的記錄 EF 核心查詢

### <a name="fetching-and-storing-data"></a>正在擷取及儲存資料

若要從 EF 核心擷取資料，您可以存取適當的屬性，並使用 LINQ 篩選結果。 您也可以使用 LINQ 來執行投影，轉換到另一種類型的結果。 下列範例會擷取 CatalogBrands，依名稱排序，它們已啟用的屬性，以進行篩選和投射到 SelectListItem 類型：

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

請務必在上述範例中新增至 ToListAsync 呼叫，以立即執行查詢。 否則，陳述式將會指派 IQueryable<SelectListItem>至 brandItems，這不會執行直到經過列舉。 有優缺點，若要從方法傳回 IQueryable 結果。 它可讓的查詢 EF 核心會建構來進一步修改，但是如果，也可以只在執行階段，就會發生的錯誤導致作業會加入至 EF 核心不能轉譯的查詢。 將任何篩選至執行資料存取，方法通常比較安全，並傳回回記憶體中集合 (例如，列出<T>) 做為結果。

EF 核心提取從持續性的實體上追蹤變更。 若要儲存變更追蹤的實體，您只需要呼叫 SaveChanges 方法 DbContext，並確定它是用來擷取實體的相同 DbContext 執行個體上。 加入和移除項目是直接在適當的 DbSet 屬性中使用 SaveChanges 呼叫，以執行資料庫命令，然後再次上。 下列範例示範如何加入、 更新和移除從持續性的實體。

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

EF 核心支援同步和非同步方法，擷取和儲存。 在 web 應用程式，則建議使用非同步/等候模式，與非同步方法，使 web 伺服器執行緒不會封鎖在等候資料存取作業完成時。

### <a name="fetching-related-data"></a>擷取相關的資料

當 EF 核心擷取實體時，它會填入所有直接與該實體資料庫中儲存的內容。 未填入導覽屬性，例如相關實體的清單，且可能有其值設定為 null。 這可確保 EF 核心未擷取超過所需的資料所在的 web 應用程式，它們必須快速處理要求並傳回回應，以有效率的方式特別重要。 若要包含與實體使用的關聯性*積極式載入*，您指定在查詢中，使用包含擴充方法的屬性所示：

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

您可以包含多個關聯性，而且您也可以包含子關聯性使用 ThenInclude。 EF 核心會執行單一查詢來擷取結果集的實體。

用於載入相關的資料的另一個選項是使用*明確載入*。 明確式載入可讓您將額外的資料載入已擷取的實體。 由於這牽涉到資料庫的個別要求，不建議的 web 應用程式應該減少資料庫的每個要求所做的往返。

*消極式載入*是會自動載入相關的資料，因為它參考應用程式的功能。 EF 核心目前不支援，但做為具有明確載入它通常必須停用 web 應用程式。

### <a name="resilient-connections"></a>具有恢復功能的連線

外部資源，例如 SQL 資料庫有時可能會無法使用。 在暫時無法使用的情況下，應用程式可以使用重試邏輯，以避免引發例外狀況。 這項技術通常稱為*連接恢復功能*。 您可以實作您[指數型輪詢使用自己的重試](https://docs.microsoft.com/azure/architecture/patterns/retry)技術，藉由嘗試重試以指數遞增的等候時間，直到達到重試次數上限為止。 這項技術採用雲端資源可能間歇會無法使用短的時間，導致失敗的某些要求的事實。

Azure SQL DB、 針對 Entity Framework Core 已經提供內部資料庫連接恢復功能和重試邏輯。 但是，您必須啟用 Entity Framework 的執行策略，針對每個 DbContext 連線，如果您想要有彈性的 EF 核心連線。

比方說，下列程式碼在 EF 核心連接層級可讓具有恢復功能的 SQL 連線的連線失敗時重試。

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>執行策略和使用 BeginTransaction 和多個 DbContexts 的明確交易 
  
  在 EF 核心連線啟用重試時，您使用 EF 核心執行每項作業會變成可重試作業。 每個查詢和 SaveChanges 每次呼叫將會重試做為一個單位發生暫時性失敗時。
  
  不過，如果您的程式碼啟動使用 BeginTransaction 的交易，您要定義您自己的作業需要被視為一個單位的群組，如果失敗，就會發生已復原在交易內的所有項目。 如果您嘗試使用的 EF 執行策略 （重試原則） 時執行該交易，並在其中包含多個 DbContexts 從數個 SaveChanges，您會看到像下列的例外狀況。

System.InvalidOperationException： 設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的交易。 在做為可重試單位的交易中執行所有作業中使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略。

解決方法是手動叫用的委派代表的所有項目需要執行的 EF 執行策略。 如果發生暫時性中斷，執行策略會叫用委派一次。 下列程式碼會示範如何實作這個方法：

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

First DbContext 是\_內，第二個 catalogContext 是 DbContext \_integrationEventLogService 物件。 最後，動作會認可所執行的多個 DbContexts，並使用 EF 執行策略。

> ### <a name="references--entity-framework-core"></a>參考 – Entity Framework Core
> - **EF 核心文件**  
> <https://docs.microsoft.com/ef/>
> - **EF Core： 相關的資料**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **避免在 ASPNET 應用程式中的延遲載入實體**  
> <http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF 核心或 MICRO-ORM 嗎？

在 EF 核心是絕佳的選擇，可用於管理持續性，並在大部分情況封裝資料庫的詳細資訊，從應用程式開發人員時，不是唯一的選擇。 另一個熱門的開放原始碼的替代方式是[Dapper](https://github.com/StackExchange/Dapper)，所謂 MICRO-ORM。 MICRO-ORM 是輕量型、 較完整的工具，將物件對應至資料結構。 Dapper，在它的設計目標專注於效能、 而非完整封裝的基本查詢會使用以擷取和更新資料。 因為它不會從開發人員抽象 SQL Dapper"接近金屬 」，並可讓開發人員撰寫的確切查詢他們想要使用指定的資料存取作業。

EF 核心有兩個重要的功能，它會提供將它與 Dapper 但也新增至它的效能負擔。 第一個是從 SQL 將 LINQ 運算式轉譯。 這些翻譯會快取，但即使如此負擔中沒有執行它們第一次。 第二個是 （以便可以產生有效的 update 陳述式），變更追蹤實體。 此行為可以關閉特定的查詢使用 AsNotTracking 延伸模組。 EF 核心也會產生 SQL 查詢，通常是非常有效率，因此在任何情況下完全可接受效能的觀點而言，但如果您需要精密控制要執行精確的查詢，您可以在自訂的 SQL 中傳遞 （或執行預存程序） 使用 EF核心，太。 Dapper 仍在此情況下，勝過 EF 核心，但只會稍微。 在她的一些效能資料可能 2016 MSDN 文章 Julie Lerman 顯示[Dapper、 Entity Framework 和混合式應用程式](https://msdn.microsoft.com/magazine/mt703432.aspx)。 可找到各種不同的資料存取方法的其他效能基準資料[Dapper 網站](https://github.com/StackExchange/Dapper)。

若要查看如何 Dapper 的語法變化從 EF 核心，請考慮下列兩個版本的相同方法來擷取項目清單：

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

如果您需要建立與 Dapper 更複雜的物件圖形，您需要自行撰寫相關的查詢，（而不是正在將 Include 加入在 EF 核心中一樣）。 這是透過各種不同的語法，包括名為多重對應，可讓您將個別資料列對應到多個對應物件的功能支援。 例如，給定類型的類別張貼的內容擁有者之使用者，下列 SQL 就會傳回所有必要的資料：

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

每個傳回的資料列包含使用者和 Post 資料。 因為使用者資料應該附加至張貼資料透過其擁有者屬性，所以會使用下列函數：

```csharp
(post, user) => { post.Owner = user; return post; }
```

會傳回其擁有者 屬性會填入相關聯的使用者資料的文章集合的完整程式碼清單：

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

因為它可以提供較少的封裝，Dapper 需要開發人員深入了解如何儲存資料，如何有效率地進行查詢，並撰寫更多的程式碼來加以擷取。 模型的變更，而不是只建立新的移轉 （另一個 EF 核心功能），及/或更新中，建立的 DbContext 的一個位置的對應資訊會受到影響的每一個查詢都必須更新。 這些查詢有未編譯時間保證，因此它們可能會中斷在執行階段以回應變更模型或資料庫，以更難快速偵測的錯誤。 這些權衡問題，出具 Dapper 提供極快速的效能。

對於大部分應用程式，以及大多數的部分幾乎所有應用程式，EF 核心會提供可接受的效能。 因此，其開發人員的生產力優勢是可能遠大於它的效能負擔。 對於可以從快取獲益的查詢，實際的查詢可能只會執行很小的百分比表示的時間，使相對較小的查詢效能差異加以改善。

## <a name="sql-or-nosql"></a>SQL 或 NoSQL

傳統上，例如 SQL Server 關聯式資料庫已大幅影響 marketplace 以取得永續性資料儲存，但不是唯一可用的解決方案。 NoSQL 資料庫喜歡[MongoDB](https://www.mongodb.com/what-is-mongodb)提供了不同的方式，以儲存物件。 而不是將物件對應至資料表和資料列，另一個選項是序列化整個物件圖形中，並且將結果儲存。 這個方法時，優點至少一開始會簡化和效能。 當然簡單比來將物件分解成許多資料表關聯性的索引鍵使用儲存單一序列化的物件，並從資料庫擷取的更新和自上次物件可能已變更的資料列。 同樣地，擷取和還原序列化金鑰為基礎的存放區中的單一物件通常是更為快速而且更為複雜的聯結或完整撰寫相同的物件，從關聯式資料庫所需的多個資料庫查詢。 缺少鎖定或交易或固定的結構描述也可讓 NoSQL 資料庫非常適合在許多機器，支援極大型資料集調整。

相反地，NoSQL 資料庫 （通常稱為） 會有其缺點。 關聯式資料庫使用正規化，以強制一致性並避免出現重複的資料。 這可減少資料庫的大小總計，並可確保對共用資料的更新可立即在整個資料庫。 在關聯式資料庫中，國家/地區的名稱已變更，如果位址記錄獲益更新而不需要更新本身的位址表格時，可能會參考國家 （地區） 資料表的識別碼。 不過，在 NoSQL 資料庫中，地址和其相關聯的國家/地區可能會序列化為許多預存物件的一部分。 國家/地區名稱的更新需要更新，而不是單一資料列的所有此類物件。 關聯式資料庫也可以確保關聯式完整性，藉由強制執行規則，例如外部索引鍵。 NoSQL 資料庫通常不會提供其資料這類條件約束。

其他複雜性 NoSQL 資料庫必須處理為版本設定。 當物件的屬性變更時，它可能無法從已儲存的過去版本還原序列化。 因此，必須更新所有現有物件的物件序列化 （舊版），才能符合新的結構描述。 這不是在概念上不同的關聯式資料庫，其中結構描述變更有時需要更新指令碼，或對應更新。 不過，您必須修改的項目數通常會大於在 NoSQL 方法中，因為沒有多個出現重複的資料。

在 NoSQL 資料庫來儲存物件的多個版本是可行的是固定的結構描述關聯式資料庫通常不支援。 不過，在此情況下您的應用程式程式碼必須帳戶存在的先前版本的物件、 將新增額外的複雜性。

NoSQL 資料庫通常不會強制執行[ACID](http://en.wikipedia.org/wiki/ACID)，這表示他們對關聯式資料庫的效能和延展性好處。 它們適用於極大型資料集並不適合在正規化的資料表結構中的儲存體的物件。 沒有的理由為何單一應用程式無法利用兩者的關聯式和 NoSQL 資料庫時，使用每個最佳適合。

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB 是完全受管理的 NoSQL 資料庫服務，提供以雲端為基礎的無結構描述的資料存放區。 DocumentDB 是建置快速且可預測的效能、 高可用性、 彈性調整和全域發佈。 儘管 NoSQL 資料庫，開發人員可以使用 JSON 資料的豐富且熟悉的 SQL 查詢功能。 DocumentDB 中的所有資源會都儲存成 JSON 文件。 資源管理做為*項目*，它會包含中繼資料文件和*摘要*，而這是集合的項目。 圖 8-2 會顯示不同的 DocumentDB 資源之間的關聯性。


![DocumentDB 的 NoSQL JSON 資料庫中的資源之間的階層式關聯性](./media/image8-2.png)

**圖 8-2。** DocumentDB 資源的組織。

DocumentDB 查詢語言是簡單但功能強大的介面，來查詢 JSON 文件。 語言支援的 ANSI SQL 文法子集，並將 JavaScript 物件、 陣列、 物件建構和函式引動過程的深度整合。

**參考 – DocumentDB**

-   DocumentDB Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>其他持續性選項

在加法關聯式和 NoSQL 存放裝置選項，ASP.NET Core 應用程式可以使用 Azure 儲存體來儲存各種不同的資料格式和檔案以雲端為基礎且可擴充的方式。 您可以一開始儲存資料和最多儲存數百或 tb，如果您的應用程式需要的小數位數的資訊量很少，所以可大幅擴充，azure 儲存體。 Azure 儲存體支援四種資料類型：

-   針對非結構化的文字或二進位存放裝置，也稱為物件儲存體的 blob 儲存體。

-   結構化資料集，可透過資料列索引鍵存取的資料表儲存體。

-   可靠的佇列架構傳訊佇列儲存體。

-   適用於 Azure 虛擬機器與內部部署應用程式之間共用的檔案存取的檔案存放裝置。

**參考 – Azure 儲存體**

-   Azure 儲存體 Introduction\
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>快取

在 web 應用程式，每個 web 要求應該可能的最短時間內完成。 為了達成此目的的方法之一是限制外部伺服器必須對完成要求的呼叫數目。 快取牽涉到在伺服器上儲存資料的複本 （或另一個資料存放區也就是更輕鬆地查詢資料來源）。 Web 應用程式，以及特別是非 SPA 傳統 web 應用程式，需要建立每個要求的整個使用者介面。 這通常牽涉到進行許多到下一個使用者要求中重複相同資料庫查詢。 在大部分情況下，此變更資料很少，因此沒有什麼道理不斷向資料庫要求。 ASP.NET Core 支援快取回應，快取整個頁面和資料快取，可支援更細微的快取行為。

當實作快取時，它是特別注意的重要性分離。 避免在資料存取邏輯，或您的使用者介面中實作快取邏輯。 相反地，封裝在其自己的類別中，快取，並使用設定管理其行為。 這會遵循開啟/關閉和單一責任原則，並讓您更輕鬆地管理您如何使用快取應用程式中的成長。

### <a name="aspnet-core-response-caching"></a>ASP.NET Core 回應快取

ASP.NET Core 支援快取回應的兩個層的級。 第一個層級並不會快取伺服器上的任何項目，但會增加指示用戶端和 proxy 伺服器來快取回應的 HTTP 標頭。 這被藉由將 ResponseCache 屬性加入個別的控制器或動作：

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

回應快取中介軟體會自動快取根據一組條件，您可以自訂的回應。 根據預設，透過 GET 或 HEAD 方法要求只能使用 「 200 （確定） 回應會快取。 此外，要求必須有與快取控制項的回應： 公用標頭，而且不能包含授權或設定 Cookie 的標頭。 請參閱[回應快取中介軟體所使用的快取條件的完整清單](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)。

### <a name="data-caching"></a>資料快取

而非 （或其他） 快取完整的 web 回應，您可以快取的個別資料查詢的結果。 這麼做，您可以使用中記憶體內部快取的 web 伺服器上，或使用[分散式快取](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)。 本節將示範如何實作記憶體內部快取中。

新增記憶體的支援 （或分散式） ConfigureServices 中的快取：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

請務必新增的 Microsoft.Extensions.Caching.Memory NuGet 封裝。

加入服務之後, 您要求 IMemoryCache 透過相依性插入每當您需要存取快取。 在此範例中，CachedCatalogService 使用 Proxy （或裝飾項目） 設計模式中，藉由提供替代的實作 ICatalogService 控制存取權 （或新增至行為） 的基礎 CatalogService 實作。

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

若要設定要使用服務的快取的版本，但仍然可讓服務取得的 CatalogService 它需要其建構函式中的執行個體的應用程式，您可以加入下列 ConfigureServices 中：

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

這位置，每分鐘一次，而不是在每次要求只會對擷取目錄資料的資料庫呼叫。 根據網站的流量，這可能會影響非常重要的資料庫，以及平均頁面載入時間，首頁目前相依於此服務所公開之查詢的這三個的查詢數目。

實作快取時，就會發生一個問題就*過時的資料*– 也就是在來源但過期的版本已變更的資料會保留在快取。 簡單的方式來減輕這個問題是使用小型的快取持續時間，因為忙碌的應用程式沒有有限的另一個好處，來擴充快取資料的長度。 例如，考慮一個頁面，可讓單一資料庫查詢，而且會要求每秒 10 倍。 如果此頁面會快取一分鐘，將會導致每分鐘做為 1，99.8%降低從 600 卸除的資料庫查詢的數目。 如果改為快取持續時間所做的一小時整體縮減 99.997%，而現在的可能性和潛在的存在時間的過時資料會同時大幅增加。

另一個方法是更新本身包含的資料時，主動移除快取項目。 如果已知其索引鍵，則可以移除任何個別的項目：

```csharp
_cache.Remove(cacheKey);
```

如果您的應用程式公開功能的更新，它會快取項目，您可以在執行更新程式碼中移除對應的快取項目。 有時可能會有許多不同的項目相依於特定的資料集。 在此情況下，可用來建立快取項目，使用 CancellationChangeToken 之間的相依性。 與 CancellationChangeToken，您可以終止多個快取項目一次取消語彙基元。

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
[上一個](develop-asp-net-core-mvc-apps.md) [下一步] (test-asp-net-core-mvc-apps.md)
