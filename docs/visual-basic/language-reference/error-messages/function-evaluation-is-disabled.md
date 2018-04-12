---
title: 函式評估已停用，因為先前的函式評估逾時
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="b6c84-102">函式評估已停用，因為先前的函式評估逾時</span><span class="sxs-lookup"><span data-stu-id="b6c84-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="b6c84-103">函式評估已停用，因為先前的函式評估已經逾時。若要重新啟用函式評估，再次逐步執行或重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="b6c84-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="b6c84-104">在 Visual Studio 偵錯工具中，運算式指定程序呼叫，但另一個評估已逾時。</span><span class="sxs-lookup"><span data-stu-id="b6c84-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="b6c84-105">程序呼叫的逾時時間的可能原因包括無限迴圈或*無止盡迴圈*。</span><span class="sxs-lookup"><span data-stu-id="b6c84-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="b6c84-106">如需詳細資訊，請參閱[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c84-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="b6c84-107">無限迴圈的特殊案例是*遞迴*。</span><span class="sxs-lookup"><span data-stu-id="b6c84-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="b6c84-108">如需詳細資訊，請參閱[遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="b6c84-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="b6c84-109">**錯誤 ID:** BC30957</span><span class="sxs-lookup"><span data-stu-id="b6c84-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6c84-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b6c84-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="b6c84-111">可能的話，請判斷先前的函式評估的已和原因逾時的時候。否則，您可能會遇到這個錯誤一次。</span><span class="sxs-lookup"><span data-stu-id="b6c84-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="b6c84-112">同樣地，逐步偵錯工具或終止，並重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="b6c84-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c84-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c84-113">See Also</span></span>  
 [<span data-ttu-id="b6c84-114">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="b6c84-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="b6c84-115">使用偵錯工具巡覽程式碼</span><span class="sxs-lookup"><span data-stu-id="b6c84-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
