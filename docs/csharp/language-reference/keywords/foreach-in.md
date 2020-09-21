---
description: foreach、in (C# 參考)
title: C# foreach 陳述式
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828886"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="63f83-103">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="63f83-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="63f83-104">`foreach`語句會針對實作為或介面之型別的實例中的每個專案，執行語句或語句區塊 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="63f83-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="63f83-105">`foreach`語句不限於這些類型。</span><span class="sxs-lookup"><span data-stu-id="63f83-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="63f83-106">您可以將它用於符合下列條件之任何類型的實例：</span><span class="sxs-lookup"><span data-stu-id="63f83-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="63f83-107">型別具有公用無參數 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="63f83-107">A type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type.</span></span> <span data-ttu-id="63f83-108">從 c # 9.0 開始， `GetEnumerator` 方法可以是類型的 [擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="63f83-108">Beginning with C# 9.0, the `GetEnumerator` method can be a type's [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>
- <span data-ttu-id="63f83-109">方法的傳回型別 `GetEnumerator` 具有公用 `Current` 屬性，以及其傳回型別為的公用無參數 `MoveNext` 方法 <xref:System.Boolean> 。</span><span class="sxs-lookup"><span data-stu-id="63f83-109">The return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="63f83-110">下列範例 `foreach` 會使用語句 <xref:System.Span%601?displayProperty=nameWithType> 搭配類型的實例，而不會執行任何介面：</span><span class="sxs-lookup"><span data-stu-id="63f83-110">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="63f83-111">從 c # 7.3 開始，如果列舉 `Current` 值的屬性傳回 [參考傳回值](ref.md#reference-return-values) (`ref T` 其中 `T` 是集合元素) 的型別，您可以使用或修飾詞來宣告反覆運算變數 `ref` `ref readonly` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="63f83-111">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="63f83-112">從 c # 8.0 開始，您可以使用 `await foreach` 語句來取用非同步資料資料流程，也就是實作為介面的集合型別 <xref:System.Collections.Generic.IAsyncEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="63f83-112">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="63f83-113">迴圈的每個反復專案可能會暫停，而下一個元素則以非同步方式抓取。</span><span class="sxs-lookup"><span data-stu-id="63f83-113">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="63f83-114">下列範例顯示如何使用 `await foreach` 語句：</span><span class="sxs-lookup"><span data-stu-id="63f83-114">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="63f83-115">根據預設，資料流程專案會在已捕捉的內容中處理。</span><span class="sxs-lookup"><span data-stu-id="63f83-115">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="63f83-116">如果您想要停用內容的捕捉，請使用 <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="63f83-116">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="63f83-117">如需同步處理內容和取得目前內容的詳細資訊，請參閱 [使用以工作為基礎的非同步模式](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="63f83-117">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="63f83-118">如需非同步資料流程的詳細資訊，請參閱[c # 8.0 的新功能文章中](../../whats-new/csharp-8.md)的[非同步資料流程](../../whats-new/csharp-8.md#asynchronous-streams)一節。</span><span class="sxs-lookup"><span data-stu-id="63f83-118">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="63f83-119">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="63f83-119">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="63f83-120">您也可以使用 `foreach` [goto](goto.md)、 [return](return.md)或 [throw](throw.md) 語句來結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="63f83-120">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="63f83-121">若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="63f83-121">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="63f83-122">如果語句的來源集合 `foreach` 是空的，則 `foreach` 不會執行和略過迴圈的主體。</span><span class="sxs-lookup"><span data-stu-id="63f83-122">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="63f83-123">反覆運算變數的類型</span><span class="sxs-lookup"><span data-stu-id="63f83-123">Type of an iteration variable</span></span>

<span data-ttu-id="63f83-124">您可以使用 `var` 關鍵字，讓編譯器推斷語句中反覆運算變數的類型 `foreach` ，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="63f83-124">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="63f83-125">您也可以明確指定反覆運算變數的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="63f83-125">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="63f83-126">在上述的表單中，collection 元素的型別 `T` 必須隱含或明確地轉換成 `V` 反覆運算變數的型別。</span><span class="sxs-lookup"><span data-stu-id="63f83-126">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="63f83-127">如果 `T` 在執行時間從到的明確轉換 `V` 失敗，則語句會擲回 `foreach` <xref:System.InvalidCastException> 。</span><span class="sxs-lookup"><span data-stu-id="63f83-127">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="63f83-128">例如，如果 `T` 是非密封類別型別，則 `V` 可以是任何介面型別，甚至是不會執行的介面型 `T` 別。</span><span class="sxs-lookup"><span data-stu-id="63f83-128">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="63f83-129">在執行時間，collection 元素的型別可能是衍生自和實際執行的型別 `T` `V` 。</span><span class="sxs-lookup"><span data-stu-id="63f83-129">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="63f83-130">如果不是這種情況， <xref:System.InvalidCastException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="63f83-130">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63f83-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="63f83-131">C# language specification</span></span>

<span data-ttu-id="63f83-132">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="63f83-132">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="63f83-133">如需有關 c # 8.0 和更新版本中新增之功能的詳細資訊，請參閱下列功能提案附注：</span><span class="sxs-lookup"><span data-stu-id="63f83-133">For more information about features added in C# 8.0 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="63f83-134">非同步資料流程 (c # 8.0) </span><span class="sxs-lookup"><span data-stu-id="63f83-134">Async streams (C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [<span data-ttu-id="63f83-135">`GetEnumerator`支援迴圈的擴充功能 `foreach` (c # 9.0) </span><span class="sxs-lookup"><span data-stu-id="63f83-135">Extension `GetEnumerator` support for `foreach` loops (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a><span data-ttu-id="63f83-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63f83-136">See also</span></span>

- [<span data-ttu-id="63f83-137">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="63f83-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="63f83-138">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="63f83-138">C# keywords</span></span>](index.md)
- [<span data-ttu-id="63f83-139">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="63f83-139">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="63f83-140">for 陳述式</span><span class="sxs-lookup"><span data-stu-id="63f83-140">for statement</span></span>](for.md)
