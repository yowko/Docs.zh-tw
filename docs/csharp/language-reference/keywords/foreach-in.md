---
title: "foreach、in (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3889a852188870ef2f5bc29e5b6594ae6ccd2954
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="0cc18-102">foreach、in (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0cc18-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="0cc18-103">`foreach` 陳述式會針對陣列或物件集合中實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面的每個元素，重複一組內嵌陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cc18-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="0cc18-104">`foreach` 陳述式可用來逐一查看集合，以取得所需的資訊，但不能用來新增或移除來源集合中的項目，以避免無法預期的副作用。</span><span class="sxs-lookup"><span data-stu-id="0cc18-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="0cc18-105">如果您必須新增或移除來源集合中的項目，請使用 [for](../../../csharp/language-reference/keywords/for.md) 迴圈。</span><span class="sxs-lookup"><span data-stu-id="0cc18-105">If you need to add or remove items from the source collection, use a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span>  
  
 <span data-ttu-id="0cc18-106">內嵌陳述式會針對陣列或集合中的每個元素繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0cc18-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="0cc18-107">在完成集合中所有元素的反覆運算之後，控制權會轉移到 `foreach` 區塊之後的下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cc18-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>  
  
 <span data-ttu-id="0cc18-108">您可以在 `foreach` 區塊內的任何位置，使用 [break](../../../csharp/language-reference/keywords/break.md) 關鍵字跳出迴圈，或使用 [continue](../../../csharp/language-reference/keywords/continue.md) 關鍵字逐步執行到迴圈中的下一個反覆運算。</span><span class="sxs-lookup"><span data-stu-id="0cc18-108">At any point within the `foreach` block, you can break out of the loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or step to the next iteration in the loop by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span>  
  
 <span data-ttu-id="0cc18-109">`foreach` 迴圈也可以透過 [goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md) 或 [throw](../../../csharp/language-reference/keywords/throw.md) 陳述式結束。</span><span class="sxs-lookup"><span data-stu-id="0cc18-109">A `foreach` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
 <span data-ttu-id="0cc18-110">如需 `foreach` 關鍵字和程式碼範例的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0cc18-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  
  
 [<span data-ttu-id="0cc18-111">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="0cc18-111">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [<span data-ttu-id="0cc18-112">如何：使用 foreach 存取集合類別</span><span class="sxs-lookup"><span data-stu-id="0cc18-112">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a><span data-ttu-id="0cc18-113">範例</span><span class="sxs-lookup"><span data-stu-id="0cc18-113">Example</span></span>  
 <span data-ttu-id="0cc18-114">下列程式碼顯示三個範例：</span><span class="sxs-lookup"><span data-stu-id="0cc18-114">The following code shows three examples:</span></span>  
  
-   <span data-ttu-id="0cc18-115">顯示整數陣列內容的一般 `foreach` 迴圈</span><span class="sxs-lookup"><span data-stu-id="0cc18-115">a typical `foreach` loop that displays the contents of an array of integers</span></span>  
  
-   <span data-ttu-id="0cc18-116">執行相同動作的 [for](../../../csharp/language-reference/keywords/for.md) 迴圈</span><span class="sxs-lookup"><span data-stu-id="0cc18-116">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>  
  
-   <span data-ttu-id="0cc18-117">維護陣列中元素數目計數的 `foreach` 迴圈</span><span class="sxs-lookup"><span data-stu-id="0cc18-117">a `foreach` loop that maintains a count of the number of elements in the array</span></span>  
  
 <span data-ttu-id="0cc18-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0cc18-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0cc18-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0cc18-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0cc18-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cc18-120">See Also</span></span>  
 <span data-ttu-id="0cc18-121">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cc18-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="0cc18-122"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cc18-122"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="0cc18-123"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cc18-123"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="0cc18-124"> [反覆運算陳述式](../../../csharp/language-reference/keywords/iteration-statements.md) </span><span class="sxs-lookup"><span data-stu-id="0cc18-124"> [Iteration Statements](../../../csharp/language-reference/keywords/iteration-statements.md) </span></span>  
<span data-ttu-id="0cc18-125"> [for](../../../csharp/language-reference/keywords/for.md)</span><span class="sxs-lookup"><span data-stu-id="0cc18-125"> [for](../../../csharp/language-reference/keywords/for.md)</span></span>
