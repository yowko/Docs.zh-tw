---
title: "Seedwork （可重複使用的基底類別和介面為您的網域模型）"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Seedwork （可重複使用的基底類別和介面為您的網域模型）"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="8a422-104">Seedwork （可重複使用的基底類別和介面為您的網域模型）</span><span class="sxs-lookup"><span data-stu-id="8a422-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="8a422-105">在方案資料夾包含*SeedWork*資料夾。</span><span class="sxs-lookup"><span data-stu-id="8a422-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="8a422-106">*SeedWork*資料夾包含自訂的基底類別，您可以使用做為基底網域實體與值物件。</span><span class="sxs-lookup"><span data-stu-id="8a422-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="8a422-107">使用這些基底類別，因此每個網域的物件類別中沒有多餘的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a422-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="8a422-108">這些類型的類別資料夾稱為*SeedWork*並不是類似*Framework*。</span><span class="sxs-lookup"><span data-stu-id="8a422-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="8a422-109">它會呼叫*SeedWork*因為資料夾包含只無法真正視為一種架構可重複使用類別的一小部分。</span><span class="sxs-lookup"><span data-stu-id="8a422-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="8a422-110">*Seedwork*詞彙所引入[Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826)和由 popularized [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html)但您也可以命名為該資料夾共同且 SharedKernel，或類似。</span><span class="sxs-lookup"><span data-stu-id="8a422-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="8a422-111">圖 9-12 顯示形成的網域模型 seedwork 順序的微服務中的類別。</span><span class="sxs-lookup"><span data-stu-id="8a422-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="8a422-112">它有幾個自訂的基底類別，例如實體、 ValueObject 和列舉型別，再加上一些介面。</span><span class="sxs-lookup"><span data-stu-id="8a422-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="8a422-113">這些介面 （IRepository 和 IUnitOfWork） 通知基礎結構層級必須實作的項目。</span><span class="sxs-lookup"><span data-stu-id="8a422-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="8a422-114">這些介面也會從應用程式層使用透過相依性插入。</span><span class="sxs-lookup"><span data-stu-id="8a422-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="8a422-115">**圖 9-12**。</span><span class="sxs-lookup"><span data-stu-id="8a422-115">**Figure 9-12**.</span></span> <span data-ttu-id="8a422-116">範例設定的網域模型 」 seedwork 「 基底類別和介面</span><span class="sxs-lookup"><span data-stu-id="8a422-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="8a422-117">這是許多開發人員共用專案，不是型式架構之間的複製和貼上重複使用的類型。</span><span class="sxs-lookup"><span data-stu-id="8a422-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="8a422-118">您可以讓 seedworks 任何圖層或程式庫中。</span><span class="sxs-lookup"><span data-stu-id="8a422-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="8a422-119">不過，如果一組類別和介面取得夠大，您可能想要建立單一類別庫。</span><span class="sxs-lookup"><span data-stu-id="8a422-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="8a422-120">自訂實體基底類別</span><span class="sxs-lookup"><span data-stu-id="8a422-120">The custom Entity base class</span></span>

<span data-ttu-id="8a422-121">下列程式碼是實體基底類別的範例程式碼，可以由任何網域的實體，實體識別碼，例如使用相同的方式放置位置[等號比較運算子](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx)等等。</span><span class="sxs-lookup"><span data-stu-id="8a422-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

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
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="8a422-122">網域模型層中的儲存機制合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="8a422-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="8a422-123">儲存機制合約是只要.NET express 的儲存機制的合約需求，每個彙總使用的介面。</span><span class="sxs-lookup"><span data-stu-id="8a422-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> <span data-ttu-id="8a422-124">儲存機制本身，EF 核心程式碼或任何其他基礎結構的相依性和程式碼中，不能實作內的網域模型;儲存機制應該只實作您所定義的介面。</span><span class="sxs-lookup"><span data-stu-id="8a422-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code, must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span>

<span data-ttu-id="8a422-125">這種作法 （放置網域模型層中的儲存機制介面） 相關的模式為分隔介面模式。</span><span class="sxs-lookup"><span data-stu-id="8a422-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="8a422-126">做為[說明](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)Martin Fowler 的 「 使用分隔介面來定義介面，其中一個封裝，但實作在另一個。</span><span class="sxs-lookup"><span data-stu-id="8a422-126">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="8a422-127">如此一來用戶端所需介面的相依性可以完全不會察覺的實作。 」</span><span class="sxs-lookup"><span data-stu-id="8a422-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="8a422-128">分隔介面模式來啟用 （在此情況下，微服務的 Web API 專案） 的應用程式層有相依於網域模型中定義的需求，但不是直接的相依關係到基礎結構/持續性圖層。</span><span class="sxs-lookup"><span data-stu-id="8a422-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="8a422-129">此外，您可以使用隔離的實作，實作基礎結構中的相依性插入 / 保存層中使用儲存機制。</span><span class="sxs-lookup"><span data-stu-id="8a422-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="8a422-130">比方說，IOrderRepository 介面使用的下列範例會定義哪些 OrderRepository 類別需要實作基礎結構層級的作業。</span><span class="sxs-lookup"><span data-stu-id="8a422-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="8a422-131">在應用程式的目前實作中，程式碼只需要將訂單新增至資料庫，因為查詢是分割下列未實作 CQS 方法和訂單的更新。</span><span class="sxs-lookup"><span data-stu-id="8a422-131">In the current implementation of the application, the code just needs to add the order to the database, since queries are split following the CQS approach, and updates to orders are not implemented.</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="8a422-132">其他資源</span><span class="sxs-lookup"><span data-stu-id="8a422-132">Additional resources</span></span>

-   <span data-ttu-id="8a422-133">**Martin Fowler：分隔的介面。** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="8a422-133">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8a422-134">[上一個](net-核心-微服務-網域-model.md) [下一步] (實作的值-objects.md)</span><span class="sxs-lookup"><span data-stu-id="8a422-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
