---
title: foreach、in (C# 參考)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 7613590686f7f7ec6439da4a2bb672e524ab01e8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565702"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="bef9f-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bef9f-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="bef9f-103">`foreach` 陳述式會針對在型別實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的執行個體中每個元素，執行其中的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="bef9f-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="bef9f-104">`foreach` 陳述式不限於那些型別，並且適用於滿足下列條件的任何型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="bef9f-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="bef9f-105">具有公用無參數的 `GetEnumerator` 方法，其傳回型別為類別、結構或介面型別。</span><span class="sxs-lookup"><span data-stu-id="bef9f-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="bef9f-106">`GetEnumerator` 方法的傳回型別具有公用的 `Current` 屬性，且公用無參數的 `MoveNext` 方法的傳回型別為 <xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="bef9f-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="bef9f-107">您可以在 `foreach` 陳述式區塊內的任何位置，使用 [break](break.md) 陳述式跳出迴圈，或使用 [continue](continue.md) 陳述式逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="bef9f-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="bef9f-108">您也可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="bef9f-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="bef9f-109">範例</span><span class="sxs-lookup"><span data-stu-id="bef9f-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="bef9f-110">下面範例針對實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的 <xref:System.Collections.Generic.List%601> 型別執行個體，示範搭配 `foreach` 陳述式時的使用方式：</span><span class="sxs-lookup"><span data-stu-id="bef9f-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="bef9f-111">下一個範例使用 `foreach` 陳述式搭配不實作任何介面的 <xref:System.Span%601?displayProperty=nameWithType> 型別執行個體：</span><span class="sxs-lookup"><span data-stu-id="bef9f-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="bef9f-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bef9f-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bef9f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bef9f-113">See also</span></span>

[<span data-ttu-id="bef9f-114">foreach 陳述式 (C# 語言規格)</span><span class="sxs-lookup"><span data-stu-id="bef9f-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="bef9f-115">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="bef9f-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="bef9f-116">for</span><span class="sxs-lookup"><span data-stu-id="bef9f-116">for</span></span>](for.md)  
[<span data-ttu-id="bef9f-117">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="bef9f-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="bef9f-118">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bef9f-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="bef9f-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bef9f-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="bef9f-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bef9f-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  