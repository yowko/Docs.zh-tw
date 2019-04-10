---
title: "'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311054"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="caf54-102">'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'</span><span class="sxs-lookup"><span data-stu-id="caf54-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
`#ElseIf` <span data-ttu-id="caf54-103">是條件式編譯指示詞。</span><span class="sxs-lookup"><span data-stu-id="caf54-103">is a conditional compilation directive.</span></span> <span data-ttu-id="caf54-104">`#ElseIf`子句之前必須搭配相對應`#If`或`#ElseIf`子句。</span><span class="sxs-lookup"><span data-stu-id="caf54-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="caf54-105">**錯誤 ID:** BC30014</span><span class="sxs-lookup"><span data-stu-id="caf54-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="caf54-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="caf54-106">To correct this error</span></span>  
  
1. <span data-ttu-id="caf54-107">請檢查前面`#If`或`#ElseIf`不已從這個分隔`#ElseIf`藉由使用介入條件式編譯區塊或不正確地放置`#End If`。</span><span class="sxs-lookup"><span data-stu-id="caf54-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2. <span data-ttu-id="caf54-108">如果`#ElseIf`前面加上`#Else`指示詞，則移除`#Else`或將它變更為`#ElseIf`。</span><span class="sxs-lookup"><span data-stu-id="caf54-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3. <span data-ttu-id="caf54-109">如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。</span><span class="sxs-lookup"><span data-stu-id="caf54-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf54-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf54-110">See also</span></span>

- [<span data-ttu-id="caf54-111">#If...Then...#Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="caf54-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
