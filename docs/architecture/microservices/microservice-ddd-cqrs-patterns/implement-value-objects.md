---
title: 實作值物件
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 深入了解使用新 Entity Framework 功能實作值物件的詳細資料與選項。
ms.date: 08/21/2020
ms.openlocfilehash: 02eed7baaa364c62aa2df599f1d8b0e700dd215f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811115"
---
# <a name="implement-value-objects"></a><span data-ttu-id="b9a96-103">實作值物件</span><span class="sxs-lookup"><span data-stu-id="b9a96-103">Implement value objects</span></span>

<span data-ttu-id="b9a96-104">如前面各節中討論的實體和彙總，身分識別是實體的基礎。</span><span class="sxs-lookup"><span data-stu-id="b9a96-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="b9a96-105">不過，系統中有許多物件和資料項目不需要身分識別和身分識別追蹤，例如值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="b9a96-106">值物件可以參考其他實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-106">A value object can reference other entities.</span></span> <span data-ttu-id="b9a96-107">例如，在產生描述如何從某點到另一點的路由的應用程式中，該路由就是值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="b9a96-108">它會是特定路由的點快照集，但此建議的路由不會有身分識別，雖然它在內部參考縣 (市)、街道等實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="b9a96-109">圖 7-13 顯示 Order 彙總內的 Address 值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![此圖表顯示 Order 匯總內的 Address 值物件。](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="b9a96-111">**圖 7-13**。</span><span class="sxs-lookup"><span data-stu-id="b9a96-111">**Figure 7-13**.</span></span> <span data-ttu-id="b9a96-112">訂單彙總內的 Address 值物件</span><span class="sxs-lookup"><span data-stu-id="b9a96-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="b9a96-113">如圖 7-13 所示，實體通常是由多個屬性組成。</span><span class="sxs-lookup"><span data-stu-id="b9a96-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="b9a96-114">例如， `Order` 實體可以模型化為具有身分識別的實體，並在內部包含一組屬性，例如 [訂單識別碼]、[日期（日期）]、[OrderItems] 等等。但位址（只是由國家/地區、街道、縣/市組成的複雜值，而且在此網域中沒有任何身分識別）必須模型化並視為值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="b9a96-115">值物件的重要特性</span><span class="sxs-lookup"><span data-stu-id="b9a96-115">Important characteristics of value objects</span></span>

<span data-ttu-id="b9a96-116">值物件有兩個主要特性：</span><span class="sxs-lookup"><span data-stu-id="b9a96-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="b9a96-117">它們沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-117">They have no identity.</span></span>

- <span data-ttu-id="b9a96-118">它們具有不變性。</span><span class="sxs-lookup"><span data-stu-id="b9a96-118">They are immutable.</span></span>

<span data-ttu-id="b9a96-119">第一個特性已討論過。</span><span class="sxs-lookup"><span data-stu-id="b9a96-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="b9a96-120">不變性是重要需求。</span><span class="sxs-lookup"><span data-stu-id="b9a96-120">Immutability is an important requirement.</span></span> <span data-ttu-id="b9a96-121">物件一旦建立，值物件的值必須不可變。</span><span class="sxs-lookup"><span data-stu-id="b9a96-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="b9a96-122">因此，在建立物件時，您必須提供必要的值，但您不能在物件的存留期內允許它們變更。</span><span class="sxs-lookup"><span data-stu-id="b9a96-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="b9a96-123">值物件因為不可變的本質，可讓您執行某些技巧以提升效能。</span><span class="sxs-lookup"><span data-stu-id="b9a96-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="b9a96-124">特別是在有數千個值物件執行個體的系統中，它們之中許多都有相同的值。</span><span class="sxs-lookup"><span data-stu-id="b9a96-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="b9a96-125">其不可變的本質可讓它們重複使用。它們可以是可互換的物件，因為它們的值相同，而且它們沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="b9a96-126">這種最佳化有時會造成執行速度緩慢的軟體和效能良好的軟體之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b9a96-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="b9a96-127">當然，所有這些情況都取決於應用程式環境和部署內容。</span><span class="sxs-lookup"><span data-stu-id="b9a96-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="b9a96-128">以 C\# 實作值物件</span><span class="sxs-lookup"><span data-stu-id="b9a96-128">Value object implementation in C\#</span></span>

<span data-ttu-id="b9a96-129">就實方面而言，您可以有一個值物件基類，它有一個基本的公用程式方法，像是根據 (的所有屬性，因為值物件不能以識別) 和其他基本特性為基礎。</span><span class="sxs-lookup"><span data-stu-id="b9a96-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on the comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="b9a96-130">下列範例示範 eShopOnContainers 訂購微服務中使用的值物件基底類別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    protected abstract IEnumerable<object> GetEqualityComponents();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        var other = (ValueObject)obj;

        return this.GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Select(x => x != null ? x.GetHashCode() : 0)
            .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

<span data-ttu-id="b9a96-131">實作您實際的值物件時，您可以使用這個類別，如同對待下列範例所示的 Address 值物件一樣：</span><span class="sxs-lookup"><span data-stu-id="b9a96-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetEqualityComponents()
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

<span data-ttu-id="b9a96-132">您可以看到此 Address 的值物件實作沒有身分識別，因此在 Address 類別，甚至是 ValueObject 類別也沒有識別碼欄位。</span><span class="sxs-lookup"><span data-stu-id="b9a96-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="b9a96-133">在 Entity Framework (EF) 的類別中不能有任何識別碼欄位，除非 EF Core 2.0，這可大幅協助您以沒有識別碼的方式來執行更好的值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="b9a96-134">這正是下一節的說明。</span><span class="sxs-lookup"><span data-stu-id="b9a96-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="b9a96-135">它可能會有人認為該值物件是不可變的，應該是唯讀的 (也就是只有) 的屬性，而且的確如此。</span><span class="sxs-lookup"><span data-stu-id="b9a96-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="b9a96-136">然而，值物件通常會經過序列化和還原序列化，以通過訊息佇列，而且是唯讀的，會使還原序列化程式無法指派值，因此您只需將其保留為 `private set` 唯讀，這就足以實際運作。</span><span class="sxs-lookup"><span data-stu-id="b9a96-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so you just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="b9a96-137">如何在具有 EF Core 2.0 和更新版本的資料庫中保存值物件</span><span class="sxs-lookup"><span data-stu-id="b9a96-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="b9a96-138">您只看到如何在您的網域模型中定義值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="b9a96-139">但是，您要如何使用 Entity Framework Core 將它保存在資料庫中，因為它通常是以身分識別為目標的實體？</span><span class="sxs-lookup"><span data-stu-id="b9a96-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="b9a96-140">使用 EF Core 1.1 的背景和較舊的方法</span><span class="sxs-lookup"><span data-stu-id="b9a96-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="b9a96-141">在使用 EF Core 1.0 和1.1 時，使用的限制是，您無法使用傳統 .NET Framework 中 EF 6.x 所定義的 [複雜類型](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) 。</span><span class="sxs-lookup"><span data-stu-id="b9a96-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="b9a96-142">因此，如果使用 EF Core 1.0 或 1.1，您需要使用識別碼欄位將您的值物件儲存為 EF 實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="b9a96-143">然後，它會看起來更像是沒有任何身分識別的值物件，您可以隱藏它的識別碼，以便您明白表示值物件的識別碼在網域模型中不重要。</span><span class="sxs-lookup"><span data-stu-id="b9a96-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="b9a96-144">您可以將識別碼當成 [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ) (shadow 屬性) 使用，隱藏該識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9a96-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="b9a96-145">因為已在 EF 基礎結構層級設定模型中隱藏識別碼的組態，所以對您的網域模型而言，它幾乎是不存在的。</span><span class="sxs-lookup"><span data-stu-id="b9a96-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="b9a96-146">在 eShopOnContainers 的初始版本中 (.NET Core 1.1)，已在基礎結構專案中使用 Fluent API，以下列方式在 DbContext 層級實作 EF Core 基礎結構所需要的隱藏識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9a96-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="b9a96-147">因此，從網域模型的觀點而言，識別碼已隱藏，但仍會出現在基礎結構中。</span><span class="sxs-lookup"><span data-stu-id="b9a96-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="b9a96-148">不過，該值物件保存在資料庫中，就像是不同資料表中的一般實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="b9a96-149">在 EF Core 2.0 和更新版本中，有更好的新方法可保存值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="b9a96-150">在 EF Core 2.0 和更新版本中，將值物件保存為擁有的實體類型</span><span class="sxs-lookup"><span data-stu-id="b9a96-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="b9a96-151">即使在 DDD 中的標準值物件模式與 EF Core 中擁有的實體類型之間有一些差距，目前仍是使用 EF Core 2.0 和更新版本保存值物件的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="b9a96-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="b9a96-152">本節結尾會列出限制。</span><span class="sxs-lookup"><span data-stu-id="b9a96-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="b9a96-153">EF Core 從 2.0 版開始新增擁有的實體類型功能。</span><span class="sxs-lookup"><span data-stu-id="b9a96-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="b9a96-154">自有實體類型可讓您在自己的所有實體內，對應那些自己身分識別未在網域模型中明確定義並用作屬性的類型，例如值物件。</span><span class="sxs-lookup"><span data-stu-id="b9a96-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="b9a96-155">擁有的實體類型與另一個實體類型共用相同的 CLR 類型 (也就是說，它只是) 的一般類別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="b9a96-156">包含定義導覽的實體是擁有者實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="b9a96-157">查詢擁有者時，預設包含擁有的類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="b9a96-158">只要查看領域模型，擁有的型別看起來就像它沒有任何身分識別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="b9a96-159">不過，在幕後，擁有的類型的確具有身分識別，但擁有者導覽屬性是此身分識別的一部分。</span><span class="sxs-lookup"><span data-stu-id="b9a96-159">However, under the covers, owned types do have the identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="b9a96-160">自有類型的執行個體身分識別不完全屬於它們自己。</span><span class="sxs-lookup"><span data-stu-id="b9a96-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="b9a96-161">它包含三個元件：</span><span class="sxs-lookup"><span data-stu-id="b9a96-161">It consists of three components:</span></span>

- <span data-ttu-id="b9a96-162">擁有者的身分識別</span><span class="sxs-lookup"><span data-stu-id="b9a96-162">The identity of the owner</span></span>

- <span data-ttu-id="b9a96-163">指向它們的導覽屬性</span><span class="sxs-lookup"><span data-stu-id="b9a96-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="b9a96-164">在擁有類型集合的情況下，EF Core 2.2 和更新版本) 支援獨立元件 (。</span><span class="sxs-lookup"><span data-stu-id="b9a96-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="b9a96-165">例如，在 eShopOnContainers 的訂購網域模型中，屬於訂單實體的一部分，Address 值物件在擁有者實體內實作為擁有的實體類型，也就是訂單實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="b9a96-166">`Address` 是在網域模型中未定義識別屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-166">`Address` is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="b9a96-167">它用做訂單類型的屬性，指定特定訂單的送貨地址。</span><span class="sxs-lookup"><span data-stu-id="b9a96-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="b9a96-168">依照慣例，會為擁有的類型建立陰影主索引鍵，而且會使用資料表分割將它對應至與擁有者相同的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9a96-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="b9a96-169">這允許以類似傳統 .NET Framework 的 EF6 使用複雜類型的方式，使用擁有的類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="b9a96-170">請務必注意，EF Core 慣例永遠不會探索到擁有的類型，所以您不必明確宣告它們。</span><span class="sxs-lookup"><span data-stu-id="b9a96-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="b9a96-171">在 eShopOnContainers 中，于 OrderingCoNtext.cs 檔案的方法內 `OnModelCreating()` ，會套用多個基礎結構設定。</span><span class="sxs-lookup"><span data-stu-id="b9a96-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="b9a96-172">其中一個與訂單實體有關。</span><span class="sxs-lookup"><span data-stu-id="b9a96-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="b9a96-173">下列程式碼會定義訂單實體的持續性基礎結構：</span><span class="sxs-lookup"><span data-stu-id="b9a96-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="b9a96-174">在先前的程式碼中，`orderConfiguration.OwnsOne(o => o.Address)` 方法指定 `Address` 屬性是 `Order` 類型的擁有的實體。</span><span class="sxs-lookup"><span data-stu-id="b9a96-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="b9a96-175">根據預設，EF Core 慣例會將擁有的實體類型的屬性資料庫資料行命名為 `EntityProperty_OwnedEntityProperty`。</span><span class="sxs-lookup"><span data-stu-id="b9a96-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="b9a96-176">因此，的內部屬性 `Address` 會出現在資料表中 `Orders` ，其中包含、和) 的名稱 `Address_Street` 、 `Address_City` (`State` 等等 `Country` `ZipCode` 。</span><span class="sxs-lookup"><span data-stu-id="b9a96-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="b9a96-177">您可以附加 `Property().HasColumnName()` fluent 方法重新命名這些資料行。</span><span class="sxs-lookup"><span data-stu-id="b9a96-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="b9a96-178">如果發生 `Address` 是公用屬性的情況，對應會如同下例：</span><span class="sxs-lookup"><span data-stu-id="b9a96-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="b9a96-179">您可以 `OwnsOne` 在流暢的對應中連結方法。</span><span class="sxs-lookup"><span data-stu-id="b9a96-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="b9a96-180">在下列假設性的範例中，`OrderDetails` 擁有 `BillingAddress` 和 `ShippingAddress`，它們兩個都是 `Address` 類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="b9a96-181">然後 `Order` 類型擁有 `OrderDetails`。</span><span class="sxs-lookup"><span data-stu-id="b9a96-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="b9a96-182">有關擁有的實體類型的其他詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9a96-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="b9a96-183">當您使用 OwnsOne fluent API 將導覽屬性設定為特定類型時，會定義自有類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="b9a96-184">在我們的中繼資料模型中，自有類型的定義由下列項目組成：擁有者類型、導覽屬性，以及自有類型的 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="b9a96-185">在我們的堆疊中，自有類型執行個體的身分識別 (金鑰) 是由擁有者類型的身分識別及自有類型的定義所組成。</span><span class="sxs-lookup"><span data-stu-id="b9a96-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="b9a96-186">擁有的實體功能</span><span class="sxs-lookup"><span data-stu-id="b9a96-186">Owned entities capabilities</span></span>

- <span data-ttu-id="b9a96-187">自有類型可以參考其他實體，可以是自有 (巢狀自有類型) 或非自有 (對其他實體的一般參考導覽屬性)。</span><span class="sxs-lookup"><span data-stu-id="b9a96-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="b9a96-188">您可以透過個別的導覽屬性，將相同的 CLR 類型對應為同一個擁有者實體中的不同自有類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="b9a96-189">資料表分割是依照慣例設定，但您可以選擇使用 ToTable 將擁有的類型對應到不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="b9a96-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="b9a96-190">積極式載入會在擁有的類型上自動執行，也就是不需要 `.Include()` 在查詢上呼叫。</span><span class="sxs-lookup"><span data-stu-id="b9a96-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="b9a96-191">可以 `[Owned]` 使用 EF Core 2.1 和更新版本的屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="b9a96-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="b9a96-192">可以處理所擁有類型的集合 (使用2.2 版和更新版本的) 。</span><span class="sxs-lookup"><span data-stu-id="b9a96-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="b9a96-193">擁有的實體限制</span><span class="sxs-lookup"><span data-stu-id="b9a96-193">Owned entities limitations</span></span>

- <span data-ttu-id="b9a96-194">您無法建立 `DbSet<T>` 由設計)  (的擁有類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="b9a96-195">您無法 `ModelBuilder.Entity<T>()` 在目前由設計)  (所擁有的類型上呼叫。</span><span class="sxs-lookup"><span data-stu-id="b9a96-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="b9a96-196">不支援選擇性的 (也就是，可以是可為 null) 擁有的類型，這些類型會與相同資料表中的擁有者對應 (也就是使用資料表分割) 。</span><span class="sxs-lookup"><span data-stu-id="b9a96-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="b9a96-197">這是因為對應是針對每個屬性進行的，因此 null 複雜值沒有個別的 sentinel。</span><span class="sxs-lookup"><span data-stu-id="b9a96-197">This is because mapping is done for each property, there is no  separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="b9a96-198">本身的型別不支援繼承對應，但您應該能夠將相同繼承階層的兩個分葉類型對應為不同的擁有類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="b9a96-199">EF Core 不會推論出它們屬於同一階層的事實。</span><span class="sxs-lookup"><span data-stu-id="b9a96-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="b9a96-200">EF6 複雜類型的主要差異</span><span class="sxs-lookup"><span data-stu-id="b9a96-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="b9a96-201">資料表分割是選擇性的，也就是說，它們可以選擇性地對應到不同的資料表，但仍然是擁有的類型。</span><span class="sxs-lookup"><span data-stu-id="b9a96-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="b9a96-202">它們可以參考其他實體 (也就是說，它們可以作為與其他非擁有類型) 關聯性的相依端。</span><span class="sxs-lookup"><span data-stu-id="b9a96-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b9a96-203">其他資源</span><span class="sxs-lookup"><span data-stu-id="b9a96-203">Additional resources</span></span>

- <span data-ttu-id="b9a96-204">**聖馬丁 Fowler。ValueObject 模式** </span><span class="sxs-lookup"><span data-stu-id="b9a96-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="b9a96-205">**Eric Evans。領域驅動設計：解決軟體核心的複雜度。**</span><span class="sxs-lookup"><span data-stu-id="b9a96-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="b9a96-206">(書籍；包含值物件的探討) </span><span class="sxs-lookup"><span data-stu-id="b9a96-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="b9a96-207">**Vaughn Vernon。實施領域導向設計。**</span><span class="sxs-lookup"><span data-stu-id="b9a96-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="b9a96-208">(書籍；包含值物件的探討) </span><span class="sxs-lookup"><span data-stu-id="b9a96-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="b9a96-209">**擁有的實體類型** </span><span class="sxs-lookup"><span data-stu-id="b9a96-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="b9a96-210">**陰影屬性** </span><span class="sxs-lookup"><span data-stu-id="b9a96-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="b9a96-211">**複雜類型和/或值物件**。</span><span class="sxs-lookup"><span data-stu-id="b9a96-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="b9a96-212">EF Core GitHub 存放庫 ([問題] 索引標籤) 的探討 </span><span class="sxs-lookup"><span data-stu-id="b9a96-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="b9a96-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="b9a96-213">**ValueObject.cs.**</span></span> <span data-ttu-id="b9a96-214">eShopOnContainers 中的基底值物件類別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="b9a96-215">**網址類別。**</span><span class="sxs-lookup"><span data-stu-id="b9a96-215">**Address class.**</span></span> <span data-ttu-id="b9a96-216">eShopOnContainers 中的範列值物件類別。</span><span class="sxs-lookup"><span data-stu-id="b9a96-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="b9a96-217">[上一個](seedwork-domain-model-base-classes-interfaces.md) 
> [下一步](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="b9a96-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>
