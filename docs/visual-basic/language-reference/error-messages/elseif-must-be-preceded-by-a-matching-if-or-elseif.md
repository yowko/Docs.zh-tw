---
title: "'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 142c142afe0d9be0ecd4d8a0340f0f1957b20470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162774"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="bc964-102">BC30014： ' #ElseIf ' 之前必須搭配相對應的 ' #If ' 或 ' #ElseIf '</span><span class="sxs-lookup"><span data-stu-id="bc964-102">BC30014: '#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>

<span data-ttu-id="bc964-103">`#ElseIf` 是條件式編譯指示詞。</span><span class="sxs-lookup"><span data-stu-id="bc964-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="bc964-104">`#ElseIf`子句之前必須搭配相對應的 `#If` 或 `#ElseIf` 子句。</span><span class="sxs-lookup"><span data-stu-id="bc964-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>

 <span data-ttu-id="bc964-105">**錯誤識別碼：** BC30014</span><span class="sxs-lookup"><span data-stu-id="bc964-105">**Error ID:** BC30014</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bc964-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc964-106">To correct this error</span></span>

1. <span data-ttu-id="bc964-107">請檢查中間的 `#If` `#ElseIf` `#ElseIf` 條件式編譯區塊或未正確放置之前的或尚未與此分隔 `#End If` 。</span><span class="sxs-lookup"><span data-stu-id="bc964-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>

2. <span data-ttu-id="bc964-108">如果 `#ElseIf` 之前是指示詞 `#Else` ，請移除 `#Else` 或將它變更為 `#ElseIf` 。</span><span class="sxs-lookup"><span data-stu-id="bc964-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>

3. <span data-ttu-id="bc964-109">如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。</span><span class="sxs-lookup"><span data-stu-id="bc964-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc964-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc964-110">See also</span></span>

- [<span data-ttu-id="bc964-111">#If .。。Then ... #Else 指示詞</span><span class="sxs-lookup"><span data-stu-id="bc964-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
