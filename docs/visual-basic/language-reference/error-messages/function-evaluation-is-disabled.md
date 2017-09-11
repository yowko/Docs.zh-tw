---
title: "函式評估已停用，因為先前的函式評估逾時 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
dev_langs:
- VB
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 127f89f4c7ddaf794f58707d8925731a511f3740
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="1369e-102">函式評估已停用，因為先前的函式評估逾時</span><span class="sxs-lookup"><span data-stu-id="1369e-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="1369e-103">函式評估已停用，因為先前的函式評估逾時。</span><span class="sxs-lookup"><span data-stu-id="1369e-103">Function evaluation is disabled because a previous function evaluation timed out.</span></span> <span data-ttu-id="1369e-104">若要重新啟用函式評估，再次逐步執行或重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="1369e-104">To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="1369e-105">在 Visual Studio 偵錯工具運算式指定的程序呼叫，但其他評估已逾時。</span><span class="sxs-lookup"><span data-stu-id="1369e-105">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="1369e-106">程序呼叫的逾時時間的可能原因包括無限迴圈或*永無止盡的迴圈*。</span><span class="sxs-lookup"><span data-stu-id="1369e-106">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="1369e-107">如需詳細資訊，請參閱[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1369e-107">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="1369e-108">無限迴圈的特殊案例是*遞迴*。</span><span class="sxs-lookup"><span data-stu-id="1369e-108">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="1369e-109">如需詳細資訊，請參閱[遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1369e-109">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="1369e-110">**錯誤識別碼︰** BC30957</span><span class="sxs-lookup"><span data-stu-id="1369e-110">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1369e-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1369e-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="1369e-112">可能的話，請判斷先前的函式評估的是和逾時時間的原因。</span><span class="sxs-lookup"><span data-stu-id="1369e-112">If possible, determine what the previous function evaluation was and what caused it to time out.</span></span> <span data-ttu-id="1369e-113">否則，您可能會遇到這個錯誤一次。</span><span class="sxs-lookup"><span data-stu-id="1369e-113">Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="1369e-114">同樣地，逐步偵錯工具或終止，並重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="1369e-114">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1369e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1369e-115">See Also</span></span>  
 <span data-ttu-id="1369e-116">[Visual Studio 偵錯](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="1369e-116">[Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="1369e-117"> [使用偵錯工具巡覽程式碼](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span><span class="sxs-lookup"><span data-stu-id="1369e-117"> [Navigating through Code with the Debugger](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span></span>
