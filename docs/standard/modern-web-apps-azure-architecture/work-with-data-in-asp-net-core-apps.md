---
title: 使用 ASP.NET Core 應用程式中的資料
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 使用 ASP.NET Core 應用程式中的資料
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9f765acce89bec1fd73e9c43a6e7d75d78be785d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423996"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>使用 ASP.NET Core 應用程式中的資料

> 「資料是非常寶貴的資產，而且比系統本身擁有更長久的價值。」
>
> Tim Berners-Lee

對所有軟體應用程式來說，資料存取都是非常重要的一部分。 ASP.NET Core 支援各種不同的資料存取選項，包括 Entity Framework Core (和 Entity Framework 6)，並可使用任何 .NET 資料存取架構。 至於要選擇使用哪種資料存取架構，則取決於應用程式的需求。 您可以將這些選項從 ApplicationCore 和 UI 專案中抽離出來，並將實作詳細資料封裝到基礎結構中，以協助產生相依性低的可測試軟體。

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (適用於關聯式資料庫)

如果您要撰寫的新 ASP.NET Core 應用程式需要使用關聯式資料，建議您讓應用程式使用 Entity Framework Core (EF Core) 來存取資料。 EF Core 是一種物件關聯式對應程式 (O/RM)，可讓 .NET 開發人員保存要進出資料來源的物件。 它可以讓開發人員免除一般需要撰寫的大多數資料存取程式碼。 EF Core 和 ASP.NET Core 一樣，已經過從頭改寫以支援模組化跨平台應用程式。 您可以將它以 NuGet 套件形式新增至應用程式，並於 啟動時進行設定，再視需要透過相依性插入對其提出要求。

若要搭配使用 EF Core 與 SQL Server 資料庫，請執行下列 dotnet CLI 命令：

dotnet add package Microsoft.EntityFrameworkCore.SqlServer

若要新增對 InMemory 資料來源的支援以進行測試：

dotnet add package Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>DbContext

若要使用 EF Core，您需要 <xref:Microsoft.EntityFrameworkCore.DbContext> 的子類別。 這個類別包含的屬性代表應用程式會用到的實體集合。 eShopOnWeb 範例包括 CatalogContext 以及項目、品牌和類型的集合：

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

您的 DbContext 必須具備可接受 DbContextOptions 的建構函式，並將此引數傳遞給基底 DbContext 建構函式。 請注意，如果您的應用程式中只有一個 DbContext，即可傳遞 DbContextOptions 的執行個體，但如果不只一個，您就必須使用泛型 DbContextOptions\<T> 類型，並將其作為泛型參數傳遞至 DbContext 類型中。

### <a name="configuring-ef-core"></a>設定 EF Core

一般來說，您需要在 ASP.NET Core 應用程式的 ConfigureServices 方法中設定 EF Core。 EF Core 使用的 DbContextOptionsBuilder 可支援幾項實用的擴充方法，以簡化其組態。 若要將 CatalogContext 設定為搭配使用 SQL Server 資料庫與 [組態] 中定義的連接字串，您可以將下列程式碼新增至 ConfigureServices：

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

若要使用記憶體內部資料庫：

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

一旦您安裝好 EF Core、建立 DbContext 子類型，並在 ConfigureServices 中進行設定，即可使用 EF Core。 您可以在任何需要 DbContext 類型執行個體的服務中，對其提出要求，並透過 LINQ 來使用您保存的實體，如同它們就在集合中一般。 EF Core 會將您的 LINQ 運算式轉譯為 SQL 查詢以儲存和擷取資料。

EF Core 會設定記錄器，並確保其層級至少設定為「資訊」以執行查詢，如圖 8-1 所示。

![](./media/image8-1.png)

圖 8-1 將 EF Core 查詢記錄到主控台

### <a name="fetching-and-storing-data"></a>擷取與儲存資料

若要從 EF Core 擷取資料，您可以存取適當的屬性，並使用 LINQ 篩選結果。 您也可以使用 LINQ 來執行投影，將某種類的結果轉換到另一種類型。 下列範例會擷取 CatalogBrands，並依名稱排序、依 Enabled 屬性篩選，然後投射到 SelectListItem 類型：

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

