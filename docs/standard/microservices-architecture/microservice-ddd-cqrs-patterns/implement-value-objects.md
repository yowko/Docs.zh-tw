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
# <a name="implementing-value-objects"></a><span data-ttu-id="7e643-104">實作值物件</span><span class="sxs-lookup"><span data-stu-id="7e643-104">Implementing value objects</span></span>

<span data-ttu-id="7e643-105">如先前章節中討論的相關實體和彙總，識別是基本的實體。</span><span class="sxs-lookup"><span data-stu-id="7e643-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="7e643-106">不過，有許多物件和資料的項目不需要身分識別和追蹤，例如值物件的身分識別系統中。</span><span class="sxs-lookup"><span data-stu-id="7e643-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="7e643-107">值物件可以參考其他實體。</span><span class="sxs-lookup"><span data-stu-id="7e643-107">A value object can reference other entities.</span></span> <span data-ttu-id="7e643-108">例如，在產生描述如何取得從一個點之間的路由的應用程式是該路由的值物件。</span><span class="sxs-lookup"><span data-stu-id="7e643-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="7e643-109">它會在特定的路由上的點的快照集，但此建議的路由不會有一個身分識別，即使它在內部參考實體，類似縣 （市）、 Road 等。</span><span class="sxs-lookup"><span data-stu-id="7e643-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="7e643-110">圖 9 13 顯示順序彙總內的位址值物件。</span><span class="sxs-lookup"><span data-stu-id="7e643-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="7e643-111">**圖 9 13**。</span><span class="sxs-lookup"><span data-stu-id="7e643-111">**Figure 9-13**.</span></span> <span data-ttu-id="7e643-112">解決順序彙總內的值物件</span><span class="sxs-lookup"><span data-stu-id="7e643-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="7e643-113">如下圖 9-13，實體通常被由多個屬性。</span><span class="sxs-lookup"><span data-stu-id="7e643-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="7e643-114">比方說，順序可以模型化成實體的身分，並在內部所組成的一組屬性，例如訂單編號、 訂單日期、 OrderItems 等等。但的位址、 只是複雜值國家/地區、 街道、 縣 （市）、 組成等等，都必須建立模型，並視為值物件。</span><span class="sxs-lookup"><span data-stu-id="7e643-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="7e643-115">值物件的重要特性</span><span class="sxs-lookup"><span data-stu-id="7e643-115">Important characteristics of value objects</span></span>

<span data-ttu-id="7e643-116">有兩個值物件的主要特性：</span><span class="sxs-lookup"><span data-stu-id="7e643-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="7e643-117">它們有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="7e643-117">They have no identity.</span></span>

-   <span data-ttu-id="7e643-118">它們是不變。</span><span class="sxs-lookup"><span data-stu-id="7e643-118">They are immutable.</span></span>

<span data-ttu-id="7e643-119">第一個特性已討論過。</span><span class="sxs-lookup"><span data-stu-id="7e643-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="7e643-120">不變性是重要的需求。</span><span class="sxs-lookup"><span data-stu-id="7e643-120">Immutability is an important requirement.</span></span> <span data-ttu-id="7e643-121">值物件的值必須是不變的一旦建立物件。</span><span class="sxs-lookup"><span data-stu-id="7e643-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="7e643-122">因此，物件建構時，您必須提供需要的值，但是您必須允許他們變更物件的存留期間。</span><span class="sxs-lookup"><span data-stu-id="7e643-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="7e643-123">值物件可讓您執行效能，這點受惠本質上不可變的特定技巧。</span><span class="sxs-lookup"><span data-stu-id="7e643-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="7e643-124">特別是在系統中可能有數千個值的物件執行個體，其中許多都有相同的值。</span><span class="sxs-lookup"><span data-stu-id="7e643-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="7e643-125">不可變本質上可讓它們可重複使用。可以是可互換的物件，因為它們的值相同，而且它們有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="7e643-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="7e643-126">這種類型的最佳化有時會使執行速度慢的軟體和軟體以良好的效能差異。</span><span class="sxs-lookup"><span data-stu-id="7e643-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="7e643-127">當然，所有這些情況取決於應用程式環境和部署內容。</span><span class="sxs-lookup"><span data-stu-id="7e643-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="7e643-128">在 C 中的值物件實作\#</span><span class="sxs-lookup"><span data-stu-id="7e643-128">Value object implementation in C\#</span></span>

