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
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274348"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="ed150-102">遞迴程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed150-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="ed150-103">*遞迴*程式是一種呼叫本身的程式。</span><span class="sxs-lookup"><span data-stu-id="ed150-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="ed150-104">一般來說，這不是撰寫 Visual Basic 程式碼最有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="ed150-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="ed150-105">下列程式會使用遞迴來計算其原始引數的階乘。</span><span class="sxs-lookup"><span data-stu-id="ed150-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="ed150-106">遞迴程式的考慮</span><span class="sxs-lookup"><span data-stu-id="ed150-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="ed150-107">**限制條件**。</span><span class="sxs-lookup"><span data-stu-id="ed150-107">**Limiting Conditions**.</span></span> <span data-ttu-id="ed150-108">您必須設計遞迴程式來測試至少一個可終止遞迴的條件，而且您也必須處理在合理數目的遞迴呼叫中不滿足這類條件的情況。</span><span class="sxs-lookup"><span data-stu-id="ed150-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="ed150-109">若沒有至少一個可以符合的條件而不會失敗，則您的程式會在無限迴圈中執行高風險。</span><span class="sxs-lookup"><span data-stu-id="ed150-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="ed150-110">**記憶體使用量**。</span><span class="sxs-lookup"><span data-stu-id="ed150-110">**Memory Usage**.</span></span> <span data-ttu-id="ed150-111">您的應用程式對於本機變數的空間數量有限。</span><span class="sxs-lookup"><span data-stu-id="ed150-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="ed150-112">每次程式呼叫本身時，它會使用更多該空間來取得其區域變數的其他複本。</span><span class="sxs-lookup"><span data-stu-id="ed150-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="ed150-113">如果此程式會無限期地繼續，最後<xref:System.StackOverflowException>會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed150-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="ed150-114">**效率**。</span><span class="sxs-lookup"><span data-stu-id="ed150-114">**Efficiency**.</span></span> <span data-ttu-id="ed150-115">您幾乎可以將迴圈替換成遞迴。</span><span class="sxs-lookup"><span data-stu-id="ed150-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="ed150-116">迴圈不會有傳遞引數、初始化額外的儲存體和傳回值的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ed150-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="ed150-117">在沒有遞迴呼叫的情況下，您的效能可能更好。</span><span class="sxs-lookup"><span data-stu-id="ed150-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="ed150-118">**相互遞迴**。</span><span class="sxs-lookup"><span data-stu-id="ed150-118">**Mutual Recursion**.</span></span> <span data-ttu-id="ed150-119">如果兩個程式彼此呼叫，您可能會發現效能不佳，甚至是無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="ed150-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="ed150-120">這種設計會以單一遞迴程式的方式呈現相同的問題，但可能難以偵測和偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ed150-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="ed150-121">**使用括弧呼叫**。</span><span class="sxs-lookup"><span data-stu-id="ed150-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="ed150-122">`Function`當程式以遞迴方式呼叫本身時，即使沒有引數清單，您也必須在程式名稱後面加上括弧。</span><span class="sxs-lookup"><span data-stu-id="ed150-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="ed150-123">否則，會採用函式名稱來表示函數的傳回值。</span><span class="sxs-lookup"><span data-stu-id="ed150-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="ed150-124">**測試**。</span><span class="sxs-lookup"><span data-stu-id="ed150-124">**Testing**.</span></span> <span data-ttu-id="ed150-125">如果您撰寫遞迴程式，您應該小心進行測試，確定它一定符合某些限制條件。</span><span class="sxs-lookup"><span data-stu-id="ed150-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="ed150-126">您也應該確保因為有太多遞迴呼叫而無法用盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="ed150-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed150-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed150-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="ed150-128">程序</span><span class="sxs-lookup"><span data-stu-id="ed150-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="ed150-129">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="ed150-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="ed150-130">函式程序</span><span class="sxs-lookup"><span data-stu-id="ed150-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="ed150-131">屬性程序</span><span class="sxs-lookup"><span data-stu-id="ed150-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="ed150-132">運算子程序</span><span class="sxs-lookup"><span data-stu-id="ed150-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="ed150-133">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="ed150-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ed150-134">程序多載化</span><span class="sxs-lookup"><span data-stu-id="ed150-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="ed150-135">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="ed150-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="ed150-136">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="ed150-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
