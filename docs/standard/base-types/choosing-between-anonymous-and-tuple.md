---
title: 在匿名和元組類型之間選擇
description: 瞭解何時適合在匿名型別和元組類型之間進行選擇。
author: IEvangelist
ms.author: dapine
ms.topic: conceptual
ms.date: 07/01/2020
ms.openlocfilehash: 1f171851c383862828600f6f43ce1e3fc1b3a168
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693080"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="e8c58-103">在匿名和元組類型之間選擇</span><span class="sxs-lookup"><span data-stu-id="e8c58-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="e8c58-104">選擇適當的類型牽涉到考慮其可用性、效能和取捨，相較于其他類型。</span><span class="sxs-lookup"><span data-stu-id="e8c58-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="e8c58-105">自 c # 3.0 起已提供匿名型別，但 <xref:System.Tuple%602?displayProperty=nameWithType> .NET Framework 4.0 引進了泛型型別。</span><span class="sxs-lookup"><span data-stu-id="e8c58-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="e8c58-106">自從起，新選項在語言層級支援上引進，像是 <xref:System.ValueTuple%602?displayProperty=nameWithType> 名稱所暗示的，提供具有匿名型別彈性的實值型別。</span><span class="sxs-lookup"><span data-stu-id="e8c58-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="e8c58-107">在本文中，您將瞭解何時適合選擇另一種類型。</span><span class="sxs-lookup"><span data-stu-id="e8c58-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="e8c58-108">可用性和功能</span><span class="sxs-lookup"><span data-stu-id="e8c58-108">Usability and functionality</span></span>

<span data-ttu-id="e8c58-109">匿名型別是在 c # 3.0 中引進的 Language-Integrated Query (LINQ) 運算式。</span><span class="sxs-lookup"><span data-stu-id="e8c58-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="e8c58-110">使用 LINQ，開發人員通常會將查詢的結果投射至匿名型別，這些型別會從他們正在使用的物件中保存一些 select 屬性。</span><span class="sxs-lookup"><span data-stu-id="e8c58-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="e8c58-111">請看下列範例，它會具現化 <xref:System.DateTime> 物件的陣列，並逐一查看其投射到具有兩個屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="e8c58-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="e8c58-112">匿名型別是使用運算子來具現化 [`new`](../../csharp/language-reference/operators/new-operator.md) ，而屬性名稱和類型則是從宣告推斷而來。</span><span class="sxs-lookup"><span data-stu-id="e8c58-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="e8c58-113">如果相同元件中有兩個或多個匿名物件初始化運算式指定的屬性順序順序相同，而且具有相同的名稱和類型，則編譯器會將這些物件視為相同型別的實例。</span><span class="sxs-lookup"><span data-stu-id="e8c58-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="e8c58-114">這些物件會共用編譯器產生的相同類型資訊。</span><span class="sxs-lookup"><span data-stu-id="e8c58-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="e8c58-115">先前的 c # 程式碼片段會使用兩個屬性來投影匿名型別，與下列編譯器產生的 c # 類別很類似：</span><span class="sxs-lookup"><span data-stu-id="e8c58-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="e8c58-116">如需詳細資訊，請參閱 [匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e8c58-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="e8c58-117">當元組投射到 LINQ 查詢時，也會有相同的功能，您可以選取屬性到元組中。</span><span class="sxs-lookup"><span data-stu-id="e8c58-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="e8c58-118">這些元組會流經查詢，就像匿名型別一樣。</span><span class="sxs-lookup"><span data-stu-id="e8c58-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="e8c58-119">現在請考慮使用下列範例 `System.Tuple<string, long>` 。</span><span class="sxs-lookup"><span data-stu-id="e8c58-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="e8c58-120">使用時 <xref:System.Tuple%602?displayProperty=nameWithType> ，實例會公開編號的專案屬性，例如 `Item1` 和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="e8c58-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="e8c58-121">這些屬性名稱可能會讓您更難以瞭解屬性值的意圖，因為屬性名稱只提供序數。</span><span class="sxs-lookup"><span data-stu-id="e8c58-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="e8c58-122">此外， `System.Tuple` 類型是參考型別 `class` 。</span><span class="sxs-lookup"><span data-stu-id="e8c58-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="e8c58-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>不過，是實值 `struct` 型別。</span><span class="sxs-lookup"><span data-stu-id="e8c58-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="e8c58-124">下列 c # 程式碼片段會使用 `ValueTuple<string, long>` 來投影至。</span><span class="sxs-lookup"><span data-stu-id="e8c58-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="e8c58-125">在這麼做時，它會使用常值語法來指派。</span><span class="sxs-lookup"><span data-stu-id="e8c58-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="e8c58-126">如需有關元組的詳細資訊，請參閱 [ (c # 參考) ](../../csharp/language-reference/builtin-types/value-tuples.md) 或 [元組 (Visual Basic) ](../../visual-basic/programming-guide/language-features/data-types/tuples.md)的元組類型。</span><span class="sxs-lookup"><span data-stu-id="e8c58-126">For more information about tuples, see [Tuple types (C# reference)](../../csharp/language-reference/builtin-types/value-tuples.md) or [Tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span></span>

<span data-ttu-id="e8c58-127">上述範例的功能相同，但它們的可用性和其基礎執行之間有些微差異。</span><span class="sxs-lookup"><span data-stu-id="e8c58-127">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="e8c58-128">權衡取捨</span><span class="sxs-lookup"><span data-stu-id="e8c58-128">Tradeoffs</span></span>

