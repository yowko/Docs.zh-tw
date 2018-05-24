---
title: foreach、in (C# 參考)
ms.date: 10/11/2017
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: c0b1481988a2e3199fc6d06ca30cb5194ab2f44c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/18/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="d4eee-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d4eee-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="d4eee-103">`foreach` 陳述式會為陣列或物件集合中每個實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的每個元素，重複一組內嵌陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4eee-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d4eee-104">[foreach 陳述式](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)可用來逐一查看集合，以取得所需的資訊，但不能用來新增或移除來源集合中的項目，以避免無法預期的副作用。</span><span class="sxs-lookup"><span data-stu-id="d4eee-104">The [foreach statement](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement) is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="d4eee-105">如果您必須新增或移除來源集合中的項目，請使用 [for](for.md) 迴圈。</span><span class="sxs-lookup"><span data-stu-id="d4eee-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="d4eee-106">內嵌陳述式會針對陣列或集合中的每個元素繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d4eee-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="d4eee-107">在完成集合中所有元素的反覆運算之後，控制權會轉移到 `foreach` 區塊之後的下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4eee-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="d4eee-108">您可以在 `foreach` 區塊內的任何位置，使用 [break](break.md) 關鍵字跳出迴圈，或使用 [continue](continue.md) 關鍵字逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="d4eee-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="d4eee-109">`foreach` 迴圈也可以透過 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束。</span><span class="sxs-lookup"><span data-stu-id="d4eee-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="d4eee-110">如需 `foreach` 關鍵字和程式碼範例的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d4eee-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="d4eee-111">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="d4eee-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="d4eee-112">如何：使用 foreach 存取集合類別</span><span class="sxs-lookup"><span data-stu-id="d4eee-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="d4eee-113">範例</span><span class="sxs-lookup"><span data-stu-id="d4eee-113">Example</span></span>

<span data-ttu-id="d4eee-114">下列程式碼顯示三個範例：</span><span class="sxs-lookup"><span data-stu-id="d4eee-114">The following code shows three examples:</span></span>

> [!TIP]
> <span data-ttu-id="d4eee-115">您可以修改範例，以試驗語法，並嘗試更類似於您的使用案例的不同使用方式。</span><span class="sxs-lookup"><span data-stu-id="d4eee-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="d4eee-116">請按 [執行] 以執行程式碼，然後編輯並再按一次 [執行]。</span><span class="sxs-lookup"><span data-stu-id="d4eee-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="d4eee-117">顯示整數陣列內容的一般 `foreach` 迴圈</span><span class="sxs-lookup"><span data-stu-id="d4eee-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="d4eee-118">執行相同動作的 [for](../../../csharp/language-reference/keywords/for.md) 迴圈</span><span class="sxs-lookup"><span data-stu-id="d4eee-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="d4eee-119">維護陣列中元素數目計數的 `foreach` 迴圈</span><span class="sxs-lookup"><span data-stu-id="d4eee-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="d4eee-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d4eee-120">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d4eee-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4eee-121">See Also</span></span>  

[<span data-ttu-id="d4eee-122">foreach 陳述式 (C# 語言規格)</span><span class="sxs-lookup"><span data-stu-id="d4eee-122">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)

[<span data-ttu-id="d4eee-123">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d4eee-123">C# Reference</span></span>](../index.md)

[<span data-ttu-id="d4eee-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d4eee-124">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="d4eee-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4eee-125">C# Keywords</span></span>](index.md)

[<span data-ttu-id="d4eee-126">反覆運算陳述式</span><span class="sxs-lookup"><span data-stu-id="d4eee-126">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="d4eee-127">for</span><span class="sxs-lookup"><span data-stu-id="d4eee-127">for</span></span>](for.md)
