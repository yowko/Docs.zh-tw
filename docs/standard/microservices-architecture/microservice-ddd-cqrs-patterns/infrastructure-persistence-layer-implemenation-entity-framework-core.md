---
title: "實作與 Entity Framework 的核心基礎結構保存層"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作與 Entity Framework 的核心基礎結構保存層"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>實作與 Entity Framework 的核心基礎結構保存層

當您使用 SQL Server、 Oracle 或 PostgreSQL 例如關聯式資料庫時，是建議的方法是實作保存層基礎上 Entity Framework (EF)。 EF 支援 LINQ，並提供您的模型，以及簡化的持續性進入您的資料庫中的強型別的的物件。

Entity Framework 必須有悠久的歷史，.NET Framework 的一部分。 當您使用.NET Core 時，您也應該使用 Entity Framework Core Windows 或 Linux 執行.NET Core 方式相同。 EF 核心是完全重寫的 Entity Framework 中，使用較小的使用量和效能的重要增強功能實作。

## <a name="introduction-to-entity-framework-core"></a>Entity Framework Core 簡介

Entity Framework (EF) 核心的輕量型可擴充的並跨平台版本常見的 Entity Framework 資料存取技術。 它是 mid 2016 中引進.NET Core。

因為簡介 EF 核心已經在 Microsoft 文件中，在這裡我們只是提供該資訊的連結。

#### <a name="additional-resources"></a>其他資源

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **開始使用 ASP.NET Core 與使用 Visual Studio 的 Entity Framework Core**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **DbContext 類別**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **比較 EF 核心 & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>在 Entity Framework Core DDD 檢視方塊中的基礎結構

從 DDD 觀點來看，EF 重要功能是能夠使用 POCO 網域實體，在做 POCO 的 EF 術語中也稱為*程式碼的第一個實體*。 如果您使用 POCO 網域實體時，您的網域模型類別是持續性-無知，遵循[永續性無知之](http://deviq.com/persistence-ignorance/)和[基礎結構忽略](https://ayende.com/blog/3137/infrastructure-ignorance)原則。

每 DDD 模式，您應該封裝網域行為和規則內的實體類別本身，讓它存取任何集合時能控制非變異項目、 驗證及規則。 因此，它不是子的最好的作法是子的在 DDD 允許公用存取權集合的實體或值的物件。 相反地，您會想要公開 （expose） 可控制如何及何時可以更新您的欄位和屬性集合，方法與哪些行為以及動作時會發生這種情況發生。

在 EF 核心 1.1 中，以滿足這些需求的 DDD 您可以有純欄位在您的實體，而不是具有公用和私用 setter 的屬性。 若不想使用可供存取，外部實體欄位，您就可以建立屬性或欄位，而不是屬性。 沒有需要使用私用 setter，如果您偏好徹底的方法。

類似的方式，您現在可以有唯讀集合使用的公用屬性類型為 IEnumerable&lt;T&gt;，備份的私用欄位成員集合 (例如清單&lt;&gt;) 中您依賴 EF 持續性的實體。 舊版的 Entity Framework 所需的集合屬性，以支援 ICollection&lt;T&gt;，這是任何使用父實體類別的開發人員無法新增或移除其屬性集合的項目。 該可能性是針對 DDD 中建議的模式。

您可以使用私用集合公開唯讀的 IEnumerable 物件時，如下列程式碼範例所示：

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
        decimal unitPrice, decimal discount,
        string pictureUrl, int units = 1)
    {
        // Validation logic...
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

請注意，OrderItems 屬性只能以唯讀方式使用清單&lt;&gt;。AsReadOnly()。 這個方法會建立私用清單的唯讀包裝函式，讓您可以針對外部更新受到保護。 它是成本更低比使用 ToList 方法，因為它沒有新的集合中，複製的所有項目相反地，它會執行包裝函式的執行個體只有一個堆積配置作業。

EF 核心可用來將網域模型對應至實體資料庫，而不會破壞網域模型。 是純 POCO.NET 程式碼，因為對應動作在保存層中實作。 在該對應的動作，您需要設定到資料庫欄位對應。 在下列範例 OnModelCreating 方法中，反白顯示的程式碼會告知 EF 核心透過其欄位存取 OrderItems 屬性。

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

當您使用欄位而非屬性時，就如同它有一個清單保存 OrderItem 實體&lt;OrderItem&gt;屬性。 不過，它會公開單一存取子 （AddOrderItem 方法），將順序中加入新項目。 如此一來，行為和資料繫結在一起，且將使用網域模型的任何應用程式程式碼一致。

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Entity Framework Core 與實作自訂的儲存機制

在實作層級的儲存機制已只是具有資料持續性程式碼的工作單位 (DBContext EF 核心中) 所協調的類別時執行更新，將下列類別中所示：

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;

        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

請注意 IBuyerRepository 介面來自網域模型層。 不過，儲存機制實作是在持續性和基礎結構層級。

EF DbContext 是透過相依性插入建構函式。 它被共用相同 HTTP 要求範圍內，這點受惠 IoC 容器 （也可以明確設定與服務其預設存留時間 (ServiceLifetime.Scoped) 多個儲存機制之間。AddDbContext&lt;&gt;)。

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>（更新或與查詢的交易） 的儲存機制中實作方法

