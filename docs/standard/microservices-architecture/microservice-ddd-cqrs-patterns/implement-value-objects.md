---
title: 實作值物件
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 深入了解使用新 Entity Framework 功能實作值物件的詳細資料與選項。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 2a8e0ad97f2ad6b4645fb493b5148667a2830ec8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145263"
---
# <a name="implement-value-objects"></a><span data-ttu-id="1dc73-103">實作值物件</span><span class="sxs-lookup"><span data-stu-id="1dc73-103">Implement value objects</span></span>

<span data-ttu-id="1dc73-104">如前面各節中討論的實體和彙總，身分識別是實體的基礎。</span><span class="sxs-lookup"><span data-stu-id="1dc73-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="1dc73-105">不過，系統中有許多物件和資料項目不需要身分識別和身分識別追蹤，例如值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="1dc73-106">值物件可以參考其他實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-106">A value object can reference other entities.</span></span> <span data-ttu-id="1dc73-107">例如，在產生描述如何從某點到另一點的路由的應用程式中，該路由就是值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="1dc73-108">它會是特定路由的點快照集，但此建議的路由不會有身分識別，雖然它在內部參考縣 (市)、街道等實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="1dc73-109">圖 7-13 顯示 Order 彙總內的 Address 值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Order 彙總內的 Address 值物件。](./media/image14.png)

<span data-ttu-id="1dc73-111">**圖 7-13**。</span><span class="sxs-lookup"><span data-stu-id="1dc73-111">**Figure 7-13**.</span></span> <span data-ttu-id="1dc73-112">訂單彙總內的 Address 值物件</span><span class="sxs-lookup"><span data-stu-id="1dc73-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="1dc73-113">如圖 7-13 所示，實體通常是由多個屬性組成。</span><span class="sxs-lookup"><span data-stu-id="1dc73-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="1dc73-114">例如，`Order` 實體可以模型化成具身分識別的實體，並且在內部由一組屬性組成，例如 OrderId、OrderDate、OrderItems 等等。但地址 (僅由國家/地區、街道、縣市等等組成的複雜值，且在此網域中沒有任何身分識別) 必須模型化並視為值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="1dc73-115">值物件的重要特性</span><span class="sxs-lookup"><span data-stu-id="1dc73-115">Important characteristics of value objects</span></span>

<span data-ttu-id="1dc73-116">值物件有兩個主要特性：</span><span class="sxs-lookup"><span data-stu-id="1dc73-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="1dc73-117">它們沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="1dc73-117">They have no identity.</span></span>

- <span data-ttu-id="1dc73-118">它們具有不變性。</span><span class="sxs-lookup"><span data-stu-id="1dc73-118">They are immutable.</span></span>

<span data-ttu-id="1dc73-119">第一個特性已討論過。</span><span class="sxs-lookup"><span data-stu-id="1dc73-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="1dc73-120">不變性是重要需求。</span><span class="sxs-lookup"><span data-stu-id="1dc73-120">Immutability is an important requirement.</span></span> <span data-ttu-id="1dc73-121">物件一旦建立，值物件的值必須不可變。</span><span class="sxs-lookup"><span data-stu-id="1dc73-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="1dc73-122">因此，在建構物件時，您必須提供必要的值，但在物件存留期間絕不能讓它們變更。</span><span class="sxs-lookup"><span data-stu-id="1dc73-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="1dc73-123">值物件因為不可變的本質，可讓您執行某些技巧以提升效能。</span><span class="sxs-lookup"><span data-stu-id="1dc73-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="1dc73-124">特別是在有數千個值物件執行個體的系統中，它們之中許多都有相同的值。</span><span class="sxs-lookup"><span data-stu-id="1dc73-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="1dc73-125">其不可變的本質可讓它們重複使用。它們可以是可互換的物件，因為它們的值相同，而且它們沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="1dc73-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="1dc73-126">這種最佳化有時會造成執行速度緩慢的軟體和效能良好的軟體之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1dc73-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="1dc73-127">當然，所有這些情況都取決於應用程式環境和部署內容。</span><span class="sxs-lookup"><span data-stu-id="1dc73-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="1dc73-128">以 C\# 實作值物件</span><span class="sxs-lookup"><span data-stu-id="1dc73-128">Value object implementation in C\#</span></span>

