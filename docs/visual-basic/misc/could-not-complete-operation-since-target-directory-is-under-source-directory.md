---
title: 無法完成作業，因為目標目錄在來源目錄底下
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: f53ad664b341d4db803dee1f0f008c3918d13d93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970114"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="b1ddb-102">無法完成作業，因為目標目錄在來源目錄底下</span><span class="sxs-lookup"><span data-stu-id="b1ddb-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="b1ddb-103">循環作業失敗。</span><span class="sxs-lookup"><span data-stu-id="b1ddb-103">A cyclic operation has failed.</span></span> <span data-ttu-id="b1ddb-104">循環作業會循環，因此無法完成。</span><span class="sxs-lookup"><span data-stu-id="b1ddb-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="b1ddb-105">例如，物件 A 可能會嘗試繼承自物件 B，而物件 B 又接著繼承自物件 A。</span><span class="sxs-lookup"><span data-stu-id="b1ddb-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b1ddb-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b1ddb-106">To correct this error</span></span>  
  
- <span data-ttu-id="b1ddb-107">繼承時，請確定沒有循環參考。</span><span class="sxs-lookup"><span data-stu-id="b1ddb-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ddb-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1ddb-108">See also</span></span>

- [<span data-ttu-id="b1ddb-109">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="b1ddb-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="b1ddb-110">使用 Visual Studio 偵錯工具中的中斷點</span><span class="sxs-lookup"><span data-stu-id="b1ddb-110">Use breakpoints in the Visual Studio debugger</span></span>](/visualstudio/debugger/using-breakpoints)
