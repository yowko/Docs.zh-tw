---
title: 使用 Entity Framework Core 實作基礎結構持續層
description: .NET 微服務：容器化 .NET 應用程式的架構 | 使用 Entity Framework Core 探索基礎結構持續層的實作詳細資料。
ms.date: 10/08/2018
ms.openlocfilehash: c6b0a022dfecb24c479a0fd3c84dbde719a390a8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639530"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="4c507-103">使用 Entity Framework Core 實作基礎結構持續層</span><span class="sxs-lookup"><span data-stu-id="4c507-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="4c507-104">當您使用例如 SQL Server、Oracle 或 PostgreSQL 等關聯式資料庫時，建議的方法是根據 Entity Framework (EF) 來實作持續層。</span><span class="sxs-lookup"><span data-stu-id="4c507-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="4c507-105">EF 支援 LINQ，並為您的模型提供強型別的物件，以及資料庫的簡化持續性。</span><span class="sxs-lookup"><span data-stu-id="4c507-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="4c507-106">Entity Framework 是 .NET Framework 的一部分，有著悠久的歷史。</span><span class="sxs-lookup"><span data-stu-id="4c507-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="4c507-107">當您使用 .NET Core 時，您也應該使用 Entity Framework Core，它在 Windows 或 Linux 上以與 .NET Core 相同的方式執行。</span><span class="sxs-lookup"><span data-stu-id="4c507-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="4c507-108">EF Core 是完全重寫的 Entity Framework，它的實作具有小上許多的使用量和效能的重要改善。</span><span class="sxs-lookup"><span data-stu-id="4c507-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="4c507-109">Entity Framework Core 簡介</span><span class="sxs-lookup"><span data-stu-id="4c507-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="4c507-110">Entity Framework (EF) Core 是常見 Entity Framework 資料存取技術的輕量型、可擴充且跨平台版本。</span><span class="sxs-lookup"><span data-stu-id="4c507-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="4c507-111">它是在 2016 年中在 .NET Core 引進。</span><span class="sxs-lookup"><span data-stu-id="4c507-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="4c507-112">因為 Microsoft 文件中已有 EF Core 的簡介，在這裡我們只是提供該資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="4c507-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4c507-113">其他資源</span><span class="sxs-lookup"><span data-stu-id="4c507-113">Additional resources</span></span>

