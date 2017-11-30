---
title: "如何：在 Visual Basic 中排序陣列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="7b3e6-102">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="7b3e6-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="7b3e6-103">這個範例會宣告陣列`String`物件命名`zooAnimals`，會填入它，然後再依字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="7b3e6-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b3e6-104">範例</span><span class="sxs-lookup"><span data-stu-id="7b3e6-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b3e6-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7b3e6-105">Compiling the Code</span></span>  
 <span data-ttu-id="7b3e6-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="7b3e6-106">This example requires:</span></span>  
  
-   <span data-ttu-id="7b3e6-107">存取 Mscorlib.dll 和<xref:System>命名空間。</span><span class="sxs-lookup"><span data-stu-id="7b3e6-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7b3e6-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7b3e6-108">Robust Programming</span></span>  
 <span data-ttu-id="7b3e6-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7b3e6-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="7b3e6-110">陣列是空的 (<xref:System.ArgumentNullException>類別)</span><span class="sxs-lookup"><span data-stu-id="7b3e6-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="7b3e6-111">陣列是多維 (<xref:System.RankException>類別)</span><span class="sxs-lookup"><span data-stu-id="7b3e6-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="7b3e6-112">不會實作一個或多個陣列項目的<xref:System.IComparable>介面 (<xref:System.InvalidOperationException>類別)</span><span class="sxs-lookup"><span data-stu-id="7b3e6-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3e6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b3e6-113">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7b3e6-114">陣列</span><span class="sxs-lookup"><span data-stu-id="7b3e6-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="7b3e6-115">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="7b3e6-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="7b3e6-116">集合</span><span class="sxs-lookup"><span data-stu-id="7b3e6-116">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="7b3e6-117">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="7b3e6-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
