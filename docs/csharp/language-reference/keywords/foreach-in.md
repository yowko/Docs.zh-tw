---
title: C# foreach 陳述式
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401884"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="fc60a-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fc60a-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="fc60a-103">`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="fc60a-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="fc60a-104">`foreach`語句不限於這些類型，而且可以套用至符合下列條件之任何類型的實例：</span><span class="sxs-lookup"><span data-stu-id="fc60a-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="fc60a-105">具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="fc60a-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="fc60a-106">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="fc60a-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="fc60a-107">在大部分的情況下， `foreach` `IEnumerable<T>` 會逐一查看每個元素的類型為的運算式 `T` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="fc60a-108">不過，元素可能是任何具有從屬性類型隱含或明確轉換的類型 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="fc60a-109">如果 `Current` 屬性傳回 `SomeType` ，則元素的類型可能是：</span><span class="sxs-lookup"><span data-stu-id="fc60a-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="fc60a-110">的任何基類 `SomeType` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="fc60a-111">所執行的任何介面 `SomeType` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="fc60a-112">此外，如果 `SomeType` 是 `class` 或， `interface` 而不是 `sealed` ，則元素的類型可能包括：</span><span class="sxs-lookup"><span data-stu-id="fc60a-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="fc60a-113">衍生自的任何類型 `SomeType` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="fc60a-114">任何任意介面。</span><span class="sxs-lookup"><span data-stu-id="fc60a-114">Any arbitrary interface.</span></span> <span data-ttu-id="fc60a-115">允許任何介面，因為任何介面都可以由衍生自或執行的類別來執行 `SomeType` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="fc60a-116">您可以使用符合上述規則的任何類型來宣告反復專案變數。</span><span class="sxs-lookup"><span data-stu-id="fc60a-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="fc60a-117">如果從轉換 `SomeType` 成反覆運算變數的類型需要明確轉換，該作業可能會 <xref:System.InvalidCastException> 在轉換失敗時擲回。</span><span class="sxs-lookup"><span data-stu-id="fc60a-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="fc60a-118">從 c # 7.3 開始，如果枚舉器的 `Current` 屬性傳回[參考傳回值](ref.md#reference-return-values)（ `ref T` 其中 `T` 是集合元素的類型），您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="fc60a-119">從 c # 8.0 開始， `await` 當集合類型執行介面時，可以將運算子套用至 `foreach` 語句 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="fc60a-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="fc60a-120">當下一個元素以非同步方式抓取時，迴圈的每個反復專案都可能會暫停。</span><span class="sxs-lookup"><span data-stu-id="fc60a-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="fc60a-121">根據預設，資料流程元素會在已捕捉的內容中處理。</span><span class="sxs-lookup"><span data-stu-id="fc60a-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="fc60a-122">如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="fc60a-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="fc60a-123">如需同步處理內容及取得目前內容的詳細資訊，請參閱有關[使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="fc60a-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="fc60a-124">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="fc60a-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="fc60a-125">您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或[throw](throw.md)語句來結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="fc60a-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="fc60a-126">若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="fc60a-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="fc60a-127">如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。</span><span class="sxs-lookup"><span data-stu-id="fc60a-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="fc60a-128">範例</span><span class="sxs-lookup"><span data-stu-id="fc60a-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="fc60a-129">下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：</span><span class="sxs-lookup"><span data-stu-id="fc60a-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="fc60a-130">下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="fc60a-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="fc60a-131">下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。</span><span class="sxs-lookup"><span data-stu-id="fc60a-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="fc60a-132">`ref readonly` 版本會逐一查看集合以列印所有值。</span><span class="sxs-lookup"><span data-stu-id="fc60a-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="fc60a-133">`readonly` 宣告會使用隱含的本機變數宣告。</span><span class="sxs-lookup"><span data-stu-id="fc60a-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="fc60a-134">您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。</span><span class="sxs-lookup"><span data-stu-id="fc60a-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="fc60a-135">下列範例會使用 `await foreach` 來逐一查看會以非同步方式產生每個元素的集合：</span><span class="sxs-lookup"><span data-stu-id="fc60a-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="fc60a-136">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="fc60a-136">C# language specification</span></span>

<span data-ttu-id="fc60a-137">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="fc60a-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc60a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc60a-138">See also</span></span>

- [<span data-ttu-id="fc60a-139">C # 參考</span><span class="sxs-lookup"><span data-stu-id="fc60a-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc60a-140">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fc60a-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc60a-141">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="fc60a-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fc60a-142">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="fc60a-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="fc60a-143">for 陳述式</span><span class="sxs-lookup"><span data-stu-id="fc60a-143">for statement</span></span>](for.md)
