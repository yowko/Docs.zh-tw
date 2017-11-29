---
title: "遞迴程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="dceb6-102">遞迴程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dceb6-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="dceb6-103">A*遞迴*程序會呼叫本身。</span><span class="sxs-lookup"><span data-stu-id="dceb6-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="dceb6-104">一般情況下，這不是最有效方式寫入[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼。</span><span class="sxs-lookup"><span data-stu-id="dceb6-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
 <span data-ttu-id="dceb6-105">下列程序會使用遞迴，計算其原始的引數的階乘。</span><span class="sxs-lookup"><span data-stu-id="dceb6-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="dceb6-106">遞迴程序的考量</span><span class="sxs-lookup"><span data-stu-id="dceb6-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="dceb6-107">**限制條件**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-107">**Limiting Conditions**.</span></span> <span data-ttu-id="dceb6-108">您必須設計遞迴程序以測試可以終止遞迴的至少一個條件，而且您也必須處理在合理的遞迴呼叫數內滿足任何這類狀況，其中的情況。</span><span class="sxs-lookup"><span data-stu-id="dceb6-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="dceb6-109">至少一個可以失敗不符合的條件，您的程序會執行在無限迴圈中執行的高風險。</span><span class="sxs-lookup"><span data-stu-id="dceb6-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="dceb6-110">**記憶體使用量**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-110">**Memory Usage**.</span></span> <span data-ttu-id="dceb6-111">您的應用程式具有有限的本機變數的空間。</span><span class="sxs-lookup"><span data-stu-id="dceb6-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="dceb6-112">每次程序呼叫本身，它會使用更多空間其區域變數的額外複本。</span><span class="sxs-lookup"><span data-stu-id="dceb6-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="dceb6-113">如果會無限期繼續此程序，它最終會導致<xref:System.StackOverflowException>錯誤。</span><span class="sxs-lookup"><span data-stu-id="dceb6-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="dceb6-114">**效率**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-114">**Efficiency**.</span></span> <span data-ttu-id="dceb6-115">您幾乎可以取代遞迴迴圈。</span><span class="sxs-lookup"><span data-stu-id="dceb6-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="dceb6-116">迴圈沒有傳遞引數，初始化其他存放裝置，並傳回值的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="dceb6-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="dceb6-117">您的效能可能會比較好沒有遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="dceb6-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="dceb6-118">**相互遞迴**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-118">**Mutual Recursion**.</span></span> <span data-ttu-id="dceb6-119">您可能發現很差的效能或甚至無限迴圈，如果兩個程序彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="dceb6-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="dceb6-120">此種設計顯示與單一遞迴程序的相同問題，但可能更難偵測及偵錯。</span><span class="sxs-lookup"><span data-stu-id="dceb6-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="dceb6-121">**以括號呼叫**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="dceb6-122">當`Function`程序呼叫本身以遞迴方式，您必須請依照下列程序名稱，加上括弧，即使沒有引數清單。</span><span class="sxs-lookup"><span data-stu-id="dceb6-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="dceb6-123">否則，函式名稱會以表示函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="dceb6-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="dceb6-124">**測試**。</span><span class="sxs-lookup"><span data-stu-id="dceb6-124">**Testing**.</span></span> <span data-ttu-id="dceb6-125">如果您撰寫的遞迴程序時，應該先確定它永遠符合某些限制狀況非常仔細地測試它。</span><span class="sxs-lookup"><span data-stu-id="dceb6-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="dceb6-126">您也應該確定您有太多的遞迴呼叫，因為記憶體不足無法執行。</span><span class="sxs-lookup"><span data-stu-id="dceb6-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dceb6-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dceb6-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="dceb6-128">程序</span><span class="sxs-lookup"><span data-stu-id="dceb6-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="dceb6-129">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="dceb6-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="dceb6-130">函式程序</span><span class="sxs-lookup"><span data-stu-id="dceb6-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="dceb6-131">屬性程序</span><span class="sxs-lookup"><span data-stu-id="dceb6-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="dceb6-132">運算子程序</span><span class="sxs-lookup"><span data-stu-id="dceb6-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="dceb6-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="dceb6-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="dceb6-134">程序多載化</span><span class="sxs-lookup"><span data-stu-id="dceb6-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="dceb6-135">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="dceb6-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="dceb6-136">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="dceb6-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="dceb6-137">疑難排解例外狀況：System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="dceb6-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
