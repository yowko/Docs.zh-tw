---
title: HOW TO：在 Visual Basic 中排序陣列
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700981"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="448b4-102">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="448b4-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="448b4-103">本文說明如何在 Visual Basic 中排序字串陣列的範例。</span><span class="sxs-lookup"><span data-stu-id="448b4-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="448b4-104">範例</span><span class="sxs-lookup"><span data-stu-id="448b4-104">Example</span></span>

<span data-ttu-id="448b4-105">這個範例會宣告名為 `zooAnimals` 的 @no__t 0 物件陣列，填入它，然後依字母順序排序：</span><span class="sxs-lookup"><span data-stu-id="448b4-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="448b4-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="448b4-106">Robust programming</span></span>

<span data-ttu-id="448b4-107">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="448b4-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="448b4-108">陣列是空的（<xref:System.ArgumentNullException> 類別）。</span><span class="sxs-lookup"><span data-stu-id="448b4-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="448b4-109">Array 是多維（@no__t 0 類別）。</span><span class="sxs-lookup"><span data-stu-id="448b4-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="448b4-110">陣列的一或多個元素不會執行 @no__t 0 介面（<xref:System.InvalidOperationException> 類別）。</span><span class="sxs-lookup"><span data-stu-id="448b4-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="448b4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="448b4-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="448b4-112">陣列</span><span class="sxs-lookup"><span data-stu-id="448b4-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="448b4-113">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="448b4-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="448b4-114">集合</span><span class="sxs-lookup"><span data-stu-id="448b4-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="448b4-115">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="448b4-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
