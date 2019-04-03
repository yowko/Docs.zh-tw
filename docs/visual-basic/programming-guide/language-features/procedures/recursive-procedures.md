---
title: 遞迴程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832381"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="0893a-102">遞迴程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0893a-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="0893a-103">A*遞迴*程序會呼叫其本身。</span><span class="sxs-lookup"><span data-stu-id="0893a-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="0893a-104">一般情況下，這不是撰寫 Visual Basic 程式碼的最有效方式。</span><span class="sxs-lookup"><span data-stu-id="0893a-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="0893a-105">下列程序會使用遞迴來計算其原始的引數的階乘。</span><span class="sxs-lookup"><span data-stu-id="0893a-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="0893a-106">遞迴程序的考量</span><span class="sxs-lookup"><span data-stu-id="0893a-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="0893a-107">**限制條件**。</span><span class="sxs-lookup"><span data-stu-id="0893a-107">**Limiting Conditions**.</span></span> <span data-ttu-id="0893a-108">您必須設計的遞迴程序，以測試可終止遞迴時，至少一個條件，而且您也必須處理在合理的遞迴呼叫數內中成立到任何這類條件的情況。</span><span class="sxs-lookup"><span data-stu-id="0893a-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="0893a-109">缺少至少一個可以在不失敗的情況下符合的條件，您的程序會執行無限迴圈中執行的較高的風險。</span><span class="sxs-lookup"><span data-stu-id="0893a-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="0893a-110">**記憶體使用量**。</span><span class="sxs-lookup"><span data-stu-id="0893a-110">**Memory Usage**.</span></span> <span data-ttu-id="0893a-111">您的應用程式具有本機變數的空間量有限。</span><span class="sxs-lookup"><span data-stu-id="0893a-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="0893a-112">每次程序呼叫本身，它會使用更多空間其本機變數的其他複本。</span><span class="sxs-lookup"><span data-stu-id="0893a-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="0893a-113">如果會無限期繼續此程序，它最終會導致<xref:System.StackOverflowException>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0893a-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="0893a-114">**效率**。</span><span class="sxs-lookup"><span data-stu-id="0893a-114">**Efficiency**.</span></span> <span data-ttu-id="0893a-115">您幾乎可以取代遞迴迴圈。</span><span class="sxs-lookup"><span data-stu-id="0893a-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="0893a-116">迴圈並沒有傳遞引數，初始化其他的儲存體，並傳回值的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="0893a-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="0893a-117">您的效能可能會遞迴呼叫沒有更好的。</span><span class="sxs-lookup"><span data-stu-id="0893a-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="0893a-118">**相互遞迴**。</span><span class="sxs-lookup"><span data-stu-id="0893a-118">**Mutual Recursion**.</span></span> <span data-ttu-id="0893a-119">您可能發現，效能非常低落或甚至是無限迴圈，如果兩個程序彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="0893a-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="0893a-120">此種設計呈現單一的遞迴程序中，相同的問題，但可以就很難偵測及偵錯。</span><span class="sxs-lookup"><span data-stu-id="0893a-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="0893a-121">**呼叫以括號**。</span><span class="sxs-lookup"><span data-stu-id="0893a-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="0893a-122">當`Function`程序呼叫本身以遞迴方式，您必須請依照下列程序名稱，加上括弧，即使沒有任何引數清單。</span><span class="sxs-lookup"><span data-stu-id="0893a-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="0893a-123">否則，函式名稱會視為函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="0893a-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="0893a-124">**測試**。</span><span class="sxs-lookup"><span data-stu-id="0893a-124">**Testing**.</span></span> <span data-ttu-id="0893a-125">如果您撰寫遞迴程序，您應該測試它非常小心地以確定它一律符合某些限制狀況。</span><span class="sxs-lookup"><span data-stu-id="0893a-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="0893a-126">您也應該確定您無法執行太多遞迴呼叫，因為記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="0893a-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0893a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0893a-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="0893a-128">程序</span><span class="sxs-lookup"><span data-stu-id="0893a-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0893a-129">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="0893a-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0893a-130">函式程序</span><span class="sxs-lookup"><span data-stu-id="0893a-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0893a-131">屬性程序</span><span class="sxs-lookup"><span data-stu-id="0893a-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0893a-132">運算子程序</span><span class="sxs-lookup"><span data-stu-id="0893a-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0893a-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="0893a-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0893a-134">程序多載化</span><span class="sxs-lookup"><span data-stu-id="0893a-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="0893a-135">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="0893a-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="0893a-136">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="0893a-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