請務必在上述範例中新增 ToListAsync 呼叫，以立即執行查詢。 否則，陳述式會指派 IQueryable\<SelectListItem> 給 brandItem，直到系統列舉它時才執行。 從方法傳回 IQueryable 結果時，也有其優缺點。 它可讓您進一步修改 EF Core 建構的查詢，但如果您將作業新增至 EF Core 不能轉譯的查詢時，也可能會出現只在執行階段發生的錯誤。 一般來說，比較安全的做法是將任何篩選條件傳遞給執行資料存取的方法，並傳回記憶體內部的集合 (例如，List\<T>) 作為結果。

EF Core 會追蹤其從持續性儲存區擷取的實體變更。 若要儲存追蹤實體的變更，您只需要在 DbContext 上呼叫 SaveChanges 方法，並確定它是用來擷取實體的相同 DbContext 執行個體。 新增和移除實體是直接在適當的 DbSet 屬性上完成，並再次地使用 SaveChanges 呼叫來執行資料庫命令。 下列範例示範如何新增、更新和移除持續性儲存區的實體。

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

EF Core 支援擷取和儲存的同步與非同步的方法。 若是 Web 應用程式，建議搭配使用非同步方法與非同步/等候模式，Web 伺服器執行緒才不會在等候資料存取作業完成期間受到封鎖。

### <a name="fetching-related-data"></a>擷取相關資料

當 EF Core 擷取實體時，它會填入與資料庫中的這個實體一起儲存的所有屬性。 EF Core 不會填入相關實體清單這類導覽屬性，且可能會將其值設為 Null。 這可確保 EF Core 不會擷取超過實際所需的資料，這對 Web 應用程式來說尤其重要，因為這類應用程式必須快速處理要求，並以有效率的方式傳回回應。 若要使用「積極式載入」  來包含實體的關聯性，您可以在查詢中使用 Include 擴充方法以指定屬性，如下所示：

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

您可以包含多個關聯性，也可以使用 ThenInclude 來包含子關聯性。 EF Core 會執行單一查詢來擷取產生的實體集。 或者您可以藉由將以 '.' 分隔的字串傳遞至 `.Include()` 擴充方法，來包含導覽屬性的導覽屬性，如下所示：

```csharp
    .Include(“Items.Products”)
```

除了封裝篩選邏輯，規格還可以指定要傳回的資料形式，包括要填入的屬性。 eShopOnWeb 範例包括數個示範在規格中封裝積極式載入資訊的規格。 您可以在這裡了解規格如何作為查詢的一部份使用：

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

另一個用來載入相關資料的選項是使用「明確式載入」  。 明確式載入可讓您將其他資料載入已擷取的實體中。 由於這牽涉到資料庫的個別要求，因此不建議用於 Web 應用程式，而應該將每項要求的資料庫往返次數降至最低。

「消極式載入」  功能會自動載入應用程式參考的相關資料。 EF Core 已在 2.1 版中新增對消極式載入的支援。 消極式載入預設不會啟用，而且需要安裝 `Microsoft.EntityFrameworkCore.Proxies`。 如同明確式載入，通常應該為 Web 應用程式停用消極式載入，因為其使用會導致在每個 Web 要求中發出額外的資料庫查詢。 不幸的是，當延遲很小且用於測試的資料集通常很小時，消極式載入所產生的額外負荷往往在開發期間不易察覺。 不過，在生產環境中，由於使用者、資料和延遲更多，額外的資料庫要求通常會導致 Web 應用程式大量使用消極式載入而效能不佳。

