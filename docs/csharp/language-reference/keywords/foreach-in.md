---
title: C# foreach 陳述式
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d84c68eb102d55b31ba20a6b6b5c01b96963924d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405846"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="f6d96-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f6d96-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="f6d96-103">`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="f6d96-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="f6d96-104">`foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="f6d96-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="f6d96-105">具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="f6d96-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="f6d96-106">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="f6d96-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="f6d96-107">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="f6d96-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f6d96-108">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="f6d96-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="f6d96-109">範例</span><span class="sxs-lookup"><span data-stu-id="f6d96-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="f6d96-110">下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：</span><span class="sxs-lookup"><span data-stu-id="f6d96-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="f6d96-111">下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="f6d96-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="f6d96-112">從 C# 7.3 開始，如果列舉值的 `Current` 屬性會傳回[參考傳回值](../../programming-guide/classes-and-structs/ref-returns.md) (`T` 是集合元素類型的 `ref T`)，您可以使用 `ref` 或 `ref readonly` 修飾詞宣告反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="f6d96-112">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="f6d96-113">下列範例會使用 `ref` 反覆運算變數來設定 stackalloc 陣列中每個項目的值。</span><span class="sxs-lookup"><span data-stu-id="f6d96-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="f6d96-114">`ref readonly` 版本會逐一查看集合以列印所有值。</span><span class="sxs-lookup"><span data-stu-id="f6d96-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="f6d96-115">`readonly` 宣告會使用隱含的本機變數宣告。</span><span class="sxs-lookup"><span data-stu-id="f6d96-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="f6d96-116">您可以搭配使用隱含的變數宣告與 `ref` 或 `ref readonly` 宣告，也可以明確地鍵入變數宣告。</span><span class="sxs-lookup"><span data-stu-id="f6d96-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="f6d96-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f6d96-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6d96-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d96-118">See also</span></span>

- [<span data-ttu-id="f6d96-119">foreach 陳述式 (C# 語言規格)</span><span class="sxs-lookup"><span data-stu-id="f6d96-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)
- [<span data-ttu-id="f6d96-120">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="f6d96-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="f6d96-121">for</span><span class="sxs-lookup"><span data-stu-id="f6d96-121">for</span></span>](for.md)
- [<span data-ttu-id="f6d96-122">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="f6d96-122">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="f6d96-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f6d96-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f6d96-124">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f6d96-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6d96-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f6d96-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