<span data-ttu-id="7e643-129">方面的實作中，您可以使用值物件基底類別具有類似相等 （因為值物件必須不識別為基礎） 的所有屬性和其他的基本特性之間的比較為基礎的基本公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="7e643-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="7e643-130">下列範例顯示用於排序的微服務從 eShopOnContainers 值的物件基底類別。</span><span class="sxs-lookup"><span data-stu-id="7e643-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="7e643-131">可以使用這個類別實作您的實際值物件時，如同下列範例所示的位址值物件：</span><span class="sxs-lookup"><span data-stu-id="7e643-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="7e643-132">使用 EF 核心保存值物件時，隱藏的識別特性</span><span class="sxs-lookup"><span data-stu-id="7e643-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="7e643-133">使用 EF 核心為其目前的版本 (EF 核心 1.1) 您無法使用時的限制[複雜型別](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7)EF 中所定義 6.x。</span><span class="sxs-lookup"><span data-stu-id="7e643-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="7e643-134">因此，您必須為 EF 實體儲存值物件。</span><span class="sxs-lookup"><span data-stu-id="7e643-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="7e643-135">不過，您可以隱藏它的識別碼，讓您清楚的身分識別不屬於值物件模型中的重要。</span><span class="sxs-lookup"><span data-stu-id="7e643-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="7e643-136">隱藏識別碼會當做陰影屬性使用的 ID。</span><span class="sxs-lookup"><span data-stu-id="7e643-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="7e643-137">由於基礎結構層級中，已設定該組態來隱藏在模型中的識別碼，它將會為您的網域模型，變成透明，而且其基礎結構實作可能會在未來變更。</span><span class="sxs-lookup"><span data-stu-id="7e643-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="7e643-138">在 eShopOnContainers，隱藏的 EF 核心基礎結構所需的識別碼中實作 DbContext 層級中以下列方式在基礎結構專案使用 fluent 應用程式開發的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="7e643-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

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

<span data-ttu-id="7e643-139">因此，從網域模型觀點來看，隱藏識別碼，且在未來，值的物件基礎結構可能也會實作為複雜型別或另一種方式。</span><span class="sxs-lookup"><span data-stu-id="7e643-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7e643-140">其他資源</span><span class="sxs-lookup"><span data-stu-id="7e643-140">Additional resources</span></span>

-   <span data-ttu-id="7e643-141">**Martin Fowler：ValueObject 模式**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="7e643-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="7e643-142">**Eric Evans：網域導向設計： 解決核心軟體的複雜度。**</span><span class="sxs-lookup"><span data-stu-id="7e643-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="7e643-143">（書籍; 包含的值物件的討論）[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="7e643-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="7e643-144">**Vaughn Vernon：實作網域導向設計。**</span><span class="sxs-lookup"><span data-stu-id="7e643-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="7e643-145">（書籍; 包含的值物件的討論）[ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="7e643-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="7e643-146">**遮蔽屬性**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="7e643-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="7e643-147">**複雜型別和/或值物件**。</span><span class="sxs-lookup"><span data-stu-id="7e643-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="7e643-148">EF 核心 GitHub 儲存機制 （問題索引標籤） 中的討論[ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="7e643-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="7e643-149">**ValueObject.cs。**</span><span class="sxs-lookup"><span data-stu-id="7e643-149">**ValueObject.cs.**</span></span> <span data-ttu-id="7e643-150">基底值 eShopOnContainers 中的物件類別。</span><span class="sxs-lookup"><span data-stu-id="7e643-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="7e643-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="7e643-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="7e643-152">**位址類別。**</span><span class="sxs-lookup"><span data-stu-id="7e643-152">**Address class.**</span></span> <span data-ttu-id="7e643-153">範例值 eShopOnContainers 中的物件類別。</span><span class="sxs-lookup"><span data-stu-id="7e643-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="7e643-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="7e643-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="7e643-155">[上一個](seedwork-domain-model-base-classes-interfaces.md) [下一步] (列舉-類別-over-列舉-types.md)</span><span class="sxs-lookup"><span data-stu-id="7e643-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
