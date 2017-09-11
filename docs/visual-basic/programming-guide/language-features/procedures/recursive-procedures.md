---
title: "遞迴程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 5e4838bb14125dcfd27798acf0c196f351ba5b90
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="4da98-102">遞迴程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4da98-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="4da98-103">A*遞迴*程序會呼叫本身。</span><span class="sxs-lookup"><span data-stu-id="4da98-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="4da98-104">一般而言，這不是最有效方式撰寫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。</span><span class="sxs-lookup"><span data-stu-id="4da98-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
 <span data-ttu-id="4da98-105">下列程序會使用遞迴來計算其原始的引數的階乘。</span><span class="sxs-lookup"><span data-stu-id="4da98-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 <span data-ttu-id="4da98-106">[!code-vb[VbVbcnProcedures #&51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4da98-106">[!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span></span>  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="4da98-107">遞迴程序的考量</span><span class="sxs-lookup"><span data-stu-id="4da98-107">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="4da98-108">**限制條件**。</span><span class="sxs-lookup"><span data-stu-id="4da98-108">**Limiting Conditions**.</span></span> <span data-ttu-id="4da98-109">您必須設計遞迴程序來測試可終止遞迴，至少一個條件，您也必須處理中沒有這類條件滿足，則在合理的遞迴呼叫數內的情況。</span><span class="sxs-lookup"><span data-stu-id="4da98-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="4da98-110">沒有至少一個可以失敗不符合的條件，您的程序會執行無限迴圈中執行的較高的風險。</span><span class="sxs-lookup"><span data-stu-id="4da98-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="4da98-111">**記憶體使用量**。</span><span class="sxs-lookup"><span data-stu-id="4da98-111">**Memory Usage**.</span></span> <span data-ttu-id="4da98-112">您的應用程式具有有限的空間供區域變數。</span><span class="sxs-lookup"><span data-stu-id="4da98-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="4da98-113">每次程序呼叫本身，它會使用更多空間其區域變數的額外複本。</span><span class="sxs-lookup"><span data-stu-id="4da98-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="4da98-114">如果此程序會無限期地繼續，則最後會導致<xref:System.StackOverflowException>錯誤。</xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="4da98-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="4da98-115">**效率**。</span><span class="sxs-lookup"><span data-stu-id="4da98-115">**Efficiency**.</span></span> <span data-ttu-id="4da98-116">您幾乎可以取代遞迴迴圈。</span><span class="sxs-lookup"><span data-stu-id="4da98-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="4da98-117">迴圈並沒有傳遞引數，初始化其他儲存體，並傳回值的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="4da98-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="4da98-118">您的效能可能沒有遞迴呼叫大幅提升。</span><span class="sxs-lookup"><span data-stu-id="4da98-118">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="4da98-119">**相互遞迴**。</span><span class="sxs-lookup"><span data-stu-id="4da98-119">**Mutual Recursion**.</span></span> <span data-ttu-id="4da98-120">您可能發現，效能非常低落或甚至無限迴圈，如果兩個程序彼此呼叫。</span><span class="sxs-lookup"><span data-stu-id="4da98-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="4da98-121">此種設計顯示單一遞迴程序中，相同的問題，但可以就很難偵測及偵錯。</span><span class="sxs-lookup"><span data-stu-id="4da98-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="4da98-122">**以括號呼叫**。</span><span class="sxs-lookup"><span data-stu-id="4da98-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="4da98-123">當`Function`程序會呼叫自己，以遞迴方式，您必須遵循的程序名稱，加上括弧，即使沒有任何引數清單。</span><span class="sxs-lookup"><span data-stu-id="4da98-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="4da98-124">否則，函式名稱會視為函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4da98-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="4da98-125">**測試**。</span><span class="sxs-lookup"><span data-stu-id="4da98-125">**Testing**.</span></span> <span data-ttu-id="4da98-126">如果您撰寫遞迴程序，應該先確認它永遠符合部分的限制條件非常仔細地測試它。</span><span class="sxs-lookup"><span data-stu-id="4da98-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="4da98-127">您也應該確定您無法執行因為有太多遞迴呼叫的記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="4da98-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da98-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da98-128">See Also</span></span>  
 <span data-ttu-id="4da98-129"><xref:System.StackOverflowException></xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="4da98-129"><xref:System.StackOverflowException></span></span>   
<span data-ttu-id="4da98-130"> [程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-130"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="4da98-131"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-131"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="4da98-132"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-132"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="4da98-133"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-133"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="4da98-134"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-134"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="4da98-135"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="4da98-136"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="4da98-137"> [疑難排解程序](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="4da98-138"> [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="4da98-138"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="4da98-139"> [疑難排解例外狀況：System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span><span class="sxs-lookup"><span data-stu-id="4da98-139"> [Troubleshooting Exceptions: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span></span>
