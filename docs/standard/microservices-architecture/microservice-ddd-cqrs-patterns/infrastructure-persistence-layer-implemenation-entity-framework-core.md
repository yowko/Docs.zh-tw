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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="93734-104">實作與 Entity Framework 的核心基礎結構保存層</span><span class="sxs-lookup"><span data-stu-id="93734-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="93734-105">當您使用 SQL Server、 Oracle 或 PostgreSQL 例如關聯式資料庫時，是建議的方法是實作保存層基礎上 Entity Framework (EF)。</span><span class="sxs-lookup"><span data-stu-id="93734-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="93734-106">EF 支援 LINQ，並提供您的模型，以及簡化的持續性進入您的資料庫中的強型別的的物件。</span><span class="sxs-lookup"><span data-stu-id="93734-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="93734-107">Entity Framework 必須有悠久的歷史，.NET Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="93734-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="93734-108">當您使用.NET Core 時，您也應該使用 Entity Framework Core Windows 或 Linux 執行.NET Core 方式相同。</span><span class="sxs-lookup"><span data-stu-id="93734-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="93734-109">EF 核心是完全重寫的 Entity Framework 中，使用較小的使用量和效能的重要增強功能實作。</span><span class="sxs-lookup"><span data-stu-id="93734-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="93734-110">Entity Framework Core 簡介</span><span class="sxs-lookup"><span data-stu-id="93734-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="93734-111">Entity Framework (EF) 核心的輕量型可擴充的並跨平台版本常見的 Entity Framework 資料存取技術。</span><span class="sxs-lookup"><span data-stu-id="93734-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="93734-112">它是 mid 2016 中引進.NET Core。</span><span class="sxs-lookup"><span data-stu-id="93734-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="93734-113">因為簡介 EF 核心已經在 Microsoft 文件中，在這裡我們只是提供該資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="93734-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="93734-114">其他資源</span><span class="sxs-lookup"><span data-stu-id="93734-114">Additional resources</span></span>

