---
title: HOW TO：在 Visual Basic 中排序陣列
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3f4dbd6dce0957de3451b1f29c3a67ccd6791045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838075"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="c197c-102">HOW TO：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="c197c-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="c197c-103">這個範例會宣告陣列`String`命名的物件`zooAnimals`，填入它，然後依字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="c197c-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c197c-104">範例</span><span class="sxs-lookup"><span data-stu-id="c197c-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c197c-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c197c-105">Compiling the Code</span></span>  
 <span data-ttu-id="c197c-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c197c-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c197c-107">Mscorlib.dll 的存取和<xref:System>命名空間。</span><span class="sxs-lookup"><span data-stu-id="c197c-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c197c-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c197c-108">Robust Programming</span></span>  
 <span data-ttu-id="c197c-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="c197c-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c197c-110">陣列是空的 (<xref:System.ArgumentNullException>類別)</span><span class="sxs-lookup"><span data-stu-id="c197c-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="c197c-111">陣列是多維 (<xref:System.RankException>類別)</span><span class="sxs-lookup"><span data-stu-id="c197c-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="c197c-112">陣列的一個或多個項目不會實作<xref:System.IComparable>介面 (<xref:System.InvalidOperationException>類別)</span><span class="sxs-lookup"><span data-stu-id="c197c-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c197c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c197c-113">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c197c-114">陣列</span><span class="sxs-lookup"><span data-stu-id="c197c-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="c197c-115">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c197c-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="c197c-116">集合</span><span class="sxs-lookup"><span data-stu-id="c197c-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="c197c-117">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="c197c-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
