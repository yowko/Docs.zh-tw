---
title: C# foreach 陳述式
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 188d909fd33b14755d9b121953b1fa434ecf536d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738820"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="5d6b0-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5d6b0-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="5d6b0-103">`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="5d6b0-104">`foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="5d6b0-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="5d6b0-105">具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="5d6b0-106">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="5d6b0-107">從 C# 7.3 開始,如果枚舉`Current`器的屬性傳回`ref T`[引用傳回值](ref.md#reference-return-values)(集合元素的`ref readonly`類型`T`),可以使用`ref`或修改器聲明反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="5d6b0-108">從 C# 8.0`await`開始,當`foreach`<xref:System.Collections.Generic.IAsyncEnumerable%601>集合類型實現 介面時,運算元可以應用於語句。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="5d6b0-109">迴圈的每個反覆運算都可以在非同步檢索下一個元素時掛起。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="5d6b0-110">默認情況元素在捕獲的上下文中處理。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="5d6b0-111">如果要禁用上下文捕獲,請使用<xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>擴展方法。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="5d6b0-112">有關同步上下文和捕獲當前上下文的詳細資訊,請參閱有關[使用基於任務的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="5d6b0-113">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="5d6b0-114">您還可以通過`foreach`[goto、](goto.md)[傳回](return.md)或[引發](throw.md)語句退出迴圈。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-114">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="5d6b0-115">若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="5d6b0-116">如果語句的`foreach`源集合為空,則不會執行和跳`foreach`過 迴圈的正文。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="5d6b0-117">範例</span><span class="sxs-lookup"><span data-stu-id="5d6b0-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="5d6b0-118">下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：</span><span class="sxs-lookup"><span data-stu-id="5d6b0-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="5d6b0-119">下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="5d6b0-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="5d6b0-120">下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="5d6b0-121">`ref readonly` 版本會逐一查看集合以列印所有值。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="5d6b0-122">`readonly` 宣告會使用隱含的本機變數宣告。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="5d6b0-123">您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="5d6b0-124">以下範例用於`await foreach`發代非同步產生每個元素的集合:</span><span class="sxs-lookup"><span data-stu-id="5d6b0-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="5d6b0-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5d6b0-125">C# language specification</span></span>

<span data-ttu-id="5d6b0-126">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="5d6b0-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d6b0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d6b0-127">See also</span></span>

- [<span data-ttu-id="5d6b0-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5d6b0-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5d6b0-129">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="5d6b0-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5d6b0-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5d6b0-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5d6b0-131">將 foreach 與陣列一起使用</span><span class="sxs-lookup"><span data-stu-id="5d6b0-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="5d6b0-132">用於語句</span><span class="sxs-lookup"><span data-stu-id="5d6b0-132">for statement</span></span>](for.md)
