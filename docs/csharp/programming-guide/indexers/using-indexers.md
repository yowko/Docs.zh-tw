---
title: 使用索引子 - C# 程式設計指南
description: '瞭解如何在 c # 中宣告和使用類別、結構或介面的索引子。 本文包含範例程式碼。'
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: a8a9e05c1d2e44841177a924c6ff51c6c9e6a05a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301862"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="0d718-104">使用索引子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0d718-104">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="0d718-105">索引子是一種語法便利性，可讓您建立用戶端應用程式可當做陣列存取的[類別](../../language-reference/keywords/class.md)、[結構](../../language-reference/builtin-types/struct.md)或[介面](../../language-reference/keywords/interface.md)。</span><span class="sxs-lookup"><span data-stu-id="0d718-105">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="0d718-106">編譯器會產生 `Item` 屬性（如果存在，則為另一個名稱為的屬性 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ），以及適當的存取子方法。</span><span class="sxs-lookup"><span data-stu-id="0d718-106">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="0d718-107">索引子最常實作於類型中，而類型的主要用途是封裝內部集合或陣列。</span><span class="sxs-lookup"><span data-stu-id="0d718-107">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="0d718-108">例如，假設您有一個類別，代表在24小時期間內，以 `TempRecord` 10 個不同時間記錄的華氏溫度。</span><span class="sxs-lookup"><span data-stu-id="0d718-108">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="0d718-109">類別包含用 `temps` `float[]` 來儲存溫度值的類型陣列。</span><span class="sxs-lookup"><span data-stu-id="0d718-109">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="0d718-110">透過在此類別中實作索引子，用戶端能以 `TempRecord` 執行個體中 `float temp = tempRecord[4]` 的形式 (而非 `float temp = tempRecord.temps[4]`) 來存取溫度。</span><span class="sxs-lookup"><span data-stu-id="0d718-110">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="0d718-111">索引子標記法不只會簡化用戶端應用程式的語法;它也讓其他開發人員瞭解類別和其用途更直覺化。</span><span class="sxs-lookup"><span data-stu-id="0d718-111">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="0d718-112">若要在類別或結構上宣告索引子，請使用 [this](../../language-reference/keywords/this.md) 關鍵字，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0d718-112">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="0d718-113">宣告索引子將會在物件上自動產生名為的屬性 `Item` 。</span><span class="sxs-lookup"><span data-stu-id="0d718-113">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="0d718-114">`Item`無法直接從實例[成員存取運算式](../../language-reference/operators/member-access-operators.md#member-access-expression-)存取屬性。</span><span class="sxs-lookup"><span data-stu-id="0d718-114">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="0d718-115">此外，如果您 `Item` 使用索引子將自己的屬性新增至物件，將會收到[CS0102 編譯器錯誤](../../misc/cs0102.md)。</span><span class="sxs-lookup"><span data-stu-id="0d718-115">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="0d718-116">若要避免這個錯誤，請使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 重新命名索引子，如下所述。</span><span class="sxs-lookup"><span data-stu-id="0d718-116">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d718-117">備註</span><span class="sxs-lookup"><span data-stu-id="0d718-117">Remarks</span></span>