在每個儲存機制類別中，您應該讓更新其相關的彙總所包含的實體狀態的持續性方法。 請記住，沒有彙總與它相關的儲存機制之間的一對一關聯性。 請考慮彙總根實體物件可能會內嵌在其 EF 圖形內的子實體。 例如，買方也可能會有多個付款方法，為相關的子系的實體。

由於 eShopOnContainers 中順序的微服務的方法也基礎 CQS/CQRS，大多數的查詢不會實作自訂儲存機制。 開發人員可以自由建立查詢和聯結所需而且沒有一般彙總，每個彙總和 DDD 的自訂儲存機制所加諸的限制展示層。 本指南所建議的自訂儲存機制大部分都有數個更新或交易式的方法，但查詢方法必須以取得要更新的資料。 例如，BuyerRepository 儲存機制實作 FindAsync 方法，因為應用程式必須知道特定買方是否存在於之前建立新的買方的訂單相關。

不過，實際的查詢方法，以取得資料以便傳送至展示層或用戶端應用程式中實作，如使用 Dapper 彈性查詢為基礎的 CQRS 查詢中所述。

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>使用自訂的儲存機制，而非直接使用 EF DbContext

Entity Framework DbContext 類別為基礎的工作單位和儲存機制模式，並可直接從程式碼，例如從 ASP.NET Core MVC 控制器。 也就是方式可以建立的最簡單的程式碼，如同在 eShopOnContainers CRUD 目錄微服務。 在您想最簡單的程式碼可能的情況下，您可以直接使用的 DbContext 類別，許多開發人員都一樣。

不過，實作自訂的儲存機制提供數個優點，實作更複雜的 microservices 或應用程式時。 工作單位和儲存機制模式被用來封裝基礎結構的持續性層級，因此它分開的應用程式和網域模型層。 實作這些模式，可以加快模擬資料庫的存取權的模擬儲存機制的使用。

圖 9-18 您所見不使用儲存機制 （直接使用 EF DbContext） 之間的差異與使用更輕鬆地模擬的儲存機制的儲存機制。

![](./media/image19.png)

**圖 9-18**。 使用自訂的儲存機制，與一般 DbContext

模擬時，有多個替代項目。 您無法模擬只儲存機制，或您無法模擬整個工作單位。 通常模擬的儲存機制已足夠，和通常不需要抽象，因此模擬整個工作單位的複雜性。

稍後，當我們將重點放在應用程式層上，您會看到 ASP.NET 核心中相依性插入 」 運作方式以及它使用儲存機制時的實作方式。

簡單地說，自訂儲存機制可讓您更輕鬆地測試不會受到資料層狀態的單元測試的程式碼。 如果您執行測試，也可透過 Entity Framework 存取實際的資料庫時，它們不是單元測試而整合測試，也就是很慢。

如果您直接使用 DbContext，唯一的選擇，您必須是執行單元測試使用與可預測資料的記憶體中的 SQL Server 單元測試。 您將無法在存放庫層級相同的方式來控制模擬物件和假資料。 當然，您一律可以測試 MVC 控制器。

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>IoC 容器中的 EF DbContext 和 IUnitOfWork 執行個體存留期

（公開為 IUnitOfWork 物件） 的 DbContext 物件可能需要由共用相同的 HTTP 要求範圍內的多個儲存機制。 比方說，這是 true 時正在執行的作業必須處理多個彙總，或只是因為您使用多個儲存機制的執行個體。 也很重要這裡 IUnitOfWork 介面是屬於網域，而不 EF 型別。

若要這樣做，請 DbContext 物件的執行個體必須具有其服務的存留期設定為 ServiceLifetime.Scoped。 這是當註冊建立的 DbContext 來與服務的預設存留時間。AddDbContext Startup.cs 中的檔案 ASP.NET Core Web API 專案的 ConfigureServices 方法從您 IoC 容器中。 以下的程式碼可說明這點。

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
    .AddDbContext<OrderingContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

DbContext 具現化模式不應設定為 ServiceLifetime.Transient 或 ServiceLifetime.Singleton。

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>儲存機制的執行個體存留期，IoC 容器中

類似的方式，儲存機制的存留期通常應該設定為已設定領域 (InstancePerLifetimeScope Autofac 中)。 它也可能是暫時性 (InstancePerDependency Autofac 中)，但您的服務時，會在與記憶體中更有效率使用已設定領域的存留期。

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

請注意，使用單一存留期的儲存機制可能導致嚴重的並行存取問題時您 DbContext 設為範圍 (InstancePerLifetimeScope) 存留期 （建立的 DBContext，預設存留時間）。

#### <a name="additional-resources"></a>其他資源

-   **ASP.NET MVC 應用程式中實作的儲存機制和工作模式單位**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen。實作策略儲存機制模式有 Entity Framework，Dapper，而且鏈結**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre：比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>資料表對應

