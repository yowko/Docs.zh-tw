---
title: 搭配陣列使用 foreach (C# 程式設計手冊)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 298ee915bbe11313f3b33ea7dae9353ef956a231
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509531"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="b4995-102">搭配陣列使用 foreach (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b4995-102">Using foreach with Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="b4995-103">[foreach](../../language-reference/keywords/foreach-in.md) 陳述式提供了一個簡單且清楚的方法來逐一查看陣列中的元素。</span><span class="sxs-lookup"><span data-stu-id="b4995-103">The [foreach](../../language-reference/keywords/foreach-in.md) statement provides a simple, clean way to iterate through the elements of an array.</span></span>

<span data-ttu-id="b4995-104">針對一維陣列，`foreach` 陳述式會以遞增索引順序處理元素，從索引 0 開始並於索引 `Length - 1` 結束：</span><span class="sxs-lookup"><span data-stu-id="b4995-104">For single-dimensional arrays, the `foreach` statement processes elements in increasing index order, starting with index 0 and ending with index `Length - 1`:</span></span>

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

<span data-ttu-id="b4995-105">針對多維陣列，元素的周遊方式是先遞增最右側維度的索引，然後下一個左側的維度，以此類推向繼續左：</span><span class="sxs-lookup"><span data-stu-id="b4995-105">For multi-dimensional arrays, elements are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on to the left:</span></span>

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

<span data-ttu-id="b4995-106">但是在使用多維陣列時，使用巢狀 [for](../../language-reference/keywords/for.md) 迴圈能夠讓您進一步控制處理陣列元素的順序。</span><span class="sxs-lookup"><span data-stu-id="b4995-106">However, with multidimensional arrays, using a nested [for](../../language-reference/keywords/for.md) loop gives you more control over the order in which to process the array elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4995-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4995-107">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="b4995-108">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b4995-108">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="b4995-109">陣列</span><span class="sxs-lookup"><span data-stu-id="b4995-109">Arrays</span></span>](index.md)  
- [<span data-ttu-id="b4995-110">一維陣列</span><span class="sxs-lookup"><span data-stu-id="b4995-110">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="b4995-111">多維陣列</span><span class="sxs-lookup"><span data-stu-id="b4995-111">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="b4995-112">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="b4995-112">Jagged Arrays</span></span>](jagged-arrays.md)