-   <span data-ttu-id="93734-115">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="93734-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="93734-116">**開始使用 ASP.NET Core 與使用 Visual Studio 的 Entity Framework Core**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="93734-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="93734-117">**DbContext 類別**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="93734-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="93734-118">**比較 EF 核心 & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="93734-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="93734-119">在 Entity Framework Core DDD 檢視方塊中的基礎結構</span><span class="sxs-lookup"><span data-stu-id="93734-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="93734-120">從 DDD 觀點來看，EF 重要功能是能夠使用 POCO 網域實體，在做 POCO 的 EF 術語中也稱為*程式碼的第一個實體*。</span><span class="sxs-lookup"><span data-stu-id="93734-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="93734-121">如果您使用 POCO 網域實體時，您的網域模型類別是持續性-無知，遵循[永續性無知之](http://deviq.com/persistence-ignorance/)和[基礎結構忽略](https://ayende.com/blog/3137/infrastructure-ignorance)原則。</span><span class="sxs-lookup"><span data-stu-id="93734-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="93734-122">每 DDD 模式，您應該封裝網域行為和規則內的實體類別本身，讓它存取任何集合時能控制非變異項目、 驗證及規則。</span><span class="sxs-lookup"><span data-stu-id="93734-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="93734-123">因此，它不是子的最好的作法是子的在 DDD 允許公用存取權集合的實體或值的物件。</span><span class="sxs-lookup"><span data-stu-id="93734-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="93734-124">相反地，您會想要公開 （expose） 可控制如何及何時可以更新您的欄位和屬性集合，方法與哪些行為以及動作時會發生這種情況發生。</span><span class="sxs-lookup"><span data-stu-id="93734-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="93734-125">在 EF 核心 1.1 中，以滿足這些需求的 DDD 您可以有純欄位在您的實體，而不是具有公用和私用 setter 的屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="93734-126">若不想使用可供存取，外部實體欄位，您就可以建立屬性或欄位，而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="93734-127">沒有需要使用私用 setter，如果您偏好徹底的方法。</span><span class="sxs-lookup"><span data-stu-id="93734-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="93734-128">類似的方式，您現在可以有唯讀集合使用的公用屬性類型為 IEnumerable&lt;T&gt;，備份的私用欄位成員集合 (例如清單&lt;&gt;) 中您依賴 EF 持續性的實體。</span><span class="sxs-lookup"><span data-stu-id="93734-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="93734-129">舊版的 Entity Framework 所需的集合屬性，以支援 ICollection&lt;T&gt;，這是任何使用父實體類別的開發人員無法新增或移除其屬性集合的項目。</span><span class="sxs-lookup"><span data-stu-id="93734-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="93734-130">該可能性是針對 DDD 中建議的模式。</span><span class="sxs-lookup"><span data-stu-id="93734-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="93734-131">您可以使用私用集合公開唯讀的 IEnumerable 物件時，如下列程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="93734-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

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

<span data-ttu-id="93734-132">請注意，OrderItems 屬性只能以唯讀方式使用清單&lt;&gt;。AsReadOnly()。</span><span class="sxs-lookup"><span data-stu-id="93734-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="93734-133">這個方法會建立私用清單的唯讀包裝函式，讓您可以針對外部更新受到保護。</span><span class="sxs-lookup"><span data-stu-id="93734-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="93734-134">它是成本更低比使用 ToList 方法，因為它沒有新的集合中，複製的所有項目相反地，它會執行包裝函式的執行個體只有一個堆積配置作業。</span><span class="sxs-lookup"><span data-stu-id="93734-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="93734-135">EF 核心可用來將網域模型對應至實體資料庫，而不會破壞網域模型。</span><span class="sxs-lookup"><span data-stu-id="93734-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="93734-136">是純 POCO.NET 程式碼，因為對應動作在保存層中實作。</span><span class="sxs-lookup"><span data-stu-id="93734-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="93734-137">在該對應的動作，您需要設定到資料庫欄位對應。</span><span class="sxs-lookup"><span data-stu-id="93734-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="93734-138">在下列範例 OnModelCreating 方法中，反白顯示的程式碼會告知 EF 核心透過其欄位存取 OrderItems 屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="93734-139">當您使用欄位而非屬性時，就如同它有一個清單保存 OrderItem 實體&lt;OrderItem&gt;屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="93734-140">不過，它會公開單一存取子 （AddOrderItem 方法），將順序中加入新項目。</span><span class="sxs-lookup"><span data-stu-id="93734-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="93734-141">如此一來，行為和資料繫結在一起，且將使用網域模型的任何應用程式程式碼一致。</span><span class="sxs-lookup"><span data-stu-id="93734-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="93734-142">Entity Framework Core 與實作自訂的儲存機制</span><span class="sxs-lookup"><span data-stu-id="93734-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="93734-143">在實作層級的儲存機制已只是具有資料持續性程式碼的工作單位 (DBContext EF 核心中) 所協調的類別時執行更新，將下列類別中所示：</span><span class="sxs-lookup"><span data-stu-id="93734-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="93734-144">請注意 IBuyerRepository 介面來自網域模型層。</span><span class="sxs-lookup"><span data-stu-id="93734-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="93734-145">不過，儲存機制實作是在持續性和基礎結構層級。</span><span class="sxs-lookup"><span data-stu-id="93734-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="93734-146">EF DbContext 是透過相依性插入建構函式。</span><span class="sxs-lookup"><span data-stu-id="93734-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="93734-147">它被共用相同 HTTP 要求範圍內，這點受惠 IoC 容器 （也可以明確設定與服務其預設存留時間 (ServiceLifetime.Scoped) 多個儲存機制之間。AddDbContext&lt;&gt;)。</span><span class="sxs-lookup"><span data-stu-id="93734-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="93734-148">（更新或與查詢的交易） 的儲存機制中實作方法</span><span class="sxs-lookup"><span data-stu-id="93734-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="93734-149">在每個儲存機制類別中，您應該讓更新其相關的彙總所包含的實體狀態的持續性方法。</span><span class="sxs-lookup"><span data-stu-id="93734-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="93734-150">請記住，沒有彙總與它相關的儲存機制之間的一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="93734-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="93734-151">請考慮彙總根實體物件可能會內嵌在其 EF 圖形內的子實體。</span><span class="sxs-lookup"><span data-stu-id="93734-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="93734-152">例如，買方也可能會有多個付款方法，為相關的子系的實體。</span><span class="sxs-lookup"><span data-stu-id="93734-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="93734-153">由於 eShopOnContainers 中順序的微服務的方法也基礎 CQS/CQRS，大多數的查詢不會實作自訂儲存機制。</span><span class="sxs-lookup"><span data-stu-id="93734-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="93734-154">開發人員可以自由建立查詢和聯結所需而且沒有一般彙總，每個彙總和 DDD 的自訂儲存機制所加諸的限制展示層。</span><span class="sxs-lookup"><span data-stu-id="93734-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="93734-155">本指南所建議的自訂儲存機制大部分都有數個更新或交易式的方法，但查詢方法必須以取得要更新的資料。</span><span class="sxs-lookup"><span data-stu-id="93734-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="93734-156">例如，BuyerRepository 儲存機制實作 FindAsync 方法，因為應用程式必須知道特定買方是否存在於之前建立新的買方的訂單相關。</span><span class="sxs-lookup"><span data-stu-id="93734-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="93734-157">不過，實際的查詢方法，以取得資料以便傳送至展示層或用戶端應用程式中實作，如使用 Dapper 彈性查詢為基礎的 CQRS 查詢中所述。</span><span class="sxs-lookup"><span data-stu-id="93734-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="93734-158">使用自訂的儲存機制，而非直接使用 EF DbContext</span><span class="sxs-lookup"><span data-stu-id="93734-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="93734-159">Entity Framework DbContext 類別為基礎的工作單位和儲存機制模式，並可直接從程式碼，例如從 ASP.NET Core MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="93734-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="93734-160">也就是方式可以建立的最簡單的程式碼，如同在 eShopOnContainers CRUD 目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="93734-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="93734-161">在您想最簡單的程式碼可能的情況下，您可以直接使用的 DbContext 類別，許多開發人員都一樣。</span><span class="sxs-lookup"><span data-stu-id="93734-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="93734-162">不過，實作自訂的儲存機制提供數個優點，實作更複雜的 microservices 或應用程式時。</span><span class="sxs-lookup"><span data-stu-id="93734-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="93734-163">工作單位和儲存機制模式被用來封裝基礎結構的持續性層級，因此它分開的應用程式和網域模型層。</span><span class="sxs-lookup"><span data-stu-id="93734-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="93734-164">實作這些模式，可以加快模擬資料庫的存取權的模擬儲存機制的使用。</span><span class="sxs-lookup"><span data-stu-id="93734-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="93734-165">圖 9-18 您所見不使用儲存機制 （直接使用 EF DbContext） 之間的差異與使用更輕鬆地模擬的儲存機制的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="93734-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="93734-166">**圖 9-18**。</span><span class="sxs-lookup"><span data-stu-id="93734-166">**Figure 9-18**.</span></span> <span data-ttu-id="93734-167">使用自訂的儲存機制，與一般 DbContext</span><span class="sxs-lookup"><span data-stu-id="93734-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="93734-168">模擬時，有多個替代項目。</span><span class="sxs-lookup"><span data-stu-id="93734-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="93734-169">您無法模擬只儲存機制，或您無法模擬整個工作單位。</span><span class="sxs-lookup"><span data-stu-id="93734-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="93734-170">通常模擬的儲存機制已足夠，和通常不需要抽象，因此模擬整個工作單位的複雜性。</span><span class="sxs-lookup"><span data-stu-id="93734-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="93734-171">稍後，當我們將重點放在應用程式層上，您會看到 ASP.NET 核心中相依性插入 」 運作方式以及它使用儲存機制時的實作方式。</span><span class="sxs-lookup"><span data-stu-id="93734-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="93734-172">簡單地說，自訂儲存機制可讓您更輕鬆地測試不會受到資料層狀態的單元測試的程式碼。</span><span class="sxs-lookup"><span data-stu-id="93734-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="93734-173">如果您執行測試，也可透過 Entity Framework 存取實際的資料庫時，它們不是單元測試而整合測試，也就是很慢。</span><span class="sxs-lookup"><span data-stu-id="93734-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="93734-174">如果您直接使用 DbContext，唯一的選擇，您必須是執行單元測試使用與可預測資料的記憶體中的 SQL Server 單元測試。</span><span class="sxs-lookup"><span data-stu-id="93734-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="93734-175">您將無法在存放庫層級相同的方式來控制模擬物件和假資料。</span><span class="sxs-lookup"><span data-stu-id="93734-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="93734-176">當然，您一律可以測試 MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="93734-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="93734-177">IoC 容器中的 EF DbContext 和 IUnitOfWork 執行個體存留期</span><span class="sxs-lookup"><span data-stu-id="93734-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="93734-178">（公開為 IUnitOfWork 物件） 的 DbContext 物件可能需要由共用相同的 HTTP 要求範圍內的多個儲存機制。</span><span class="sxs-lookup"><span data-stu-id="93734-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="93734-179">比方說，這是 true 時正在執行的作業必須處理多個彙總，或只是因為您使用多個儲存機制的執行個體。</span><span class="sxs-lookup"><span data-stu-id="93734-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="93734-180">也很重要這裡 IUnitOfWork 介面是屬於網域，而不 EF 型別。</span><span class="sxs-lookup"><span data-stu-id="93734-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="93734-181">若要這樣做，請 DbContext 物件的執行個體必須具有其服務的存留期設定為 ServiceLifetime.Scoped。</span><span class="sxs-lookup"><span data-stu-id="93734-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="93734-182">這是當註冊建立的 DbContext 來與服務的預設存留時間。AddDbContext Startup.cs 中的檔案 ASP.NET Core Web API 專案的 ConfigureServices 方法從您 IoC 容器中。</span><span class="sxs-lookup"><span data-stu-id="93734-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="93734-183">以下的程式碼可說明這點。</span><span class="sxs-lookup"><span data-stu-id="93734-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="93734-184">DbContext 具現化模式不應設定為 ServiceLifetime.Transient 或 ServiceLifetime.Singleton。</span><span class="sxs-lookup"><span data-stu-id="93734-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="93734-185">儲存機制的執行個體存留期，IoC 容器中</span><span class="sxs-lookup"><span data-stu-id="93734-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="93734-186">類似的方式，儲存機制的存留期通常應該設定為已設定領域 (InstancePerLifetimeScope Autofac 中)。</span><span class="sxs-lookup"><span data-stu-id="93734-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="93734-187">它也可能是暫時性 (InstancePerDependency Autofac 中)，但您的服務時，會在與記憶體中更有效率使用已設定領域的存留期。</span><span class="sxs-lookup"><span data-stu-id="93734-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="93734-188">請注意，使用單一存留期的儲存機制可能導致嚴重的並行存取問題時您 DbContext 設為範圍 (InstancePerLifetimeScope) 存留期 （建立的 DBContext，預設存留時間）。</span><span class="sxs-lookup"><span data-stu-id="93734-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="93734-189">其他資源</span><span class="sxs-lookup"><span data-stu-id="93734-189">Additional resources</span></span>

-   <span data-ttu-id="93734-190">**ASP.NET MVC 應用程式中實作的儲存機制和工作模式單位**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="93734-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="93734-191">**Jonathan Allen。實作策略儲存機制模式有 Entity Framework，Dapper，而且鏈結**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="93734-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="93734-192">**Cesar de la Torre：比較 ASP.NET Core IoC 容器服務存留期與 Autofac IoC 容器執行個體範圍**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="93734-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="93734-193">資料表對應</span><span class="sxs-lookup"><span data-stu-id="93734-193">Table mapping</span></span>

<span data-ttu-id="93734-194">資料表對應會識別要從查詢的資料表資料，並儲存到資料庫。</span><span class="sxs-lookup"><span data-stu-id="93734-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="93734-195">先前您已看到如何使用網域實體 （例如產品或順序網域），來產生相關的資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="93734-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="93734-196">EF 強設計的概念*慣例*。</span><span class="sxs-lookup"><span data-stu-id="93734-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="93734-197">慣例位址類似 「 將資料表的名稱是什麼？ 」</span><span class="sxs-lookup"><span data-stu-id="93734-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="93734-198">或者 「 屬性 」 的主索引鍵嗎？</span><span class="sxs-lookup"><span data-stu-id="93734-198">or “What property is the primary key?”</span></span> <span data-ttu-id="93734-199">慣例通常依據傳統的名稱 — 比方說，它是典型的主索引鍵屬性，結尾是識別碼。</span><span class="sxs-lookup"><span data-stu-id="93734-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="93734-200">依照慣例，每個實體將會設定對應至資料表，以與 DbSet 同名&lt;TEntity&gt;公開衍生內容上的實體的屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="93734-201">如果沒有 DbSet&lt;TEntity&gt;值會提供指定之實體，使用此類別名稱。</span><span class="sxs-lookup"><span data-stu-id="93734-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="93734-202">資料註解或 fluent 應用程式開發的應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="93734-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="93734-203">有許多其他的 EF 核心慣例，而且大部分是可以使用資料註解或 Fluent API，在 OnModelCreating 方法內實作變更。</span><span class="sxs-lookup"><span data-stu-id="93734-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="93734-204">資料註解必須使用的實體模型類別本身，這是從 DDD 觀點來看受到更多干擾方法。</span><span class="sxs-lookup"><span data-stu-id="93734-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="93734-205">這是因為您會使用與基礎結構資料庫相關的資料註解破壞您的模型。</span><span class="sxs-lookup"><span data-stu-id="93734-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="93734-206">相反地，Fluent API 是便利的方式來變更大部分慣例和程式資料持續性基礎結構層級中的對應，所以實體模型會清楚和低耦合從持續性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="93734-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="93734-207">關於 fluent API 和 OnModelCreating 方法</span><span class="sxs-lookup"><span data-stu-id="93734-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="93734-208">如前所述，才能變更慣例和對應，可用於 OnModelCreating 方法將 DbContext 類別。</span><span class="sxs-lookup"><span data-stu-id="93734-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="93734-209">下列範例會示範如何在這麼 eShopOnContainers 中順序的微服務中。</span><span class="sxs-lookup"><span data-stu-id="93734-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

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

<span data-ttu-id="93734-210">您可以設定在相同的 OnModelCreating 方法中，所有 Fluent API 對應，但建議您最好要分割該程式碼，並有多個 submethods，其中每個實體，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="93734-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="93734-211">針對極大的模型，它甚至可以是建議您在有不同的來源檔案 （靜態類別） 設定不同的實體類型。</span><span class="sxs-lookup"><span data-stu-id="93734-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="93734-212">此範例中的程式碼會明確。</span><span class="sxs-lookup"><span data-stu-id="93734-212">The code in the example is explicit.</span></span> <span data-ttu-id="93734-213">不過，EF 核心慣例大部分的自動執行，因此您需要寫入來達成相同的實際程式碼會小很多。</span><span class="sxs-lookup"><span data-stu-id="93734-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="93734-214">在 EF 核心 Hi/Lo 演算法</span><span class="sxs-lookup"><span data-stu-id="93734-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="93734-215">在上述範例中的程式碼的有趣層面是，它會使用[Hi/Lo 演算法](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/)做為金鑰產生策略。</span><span class="sxs-lookup"><span data-stu-id="93734-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="93734-216">Hi/Lo 演算法時，您需要唯一索引鍵。</span><span class="sxs-lookup"><span data-stu-id="93734-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="93734-217">為摘要，Hi-Lo 演算法會將唯一識別碼指派給資料表資料列，而不根據立即儲存在資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="93734-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="93734-218">這可讓您啟動發生與一般循序資料庫識別碼，因此以立即開始使用的識別碼。</span><span class="sxs-lookup"><span data-stu-id="93734-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="93734-219">Hi/Lo 演算法描述用來產生用戶端，而不是在資料庫中的安全識別碼的機制。</span><span class="sxs-lookup"><span data-stu-id="93734-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="93734-220">*安全*在此內容中，表示沒有衝突。</span><span class="sxs-lookup"><span data-stu-id="93734-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="93734-221">基於這些理由，這個演算法是有興趣：</span><span class="sxs-lookup"><span data-stu-id="93734-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="93734-222">它不會中斷工作單位的模式。</span><span class="sxs-lookup"><span data-stu-id="93734-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="93734-223">它不需要其他 Dbms 中的往返方式順序產生器。</span><span class="sxs-lookup"><span data-stu-id="93734-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="93734-224">它會產生為人類可讀取的識別項與不同的是使用 Guid 的技術。</span><span class="sxs-lookup"><span data-stu-id="93734-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="93734-225">EF 核心支援[HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo 方法，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="93734-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="93734-226">對應欄位而非屬性</span><span class="sxs-lookup"><span data-stu-id="93734-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="93734-227">資料行對應到欄位的 EF 核心 1.1 的功能，很可能在實體類別中，使用任何內容，而只是為了將欄位從資料表的資料行對應。</span><span class="sxs-lookup"><span data-stu-id="93734-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="93734-228">常見用途，將任何內部狀態不需要從外部實體存取的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="93734-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="93734-229">EF 1.1 支援的方法將沒有相關屬性的欄位對應到資料庫中的資料行。</span><span class="sxs-lookup"><span data-stu-id="93734-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="93734-230">您可以使用單一欄位或與集合，例如清單&lt;&gt;欄位。</span><span class="sxs-lookup"><span data-stu-id="93734-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="93734-231">此點是當我們討論過模型化的網域模型類別，但您可以查看如何使用先前的程式碼中反白顯示 PropertyAccessMode.Field 組態會執行該對應之前所述。</span><span class="sxs-lookup"><span data-stu-id="93734-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="93734-232">使用值物件中的遮蔽屬性隱藏基礎結構層級識別碼</span><span class="sxs-lookup"><span data-stu-id="93734-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="93734-233">在 EF 核心中的陰影屬性是不存在於您的實體類別模型的屬性。</span><span class="sxs-lookup"><span data-stu-id="93734-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="93734-234">值和狀態，這些屬性會維護單純地在[ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker)基礎結構層級的類別。</span><span class="sxs-lookup"><span data-stu-id="93734-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="93734-235">DDD 觀點來看，遮蔽屬性的便利的方式來實作，隱藏陰影屬性主索引鍵識別碼的值物件。</span><span class="sxs-lookup"><span data-stu-id="93734-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="93734-236">這很重要，因為值物件不應該有身分識別 （至少，您應該不需要識別碼網域模型層中用來形成值物件時）。</span><span class="sxs-lookup"><span data-stu-id="93734-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="93734-237">重點是，為準，EF 核心最新版本，EF 核心不需要實作的物件做為值的方法[複雜型別](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx)，盡可能在 EF 6.x。</span><span class="sxs-lookup"><span data-stu-id="93734-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="93734-238">這就是為什麼您目前必須實作為實體隱藏 id （主索引鍵） 設定為陰影屬性的值物件。</span><span class="sxs-lookup"><span data-stu-id="93734-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="93734-239">您可以看到在[位址值物件](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)eShopOnContainers，在位址模型中看不到識別碼：</span><span class="sxs-lookup"><span data-stu-id="93734-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

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

<span data-ttu-id="93734-240">但實際上，我們需要提供 ID，以便 EF 核心是能夠保留此資料庫資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="93734-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="93734-241">我們該怎麼做的 ConfigureAddress 方法[OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs)在基礎結構層級，所以我們不會干擾 EF 基礎結構程式碼使用的網域模型類別。</span><span class="sxs-lookup"><span data-stu-id="93734-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="93734-242">其他資源</span><span class="sxs-lookup"><span data-stu-id="93734-242">Additional resources</span></span>

-   <span data-ttu-id="93734-243">**資料表對應**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="93734-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="93734-244">**用於產生金鑰與 Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="93734-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="93734-245">**支援欄位**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="93734-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="93734-246">**Steve Smith。封裝中 Entity Framework Core 集合**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="93734-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="93734-247">**遮蔽屬性**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="93734-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="93734-248">[上一個](基礎結構-持續性-層-design.md) [下一步] (nosql-資料庫-持續性-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="93734-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