資料表對應會識別要從查詢的資料表資料，並儲存到資料庫。 先前您已看到如何使用網域實體 （例如產品或順序網域），來產生相關的資料庫結構描述。 EF 強設計的概念*慣例*。 慣例位址類似 「 將資料表的名稱是什麼？ 」 或者 「 屬性 」 的主索引鍵嗎？ 慣例通常依據傳統的名稱 — 比方說，它是典型的主索引鍵屬性，結尾是識別碼。

依照慣例，每個實體將會設定對應至資料表，以與 DbSet 同名&lt;TEntity&gt;公開衍生內容上的實體的屬性。 如果沒有 DbSet&lt;TEntity&gt;值會提供指定之實體，使用此類別名稱。

### <a name="data-annotations-versus-fluent-api"></a>資料註解或 fluent 應用程式開發的應用程式開發介面

有許多其他的 EF 核心慣例，而且大部分是可以使用資料註解或 Fluent API，在 OnModelCreating 方法內實作變更。

資料註解必須使用的實體模型類別本身，這是從 DDD 觀點來看受到更多干擾方法。 這是因為您會使用與基礎結構資料庫相關的資料註解破壞您的模型。 相反地，Fluent API 是便利的方式來變更大部分慣例和程式資料持續性基礎結構層級中的對應，所以實體模型會清楚和低耦合從持續性基礎結構。

### <a name="fluent-api-and-the-onmodelcreating-method"></a>關於 fluent API 和 OnModelCreating 方法

如前所述，才能變更慣例和對應，可用於 OnModelCreating 方法將 DbContext 類別。 下列範例會示範如何在這麼 eShopOnContainers 中順序的微服務中。

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

您可以設定在相同的 OnModelCreating 方法中，所有 Fluent API 對應，但建議您最好要分割該程式碼，並有多個 submethods，其中每個實體，如範例所示。 針對極大的模型，它甚至可以是建議您在有不同的來源檔案 （靜態類別） 設定不同的實體類型。

此範例中的程式碼會明確。 不過，EF 核心慣例大部分的自動執行，因此您需要寫入來達成相同的實際程式碼會小很多。

### <a name="the-hilo-algorithm-in-ef-core"></a>在 EF 核心 Hi/Lo 演算法

在上述範例中的程式碼的有趣層面是，它會使用[Hi/Lo 演算法](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/)做為金鑰產生策略。

Hi/Lo 演算法時，您需要唯一索引鍵。 為摘要，Hi-Lo 演算法會將唯一識別碼指派給資料表資料列，而不根據立即儲存在資料庫中的資料列。 這可讓您啟動發生與一般循序資料庫識別碼，因此以立即開始使用的識別碼。

Hi/Lo 演算法描述用來產生用戶端，而不是在資料庫中的安全識別碼的機制。 *安全*在此內容中，表示沒有衝突。 基於這些理由，這個演算法是有興趣：

-   它不會中斷工作單位的模式。

-   它不需要其他 Dbms 中的往返方式順序產生器。

-   它會產生為人類可讀取的識別項與不同的是使用 Guid 的技術。

EF 核心支援[HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo 方法，如上述範例所示。

### <a name="mapping-fields-instead-of-properties"></a>對應欄位而非屬性

資料行對應到欄位的 EF 核心 1.1 的功能，很可能在實體類別中，使用任何內容，而只是為了將欄位從資料表的資料行對應。 常見用途，將任何內部狀態不需要從外部實體存取的私用欄位。

EF 1.1 支援的方法將沒有相關屬性的欄位對應到資料庫中的資料行。 您可以使用單一欄位或與集合，例如清單&lt;&gt;欄位。 此點是當我們討論過模型化的網域模型類別，但您可以查看如何使用先前的程式碼中反白顯示 PropertyAccessMode.Field 組態會執行該對應之前所述。

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>使用值物件中的遮蔽屬性隱藏基礎結構層級識別碼

在 EF 核心中的陰影屬性是不存在於您的實體類別模型的屬性。 值和狀態，這些屬性會維護單純地在[ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker)基礎結構層級的類別。

DDD 觀點來看，遮蔽屬性的便利的方式來實作，隱藏陰影屬性主索引鍵識別碼的值物件。 這很重要，因為值物件不應該有身分識別 （至少，您應該不需要識別碼網域模型層中用來形成值物件時）。 重點是，為準，EF 核心最新版本，EF 核心不需要實作的物件做為值的方法[複雜型別](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx)，盡可能在 EF 6.x。 這就是為什麼您目前必須實作為實體隱藏 id （主索引鍵） 設定為陰影屬性的值物件。

您可以看到在[位址值物件](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)eShopOnContainers，在位址模型中看不到識別碼：

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

但實際上，我們需要提供 ID，以便 EF 核心是能夠保留此資料庫資料表中的資料。 我們該怎麼做的 ConfigureAddress 方法[OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs)在基礎結構層級，所以我們不會干擾 EF 基礎結構程式碼使用的網域模型類別。

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a>其他資源

-   **資料表對應**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **用於產生金鑰與 Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **支援欄位**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith。封裝中 Entity Framework Core 集合**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **遮蔽屬性**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[上一個](基礎結構-持續性-層-design.md) [下一步] (nosql-資料庫-持續性-infrastructure.md)