<span data-ttu-id="1dc73-129">就實作而言，您可有一個值物件基底類別，此類別具有基本的公用程式方法，例如以所有屬性 (因為值物件絕對不能以身分識別為基礎) 和其他基本特性之間的比較為基礎的相等。</span><span class="sxs-lookup"><span data-stu-id="1dc73-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="1dc73-130">下列範例示範 eShopOnContainers 訂購微服務中使用的值物件基底類別。</span><span class="sxs-lookup"><span data-stu-id="1dc73-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }        
    // Other utilility methods
}
```

<span data-ttu-id="1dc73-131">實作您實際的值物件時，您可以使用這個類別，如同對待下列範例所示的 Address 值物件一樣：</span><span class="sxs-lookup"><span data-stu-id="1dc73-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

<span data-ttu-id="1dc73-132">您可以看到此 Address 的值物件實作沒有身分識別，因此在 Address 類別，甚至是 ValueObject 類別也沒有識別碼欄位。</span><span class="sxs-lookup"><span data-stu-id="1dc73-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="1dc73-133">類別中不能沒有識別碼欄位供 Entity Framework 使用，直到 EF Core 2.0 出現，才讓沒有識別碼的值物件實作過程變得順利許多。</span><span class="sxs-lookup"><span data-stu-id="1dc73-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0 which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="1dc73-134">這正是下一節的說明。</span><span class="sxs-lookup"><span data-stu-id="1dc73-134">That is precisely the explanation of the next section.</span></span> 

<span data-ttu-id="1dc73-135">有人認為值物件 (固定) 應為唯讀 (亦即 get-only 屬性)，而實際上正是如此。</span><span class="sxs-lookup"><span data-stu-id="1dc73-135">It could be argued that value objects, being immutable, should be read only (i.e. get-only properties) and that’s indeed true.</span></span> <span data-ttu-id="1dc73-136">然而，值物件通常會經過序列化及還原序列化以通過訊息佇列，而且會是唯讀的，讓還原序列化程式停止指派值，因而能停留在剛好夠用的唯讀私人集合狀態。</span><span class="sxs-lookup"><span data-stu-id="1dc73-136">However, value objects are usually serialized and deserialized to go through message queues, and being read only, stops the deserializer from assigning values so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="1dc73-137">如何在使用 EF Core 2.0 的資料庫中保存值物件</span><span class="sxs-lookup"><span data-stu-id="1dc73-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="1dc73-138">您只看到如何在您的網域模型中定義值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="1dc73-139">但您如何透過通常以身分識別鎖定實體的 Entity Framework (EF) Core，在資料庫中真正保存它？</span><span class="sxs-lookup"><span data-stu-id="1dc73-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="1dc73-140">使用 EF Core 1.1 的背景和較舊的方法</span><span class="sxs-lookup"><span data-stu-id="1dc73-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="1dc73-141">追根究柢，使用 EF Core 1.0 和 1.1 時有一項限制，就是您無法使用在傳統 .NET Framework 中 EF 6.x 定義的[複雜類型](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="1dc73-142">因此，如果使用 EF Core 1.0 或 1.1，您需要使用識別碼欄位將您的值物件儲存為 EF 實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="1dc73-143">然後，它會看起來更像是沒有任何身分識別的值物件，您可以隱藏它的識別碼，以便您明白表示值物件的識別碼在網域模型中不重要。</span><span class="sxs-lookup"><span data-stu-id="1dc73-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="1dc73-144">您可以將識別碼當成 [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ) (shadow 屬性) 使用，隱藏該識別碼。</span><span class="sxs-lookup"><span data-stu-id="1dc73-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="1dc73-145">因為已在 EF 基礎結構層級設定模型中隱藏識別碼的組態，所以對您的網域模型而言，它幾乎是不存在的。</span><span class="sxs-lookup"><span data-stu-id="1dc73-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="1dc73-146">在 eShopOnContainers 的初始版本中 (.NET Core 1.1)，已在基礎結構專案中使用 Fluent API，以下列方式在 DbContext 層級實作 EF Core 基礎結構所需要的隱藏識別碼。</span><span class="sxs-lookup"><span data-stu-id="1dc73-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="1dc73-147">因此，從網域模型的觀點而言，識別碼已隱藏，但仍會出現在基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="1dc73-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="1dc73-148">不過，該值物件保存在資料庫中，就像是不同資料表中的一般實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="1dc73-149">EF Core 2.0 有更好的新方法保存值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="1dc73-150">EF Core 2.0 將值物件保存為擁有的實體類型</span><span class="sxs-lookup"><span data-stu-id="1dc73-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="1dc73-151">雖然 DDD 標準值物件模式與 EF Core 擁有的實體類型之間仍有距離，但這是目前使用 EF Core 2.0 保存值物件的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="1dc73-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="1dc73-152">本節結尾會列出限制。</span><span class="sxs-lookup"><span data-stu-id="1dc73-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="1dc73-153">EF Core 從 2.0 版開始新增擁有的實體類型功能。</span><span class="sxs-lookup"><span data-stu-id="1dc73-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="1dc73-154">自有實體類型可讓您在自己的所有實體內，對應那些自己身分識別未在網域模型中明確定義並用作屬性的類型，例如值物件。</span><span class="sxs-lookup"><span data-stu-id="1dc73-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="1dc73-155">自有實體類型與其他實體類型共用相同的 CLR 類型 (亦即其僅為一般類別)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="1dc73-156">包含定義導覽的實體是擁有者實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="1dc73-157">查詢擁有者時，預設包含擁有的類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="1dc73-158">如果只看網域模型，擁有的類型看似沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="1dc73-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="1dc73-159">不過，擁有的類型其實有身分識別，但擁有者導覽屬性是此身分識別的一部分。</span><span class="sxs-lookup"><span data-stu-id="1dc73-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="1dc73-160">自有類型的執行個體身分識別不完全屬於它們自己。</span><span class="sxs-lookup"><span data-stu-id="1dc73-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="1dc73-161">它包含三個元件：</span><span class="sxs-lookup"><span data-stu-id="1dc73-161">It consists of three components:</span></span>

- <span data-ttu-id="1dc73-162">擁有者的身分識別</span><span class="sxs-lookup"><span data-stu-id="1dc73-162">The identity of the owner</span></span>

- <span data-ttu-id="1dc73-163">指向它們的導覽屬性</span><span class="sxs-lookup"><span data-stu-id="1dc73-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="1dc73-164">如果是自有類型的集合，則為獨立元件 (EF Core 2.0 尚不支援，即將於 2.2 推出)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="1dc73-165">例如，在 eShopOnContainers 的訂購網域模型中，屬於訂單實體的一部分，Address 值物件在擁有者實體內實作為擁有的實體類型，也就是訂單實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="1dc73-166">Address 是網域模型中未定義任何身分識別屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="1dc73-167">它用做訂單類型的屬性，指定特定訂單的送貨地址。</span><span class="sxs-lookup"><span data-stu-id="1dc73-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="1dc73-168">依照慣例，會為擁有的類型建立陰影主索引鍵，而且會使用資料表分割將它對應至與擁有者相同的資料表。</span><span class="sxs-lookup"><span data-stu-id="1dc73-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="1dc73-169">這允許以類似傳統 .NET Framework 的 EF6 使用複雜類型的方式，使用擁有的類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="1dc73-170">請務必注意，EF Core 慣例永遠不會探索到擁有的類型，所以您不必明確宣告它們。</span><span class="sxs-lookup"><span data-stu-id="1dc73-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="1dc73-171">在 eShopOnContainers 的 OrderingContext.cs 的 OnModelCreating() 方法中，正在套用多個基礎結構組態。</span><span class="sxs-lookup"><span data-stu-id="1dc73-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="1dc73-172">其中一個與訂單實體有關。</span><span class="sxs-lookup"><span data-stu-id="1dc73-172">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="1dc73-173">下列程式碼會定義訂單實體的持續性基礎結構：</span><span class="sxs-lookup"><span data-stu-id="1dc73-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="1dc73-174">在先前的程式碼中，`orderConfiguration.OwnsOne(o => o.Address)` 方法指定 `Address` 屬性是 `Order` 類型的擁有的實體。</span><span class="sxs-lookup"><span data-stu-id="1dc73-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="1dc73-175">根據預設，EF Core 慣例會將擁有的實體類型的屬性資料庫資料行命名為 `EntityProperty_OwnedEntityProperty`。</span><span class="sxs-lookup"><span data-stu-id="1dc73-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="1dc73-176">因此，`Address` 的內部屬性會出現在 `Orders` 資料表中，名為 `Address_Street`、`Address_City` (及 `State`、`Country` 和 `ZipCode`)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="1dc73-177">您可以附加 `Property().HasColumnName()` fluent 方法重新命名這些資料行。</span><span class="sxs-lookup"><span data-stu-id="1dc73-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="1dc73-178">如果發生 `Address` 是公用屬性的情況，對應會如同下例：</span><span class="sxs-lookup"><span data-stu-id="1dc73-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="1dc73-179">可在 fluent 對應中鏈結 `OwnsOne` 方法。</span><span class="sxs-lookup"><span data-stu-id="1dc73-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="1dc73-180">在下列假設性的範例中，`OrderDetails` 擁有 `BillingAddress` 和 `ShippingAddress`，它們兩個都是 `Address` 類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="1dc73-181">然後 `Order` 類型擁有 `OrderDetails`。</span><span class="sxs-lookup"><span data-stu-id="1dc73-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="1dc73-182">有關擁有的實體類型的其他詳細資料</span><span class="sxs-lookup"><span data-stu-id="1dc73-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="1dc73-183">當您使用 OwnsOne fluent API 將導覽屬性設定為特定類型時，會定義自有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="1dc73-184">在我們的中繼資料模型中，自有類型的定義由下列項目組成：擁有者類型、導覽屬性，以及自有類型的 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="1dc73-185">在我們的堆疊中，自有類型執行個體的身分識別 (金鑰) 是由擁有者類型的身分識別及自有類型的定義所組成。</span><span class="sxs-lookup"><span data-stu-id="1dc73-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="1dc73-186">擁有的實體的功能：</span><span class="sxs-lookup"><span data-stu-id="1dc73-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="1dc73-187">自有類型可以參考其他實體，可以是自有 (巢狀自有類型) 或非自有 (對其他實體的一般參考導覽屬性)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="1dc73-188">您可以透過個別的導覽屬性，將相同的 CLR 類型對應為同一個擁有者實體中的不同自有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="1dc73-189">資料表分割會按慣例設定，但您可以選擇不這麼做，而使用 ToTable 將自有類型對應至不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="1dc73-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="1dc73-190">積極式載入會自動在自有類型上執行，亦即不需要對查詢呼叫 Include()。</span><span class="sxs-lookup"><span data-stu-id="1dc73-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="1dc73-191">到 EF Core 2.1 為止，可使用屬性 \[Owned\] 來設定</span><span class="sxs-lookup"><span data-stu-id="1dc73-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="1dc73-192">擁有的實體的限制：</span><span class="sxs-lookup"><span data-stu-id="1dc73-192">Owned entities limitations:</span></span>

- <span data-ttu-id="1dc73-193">您無法建立自有類型的 DbSet\<T\> (特意設計)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="1dc73-194">您無法在自有類型上呼叫 ModelBuilder.Entity\<T\>() (目前特意設計)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="1dc73-195">尚無任何自有類型的集合 (到 EF Core 2.1 為止，但 2.2 後的版本會予以支援)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="1dc73-196">不支援選擇性 (亦即可為 null) 的自有類型，其在相同的資料表中與擁有者對應 (亦即使用資料表分割)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="1dc73-197">這是因為對應會分別為各個屬性執行，而我們沒有整體 null 複雜值的個別防衛單位。</span><span class="sxs-lookup"><span data-stu-id="1dc73-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="1dc73-198">不支援自有類型的繼承對應，但您應該能夠將兩種同一繼承階層的分葉類型當成不同的自有類型對應。</span><span class="sxs-lookup"><span data-stu-id="1dc73-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="1dc73-199">EF Core 不會推論出它們屬於同一階層的事實。</span><span class="sxs-lookup"><span data-stu-id="1dc73-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="1dc73-200">EF6 複雜類型的主要差異</span><span class="sxs-lookup"><span data-stu-id="1dc73-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="1dc73-201">資料表分割為選擇性，亦即其可以選擇性地對應至不同的資料表，但仍為自有類型。</span><span class="sxs-lookup"><span data-stu-id="1dc73-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="1dc73-202">它們可以參考其他實體 (也就是可在其他非自有類型的關聯性中當作相依端)。</span><span class="sxs-lookup"><span data-stu-id="1dc73-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1dc73-203">其他資源</span><span class="sxs-lookup"><span data-stu-id="1dc73-203">Additional resources</span></span>

- <span data-ttu-id="1dc73-204">**Martin Fowler：ValueObject 模式** \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-204">**Martin Fowler. ValueObject pattern** \\</span></span>
  [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

- <span data-ttu-id="1dc73-205">**Eric Evans：Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span><span class="sxs-lookup"><span data-stu-id="1dc73-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="1dc73-206">(書籍；包含值物件的探討) \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-206">(Book; includes a discussion of value objects) \\</span></span>
  [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- <span data-ttu-id="1dc73-207">**Vaughn Vernon：Implementing Domain-Driven Design.**</span><span class="sxs-lookup"><span data-stu-id="1dc73-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="1dc73-208">(書籍；包含值物件的探討) \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-208">(Book; includes a discussion of value objects) \\</span></span>
  [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- <span data-ttu-id="1dc73-209">**陰影屬性** \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-209">**Shadow Properties** \\</span></span>
  [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

- <span data-ttu-id="1dc73-210">**複雜類型和/或值物件**。</span><span class="sxs-lookup"><span data-stu-id="1dc73-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="1dc73-211">EF Core GitHub 存放庫 ([問題] 索引標籤) 的探討 \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-211">Discussion in the EF Core GitHub repo (Issues tab) \\</span></span>
  [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

- <span data-ttu-id="1dc73-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="1dc73-212">**ValueObject.cs.**</span></span> <span data-ttu-id="1dc73-213">eShopOnContainers 中的基底值物件類別。**  \\</span><span class="sxs-lookup"><span data-stu-id="1dc73-213">Base value object class in eShopOnContainers.**  \\</span></span>
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

- <span data-ttu-id="1dc73-214">**網址類別。**</span><span class="sxs-lookup"><span data-stu-id="1dc73-214">**Address class.**</span></span> <span data-ttu-id="1dc73-215">eShopOnContainers 中的範列值物件類別。</span><span class="sxs-lookup"><span data-stu-id="1dc73-215">Sample value object class in eShopOnContainers.</span></span> \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)

>[!div class="step-by-step"]
><span data-ttu-id="1dc73-216">[上一頁](seedwork-domain-model-base-classes-interfaces.md)
>[下一頁](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="1dc73-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>