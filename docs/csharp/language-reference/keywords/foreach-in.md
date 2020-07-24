---
title: C# foreach 陳述式
ms.date: 07/22/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 4af431d29e538c1516efeaad3008eaa3b2229ece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104246"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="17764-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="17764-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="17764-103">`foreach`語句會針對實作為或介面之類型實例中的每個專案執行語句或語句區塊 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="17764-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="17764-104">`foreach`語句不限於那些類型。</span><span class="sxs-lookup"><span data-stu-id="17764-104">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="17764-105">您可以將它與符合下列條件的任何類型實例搭配使用：</span><span class="sxs-lookup"><span data-stu-id="17764-105">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="17764-106">型別具有公用無參數 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別，</span><span class="sxs-lookup"><span data-stu-id="17764-106">a type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="17764-107">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="17764-107">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="17764-108">下列範例 `foreach` 會使用語句 <xref:System.Span%601?displayProperty=nameWithType> 搭配類型的實例，而不會執行任何介面：</span><span class="sxs-lookup"><span data-stu-id="17764-108">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="17764-109">從 c # 7.3 開始，如果枚舉器的 `Current` 屬性傳回[參考傳回值](ref.md#reference-return-values)（ `ref T` 其中 `T` 是集合元素的類型），您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="17764-109">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="17764-110">從 c # 8.0 開始，您可以使用 `await foreach` 語句來取用非同步資料資料流程，也就是實作為介面的集合型別 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="17764-110">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="17764-111">當下一個元素以非同步方式抓取時，迴圈的每個反復專案都可能會暫停。</span><span class="sxs-lookup"><span data-stu-id="17764-111">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="17764-112">下列範例顯示如何使用 `await foreach` 語句：</span><span class="sxs-lookup"><span data-stu-id="17764-112">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="17764-113">根據預設，資料流程元素會在已捕捉的內容中處理。</span><span class="sxs-lookup"><span data-stu-id="17764-113">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="17764-114">如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="17764-114">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="17764-115">如需同步處理內容和捕捉目前內容的詳細資訊，請參閱[使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="17764-115">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="17764-116">如需非同步資料流程的詳細資訊，請參閱[c # 8.0 的新功能](../../whats-new/csharp-8.md)一文中的[非同步資料流程](../../whats-new/csharp-8.md#asynchronous-streams)一節。</span><span class="sxs-lookup"><span data-stu-id="17764-116">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="17764-117">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="17764-117">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="17764-118">您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或[throw](throw.md)語句來結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="17764-118">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="17764-119">若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="17764-119">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="17764-120">如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。</span><span class="sxs-lookup"><span data-stu-id="17764-120">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="17764-121">反復專案變數的類型</span><span class="sxs-lookup"><span data-stu-id="17764-121">Type of an iteration variable</span></span>

<span data-ttu-id="17764-122">您可以使用 `var` 關鍵字，讓編譯器推斷語句中反覆運算變數的類型 `foreach` ，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="17764-122">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="17764-123">您也可以明確指定反復專案變數的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="17764-123">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="17764-124">在上述表單中， `T` 集合元素的類型必須隱含或明確地轉換成 `V` 反覆運算變數的類型。</span><span class="sxs-lookup"><span data-stu-id="17764-124">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="17764-125">如果從到的明確 `T` 轉換 `V` 在執行時間失敗，則語句會擲回 `foreach` <xref:System.InvalidCastException> 。</span><span class="sxs-lookup"><span data-stu-id="17764-125">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="17764-126">例如，如果 `T` 是非密封的類別類型， `V` 可以是任何介面類別型，即使不是要執行的也一樣 `T` 。</span><span class="sxs-lookup"><span data-stu-id="17764-126">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="17764-127">在執行時間，集合元素的類型可能是衍生自並實際執行的專案 `T` `V` 。</span><span class="sxs-lookup"><span data-stu-id="17764-127">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="17764-128">如果不是這種情況， <xref:System.InvalidCastException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="17764-128">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17764-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="17764-129">C# language specification</span></span>

<span data-ttu-id="17764-130">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="17764-130">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17764-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="17764-131">See also</span></span>

- [<span data-ttu-id="17764-132">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="17764-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="17764-133">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="17764-133">C# keywords</span></span>](index.md)
- [<span data-ttu-id="17764-134">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="17764-134">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="17764-135">for 陳述式</span><span class="sxs-lookup"><span data-stu-id="17764-135">for statement</span></span>](for.md)
