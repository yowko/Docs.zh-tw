---
title: "如何：傳回程序的值 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="5e0de-102">如何：傳回程序的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e0de-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="5e0de-103">A`Function`值傳回給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e0de-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="5e0de-104">傳回值，使用 Return 的陳述式</span><span class="sxs-lookup"><span data-stu-id="5e0de-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="5e0de-105">Put`Return`程序的工作完成的位置處的陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e0de-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="5e0de-106">請遵循`Return`您想要傳回呼叫程式碼會產生值的運算式的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5e0de-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="5e0de-107">同一個程序中可以有多個 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e0de-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="5e0de-108">下列`Function`程序會計算直角三角形斜邊的最長邊，並傳回到呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e0de-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="5e0de-109">下列範例會示範一般呼叫`hypotenuse`，它會儲存傳回的值。</span><span class="sxs-lookup"><span data-stu-id="5e0de-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="5e0de-110">傳回值使用結束函式或結束函式</span><span class="sxs-lookup"><span data-stu-id="5e0de-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="5e0de-111">在中至少一個就地`Function`程序中，指派值到程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e0de-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="5e0de-112">當您執行`Exit Function`或`End Function`陳述式，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]傳回最近指派給程序的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="5e0de-112">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="5e0de-113">同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5e0de-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="5e0de-114">您只能有一個`End Function`陳述式中的`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="5e0de-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="5e0de-115">如需詳細資訊和範例，請參閱 「 傳回的值 」 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5e0de-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0de-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e0de-116">See Also</span></span>  
 [<span data-ttu-id="5e0de-117">程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5e0de-118">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="5e0de-119">屬性程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="5e0de-120">運算子程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="5e0de-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="5e0de-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5e0de-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="5e0de-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5e0de-123">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="5e0de-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="5e0de-124">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="5e0de-125">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="5e0de-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
