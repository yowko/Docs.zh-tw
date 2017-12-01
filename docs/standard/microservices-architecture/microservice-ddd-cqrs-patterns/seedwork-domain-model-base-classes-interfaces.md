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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork （可重複使用的基底類別和介面為您的網域模型）

在方案資料夾包含*SeedWork*資料夾。 *SeedWork*資料夾包含自訂的基底類別，您可以使用做為基底網域實體與值物件。 使用這些基底類別，因此每個網域的物件類別中沒有多餘的程式碼。 這些類型的類別資料夾稱為*SeedWork*並不是類似*Framework*。 它會呼叫*SeedWork*因為資料夾包含只無法真正視為一種架構可重複使用類別的一小部分。 *Seedwork*詞彙所引入[Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826)和由 popularized [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html)但您也可以命名為該資料夾共同且 SharedKernel，或類似。

圖 9-12 顯示形成的網域模型 seedwork 順序的微服務中的類別。 它有幾個自訂的基底類別，例如實體、 ValueObject 和列舉型別，再加上一些介面。 這些介面 （IRepository 和 IUnitOfWork） 通知基礎結構層級必須實作的項目。 這些介面也會從應用程式層使用透過相依性插入。

![](./media/image13.PNG)

**圖 9-12**。 範例設定的網域模型 」 seedwork 「 基底類別和介面

這是許多開發人員共用專案，不是型式架構之間的複製和貼上重複使用的類型。 您可以讓 seedworks 任何圖層或程式庫中。 不過，如果一組類別和介面取得夠大，您可能想要建立單一類別庫。

## <a name="the-custom-entity-base-class"></a>自訂實體基底類別

下列程式碼是實體基底類別的範例程式碼，可以由任何網域的實體，實體識別碼，例如使用相同的方式放置位置[等號比較運算子](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx)等等。

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

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>網域模型層中的儲存機制合約 （介面）

儲存機制合約是只要.NET express 的儲存機制的合約需求，每個彙總使用的介面。 儲存機制本身，EF 核心程式碼或任何其他基礎結構的相依性和程式碼中，不能實作內的網域模型;儲存機制應該只實作您所定義的介面。

這種作法 （放置網域模型層中的儲存機制介面） 相關的模式為分隔介面模式。 做為[說明](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)Martin Fowler 的 「 使用分隔介面來定義介面，其中一個封裝，但實作在另一個。 如此一來用戶端所需介面的相依性可以完全不會察覺的實作。 」

分隔介面模式來啟用 （在此情況下，微服務的 Web API 專案） 的應用程式層有相依於網域模型中定義的需求，但不是直接的相依關係到基礎結構/持續性圖層。 此外，您可以使用隔離的實作，實作基礎結構中的相依性插入 / 保存層中使用儲存機制。

比方說，IOrderRepository 介面使用的下列範例會定義哪些 OrderRepository 類別需要實作基礎結構層級的作業。 在應用程式的目前實作中，程式碼只需要將訂單新增至資料庫，因為查詢是分割下列未實作 CQS 方法和訂單的更新。

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

## <a name="additional-resources"></a>其他資源

-   **Martin Fowler：分隔的介面。** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[上一個](net-核心-微服務-網域-model.md) [下一步] (實作的值-objects.md)
