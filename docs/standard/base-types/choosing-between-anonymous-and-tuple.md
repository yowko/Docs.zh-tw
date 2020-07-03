---
title: 在匿名和元組類型之間選擇
description: 瞭解何時適合在匿名型別和元組類型之間進行選擇。
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 24ab770d709b9f3968f4c7fe4b01eb0729dbd751
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853996"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="62de5-103">在匿名和元組類型之間選擇</span><span class="sxs-lookup"><span data-stu-id="62de5-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="62de5-104">選擇適當的類型牽涉到考慮與其他類型相較之下的可用性、效能和取捨。</span><span class="sxs-lookup"><span data-stu-id="62de5-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="62de5-105">自 c # 3.0 開始已提供匿名型別，而泛型 <xref:System.Tuple%602?displayProperty=nameWithType> 類型是在 .NET Framework 4.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="62de5-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="62de5-106">自起，已引進語言層級支援的新選項，例如 <xref:System.ValueTuple%602?displayProperty=nameWithType> ，如名稱所示，則提供具有匿名型別彈性的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="62de5-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="62de5-107">在本文中，您將瞭解何時適合選擇其中一種類型。</span><span class="sxs-lookup"><span data-stu-id="62de5-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="62de5-108">可用性和功能</span><span class="sxs-lookup"><span data-stu-id="62de5-108">Usability and functionality</span></span>

<span data-ttu-id="62de5-109">匿名型別是使用語言整合式查詢（LINQ）運算式，在 c # 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="62de5-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="62de5-110">使用 LINQ 時，開發人員通常會將查詢的結果投影到匿名型別，其中包含所要使用之物件的幾個 select 屬性。</span><span class="sxs-lookup"><span data-stu-id="62de5-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="62de5-111">請考慮下列範例，其會具現化 <xref:System.DateTime> 物件的陣列，並逐一查看其投射為具有兩個屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="62de5-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

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

<span data-ttu-id="62de5-112">匿名型別是使用運算子來具現化 [`new`](../../csharp/language-reference/operators/new-operator.md) ，而屬性名稱和類型則是從宣告推斷而來。</span><span class="sxs-lookup"><span data-stu-id="62de5-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="62de5-113">如果相同元件中的兩個或多個匿名物件初始化運算式指定順序相同且具有相同名稱和類型的屬性，則編譯器會將這些物件視為相同類型的實例。</span><span class="sxs-lookup"><span data-stu-id="62de5-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="62de5-114">這些物件會共用編譯器產生的相同類型資訊。</span><span class="sxs-lookup"><span data-stu-id="62de5-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="62de5-115">先前的 c # 程式碼片段會使用兩個屬性來投射匿名型別，與下列編譯器產生的 c # 類別非常類似：</span><span class="sxs-lookup"><span data-stu-id="62de5-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

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

