---
title: "搭配陣列使用 foreach (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 797cb9a63a5e1009b170b2afda8634bd21a50035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="d5de3-102">搭配陣列使用 foreach (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d5de3-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="d5de3-103">C# 還提供 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d5de3-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="d5de3-104">這個陳述式提供了一個簡單且清楚的方法來逐一查看陣列中或任何可列舉集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="d5de3-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="d5de3-105">`foreach` 陳述式會依照陣列或集合類型的列舉值傳回的順序處理元素，通常是從第 0 個元素到最後一個元素。</span><span class="sxs-lookup"><span data-stu-id="d5de3-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="d5de3-106">例如，下列程式碼會建立名為 `numbers` 的陣列，並使用 `foreach` 陳述式逐一查看該陣列：</span><span class="sxs-lookup"><span data-stu-id="d5de3-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 <span data-ttu-id="d5de3-107">使用多維陣列時，就可以使用相同的方法來逐一查看元素，例如：</span><span class="sxs-lookup"><span data-stu-id="d5de3-107">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 <span data-ttu-id="d5de3-108">但是在使用多維陣列時，使用巢狀 [for](../../../csharp/language-reference/keywords/for.md) 迴圈能夠讓您進一步控制陣列元素。</span><span class="sxs-lookup"><span data-stu-id="d5de3-108">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5de3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5de3-109">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="d5de3-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d5de3-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d5de3-111">陣列</span><span class="sxs-lookup"><span data-stu-id="d5de3-111">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="d5de3-112">一維陣列</span><span class="sxs-lookup"><span data-stu-id="d5de3-112">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="d5de3-113">多維陣列</span><span class="sxs-lookup"><span data-stu-id="d5de3-113">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="d5de3-114">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="d5de3-114">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
