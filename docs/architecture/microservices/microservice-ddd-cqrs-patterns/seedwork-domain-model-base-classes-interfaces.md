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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (網域模型的可重複使用基底類別和介面)

方案資料夾中包含了一個 *SeedWork* 資料夾。 此資料夾包含自訂基底類別，您可以使用它們作為您領域實體和值物件的基底。 藉由使用這些基底類別，您的每個領域物件類別中便不會有冗餘的程式碼。 這些類別類型的資料夾名為 *SeedWork*，而非 *Framework*。 它之所以名為 *SeedWork*，是因為資料夾僅包含了可重複使用類別的小型子集，而無法視為架構。 *SeedWork* 是一個由 [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) 引入的字詞，並由 [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) 進一步推廣，但您也可以將資料夾命名為 Common、SharedKernel 或其他相似名稱。

圖 7-12 顯示了組成 Ordering 微服務中領域模型 seedwork 的類別。 它有幾個自訂的基底類別，像是 Entity、ValueObject 及 Enumeration，以及其他幾個介面。 這些介面 (IRepository 和 IUnitOfWork) 會通知基礎結構層需要實作的內容。 這些介面也會透過來自應用程式層的相依性插入使用。

![SeedWork 資料夾的詳細內容包含基底類別及介面：Entity.cs、Enumeration.cs、IAggregateRoot.cs、IRepository.cs、IUnitOfWork.cs 及 ValueObject.cs](./media/image13.PNG)

**圖 7-12**。 領域模型 “seedwork" 基底類別與介面的範例組

這是一種許多開發人員在物件之間共用的複製及貼上重複使用內容，而非正式的架構。 您可以在任何層或程式庫中具有 seedwork。 然而，若類別和介面的組合變得更大，便建議您建立單一類別庫。

## <a name="the-custom-entity-base-class"></a>自訂 Entity 基底類別

下列程式碼是 Entity 基底類別的範例，您可以在其中放置可由任何領域實體透過相同方式使用的程式碼，例如實體識別碼、[等號比較運算子](../../../csharp/language-reference/operators/equality-operators.md)、每的實體的領域事件清單等。

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

先前使用每個實體領域事件清單的程式碼會在下一個聚焦於領域事件的章節中解釋。

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>領域模型層中的存放庫合約 (介面)

存放庫合約只是表達用於每個彙總之存放庫合約需求的 .NET 介面。

存放庫本身，包含 EF Core 程式碼或任何其他的基礎結構相依性和程式碼 (Linq、SQL 等) 都不可在領域模型中實作。存放庫應僅實作您在領域模型中定義的介面。

與這種做法 (將存放庫介面放置在領域模型層中) 有關的模式便是分離介面 (Separated Interface) 模式。 如同 Martin Fowler 所[解釋](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)的，「使用分離介面來在一個套件中定義介面，但在另外一個套件中實作它。 如此一來，需要相依於介面的用戶端便可以完全無須了解實作。」

遵循分離介面模式可讓應用程式層 (在此案例中為微服務的 Web API 專案) 相依於領域模型中定義的需求，但不會直接相依於基礎結構/永續性層。 此外，您可以使用相依性插入來隔離使用存放庫在基礎結構/永續層中實作的實作。

例如，下列使用 IOrderRepository 介面的範例定義了 OrderRepository 類別需要用來在基礎結構層實作的作業。 在目前的應用程式實作中，程式碼只需要將訂單新增或更新至資料庫，因為查詢已遵循簡化的 CQRS 方法進行分離。

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

## <a name="additional-resources"></a>其他資源

- **Martin Fowler：分離的介面。** \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
>[上一頁](net-core-microservice-domain-model.md)
>[下一頁](implement-value-objects.md)