<span data-ttu-id="62de5-116">如需詳細資訊，請參閱[匿名](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="62de5-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="62de5-117">在投射至 LINQ 查詢時，元組也存在相同的功能，您可以選取屬性到元組中。</span><span class="sxs-lookup"><span data-stu-id="62de5-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="62de5-118">這些元組會流經查詢，就像匿名型別一樣。</span><span class="sxs-lookup"><span data-stu-id="62de5-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="62de5-119">現在請考慮下列使用的範例 `System.Tuple<string, long>` 。</span><span class="sxs-lookup"><span data-stu-id="62de5-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

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

<span data-ttu-id="62de5-120">使用 <xref:System.Tuple%602?displayProperty=nameWithType> ，實例會公開編號的專案屬性，例如 `Item1` 、和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="62de5-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="62de5-121">這些屬性名稱可能會讓您更難以瞭解屬性值的用途，因為屬性名稱只會提供序數。</span><span class="sxs-lookup"><span data-stu-id="62de5-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="62de5-122">此外， `System.Tuple` 類型是引用 `class` 類型。</span><span class="sxs-lookup"><span data-stu-id="62de5-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="62de5-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>不過，是實值 `struct` 型別。</span><span class="sxs-lookup"><span data-stu-id="62de5-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="62de5-124">下列 c # 程式碼片段會使用 `ValueTuple<string, long>` 來投影至。</span><span class="sxs-lookup"><span data-stu-id="62de5-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="62de5-125">在這麼做的情況下，它會使用常值語法來指派。</span><span class="sxs-lookup"><span data-stu-id="62de5-125">In doing so, it assigns using a literal syntax.</span></span>

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

<span data-ttu-id="62de5-126">C # 提供具有類型的元組語言支援 <xref:System.ValueTuple> ，以及的語義：</span><span class="sxs-lookup"><span data-stu-id="62de5-126">C# provides language support of tuples with the <xref:System.ValueTuple> type, and semantics for:</span></span>

- [<span data-ttu-id="62de5-127">元組指派</span><span class="sxs-lookup"><span data-stu-id="62de5-127">Tuple assignment</span></span>](../../csharp/tuples.md#assignment-and-tuples)
- <span data-ttu-id="62de5-128">[元組解構](../../csharp/deconstruct.md)（不限於元組）</span><span class="sxs-lookup"><span data-stu-id="62de5-128">[Tuple deconstruction](../../csharp/deconstruct.md) (not limited to tuples)</span></span>
- [<span data-ttu-id="62de5-129">元組等號檢查</span><span class="sxs-lookup"><span data-stu-id="62de5-129">Tuple equality checks</span></span>](../../csharp/tuples.md#equality-and-tuples)
- [<span data-ttu-id="62de5-130">元組投影初始設定式</span><span class="sxs-lookup"><span data-stu-id="62de5-130">Tuple projection initializers</span></span>](../../csharp/tuples.md#tuple-projection-initializers)

<span data-ttu-id="62de5-131">不過，上述範例的功能完全相同。其可用性和其基礎的執行方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="62de5-131">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="62de5-132">權衡取捨</span><span class="sxs-lookup"><span data-stu-id="62de5-132">Tradeoffs</span></span>

<span data-ttu-id="62de5-133">您可能想要一律使用 <xref:System.ValueTuple> over <xref:System.Tuple> 和匿名型別，但您應該考慮一些取捨。</span><span class="sxs-lookup"><span data-stu-id="62de5-133">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="62de5-134"><xref:System.ValueTuple>類型是可變動的，而 <xref:System.Tuple> 是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="62de5-134">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="62de5-135">匿名型別可以在運算式樹狀架構中使用，而元組則不能。</span><span class="sxs-lookup"><span data-stu-id="62de5-135">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="62de5-136">下表概述一些主要差異。</span><span class="sxs-lookup"><span data-stu-id="62de5-136">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="62de5-137">重要差異</span><span class="sxs-lookup"><span data-stu-id="62de5-137">Key differences</span></span>

| <span data-ttu-id="62de5-138">名稱</span><span class="sxs-lookup"><span data-stu-id="62de5-138">Name</span></span>                     | <span data-ttu-id="62de5-139">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="62de5-139">Access modifier</span></span> | <span data-ttu-id="62de5-140">類型</span><span class="sxs-lookup"><span data-stu-id="62de5-140">Type</span></span>     | <span data-ttu-id="62de5-141">自訂屬性名稱</span><span class="sxs-lookup"><span data-stu-id="62de5-141">Custom property name</span></span> | <span data-ttu-id="62de5-142">解構支援</span><span class="sxs-lookup"><span data-stu-id="62de5-142">Deconstruction support</span></span> | <span data-ttu-id="62de5-143">運算式樹狀架構支援</span><span class="sxs-lookup"><span data-stu-id="62de5-143">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="62de5-144">匿名型別</span><span class="sxs-lookup"><span data-stu-id="62de5-144">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="62de5-145">✔️</span><span class="sxs-lookup"><span data-stu-id="62de5-145">✔️</span></span>                   | ❌                     | <span data-ttu-id="62de5-146">✔️</span><span class="sxs-lookup"><span data-stu-id="62de5-146">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="62de5-147">✔️</span><span class="sxs-lookup"><span data-stu-id="62de5-147">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="62de5-148">✔️</span><span class="sxs-lookup"><span data-stu-id="62de5-148">✔️</span></span>                   | <span data-ttu-id="62de5-149">✔️</span><span class="sxs-lookup"><span data-stu-id="62de5-149">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="62de5-150">序列化</span><span class="sxs-lookup"><span data-stu-id="62de5-150">Serialization</span></span>

<span data-ttu-id="62de5-151">選擇類型時，有一個重要的考慮，那就是是否需要將它序列化。</span><span class="sxs-lookup"><span data-stu-id="62de5-151">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="62de5-152">序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。</span><span class="sxs-lookup"><span data-stu-id="62de5-152">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="62de5-153">如需詳細資訊，請參閱[序列化](../../csharp/programming-guide/concepts/serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="62de5-153">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="62de5-154">當序列化很重要時， `class` `struct` 最好是透過匿名型別或元組類型來建立或。</span><span class="sxs-lookup"><span data-stu-id="62de5-154">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="62de5-155">效能</span><span class="sxs-lookup"><span data-stu-id="62de5-155">Performance</span></span>

<span data-ttu-id="62de5-156">這些類型之間的效能取決於案例。</span><span class="sxs-lookup"><span data-stu-id="62de5-156">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="62de5-157">主要的影響牽涉到配置與複製之間的取捨。</span><span class="sxs-lookup"><span data-stu-id="62de5-157">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="62de5-158">在大部分的情況下，影響很小。</span><span class="sxs-lookup"><span data-stu-id="62de5-158">In most scenarios, the impact is small.</span></span> <span data-ttu-id="62de5-159">發生重大影響時，應該採取測量來通知決策。</span><span class="sxs-lookup"><span data-stu-id="62de5-159">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="62de5-160">結論</span><span class="sxs-lookup"><span data-stu-id="62de5-160">Conclusion</span></span>

<span data-ttu-id="62de5-161">身為開發人員選擇元組和匿名型別，有幾個因素需要考慮。</span><span class="sxs-lookup"><span data-stu-id="62de5-161">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="62de5-162">一般來說，如果您不是使用[運算式樹狀](../../csharp/expression-trees.md)架構，而且您很熟悉元組語法，請選擇， <xref:System.ValueTuple> 因為它們提供實值型別並具有名稱屬性的彈性。</span><span class="sxs-lookup"><span data-stu-id="62de5-162">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="62de5-163">如果您是使用運算式樹狀架構，而且想要命名屬性，請選擇 [匿名型別]。</span><span class="sxs-lookup"><span data-stu-id="62de5-163">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="62de5-164">否則，使用 <xref:System.Tuple>。</span><span class="sxs-lookup"><span data-stu-id="62de5-164">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="62de5-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62de5-165">See also</span></span>

- [<span data-ttu-id="62de5-166">匿名型別</span><span class="sxs-lookup"><span data-stu-id="62de5-166">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="62de5-167">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="62de5-167">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="62de5-168">元組類型</span><span class="sxs-lookup"><span data-stu-id="62de5-168">Tuple types</span></span>](../../csharp/tuples.md)
- [<span data-ttu-id="62de5-169">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="62de5-169">Type design guidelines</span></span>](../design-guidelines/type.md)