[避免在 Web 應用程式中消極載入實體](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>封裝資料

EF Core 支援多種功能，可讓您的模型正確封裝其狀態。 領域模型中的常見問題之一便是他們會將集合導覽屬性作為可公開存取的清單類型公開。 這可讓任何共同作業者操縱這些集合類型的內容，使其略過與集合相關的重要商務規則，並可能讓物件處於無效狀態。 其解決方案便是公開相關集合的唯讀存取，並明確提供定義用戶端可操縱他們之方式的方法，如下列範例所示：

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

請注意，這個實體類型不會公開公開的 `List` 或 `ICollection` 屬性，但是會公開包裝基礎 List 類型的 `IReadOnlyCollection` 類型。 在使用這個模式時，您可以透過 Entity Framework Core 來使用支援欄位，如下所示：

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

另一種可供您改進領域模型的方式是使用缺少身分識別並只能由其屬性來辨別之類型的值物件。 使用這種類型作為您實體的屬性，可協助保持邏輯專屬於其所屬值物件，並可避免使用相同概念的多個實體間出現重複的邏輯。 在 Entity Framework Core 中，您可以藉由將類型設定為自有實體，來使值物件保留在與其專屬實體相同的資料表中，如下所示：

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

在此範例中，`ShipToAddress` 屬性的類型為 `Address`。 `Address` 是擁有多個屬性 (例如 `Street` 及 `City`) 的值物件。 EF Core 以每個 `Order` 屬性一個資料行來將 `Address` 物件對應到其資料表，並以屬性名稱作為每個資料行名稱的開頭。 在這個範例中，`Order` 資料表會包含像是 `ShipToAddress_Street` 及 `ShipToAddress_City` 的資料行。

[EF Core 2.2 推出了自有實體集合的支援](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a>具復原功能的連接

有時您可能會無法使用 SQL 資料庫等外部資源。 在暫時無法使用的情況下，應用程式可以使用重試邏輯，以避免引發例外狀況。 這項技術通常稱為「連線復原能力」  。 您可以重試某項作業，並以指數方式增加等候時間，直到已達重試計數上限為止，藉此實作[使用指數輪詢重試](https://docs.microsoft.com/azure/architecture/patterns/retry)技術。 這項技術是為了因應雲端資源可能會在短時間內斷斷續續無法使用，而導致某些要求失敗的問題。

在 Azure SQL DB 中，Entity Framework Core 已提供內部資料庫恢復連接功能和重試邏輯。 如果您想要使用具復原功能的 EF Core 連線，則必須為每個 DbContext 連線啟用 Entity Framework 執行策略。

例如，EF Core 連接層級的下列程式碼可在連接失敗時重試具有恢復功能的 SQL 連接。

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>使用 BeginTransaction 和多個 DbContext 的執行策略和明確異動

在 EF Core 連接中啟用重試時，您使用 EF Core 執行的每項作業都會變成其本身可重試的作業。 如果發生暫時性失敗，SaveChanges 的每個查詢和每個呼叫會當做一個單位來重試。

不過，如果您的程式碼使用 BeginTransaction 來起始異動，您將定義需視為一個單位的專屬作業群組；如果失敗，則必須復原異動內的所有項目。 如果您在使用 EF 執行策略 (重試原則) 時嘗試執行該交易，並在交易中包含來自多個 DbContext 的數個 SaveChanges，則會看到類似如下的例外狀況。

System.InvalidOperationException：已設定的執行策略 'SqlServerRetryingExecutionStrategy' 不支援使用者起始的異動。 使用 'DbContext.Database.CreateExecutionStrategy()' 所傳回的執行策略，將異動中的所有作業當做一個可重試的單位來執行。

解決方法是使用代表必須執行之所有項目的委派，來手動叫用 EF 執行策略。 如果發生暫時性失敗，執行策略會再叫用委派一次。 下列程式碼會示範如何實作這個方法：

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

第一個 DbContext 是 \_catalogContext，第二個 DbContext 則位於 \_integrationEventLogService 物件內。 最後，系統會使用 EF 執行策略執行多個 DbContext 的認可動作。

> ### <a name="references--entity-framework-core"></a>參考資料 – Entity Framework Core
>
> - **EF Core 文件**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core：相關資料**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **避免在 ASPNET 應用程式中消極載入實體**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>該使用 EF Core 或微型 ORM？

雖然 EF Core 是管理持續性的絕佳選擇，甚至能封裝應用程式開發人員提供的資料庫詳細資料，但它並不是唯一的選擇。 另一個熱門的開放原始碼替代方法是 [Dapper](https://github.com/StackExchange/Dapper)，也就是所謂的微型 ORM。 微型 ORM 是一種功能較簡單的輕量型工具，可將物件對應至資料結構。 舉 Dapper 為例，其設計目標著重在效能，而非完整封裝用來擷取和更新資料的基礎查詢。 因為 Dapper 不需要開發人員完全抽離 SQL，所以是比較單純的「試用版」，可讓開發人員撰寫想用於指定資料存取作業的確切查詢。

EF Core 與 Dapper 的主要差異是前者提供下列兩個重要的功能，但這也會對效能產生額外負荷。 第一個是它會將 LINQ 運算式轉譯為 SQL。 雖然系統會快取這些轉譯，第一次執行時仍會產生額外負荷。 第二個是追蹤實體的變更 (以便產生有效的 UPDATE 陳述式)。 您可以使用 AsNotTracking 延伸模組，將特定查詢的這項行為關閉。 EF Core 也會產生非常有效率的 SQL 查詢，而且在任何情況下，效能都是完全可以接受的等級；但如果您需要妥善控制要執行的精確查詢，您也可以使用 EF Core 傳入自訂的 SQL (或執行預存程序)。 在這種情況下，Dapper 就略勝於 EF Core。 Julie Lerman 在 2016 年 5 月的 [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx) (Dapper、Entity Framework 和混合式應用程式) MSDN 文章中提供了一些效能資料。 如需各種不同資料存取方法的其他效能基準測試資料，請參閱 [Dapper 網站](https://github.com/StackExchange/Dapper)。

若要查看 Dapper 和 EF Core 的語法差異，請參考下列用來擷取項目清單之相同方法的兩個版本：

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

如果您需要使用 Dapper 建立更複雜的物件圖形，則必須自行撰寫相關的查詢 (反之，在 EF Core 中是要新增 Include)。 上述作業是透過各種語法來支援，包括「多重對應」這項功能，可讓您將個別資料列對應到多個對應物件。 例如，假設 Post 類別具有 User 類型的 Owner 屬性 ，下列 SQL 就會傳回所有必要的資料：

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

每個傳回的資料列都包含 User 和 Post 資料。 因為 User 資料應該透過其 Owner 屬性附加至 Post 資料，所以會使用下列函式：

```csharp
(post, user) => { post.Owner = user; return post; }
```

下列為完整的程式碼清單，其會傳回文章集合，並以相關聯的使用者資料填入 Owner 屬性：

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

因為 Dapper 提供較少的封裝，所以開發人員必須進一步了解如何儲存資料、如何有效率地查詢資料，並撰寫更多程式碼來擷取資料。 當模型變更時，您不只要建立新的移轉 (另一個 EF Core 功能)，及/或逐一更新 DbContext 中每個位置的對應資訊，還要更新會受到影響的每一個查詢。 這些查詢的編譯時間無法保證，因此為了回應模型或資料庫的變更，查詢可能會在執行階段中斷，導致更難快速偵測錯誤。 Dapper 折衷了上述情況，以提供極快速的效能。

對於大部分應用程式以及幾乎所有主要的應用程式來說，EF Core 可提供還不錯的效能。 因此，其開發人員的生產力優勢可能遠大於它的效能負擔。 如果查詢可受益於快取，實際的查詢可能只會執行很短的時間，這時查詢效能之間的微小差異就無傷大雅了。

## <a name="sql-or-nosql"></a>SQL 或 NoSQL

傳統上來看，SQL Server 這類關聯式資料庫主導了永續性資料儲存的市場，但它們並不是唯一可用的解決方案。 [MongoDB](https://www.mongodb.com/what-is-mongodb) 這類 NoSQL 資料庫提供儲存物件的不同方式。 這個選項不會將物件對應至資料表和資料列，而是序列化整個物件圖形，並且將結果儲存。 初步來講，這個方法的優點是簡潔和效能。 比起將物件分解成許多關聯性資料表，並更新自上次從資料庫擷取物件之後可能已變更的資料列，使用索引鍵儲存單一序列化的物件，當然更加簡單。 同樣地，相較於從關聯式資料庫完整撰寫相同物件所需的複雜聯結或多個資料庫查詢，從以索引鍵為基礎的存放區中擷取和還原序列化單一物件通常更為快速、簡單。 NoSQL 資料庫不具鎖定、異動或固定結構描述的特質，也非常適合跨多部機器調整規模，同時支援大型資料集。

另一方面來看，NoSQL 資料庫 (如字面通稱) 也有其缺點。 關聯式資料庫使用正規化功能，強制執行一致性並避免出現重複的資料。 這可減少資料庫的大小總計，並確保對共用資料所做的更新可在整個資料庫中立即生效。 在關聯式資料庫中，假設「地址」資料表參考「國家/地區」資料表中的識別碼，則當國家/地區的名稱變更時，地址記錄也會隨之更新，因此您不需要另行更新地址記錄。 不過，在 NoSQL 資料庫中，「地址」和其相關聯的「國家/地區」可能會序列化為許多預存物件的一部分。 更新國家/地區名稱時，也必須更新所有相關物件，而不是單一資料列。 關聯式資料庫也可以強制執行規則 (例如外部索引鍵)，以確保關聯的完整性。 NoSQL 資料庫通常不會對其資料提供這類條件約束。

NoSQL 資料庫還有一個必須處理的複雜問題是版本設定。 當物件的屬性變更時，您可能無法從過去已儲存的版本將它還原序列化。 因此，所有含序列化版本 (舊版) 物件的現有物件，都必須更新以符合新的結構描述。 而在關聯式資料庫中，當結構描述變更時，有時需要更新指令碼或對應更新，因此兩者已不只是概念上的差異。 不過，使用 NoSQL 方法時，您必須修改的項目數通常非常多，因為重複的資料比較多。

您可以在 NoSQL 資料庫中儲存物件的多個版本，而固定結構描述的關聯式資料庫通常不支援這項功能。 不過，在這種情況下，應用程式的程式碼必須找出存在的舊版本物件，這增加了其額外的複雜性。

NoSQL 資料庫通常不會強制執行 [ACID](https://en.wikipedia.org/wiki/ACID)，因此在效能和延展性方面比關聯式資料庫更有優勢。 因此針對不適用於正規化資料表結構儲存區的極大型資料集以及物件，就非常適合使用這種資料庫。 單一應用程式也可以同時利用關聯式和 NoSQL 資料庫，只要依據最適合的情況來選擇即可。

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB 是全受控的 NoSQL 資料庫服務，可提供以雲端為基礎的無結構描述資料儲存區。 DocumentDB 是專為滿足快速及可預測的效能、高可用性、彈性調整和全域發佈需求所建置。 即使在 NoSQL 資料庫中，開發人員仍可以對 JSON 資料使用豐富且熟悉的 SQL 查詢功能。 DocumentDB 中的所有資源都會儲存為 JSON 文件。 系統會以「項目」  形式來管理資源；也就是說，資源是包含中繼資料和「摘要」  的文件，也是項目的集合。 圖 8-2 顯示不同 DocumentDB 資源之間的關聯性。

![DocumentDB (其為 NoSQL JSON 資料庫) 資源之間的階層式關聯性](./media/image8-2.png)

**圖 8-2**： DocumentDB 資源的組織。

DocumentDB 查詢語言是一種簡單但功能強大的介面，適用於查詢 JSON 文件。 該語言支援 ANSI SQL 文法子集，並深度整合 JavaScript 物件、陣列、物件建構和函式引動過程。

**參考資料 – DocumentDB**

- DocumentDB 簡介  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>其他持續性選項

除了關聯式和 NoSQL 儲存區選項，ASP.NET Core 應用程式也可以使用 Azure 儲存體，透過以雲端為基礎且可擴充的方式，來儲存各種不同的資料格式和檔案。 Azure 儲存體可大幅進行調整，因此您可以一開始先儲存少量資料，之後再視應用程式的需要，擴充儲存至數百 GB 或 TB。 Azure 儲存體支援下列四種資料類型：

- Blob 儲存體，也稱為物件儲存體，適用於非結構化的文字或二進位儲存。

- 資料表儲存體，可透過資料列索引鍵存取，適用於結構化資料集。

- 佇列儲存體，適合用來進行以佇列為主的通訊。

- 檔案儲存體，適合用來存取 Azure 虛擬機器和內部部署應用程式之間的共用檔案。

**參考資料 – Azure 儲存體**

- Azure 儲存體簡介  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>快取

在 Web 應用程式中，每個 Web 要求都應盡量在最短時間內完成。 為了達成上述目的，其中一個方法是限制伺服器為完成要求必須發出的外部呼叫數目。 快取功能會將資料的複本儲存到伺服器 (或比資料來源更容易查詢的其他資料存放區)。 Web 應用程式 (特別是非 SPA 的傳統 Web 應用程式) 必須使用每個要求來建置完整的使用者介面。 若要這麼做，通常要從某個使用者要求到下一個使用者要求不斷重複進行許多相同的資料庫查詢。 在大部分情況下，這些資料很少變更，因此實在沒有必要不斷向資料庫提出要求。 ASP.NET Core 支援可快取整個頁面的回應快取，以及可支援更細微快取行為的資料快取。

當實作快取時，應特別注意關注點分離原則。 避免在資料存取邏輯或使用者介面中，實作快取邏輯。 相反地，請將快取封裝在其自身的類別中，並使用組態來管理它的行為。 這會遵循開啟/關閉準則 (Open/Closed Principle) 和單一責任準則 (Single Responsibility Principle)，並可讓您更輕鬆管理應用程式增長時的快取使用方式。

### <a name="aspnet-core-response-caching"></a>ASP.NET Core 回應快取

ASP.NET Core 支援兩個層級的快取回應。 第一個層級不會快取伺服器上的任何項目，但會新增 HTTP 標頭以指示用戶端和 Proxy 伺服器來快取回應。 上述作業的實作方式為將 ResponseCache 屬性新增至個別的控制器或動作：

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

上述範例會導致將下列標頭新增至回應，並指示用戶端快取結果高達 60 秒。

Cache-Control: public,max-age=60

若要將伺服器端記憶體內部快取新增至應用程式，您必須參考 Microsoft.AspNetCore.ResponseCaching NuGet 套件，然後新增回應快取中介軟體。 此中介軟體是在啟動的 ConfigureServices 和 Configure 中設定：

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

回應快取中介軟體會根據一組可自訂的條件來自動快取回應。 根據預設，只會快取透過 GET 或 HEAD 方法要求的 200 (沒問題) 回應。 此外，要求的回應必須具備 Cache-Control: public 標頭，而且不能包含 Authorization 或 Set-Cookie 的標頭。 請參閱[回應快取中介軟體所使用的快取條件完整清單](/aspnet/core/performance/caching/middleware#conditions-for-caching)。

### <a name="data-caching"></a>資料快取

您可以只快取個別的資料查詢結果，或同時快取完整的 Web 回應。 若要這麼做，您可以在 Web 伺服器上使用記憶體內部快取，或使用[分散式快取](/aspnet/core/performance/caching/distributed)。 本節將示範如何實作記憶體內部快取。

在 ConfigureServices 中，新增對記憶體 (或分散式) 快取的支援：

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

請務必一併新增 Microsoft.Extensions.Caching.Memory NuGet 套件。

新增服務之後，每當您需要存取快取時，即可透過相依性插入要求 IMemoryCache。 在此範例中，CachedCatalogService 會提供 ICatalogService 的替代實作來使用 Proxy (或裝飾項目) 設計模式，以控制基礎 CatalogService 實作的存取權 (或新增行為至基礎 CatalogService 實作)。

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

若要將應用程式設定為使用服務的快取版本，但仍然允許服務取得其建構函式中所需的 CatalogService 執行個體，您可以在 ConfigureServices 中新增下列項目：

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

完成上述作業時，系統只會每分鐘呼叫一次資料庫以擷取目錄資料，而不會在每次要求時都呼叫。 根據網站的流量而定，這可能會大幅影響資料庫的查詢數目以及首頁 (目前相依於此服務所公開的所有三個查詢) 的平均頁面載入時間。

實作快取時會引發「過時資料」  的問題 – 亦即，來源的資料已變更，但快取中仍保留過期的版本。 若要緩和這個問題，一個簡單的方式是將快取持續時間縮短，因為對忙碌的應用程式來說，延長快取資料的時間長度意義不大。 例如，假設某個頁面會進行單一資料庫查詢，且每秒要求 10 次。 如果將這個頁面快取一分鐘，則資料庫每分鐘查詢的數目可從 600 降到 1，減少了 99.8%。 如果快取持續時間設為一小時，整體可以減少 99.997%；不過，這樣一來，過時資料的可能性和存在時間都會大幅增加。

另一個方法是當快取項目包含的資料有所更新時，就主動移除快取項目。 只要知道索引鍵，就可以移除任何個別的項目：

```csharp
_cache.Remove(cacheKey);
```

如果應用程式會公開功能以更新它的快取項目，您可以在執行更新的程式碼中移除對應的快取項目。 有時候，可能會有許多不同的項目相依於特定的資料集。 在此情況下，您可以使用 CancellationChangeToken 來建立快取項目之間的相依性。 使用 CancellationChangeToken 時，您只要取消權杖即可一次讓多個快取項目到期。

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

快取可大幅提升從資料庫反覆要求相同值的網頁效能。 請務必測量資料存取和頁面效能，再套用快取，並僅在看到有改進的需求時才套用快取。 快取會耗用網頁伺服器記憶體資源，並增加應用程式的複雜度，因此請務必不要太早使用此技術進行最佳化。

>[!div class="step-by-step"]
>[上一頁](develop-asp-net-core-mvc-apps.md)
>[下一頁](test-asp-net-core-mvc-apps.md)
