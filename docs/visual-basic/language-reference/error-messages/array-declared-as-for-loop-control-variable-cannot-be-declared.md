---
title: 宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: bee3bcd3701945f5cf77f6761defc8be77acf49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843574"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="d162a-102">宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小</span><span class="sxs-lookup"><span data-stu-id="d162a-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="d162a-103">A`For Each`迴圈會使用陣列做為其*項目*反覆運算變數但初始化該陣列。</span><span class="sxs-lookup"><span data-stu-id="d162a-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="d162a-104">下列陳述式會顯示可以產生此錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="d162a-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="d162a-105">第一個`For Each`陳述式是正確的方式來存取元素的`arrayList`。</span><span class="sxs-lookup"><span data-stu-id="d162a-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="d162a-106">第二個`For Each`陳述式會產生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="d162a-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="d162a-107">**錯誤 ID:** BC32039</span><span class="sxs-lookup"><span data-stu-id="d162a-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d162a-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d162a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="d162a-109">從宣告中移除初始化*項目*反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="d162a-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d162a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d162a-110">See also</span></span>

- [<span data-ttu-id="d162a-111">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="d162a-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="d162a-112">陣列</span><span class="sxs-lookup"><span data-stu-id="d162a-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d162a-113">集合</span><span class="sxs-lookup"><span data-stu-id="d162a-113">Collections</span></span>](../../../standard/collections/index.md)
