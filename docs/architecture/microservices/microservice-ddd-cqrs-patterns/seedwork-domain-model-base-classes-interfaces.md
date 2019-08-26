---
title: Seedwork (網域模型的可重複使用基底類別和介面)
description: .NET 微服務：容器化 .NET 應用程式的架構 | 使用 seedwork 概念作為起點，開始實作 DDD 導向的領域模型。
ms.date: 10/08/2018
ms.openlocfilehash: a49f9e0b40ea306a846d9fb472bac388eedbfe02
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660766"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="0a084-103">Seedwork (網域模型的可重複使用基底類別和介面)</span><span class="sxs-lookup"><span data-stu-id="0a084-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="0a084-104">方案資料夾中包含了一個 *SeedWork* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a084-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="0a084-105">此資料夾包含自訂基底類別，您可以使用它們作為您領域實體和值物件的基底。</span><span class="sxs-lookup"><span data-stu-id="0a084-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="0a084-106">藉由使用這些基底類別，您的每個領域物件類別中便不會有冗餘的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a084-106">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="0a084-107">這些類別類型的資料夾名為 *SeedWork*，而非 *Framework*。</span><span class="sxs-lookup"><span data-stu-id="0a084-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="0a084-108">它之所以名為 *SeedWork*，是因為資料夾僅包含了可重複使用類別的小型子集，而無法視為架構。</span><span class="sxs-lookup"><span data-stu-id="0a084-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="0a084-109">*SeedWork* 是一個由 [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) 引入的字詞，並由 [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) 進一步推廣，但您也可以將資料夾命名為 Common、SharedKernel 或其他相似名稱。</span><span class="sxs-lookup"><span data-stu-id="0a084-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="0a084-110">圖 7-12 顯示了組成 Ordering 微服務中領域模型 seedwork 的類別。</span><span class="sxs-lookup"><span data-stu-id="0a084-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="0a084-111">它有幾個自訂的基底類別，像是 Entity、ValueObject 及 Enumeration，以及其他幾個介面。</span><span class="sxs-lookup"><span data-stu-id="0a084-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="0a084-112">這些介面 (IRepository 和 IUnitOfWork) 會通知基礎結構層需要實作的內容。</span><span class="sxs-lookup"><span data-stu-id="0a084-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="0a084-113">這些介面也會透過來自應用程式層的相依性插入使用。</span><span class="sxs-lookup"><span data-stu-id="0a084-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![SeedWork 資料夾的詳細內容包含基底類別及介面：Entity.cs、Enumeration.cs、IAggregateRoot.cs、IRepository.cs、IUnitOfWork.cs 及 ValueObject.cs](./media/image13.PNG)

<span data-ttu-id="0a084-115">**圖 7-12**。</span><span class="sxs-lookup"><span data-stu-id="0a084-115">**Figure 7-12**.</span></span> <span data-ttu-id="0a084-116">領域模型 “seedwork" 基底類別與介面的範例組</span><span class="sxs-lookup"><span data-stu-id="0a084-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="0a084-117">這是一種許多開發人員在物件之間共用的複製及貼上重複使用內容，而非正式的架構。</span><span class="sxs-lookup"><span data-stu-id="0a084-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="0a084-118">您可以在任何層或程式庫中具有 seedwork。</span><span class="sxs-lookup"><span data-stu-id="0a084-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="0a084-119">然而，若類別和介面的組合變得更大，便建議您建立單一類別庫。</span><span class="sxs-lookup"><span data-stu-id="0a084-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="0a084-120">自訂 Entity 基底類別</span><span class="sxs-lookup"><span data-stu-id="0a084-120">The custom Entity base class</span></span>

<span data-ttu-id="0a084-121">下列程式碼是 Entity 基底類別的範例，您可以在其中放置可由任何領域實體透過相同方式使用的程式碼，例如實體識別碼、[等號比較運算子](../../../csharp/language-reference/operators/equality-operators.md)、每的實體的領域事件清單等。</span><span class="sxs-lookup"><span data-stu-id="0a084-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;    
    private List<INotification> _domainEvents;
    public virtual int Id 
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public List<INotification> DomainEvents => _domainEvents;        
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://blogs.msdn.microsoft.com/ericlippert/2011/02/28/guidelines-and-rules-for-gethashcode/
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="0a084-122">先前使用每個實體領域事件清單的程式碼會在下一個聚焦於領域事件的章節中解釋。</span><span class="sxs-lookup"><span data-stu-id="0a084-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="0a084-123">領域模型層中的存放庫合約 (介面)</span><span class="sxs-lookup"><span data-stu-id="0a084-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="0a084-124">存放庫合約只是表達用於每個彙總之存放庫合約需求的 .NET 介面。</span><span class="sxs-lookup"><span data-stu-id="0a084-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="0a084-125">存放庫本身，包含 EF Core 程式碼或任何其他的基礎結構相依性和程式碼 (Linq、SQL 等) 都不可在領域模型中實作。存放庫應僅實作您在領域模型中定義的介面。</span><span class="sxs-lookup"><span data-stu-id="0a084-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="0a084-126">與這種做法 (將存放庫介面放置在領域模型層中) 有關的模式便是分離介面 (Separated Interface) 模式。</span><span class="sxs-lookup"><span data-stu-id="0a084-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="0a084-127">如同 Martin Fowler 所[解釋](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)的，「使用分離介面來在一個套件中定義介面，但在另外一個套件中實作它。</span><span class="sxs-lookup"><span data-stu-id="0a084-127">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="0a084-128">如此一來，需要相依於介面的用戶端便可以完全無須了解實作。」</span><span class="sxs-lookup"><span data-stu-id="0a084-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="0a084-129">遵循分離介面模式可讓應用程式層 (在此案例中為微服務的 Web API 專案) 相依於領域模型中定義的需求，但不會直接相依於基礎結構/永續性層。</span><span class="sxs-lookup"><span data-stu-id="0a084-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="0a084-130">此外，您可以使用相依性插入來隔離使用存放庫在基礎結構/永續層中實作的實作。</span><span class="sxs-lookup"><span data-stu-id="0a084-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="0a084-131">例如，下列使用 IOrderRepository 介面的範例定義了 OrderRepository 類別需要用來在基礎結構層實作的作業。</span><span class="sxs-lookup"><span data-stu-id="0a084-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="0a084-132">在目前的應用程式實作中，程式碼只需要將訂單新增或更新至資料庫，因為查詢已遵循簡化的 CQRS 方法進行分離。</span><span class="sxs-lookup"><span data-stu-id="0a084-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="0a084-133">其他資源</span><span class="sxs-lookup"><span data-stu-id="0a084-133">Additional resources</span></span>

- <span data-ttu-id="0a084-134">**Martin Fowler：分離的介面。**</span><span class="sxs-lookup"><span data-stu-id="0a084-134">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="0a084-135">[上一頁](net-core-microservice-domain-model.md)
>[下一頁](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="0a084-135">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>
