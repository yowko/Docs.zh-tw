---
title: 遺漏陣列註標運算式
ms.date: 07/20/2015
f1_keywords:
- bc30306
- vbc30306
helpviewer_keywords:
- BC30306
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
ms.openlocfilehash: 4dadad63f4321e88b79f2006a9e6b7befa27909a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837555"
---
# <a name="array-subscript-expression-missing"></a><span data-ttu-id="27639-102">遺漏陣列註標運算式</span><span class="sxs-lookup"><span data-stu-id="27639-102">Array subscript expression missing</span></span>
<span data-ttu-id="27639-103">陣列初始化省去了一個或多個定義陣列界限的註標。</span><span class="sxs-lookup"><span data-stu-id="27639-103">An array initialization leaves out one or more of the subscripts that define the array bounds.</span></span> <span data-ttu-id="27639-104">例如，此陳述式可能會包含運算式`myArray (5,5,,10)`，它將被排除的第三個註標。</span><span class="sxs-lookup"><span data-stu-id="27639-104">For example, the statement might contain the expression `myArray (5,5,,10)`, which leaves out the third subscript.</span></span>  
  
 <span data-ttu-id="27639-105">**錯誤 ID:** BC30306</span><span class="sxs-lookup"><span data-stu-id="27639-105">**Error ID:** BC30306</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27639-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="27639-106">To correct this error</span></span>  
  
-   <span data-ttu-id="27639-107">提供遺漏的註標。</span><span class="sxs-lookup"><span data-stu-id="27639-107">Supply the missing subscript.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27639-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27639-108">See also</span></span>

- [<span data-ttu-id="27639-109">陣列</span><span class="sxs-lookup"><span data-stu-id="27639-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
