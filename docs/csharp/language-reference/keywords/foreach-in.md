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
ms.openlocfilehash: 3fbaacb96be2714aaff49679836e5d2d4a3783da
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422479"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="81ef5-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="81ef5-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="81ef5-103">`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="81ef5-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="81ef5-104">`foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="81ef5-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="81ef5-105">具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="81ef5-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="81ef5-106">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="81ef5-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="81ef5-107">從 C# 7.3 開始，如果列舉值的 `Current` 屬性會傳回[參考傳回值](ref.md#reference-return-values) (`T` 是集合元素類型的 `ref T`)，您可以使用 `ref` 或 `ref readonly` 修飾詞宣告反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="81ef5-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="81ef5-108">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="81ef5-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="81ef5-109">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="81ef5-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="81ef5-110">若將 `foreach` 陳述式套用到 `null`，則會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="81ef5-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="81ef5-111">若 `foreach` 陳述式的來源集合為空白，則不會執行 `foreach` 迴圈的主體，且會跳過該主體。</span><span class="sxs-lookup"><span data-stu-id="81ef5-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="81ef5-112">範例</span><span class="sxs-lookup"><span data-stu-id="81ef5-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="81ef5-113">下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：</span><span class="sxs-lookup"><span data-stu-id="81ef5-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="81ef5-114">下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="81ef5-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="81ef5-115">下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。</span><span class="sxs-lookup"><span data-stu-id="81ef5-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="81ef5-116">`ref readonly` 版本會逐一查看集合以列印所有值。</span><span class="sxs-lookup"><span data-stu-id="81ef5-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="81ef5-117">`readonly` 宣告會使用隱含的本機變數宣告。</span><span class="sxs-lookup"><span data-stu-id="81ef5-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="81ef5-118">您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。</span><span class="sxs-lookup"><span data-stu-id="81ef5-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="81ef5-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="81ef5-119">C# language specification</span></span>

<span data-ttu-id="81ef5-120">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的 [foreach 陳述式](~/_csharplang/spec/statements.md#the-foreach-statement)一節。</span><span class="sxs-lookup"><span data-stu-id="81ef5-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81ef5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81ef5-121">See also</span></span>

- [<span data-ttu-id="81ef5-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="81ef5-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="81ef5-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81ef5-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="81ef5-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="81ef5-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="81ef5-125">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="81ef5-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="81ef5-126">for 陳述式</span><span class="sxs-lookup"><span data-stu-id="81ef5-126">for statement</span></span>](for.md)
