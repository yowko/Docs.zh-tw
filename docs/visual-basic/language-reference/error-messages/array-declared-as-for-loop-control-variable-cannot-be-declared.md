---
title: 宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9e8bb7b79b5a770c3c92e47d8e7c01c5b83d6061
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701215"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="796eb-102">宣告為 for 迴圈控制變數的陣列不能宣告它的初始大小</span><span class="sxs-lookup"><span data-stu-id="796eb-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="796eb-103">@No__t-0 迴圈使用陣列做為其*元素*反復專案變數，但會初始化該陣列。</span><span class="sxs-lookup"><span data-stu-id="796eb-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="796eb-104">下列語句會顯示如何產生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="796eb-104">The following statements show how this error can be generated.</span></span>  
  
```vb  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="796eb-105">第一個 `For Each` 語句是存取 `arrayList` 之元素的正確方式。</span><span class="sxs-lookup"><span data-stu-id="796eb-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="796eb-106">第二個 `For Each` 語句會產生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="796eb-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="796eb-107">**錯誤識別碼：** BC32039</span><span class="sxs-lookup"><span data-stu-id="796eb-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="796eb-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="796eb-108">To correct this error</span></span>  
  
- <span data-ttu-id="796eb-109">從*元素*反復專案變數的宣告中移除初始化。</span><span class="sxs-lookup"><span data-stu-id="796eb-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796eb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="796eb-110">See also</span></span>

- [<span data-ttu-id="796eb-111">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="796eb-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="796eb-112">陣列</span><span class="sxs-lookup"><span data-stu-id="796eb-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="796eb-113">集合</span><span class="sxs-lookup"><span data-stu-id="796eb-113">Collections</span></span>](../../../standard/collections/index.md)
