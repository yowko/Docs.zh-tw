---
title: 函式評估已停用，因為先前的函式評估逾時
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6c3b0d3b86e871228c4bf3b30f0871015641a730
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718269"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="f45ec-102">函式評估已停用，因為先前的函式評估逾時</span><span class="sxs-lookup"><span data-stu-id="f45ec-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="f45ec-103">函式評估已停用，因為先前的函式評估逾時。若要重新啟用函式評估，再次逐步執行或重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="f45ec-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="f45ec-104">在 Visual Studio 偵錯工具中，運算式指定程序呼叫，但另一個評估已逾時。</span><span class="sxs-lookup"><span data-stu-id="f45ec-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="f45ec-105">程序呼叫的逾時時間的可能原因包括無限的迴圈或*永無止盡的迴圈*。</span><span class="sxs-lookup"><span data-stu-id="f45ec-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="f45ec-106">如需詳細資訊，請參閱[For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f45ec-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="f45ec-107">是特殊形式的無限迴圈*遞迴*。</span><span class="sxs-lookup"><span data-stu-id="f45ec-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="f45ec-108">如需詳細資訊，請參閱 <<c0> [ 遞迴程序](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="f45ec-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="f45ec-109">**錯誤 ID:** BC30957</span><span class="sxs-lookup"><span data-stu-id="f45ec-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f45ec-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f45ec-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="f45ec-111">可能的話，判斷先前的函式評估的已和逾時的原因。否則，您可能會遇到這個錯誤一次。</span><span class="sxs-lookup"><span data-stu-id="f45ec-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="f45ec-112">同樣地，逐步偵錯工具或終止，並重新啟動偵錯。</span><span class="sxs-lookup"><span data-stu-id="f45ec-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f45ec-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f45ec-113">See also</span></span>
- [<span data-ttu-id="f45ec-114">Visual Studio 偵錯</span><span class="sxs-lookup"><span data-stu-id="f45ec-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="f45ec-115">使用偵錯工具巡覽程式碼</span><span class="sxs-lookup"><span data-stu-id="f45ec-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