- <span data-ttu-id="4c507-114">**Entity Framework Core** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-114">**Entity Framework Core** \\</span></span>
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="4c507-115">**使用 Visual Studio 的 ASP.NET Core 與 Entity Framework Core 使用者入門** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="4c507-116">**DbContext 類別** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-116">**DbContext Class** \\</span></span>
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="4c507-117">**比較 EF Core 與 EF6.x** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-117">**Compare EF Core & EF6.x** \\</span></span>
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="4c507-118">DDD 觀點的 Entity Framework Core 基礎結構</span><span class="sxs-lookup"><span data-stu-id="4c507-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="4c507-119">從 DDD 觀點來看，EF 的一項重要功能是能夠使用 POCO 網域實體，在 EF 術語中也稱為 POCO「程式碼優先的實體」。</span><span class="sxs-lookup"><span data-stu-id="4c507-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="4c507-120">如果您使用 POCO 網域實體，您的網域模型類別會是持續性無知 (persistence-ignorant)，並遵循 [Persistence Ignorance](https://deviq.com/persistence-ignorance/) (持續性無知) 和 [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) (基礎結構無知) 準則。</span><span class="sxs-lookup"><span data-stu-id="4c507-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="4c507-121">根據 DDD 模式，您應該將網域行為和規則封裝在實體類別本身內，讓它可以在存取任何集合時控制非變異項目、驗證及規則。</span><span class="sxs-lookup"><span data-stu-id="4c507-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="4c507-122">因此，在 DDD 中允許對子系實體或值物件之集合的公用存取權並不是一項好的做法。</span><span class="sxs-lookup"><span data-stu-id="4c507-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="4c507-123">相反地，您會想要公開可控制欄位和屬性集合更新方式與時機，以及發生這種情況時應發生哪些行為和動作的方法。</span><span class="sxs-lookup"><span data-stu-id="4c507-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="4c507-124">從 EF Core 1.1 開始，要滿足那些 DDD 需求，您可以在實體中使用純欄位，而不要使用公用屬性。</span><span class="sxs-lookup"><span data-stu-id="4c507-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="4c507-125">若不想讓實體欄位可供外部存取，只需建立屬性 (attribute) 或欄位，而不是屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="4c507-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="4c507-126">您也可以使用私用屬性設定程式。</span><span class="sxs-lookup"><span data-stu-id="4c507-126">You can also use private property setters.</span></span>

<span data-ttu-id="4c507-127">同樣地，您現在可以使用類型為 `IReadOnlyCollection<T>` 的公用屬性唯讀地存取集合，其背後的支持是依賴 EF 以獲得持續性的實體中，集合的私用欄位成員 (例如 `List<T>`)。</span><span class="sxs-lookup"><span data-stu-id="4c507-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="4c507-128">舊版的 Entity Framework 需要屬性集合支援 `ICollection<T>`，這表示任何使用父實體類別的開發人員都可以透過屬性集合來新增或移除項目。</span><span class="sxs-lookup"><span data-stu-id="4c507-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="4c507-129">該項可能性違反了 DDD 中的建議模式。</span><span class="sxs-lookup"><span data-stu-id="4c507-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="4c507-130">您可以使用私用集合，同時公開唯讀 `IReadOnlyCollection<T>` 物件，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="4c507-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

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

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="4c507-131">請注意，`OrderItems` 屬性只可以使用 `IReadOnlyCollection<OrderItem>` 以唯讀方式存取。</span><span class="sxs-lookup"><span data-stu-id="4c507-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="4c507-132">此類型為唯讀，因此它會受到保護，可避免定期的外部更新。</span><span class="sxs-lookup"><span data-stu-id="4c507-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="4c507-133">EF Core 可用來將網域模型對應至實體資料庫，而不含「破壞」網域模型。</span><span class="sxs-lookup"><span data-stu-id="4c507-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="4c507-134">它是純粹的 POCO.NET 程式碼，因為對應動作在持續層中實作。</span><span class="sxs-lookup"><span data-stu-id="4c507-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="4c507-135">在該對應動作中，您需要設定欄位到資料庫的對應。</span><span class="sxs-lookup"><span data-stu-id="4c507-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="4c507-136">在下列來自 `OrderingContext` 和 `OrderEntityTypeConfiguration` 類別的 `OnModelCreating` 方法範例中，呼叫 `SetPropertyAccessMode` 通知 EF Core 透過其欄位存取 `OrderItems` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4c507-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="4c507-137">當您使用欄位而不使用屬性時，會保存 `OrderItem` 實體，就好像它有 `List<OrderItem>` 屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="4c507-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="4c507-138">不過，它會公開單一存取子，亦即 `AddOrderItem` 方法，將新的項目新增至訂單中。</span><span class="sxs-lookup"><span data-stu-id="4c507-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="4c507-139">因此，行為和資料會繫結在一起，且將在使用網域模型的任何應用程式程式碼中都一致。</span><span class="sxs-lookup"><span data-stu-id="4c507-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="4c507-140">使用 Entity Framework Core 實作自訂存放庫</span><span class="sxs-lookup"><span data-stu-id="4c507-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="4c507-141">在實作層級，存放庫只是具有資料持續性程式碼的類別，在執行更新時會由工作單位 (EF Core 中的 DBContext) 所協調，如下列類別中所示：</span><span class="sxs-lookup"><span data-stu-id="4c507-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="4c507-142">請注意，IBuyerRepository 介面以合約的方式來自網域模型層。</span><span class="sxs-lookup"><span data-stu-id="4c507-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="4c507-143">不過，存放庫實作是在持續層和基礎結構層進行。</span><span class="sxs-lookup"><span data-stu-id="4c507-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="4c507-144">EF DbContext 是透過相依性插入而通過建構函式。</span><span class="sxs-lookup"><span data-stu-id="4c507-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="4c507-145">它會在相同 HTTP 要求範圍內的多個存放庫之間共用，這點受惠於 IoC 容器 (也可以明確使用 `services.AddDbContext<>` 設定) 中的預設存留期 (`ServiceLifetime.Scoped`)。</span><span class="sxs-lookup"><span data-stu-id="4c507-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="4c507-146">要在存放庫實作的方法 (更新或交易與查詢)</span><span class="sxs-lookup"><span data-stu-id="4c507-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="4c507-147">在每個存放庫類別中，您應該放置更新其相關彙總所包含之實體狀態的持續性方法。</span><span class="sxs-lookup"><span data-stu-id="4c507-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="4c507-148">請記住，彙總與它相關存放庫之間有一對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4c507-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="4c507-149">請考慮彙總根實體物件在其 EF 圖形內可能會有內嵌的子實體。</span><span class="sxs-lookup"><span data-stu-id="4c507-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="4c507-150">例如，買方可能會有多個付款方法，作為相關的子實體。</span><span class="sxs-lookup"><span data-stu-id="4c507-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="4c507-151">由於 eShopOnContainers 中排序微服務的方法也是基於 CQS/CQRS，大多數的查詢不會在自訂存放庫中實作。</span><span class="sxs-lookup"><span data-stu-id="4c507-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="4c507-152">開發人員可以自由地為展示層建立所需的查詢和聯結，而且一般而言沒有彙總、關於彙總的自訂存放庫以及 DDD 等所加諸的限制。</span><span class="sxs-lookup"><span data-stu-id="4c507-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="4c507-153">本指南所建議的大部分自訂存放庫都有數個更新或交易式的方法，但只有查詢方法必須取得資料以便更新。</span><span class="sxs-lookup"><span data-stu-id="4c507-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="4c507-154">例如，BuyerRepository 存放庫會實作 FindAsync 方法，因為應用程式必須知道特定買方是否存在，然後才能建立與訂單相關的新買方。</span><span class="sxs-lookup"><span data-stu-id="4c507-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="4c507-155">不過，實際取得資料以便傳送至展示層或用戶端應用程式的查詢方法，會如所述地在根據使用 Dapper 之彈性查詢的 CQRS 查詢中實作。</span><span class="sxs-lookup"><span data-stu-id="4c507-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="4c507-156">使用自訂存放庫與直接使用 EF DbContext</span><span class="sxs-lookup"><span data-stu-id="4c507-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="4c507-157">Entity Framework DbContext 類別是根據工作單位和存放庫模式，並可直接從程式碼使用，例如從 ASP.NET Core MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="4c507-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="4c507-158">那就是您可以建立最簡單程式碼的方式，如同在 eShopOnContainers 中的 CRUD 目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="4c507-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="4c507-159">當您想要盡可能簡單的程式碼時，可以直接使用 DbContext 類別，有許多開發人員都這麼做。</span><span class="sxs-lookup"><span data-stu-id="4c507-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="4c507-160">不過，實作自訂存放庫在實作更複雜的微服務或應用程式時提供數個優點。</span><span class="sxs-lookup"><span data-stu-id="4c507-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="4c507-161">工作單位和存放庫模式是要用來封裝基礎結構持續層，因此它會與應用程式和網域模型層分開。</span><span class="sxs-lookup"><span data-stu-id="4c507-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="4c507-162">實作這些模式，可以方便使用模擬資料庫存取權的模擬存放庫。</span><span class="sxs-lookup"><span data-stu-id="4c507-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="4c507-163">在圖 7-18 中，您可以看到不使用存放庫 (直接使用 EF DbContext)，與使用存放庫來簡單模擬存放庫，這二種方式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="4c507-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![比較使用自訂存放庫與一般 DbContext：自訂存放庫會新增一個抽象層，可模擬存放庫用以簡化測試。](./media/image19.png)

<span data-ttu-id="4c507-165">**圖 7-18**。</span><span class="sxs-lookup"><span data-stu-id="4c507-165">**Figure 7-18**.</span></span> <span data-ttu-id="4c507-166">使用自訂存放庫與一般 DbContext</span><span class="sxs-lookup"><span data-stu-id="4c507-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="4c507-167">在模擬時有多種替代方式。</span><span class="sxs-lookup"><span data-stu-id="4c507-167">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="4c507-168">您可以只模擬存放庫，或是模擬整個工作單位。</span><span class="sxs-lookup"><span data-stu-id="4c507-168">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="4c507-169">通常只模擬存放庫便已足夠，通常不需要抽象與模擬整個工作單位的複雜性。</span><span class="sxs-lookup"><span data-stu-id="4c507-169">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="4c507-170">稍後，當我們將重點放在應用程式層上，您會看到相依性插入在 ASP.NET Core 中的運作方式，以及在使用存放庫時的實作方式。</span><span class="sxs-lookup"><span data-stu-id="4c507-170">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="4c507-171">簡單地說，自訂存放庫可讓您更輕鬆地使用不受資料層狀態影響的單元測試來測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c507-171">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="4c507-172">如果您執行的測試也會透過 Entity Framework 存取實際資料庫，它們便不是單元測試而是整合測試，速度會慢上許多。</span><span class="sxs-lookup"><span data-stu-id="4c507-172">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="4c507-173">如果直接使用 DbContext，您可能必須模擬它，或使用記憶體內部的 SQL Server 和單元測試的可預測資料，來執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="4c507-173">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="4c507-174">但是模擬 DbContext 或控制假資料，所需工作量比存放庫層級的模擬還大。</span><span class="sxs-lookup"><span data-stu-id="4c507-174">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="4c507-175">當然，您一律可以測試 MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="4c507-175">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="4c507-176">IoC 容器中的 EF DbContext 和 IUnitOfWork 執行個體存留期</span><span class="sxs-lookup"><span data-stu-id="4c507-176">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="4c507-177">`DbContext` 物件 (公開為 `IUnitOfWork` 物件) 應在相同 HTTP 要求範圍內的多個存放庫之間共用。</span><span class="sxs-lookup"><span data-stu-id="4c507-177">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="4c507-178">比方說，當正在執行的作業必須處理多個彙總時，或是因為您正在使用多個存放庫執行個體時，便是如此。</span><span class="sxs-lookup"><span data-stu-id="4c507-178">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="4c507-179">還有一點也很重要，`IUnitOfWork` 介面是網域層的一部分，不是 EF Core 類型。</span><span class="sxs-lookup"><span data-stu-id="4c507-179">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="4c507-180">為了這樣做，`DbContext` 物件的執行個體必須將其服務存留期設定為 ServiceLifetime.Scoped。</span><span class="sxs-lookup"><span data-stu-id="4c507-180">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="4c507-181">這是在您的 ASP.NET Core Web API 專案中，從 `Startup.cs` 檔案的 ConfigureServices 方法，在 IoC 容器中向 `services.AddDbContext` 登錄 `DbContext` 時的預設存留期。</span><span class="sxs-lookup"><span data-stu-id="4c507-181">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="4c507-182">以下的程式碼可說明這點。</span><span class="sxs-lookup"><span data-stu-id="4c507-182">The following code illustrates this.</span></span>

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
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="4c507-183">DbContext 具現化模式不應該設定為 ServiceLifetime.Transient 或 ServiceLifetime.Singleton。</span><span class="sxs-lookup"><span data-stu-id="4c507-183">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="4c507-184">IoC 容器中的存放庫執行個體存留期</span><span class="sxs-lookup"><span data-stu-id="4c507-184">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="4c507-185">同樣地，存放庫的存留期通常應該設定為已設定範圍 (Autofac 中的 InstancePerLifetimeScope)。</span><span class="sxs-lookup"><span data-stu-id="4c507-185">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="4c507-186">它也可能是暫時性 (Autofac 中的 InstancePerDependency)，但您的服務在使用已設定範圍的存留期時，在記憶體方面會更有效率。</span><span class="sxs-lookup"><span data-stu-id="4c507-186">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="4c507-187">請注意，在您的 DbContext 設定為已設定範圍的 (InstancePerLifetimeScope) 存留期時，存放庫使用單一存留期可能導致嚴重的並行存取問題 (DBContext 的預設存留期)。</span><span class="sxs-lookup"><span data-stu-id="4c507-187">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4c507-188">其他資源</span><span class="sxs-lookup"><span data-stu-id="4c507-188">Additional resources</span></span>

- <span data-ttu-id="4c507-189">**在 ASP.NET MVC 應用程式中實作存放庫與工作單位模式** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-189">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** \\</span></span>
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="4c507-190">**Jonathan Allen.使用 Entity Framework、Dapper 及 Chain 實作存放庫模式策略** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-190">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** \\</span></span>
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="4c507-191">**Cesar de la Torre：比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-191">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** \\</span></span>
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="4c507-192">資料表對應</span><span class="sxs-lookup"><span data-stu-id="4c507-192">Table mapping</span></span>

<span data-ttu-id="4c507-193">資料表對應會識別要從中查詢的資料表資料，並儲存到資料庫。</span><span class="sxs-lookup"><span data-stu-id="4c507-193">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="4c507-194">先前您已看到如何使用網域實體 (例如產品或訂單網域) 來產生相關的資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="4c507-194">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="4c507-195">EF 的設計高度圍繞著「慣例」的概念。</span><span class="sxs-lookup"><span data-stu-id="4c507-195">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="4c507-196">慣例處理的問題例如「資料表的名稱是什麼？」</span><span class="sxs-lookup"><span data-stu-id="4c507-196">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="4c507-197">或「主索引鍵是哪個屬性？」</span><span class="sxs-lookup"><span data-stu-id="4c507-197">or “What property is the primary key?”</span></span> <span data-ttu-id="4c507-198">慣例通常依據傳統的名稱 — 例如，主索引鍵通常是以 Id 為結尾的屬性。</span><span class="sxs-lookup"><span data-stu-id="4c507-198">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="4c507-199">依照慣例，每個實體都會設定成對應至與 `DbSet<TEntity>` 屬性同名的資料表，該屬性會在衍生內容上公開實體。</span><span class="sxs-lookup"><span data-stu-id="4c507-199">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="4c507-200">如不為指定的實體提供 `DbSet<TEntity>` 值，即使用類別名稱。</span><span class="sxs-lookup"><span data-stu-id="4c507-200">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="4c507-201">資料註解與 Fluent API</span><span class="sxs-lookup"><span data-stu-id="4c507-201">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="4c507-202">有許多其他的 EF Core 慣例，而且大部分可以使用資料註解或 Fluent API 來變更 (在 OnModelCreating 方法內實作)。</span><span class="sxs-lookup"><span data-stu-id="4c507-202">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="4c507-203">資料註解必須用於實體模型類別本身，這從 DDD 觀點來看是較多干擾的方法。</span><span class="sxs-lookup"><span data-stu-id="4c507-203">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="4c507-204">這是因為您會使用與基礎結構資料庫相關的資料註解破壞您的模型。</span><span class="sxs-lookup"><span data-stu-id="4c507-204">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="4c507-205">在另一方面，Fluent API 能夠方便地變更資料持續性基礎結構層內的大部分慣例和對應，所以實體模型會很清楚且與持續性基礎結構分開。</span><span class="sxs-lookup"><span data-stu-id="4c507-205">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="4c507-206">Fluent API 和 OnModelCreating 方法</span><span class="sxs-lookup"><span data-stu-id="4c507-206">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="4c507-207">如前所述，為了變更慣例和對應，您可以在 DbContext 類別中使用 OnModelCreating 方法。</span><span class="sxs-lookup"><span data-stu-id="4c507-207">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="4c507-208">eShopOnContainers 中的排序微服務，會視需要實作明確的對應和設定，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4c507-208">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="4c507-209">您可以在相同的 OnModelCreating 方法中設定所有 Fluent API 對應，但建議您最好分割該程式碼，並有多個設定類別，每個實體一個組態類別，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c507-209">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="4c507-210">特別是針對極大的模型，建議您最好有個別的組態類別來設定不同的實體類型。</span><span class="sxs-lookup"><span data-stu-id="4c507-210">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="4c507-211">範例中的程式碼顯示一些明確宣告和對應。</span><span class="sxs-lookup"><span data-stu-id="4c507-211">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="4c507-212">不過，EF Core 慣例會自動執行許多對應，因此在您的案例中需要的實際程式碼可能會較小。</span><span class="sxs-lookup"><span data-stu-id="4c507-212">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="4c507-213">EF Core 中的 Hi/Lo 演算法</span><span class="sxs-lookup"><span data-stu-id="4c507-213">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="4c507-214">上述範例中的程式碼有一個有趣的層面是，它會使用[Hi/Lo 演算法](https://vladmihalcea.com/the-hilo-algorithm/)作為金鑰產生策略。</span><span class="sxs-lookup"><span data-stu-id="4c507-214">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="4c507-215">當您需要唯一索引鍵才能認可變更時，Hi/Lo 演算法十分有用。</span><span class="sxs-lookup"><span data-stu-id="4c507-215">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="4c507-216">總而言之，Hi-Lo 演算法會將唯一識別碼指派給資料表資料列，而不依賴將資料列立即儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="4c507-216">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="4c507-217">這可讓您立即開始使用識別碼，如同一般循序資料庫識別碼那樣。</span><span class="sxs-lookup"><span data-stu-id="4c507-217">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="4c507-218">Hi/Lo 演算法描述從相關的料庫序列取得一批唯一識別碼的機制。</span><span class="sxs-lookup"><span data-stu-id="4c507-218">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="4c507-219">這些識別碼沒有使用的安全顧慮，因為資料庫可保證唯一性，所以使用者之間不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="4c507-219">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="4c507-220">基於這些理由，這個演算法是有趣的：</span><span class="sxs-lookup"><span data-stu-id="4c507-220">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="4c507-221">它不會中斷工作單位模式。</span><span class="sxs-lookup"><span data-stu-id="4c507-221">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="4c507-222">它會分批取得序列識別碼，減少對資料庫的反覆存取。</span><span class="sxs-lookup"><span data-stu-id="4c507-222">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="4c507-223">它會產生人類可閱讀的識別碼，而不像使用 GUID 的技術。</span><span class="sxs-lookup"><span data-stu-id="4c507-223">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="4c507-224">EF Core 以 ForSqlServerUseSequenceHiLo 方法支援 [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm)，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="4c507-224">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="4c507-225">對應欄位，而不是對應屬性</span><span class="sxs-lookup"><span data-stu-id="4c507-225">Map fields instead of properties</span></span>

<span data-ttu-id="4c507-226">利用此功能 (從 EF Core 1.1 開始提供)，您可以直接將資料行對應至欄位。</span><span class="sxs-lookup"><span data-stu-id="4c507-226">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="4c507-227">您可以不在實體類別中使用屬性，而只是將資料行從資料表對應至欄位。</span><span class="sxs-lookup"><span data-stu-id="4c507-227">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="4c507-228">常見的用途是不需要從實體外部存取之任何內部狀態的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="4c507-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="4c507-229">您可以使用單一欄位或集合 (例如 `List<>` 欄位) 來這麼做。</span><span class="sxs-lookup"><span data-stu-id="4c507-229">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="4c507-230">當我們稍早討論模型化網域模型類別時已提到此點，但在這裡您可以藉由先前程式碼中反白顯示的 `PropertyAccessMode.Field`　組態，看到該對應的執行方式。</span><span class="sxs-lookup"><span data-stu-id="4c507-230">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="4c507-231">使用隱藏在基礎結構層之 EF Core 的陰影屬性</span><span class="sxs-lookup"><span data-stu-id="4c507-231">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="4c507-232">在 EF Core 中，陰影屬性是不存在於您實體類別模型的屬性。</span><span class="sxs-lookup"><span data-stu-id="4c507-232">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="4c507-233">這些屬性的值和狀態會單純地在基礎結構層的 [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) 類別中維護。</span><span class="sxs-lookup"><span data-stu-id="4c507-233">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="4c507-234">實作查詢規格模式</span><span class="sxs-lookup"><span data-stu-id="4c507-234">Implement the Query Specification pattern</span></span>

<span data-ttu-id="4c507-235">如稍早在設計一節中所介紹，查詢規格模式是網域導向的設計模式，設計成您可以放置查詢定義以及選擇性排序和分頁邏輯的位置。</span><span class="sxs-lookup"><span data-stu-id="4c507-235">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="4c507-236">查詢規格模式會定義物件中的查詢。</span><span class="sxs-lookup"><span data-stu-id="4c507-236">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="4c507-237">例如，若要封裝搜尋一些產品的分頁查詢，您可以建立 PagedProduct 規格來接受必要的輸入參數 (pageNumber、pageSize、filter 等)。</span><span class="sxs-lookup"><span data-stu-id="4c507-237">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="4c507-238">然後，在任何存放庫方法中 (通常是 List() 多載)，它會接受 IQuerySpecification，並根據該規格執行預期的查詢。</span><span class="sxs-lookup"><span data-stu-id="4c507-238">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="4c507-239">泛型規格介面的一個範例是來自 [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) 的下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="4c507-239">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="4c507-240">然後，泛型規格基底類別的實作如下所示。</span><span class="sxs-lookup"><span data-stu-id="4c507-240">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="4c507-241">下列規格會載入單一購物籃實體，該實體會獲得購物籃識別碼或購物籃所屬買方的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4c507-241">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="4c507-242">它會[立即載入](https://docs.microsoft.com/ef/core/querying/related-data)購物籃的項目集合。</span><span class="sxs-lookup"><span data-stu-id="4c507-242">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="4c507-243">最後，您可以在下面看到泛型 EF 存放庫如何使用這類的規格來篩選與立即載入與指定實體類型 T 相關的資料。</span><span class="sxs-lookup"><span data-stu-id="4c507-243">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="4c507-244">除了封裝篩選邏輯，規格還可以指定要傳回的資料形式，包括要填入的屬性。</span><span class="sxs-lookup"><span data-stu-id="4c507-244">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="4c507-245">雖然我們不建議從存放庫傳回 IQueryable，但在存放庫中使用它們建立一組結果完全沒有問題。</span><span class="sxs-lookup"><span data-stu-id="4c507-245">Although we don’t recommend to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="4c507-246">您可以在上述的 List 方法中看到使用此方式，它使用中繼 IQueryable 運算式來建置查詢的包含清單，然後才執行查詢，在最後一行則為規格的準則。</span><span class="sxs-lookup"><span data-stu-id="4c507-246">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4c507-247">其他資源</span><span class="sxs-lookup"><span data-stu-id="4c507-247">Additional resources</span></span>

- <span data-ttu-id="4c507-248">**資料表對應** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-248">**Table Mapping** \\</span></span>
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="4c507-249">**使用 HiLo 配合 Entity Framework Core 產生金鑰** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-249">**Use HiLo to generate keys with Entity Framework Core** \\</span></span>
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="4c507-250">**支援欄位** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-250">**Backing Fields** \\</span></span>
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="4c507-251">**Steve Smith.Entity Framework Core 中的封裝式集合** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-251">**Steve Smith. Encapsulated Collections in Entity Framework Core** \\</span></span>
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="4c507-252">**陰影屬性** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-252">**Shadow Properties** \\</span></span>
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="4c507-253">**規格模式** \\</span><span class="sxs-lookup"><span data-stu-id="4c507-253">**The Specification pattern** \\</span></span>
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="4c507-254">[上一頁](infrastructure-persistence-layer-design.md)
> [下一頁](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="4c507-254">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