<span data-ttu-id="0d718-118">索引子類型和其參數類型至少必須可以像索引子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="0d718-118">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="0d718-119">如需存取範圍層級的詳細資訊，請參閱[存取修飾詞](../../language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="0d718-119">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="0d718-120">如需如何搭配使用索引子與介面的詳細資訊，請參閱[介面索引子](./indexers-in-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="0d718-120">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="0d718-121">索引子的簽章包含其型式參數的數目和類型。</span><span class="sxs-lookup"><span data-stu-id="0d718-121">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="0d718-122">它不包含索引子類型或正式參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d718-122">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="0d718-123">如果您在相同的類別中宣告多個索引子，則它們必須具有不同的簽章。</span><span class="sxs-lookup"><span data-stu-id="0d718-123">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="0d718-124">索引子值不會分類為變數；因此，您無法將索引子值傳遞為 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。</span><span class="sxs-lookup"><span data-stu-id="0d718-124">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="0d718-125">若要以其他語言可使用的名稱提供索引子，請使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="0d718-125">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="0d718-126">此索引子會有名稱 `TheItem` ，因為它是由索引子名稱屬性所覆寫。</span><span class="sxs-lookup"><span data-stu-id="0d718-126">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="0d718-127">根據預設，索引子名稱是 `Item` 。</span><span class="sxs-lookup"><span data-stu-id="0d718-127">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="0d718-128">範例 1</span><span class="sxs-lookup"><span data-stu-id="0d718-128">Example 1</span></span>

<span data-ttu-id="0d718-129">下列範例示範如何宣告私用陣列欄位 `temps` 和索引子。</span><span class="sxs-lookup"><span data-stu-id="0d718-129">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="0d718-130">索引子可讓您直接存取執行個體 `tempRecord[i]`。</span><span class="sxs-lookup"><span data-stu-id="0d718-130">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="0d718-131">使用索引子的替代方式是將陣列宣告為 [public](../../language-reference/keywords/public.md) 成員，並直接存取其成員 `tempRecord.temps[i]`。</span><span class="sxs-lookup"><span data-stu-id="0d718-131">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="0d718-132">請注意，評估索引子的存取時 (例如，在 `Console.Write` 陳述式中)，會叫用 [get](../../language-reference/keywords/get.md) 存取子。</span><span class="sxs-lookup"><span data-stu-id="0d718-132">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="0d718-133">因此，如果沒有 `get` 存取子，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="0d718-133">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="0d718-134">使用其他值編製索引</span><span class="sxs-lookup"><span data-stu-id="0d718-134">Indexing using other values</span></span>

<span data-ttu-id="0d718-135">C# 不會將索引子參數類型限制為整數。</span><span class="sxs-lookup"><span data-stu-id="0d718-135">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="0d718-136">例如，搭配使用字串與索引子可能十分有用。</span><span class="sxs-lookup"><span data-stu-id="0d718-136">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="0d718-137">在集合中搜尋字串，並傳回適當的值，可能會實作這類索引子。</span><span class="sxs-lookup"><span data-stu-id="0d718-137">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="0d718-138">當存取子可以多載時，字串和整數版本可以並存。</span><span class="sxs-lookup"><span data-stu-id="0d718-138">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="0d718-139">範例 2</span><span class="sxs-lookup"><span data-stu-id="0d718-139">Example 2</span></span>

<span data-ttu-id="0d718-140">下列範例宣告的類別會儲存週中的日。</span><span class="sxs-lookup"><span data-stu-id="0d718-140">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="0d718-141">`get` 存取子接受字串 (日的名稱)，並傳回對應的整數。</span><span class="sxs-lookup"><span data-stu-id="0d718-141">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="0d718-142">例如，"Sunday" 會傳回 0，"Monday" 會傳回 1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0d718-142">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="0d718-143">使用範例2</span><span class="sxs-lookup"><span data-stu-id="0d718-143">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="0d718-144">範例 3</span><span class="sxs-lookup"><span data-stu-id="0d718-144">Example 3</span></span>

<span data-ttu-id="0d718-145">下列範例會宣告一個類別，它會使用列舉來儲存一周的哪幾天 <xref:System.DayOfWeek?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="0d718-145">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="0d718-146">`get`存取子會接受 `DayOfWeek` ，其值為 day，並傳回對應的整數。</span><span class="sxs-lookup"><span data-stu-id="0d718-146">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="0d718-147">例如，會傳回 `DayOfWeek.Sunday` 0，傳回 `DayOfWeek.Monday` 1，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0d718-147">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="0d718-148">使用範例3</span><span class="sxs-lookup"><span data-stu-id="0d718-148">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="0d718-149">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0d718-149">Robust programming</span></span>

<span data-ttu-id="0d718-150">有兩種主要的方式可以改善索引子的安全性和可靠性：</span><span class="sxs-lookup"><span data-stu-id="0d718-150">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="0d718-151">請務必包含某種類型的錯誤處理策略來處理用戶端程式碼傳入無效索引值的機會。</span><span class="sxs-lookup"><span data-stu-id="0d718-151">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="0d718-152">在本主題稍早的第一個範例中，TempRecord 類別提供 Length 屬性，以讓用戶端程式碼先確認輸入，再將其傳遞給索引子。</span><span class="sxs-lookup"><span data-stu-id="0d718-152">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="0d718-153">您也可以將錯誤處理程式碼放在索引子本身內。</span><span class="sxs-lookup"><span data-stu-id="0d718-153">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="0d718-154">請務必為使用者記載您在索引子存取子內擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0d718-154">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="0d718-155">將 [get](../../language-reference/keywords/get.md) 與 [set](../../language-reference/keywords/set.md) 存取子的存取範圍設定為合理限制。</span><span class="sxs-lookup"><span data-stu-id="0d718-155">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="0d718-156">這對 `set` 存取子特別重要。</span><span class="sxs-lookup"><span data-stu-id="0d718-156">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="0d718-157">如需詳細資訊，請參閱[限制存取子的存取範圍](../classes-and-structs/restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="0d718-157">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d718-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d718-158">See also</span></span>

- [<span data-ttu-id="0d718-159">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0d718-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0d718-160">索引子</span><span class="sxs-lookup"><span data-stu-id="0d718-160">Indexers</span></span>](./index.md)
- [<span data-ttu-id="0d718-161">屬性</span><span class="sxs-lookup"><span data-stu-id="0d718-161">Properties</span></span>](../classes-and-structs/properties.md)
