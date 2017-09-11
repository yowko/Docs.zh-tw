---
title: "如何︰ 從 (Visual Basic) 的程序傳回值 |Microsoft 文件"
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
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 601cd3adca0105eb829bb6156f94289b5c9f5f72
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="4ad8f-102">如何：傳回程序的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ad8f-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="4ad8f-103">A`Function`值傳回給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="4ad8f-104">傳回值，使用 Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="4ad8f-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="4ad8f-105">將`Return`陳述式，在完成該程序的工作之處。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="4ad8f-106">請依照下列`Return`您想要傳回給呼叫程式碼將會產生值的運算式的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="4ad8f-107">您可以有一個以上`Return`陳述式中相同的程序。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="4ad8f-108">下列`Function`程序會計算直角三角形斜邊的最長邊，並將其傳回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     <span data-ttu-id="4ad8f-109">[!code-vb[VbVbcnProcedures #&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4ad8f-109">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="4ad8f-110">下列範例會示範一般呼叫`hypotenuse`，它會儲存傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     <span data-ttu-id="4ad8f-111">[!code-vb[VbVbcnProcedures #&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4ad8f-111">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span></span>  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="4ad8f-112">傳回值使用結束函式或結束函式</span><span class="sxs-lookup"><span data-stu-id="4ad8f-112">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="4ad8f-113">在中至少一個就地`Function`程序中，指派值給程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-113">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="4ad8f-114">當您執行`Exit Function`或`End Function`陳述式，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]傳回最近指派給程序的名稱的值。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-114">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="4ad8f-115">您可以有一個以上`Exit Function`陳述式中相同的程序，而且您可以混合`Return`和`Exit Function`陳述式中相同的程序。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-115">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="4ad8f-116">您只能有一個`End Function`陳述式中的`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-116">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="4ad8f-117">如需詳細資訊和範例，請參閱 「 傳回的值 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad8f-117">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad8f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad8f-118">See Also</span></span>  
 <span data-ttu-id="4ad8f-119">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-119">[Procedures](./index.md) </span></span>  
<span data-ttu-id="4ad8f-120"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-120"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="4ad8f-121"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="4ad8f-122"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-122"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="4ad8f-123"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-123"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="4ad8f-124"> [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-124"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="4ad8f-125"> [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-125"> [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md) </span></span>  
<span data-ttu-id="4ad8f-126"> [如何︰ 建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="4ad8f-126"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="4ad8f-127"> [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="4ad8f-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
