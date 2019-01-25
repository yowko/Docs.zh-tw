---
title: '&#39;#ElseIf&#39;之前必須搭配相對應的&#39;#If&#39;或&#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 1e63595ee573e9356f6870a02b2131897c725baf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505779"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="dbd2d-102">&#39;#ElseIf&#39;之前必須搭配相對應的&#39;#If&#39;或&#39;#ElseIf&#39;</span><span class="sxs-lookup"><span data-stu-id="dbd2d-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="dbd2d-103">`#ElseIf` 是條件式編譯指示詞。</span><span class="sxs-lookup"><span data-stu-id="dbd2d-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="dbd2d-104">`#ElseIf`子句之前必須搭配相對應`#If`或`#ElseIf`子句。</span><span class="sxs-lookup"><span data-stu-id="dbd2d-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="dbd2d-105">**錯誤 ID:** BC30014</span><span class="sxs-lookup"><span data-stu-id="dbd2d-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dbd2d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="dbd2d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="dbd2d-107">請檢查前面`#If`或`#ElseIf`不已從這個分隔`#ElseIf`藉由使用介入條件式編譯區塊或不正確地放置`#End If`。</span><span class="sxs-lookup"><span data-stu-id="dbd2d-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="dbd2d-108">如果`#ElseIf`前面加上`#Else`指示詞，則移除`#Else`或將它變更為`#ElseIf`。</span><span class="sxs-lookup"><span data-stu-id="dbd2d-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="dbd2d-109">如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。</span><span class="sxs-lookup"><span data-stu-id="dbd2d-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd2d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbd2d-110">See also</span></span>
- [<span data-ttu-id="dbd2d-111">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="dbd2d-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
