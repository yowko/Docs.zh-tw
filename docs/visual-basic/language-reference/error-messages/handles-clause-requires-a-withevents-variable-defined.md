---
title: Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 99901432375c02e6a0e500cb772f8fd029276b2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587429"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="a2303-102">Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中</span><span class="sxs-lookup"><span data-stu-id="a2303-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="a2303-103">您並未提供`WithEvents`變數中您`Handles`子句。</span><span class="sxs-lookup"><span data-stu-id="a2303-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="a2303-104">`Handles`程序宣告結尾處的關鍵字會導致它處理由使用所宣告物件變數引發的事件`WithEvents`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a2303-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>  
  
 <span data-ttu-id="a2303-105">**錯誤 ID:** BC30506</span><span class="sxs-lookup"><span data-stu-id="a2303-105">**Error ID:** BC30506</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a2303-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a2303-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a2303-107">提供必要`WithEvents`變數。</span><span class="sxs-lookup"><span data-stu-id="a2303-107">Supply the necessary `WithEvents` variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2303-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2303-108">See Also</span></span>  
 [<span data-ttu-id="a2303-109">Handles</span><span class="sxs-lookup"><span data-stu-id="a2303-109">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
