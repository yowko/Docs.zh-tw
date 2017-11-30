---
title: "實作值物件"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |實作值物件"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a>實作值物件

如先前章節中討論的相關實體和彙總，識別是基本的實體。 不過，有許多物件和資料的項目不需要身分識別和追蹤，例如值物件的身分識別系統中。

值物件可以參考其他實體。 例如，在產生描述如何取得從一個點之間的路由的應用程式是該路由的值物件。 它會在特定的路由上的點的快照集，但此建議的路由不會有一個身分識別，即使它在內部參考實體，類似縣 （市）、 Road 等。

圖 9 13 顯示順序彙總內的位址值物件。

![](./media/image14.png)

**圖 9 13**。 解決順序彙總內的值物件

如下圖 9-13，實體通常被由多個屬性。 比方說，順序可以模型化成實體的身分，並在內部所組成的一組屬性，例如訂單編號、 訂單日期、 OrderItems 等等。但的位址、 只是複雜值國家/地區、 街道、 縣 （市）、 組成等等，都必須建立模型，並視為值物件。

## <a name="important-characteristics-of-value-objects"></a>值物件的重要特性

有兩個值物件的主要特性：

-   它們有任何身分識別。

-   它們是不變。

第一個特性已討論過。 不變性是重要的需求。 值物件的值必須是不變的一旦建立物件。 因此，物件建構時，您必須提供需要的值，但是您必須允許他們變更物件的存留期間。

值物件可讓您執行效能，這點受惠本質上不可變的特定技巧。 特別是在系統中可能有數千個值的物件執行個體，其中許多都有相同的值。 不可變本質上可讓它們可重複使用。可以是可互換的物件，因為它們的值相同，而且它們有任何身分識別。 這種類型的最佳化有時會使執行速度慢的軟體和軟體以良好的效能差異。 當然，所有這些情況取決於應用程式環境和部署內容。

## <a name="value-object-implementation-in-c"></a>在 C 中的值物件實作\#

方面的實作中，您可以使用值物件基底類別具有類似相等 （因為值物件必須不識別為基礎） 的所有屬性和其他的基本特性之間的比較為基礎的基本公用程式方法。 下列範例顯示用於排序的微服務從 eShopOnContainers 值的物件基底類別。

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

可以使用這個類別實作您的實際值物件時，如同下列範例所示的位址值物件：

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>使用 EF 核心保存值物件時，隱藏的識別特性

使用 EF 核心為其目前的版本 (EF 核心 1.1) 您無法使用時的限制[複雜型別](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7)EF 中所定義 6.x。 因此，您必須為 EF 實體儲存值物件。 不過，您可以隱藏它的識別碼，讓您清楚的身分識別不屬於值物件模型中的重要。 隱藏識別碼會當做陰影屬性使用的 ID。 由於基礎結構層級中，已設定該組態來隱藏在模型中的識別碼，它將會為您的網域模型，變成透明，而且其基礎結構實作可能會在未來變更。

在 eShopOnContainers，隱藏的 EF 核心基礎結構所需的識別碼中實作 DbContext 層級中以下列方式在基礎結構專案使用 fluent 應用程式開發的應用程式開發介面。

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

因此，從網域模型觀點來看，隱藏識別碼，且在未來，值的物件基礎結構可能也會實作為複雜型別或另一種方式。

## <a name="additional-resources"></a>其他資源

-   **Martin Fowler：ValueObject 模式**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans：網域導向設計： 解決核心軟體的複雜度。** （書籍; 包含的值物件的討論）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon：實作網域導向設計。** （書籍; 包含的值物件的討論）[ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **遮蔽屬性**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **複雜型別和/或值物件**。 EF 核心 GitHub 儲存機制 （問題索引標籤） 中的討論[ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs。** 基底值 eShopOnContainers 中的物件類別。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **位址類別。** 範例值 eShopOnContainers 中的物件類別。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[上一個](seedwork-domain-model-base-classes-interfaces.md) [下一步] (列舉-類別-over-列舉-types.md)
