---
title: 遺漏陣列註標運算式
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30306
- vbc30306
helpviewer_keywords:
- BC30306
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aac09a90abf69fe53f46910fe4b542c6cc632c3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="array-subscript-expression-missing"></a><span data-ttu-id="64f2f-102">遺漏陣列註標運算式</span><span class="sxs-lookup"><span data-stu-id="64f2f-102">Array subscript expression missing</span></span>
<span data-ttu-id="64f2f-103">陣列初始設定省去了一個或多個定義陣列註標。</span><span class="sxs-lookup"><span data-stu-id="64f2f-103">An array initialization leaves out one or more of the subscripts that define the array bounds.</span></span> <span data-ttu-id="64f2f-104">例如，陳述式可能會包含運算式`myArray (5,5,,10)`，，讓第三個註標出。</span><span class="sxs-lookup"><span data-stu-id="64f2f-104">For example, the statement might contain the expression `myArray (5,5,,10)`, which leaves out the third subscript.</span></span>  
  
 <span data-ttu-id="64f2f-105">**錯誤 ID:** BC30306</span><span class="sxs-lookup"><span data-stu-id="64f2f-105">**Error ID:** BC30306</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="64f2f-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="64f2f-106">To correct this error</span></span>  
  
-   <span data-ttu-id="64f2f-107">提供遺漏的註標。</span><span class="sxs-lookup"><span data-stu-id="64f2f-107">Supply the missing subscript.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f2f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64f2f-108">See Also</span></span>  
 [<span data-ttu-id="64f2f-109">陣列</span><span class="sxs-lookup"><span data-stu-id="64f2f-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
