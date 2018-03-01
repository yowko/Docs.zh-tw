---
title: "無法完成作業，因為目標目錄在來源目錄底下"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a17877b2335ee010a97f0b522bd4c399867cd7d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="87fa6-102">無法完成作業，因為目標目錄在來源目錄底下</span><span class="sxs-lookup"><span data-stu-id="87fa6-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="87fa6-103">循環作業失敗。</span><span class="sxs-lookup"><span data-stu-id="87fa6-103">A cyclic operation has failed.</span></span> <span data-ttu-id="87fa6-104">循環作業會循環，因此無法完成。</span><span class="sxs-lookup"><span data-stu-id="87fa6-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="87fa6-105">例如，物件 A 可能會嘗試繼承自物件 B，而物件 B 又接著繼承自物件 A。</span><span class="sxs-lookup"><span data-stu-id="87fa6-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87fa6-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="87fa6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="87fa6-107">繼承時，請確定沒有循環參考。</span><span class="sxs-lookup"><span data-stu-id="87fa6-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fa6-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="87fa6-108">See Also</span></span>  
 [<span data-ttu-id="87fa6-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="87fa6-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="87fa6-110">偵錯基本概念： 中斷點</span><span class="sxs-lookup"><span data-stu-id="87fa6-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