<span data-ttu-id="e8c58-129">您可能會想要一律使用 <xref:System.ValueTuple> over <xref:System.Tuple> 和匿名型別，但您應該考慮一些取捨。</span><span class="sxs-lookup"><span data-stu-id="e8c58-129">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="e8c58-130">這些 <xref:System.ValueTuple> 類型是可變動的，而 <xref:System.Tuple> 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="e8c58-130">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="e8c58-131">匿名型別可在運算式樹狀架構中使用，而元組則無法使用。</span><span class="sxs-lookup"><span data-stu-id="e8c58-131">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="e8c58-132">下表概述一些主要差異。</span><span class="sxs-lookup"><span data-stu-id="e8c58-132">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="e8c58-133">主要差異</span><span class="sxs-lookup"><span data-stu-id="e8c58-133">Key differences</span></span>

| <span data-ttu-id="e8c58-134">Name</span><span class="sxs-lookup"><span data-stu-id="e8c58-134">Name</span></span>                     | <span data-ttu-id="e8c58-135">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="e8c58-135">Access modifier</span></span> | <span data-ttu-id="e8c58-136">類型</span><span class="sxs-lookup"><span data-stu-id="e8c58-136">Type</span></span>     | <span data-ttu-id="e8c58-137">自訂成員名稱</span><span class="sxs-lookup"><span data-stu-id="e8c58-137">Custom member name</span></span> | <span data-ttu-id="e8c58-138">解構支援</span><span class="sxs-lookup"><span data-stu-id="e8c58-138">Deconstruction support</span></span> | <span data-ttu-id="e8c58-139">運算式樹狀架構支援</span><span class="sxs-lookup"><span data-stu-id="e8c58-139">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="e8c58-140">匿名型別</span><span class="sxs-lookup"><span data-stu-id="e8c58-140">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="e8c58-141">✔️</span><span class="sxs-lookup"><span data-stu-id="e8c58-141">✔️</span></span>                   | ❌                     | <span data-ttu-id="e8c58-142">✔️</span><span class="sxs-lookup"><span data-stu-id="e8c58-142">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="e8c58-143">✔️</span><span class="sxs-lookup"><span data-stu-id="e8c58-143">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="e8c58-144">✔️</span><span class="sxs-lookup"><span data-stu-id="e8c58-144">✔️</span></span>                   | <span data-ttu-id="e8c58-145">✔️</span><span class="sxs-lookup"><span data-stu-id="e8c58-145">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="e8c58-146">序列化</span><span class="sxs-lookup"><span data-stu-id="e8c58-146">Serialization</span></span>

<span data-ttu-id="e8c58-147">選擇類型時的一個重要考慮是，是否需要將它序列化。</span><span class="sxs-lookup"><span data-stu-id="e8c58-147">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="e8c58-148">序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。</span><span class="sxs-lookup"><span data-stu-id="e8c58-148">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="e8c58-149">如需詳細資訊，請參閱 [序列化](../../csharp/programming-guide/concepts/serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e8c58-149">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="e8c58-150">當序列化很重要時，最好 `class` 透過 `struct` 匿名型別或元組類型來建立或。</span><span class="sxs-lookup"><span data-stu-id="e8c58-150">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="e8c58-151">效能</span><span class="sxs-lookup"><span data-stu-id="e8c58-151">Performance</span></span>

<span data-ttu-id="e8c58-152">這些類型之間的效能取決於案例。</span><span class="sxs-lookup"><span data-stu-id="e8c58-152">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="e8c58-153">主要的影響牽涉到配置和複製之間的取捨。</span><span class="sxs-lookup"><span data-stu-id="e8c58-153">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="e8c58-154">在大部分的情況下，影響很小。</span><span class="sxs-lookup"><span data-stu-id="e8c58-154">In most scenarios, the impact is small.</span></span> <span data-ttu-id="e8c58-155">發生重大影響時，應該採取度量來通知決策。</span><span class="sxs-lookup"><span data-stu-id="e8c58-155">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="e8c58-156">結論</span><span class="sxs-lookup"><span data-stu-id="e8c58-156">Conclusion</span></span>

<span data-ttu-id="e8c58-157">當開發人員在元組和匿名型別之間進行選擇時，需要考慮幾個因素。</span><span class="sxs-lookup"><span data-stu-id="e8c58-157">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="e8c58-158">一般來說，如果您不是使用 [運算式樹狀](../../csharp/expression-trees.md)架構，而且您熟悉元組語法，則請選擇 <xref:System.ValueTuple> 其提供實值型別，而且可以彈性地命名屬性。</span><span class="sxs-lookup"><span data-stu-id="e8c58-158">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="e8c58-159">如果您是使用運算式樹狀架構，而且想要命名屬性，請選擇 [匿名型別]。</span><span class="sxs-lookup"><span data-stu-id="e8c58-159">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="e8c58-160">否則，使用 <xref:System.Tuple>。</span><span class="sxs-lookup"><span data-stu-id="e8c58-160">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8c58-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8c58-161">See also</span></span>

- [<span data-ttu-id="e8c58-162">匿名型別</span><span class="sxs-lookup"><span data-stu-id="e8c58-162">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="e8c58-163">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="e8c58-163">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="e8c58-164">元組類型 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="e8c58-164">Tuple types (C# reference)</span></span>](../../csharp/language-reference/builtin-types/value-tuples.md)
- [<span data-ttu-id="e8c58-165">元組 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="e8c58-165">Tuples (Visual Basic)</span></span>](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [<span data-ttu-id="e8c58-166">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e8c58-166">Type design guidelines</span></span>](../design-guidelines/type.md)
