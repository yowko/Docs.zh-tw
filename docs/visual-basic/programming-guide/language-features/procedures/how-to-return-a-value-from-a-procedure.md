---
title: HOW TO：傳回值，從程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307882"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="9402f-102">HOW TO：傳回值，從程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9402f-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="9402f-103">A`Function`程序傳回值給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="9402f-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="9402f-104">傳回值，使用 Return 的陳述式</span><span class="sxs-lookup"><span data-stu-id="9402f-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="9402f-105">Put`Return`程序的工作完成的其中一點的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9402f-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="9402f-106">請依照下列`Return`您想要傳回給呼叫程式碼會產生值的運算式的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9402f-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="9402f-107">同一個程序中可以有多個 `Return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9402f-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="9402f-108">下列`Function`程序會計算直角三角形斜邊的最長的側邊，並將它傳回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="9402f-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="9402f-109">下列範例示範的典型呼叫`hypotenuse`，它會儲存傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9402f-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="9402f-110">傳回值，使用 Exit 函式或結束函式</span><span class="sxs-lookup"><span data-stu-id="9402f-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="9402f-111">在中的至少一個就地`Function`程序中，指派值至該程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="9402f-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="9402f-112">當您執行`Exit Function`或`End Function`陳述式，Visual Basic 會傳回最近指派給此程序名稱的值。</span><span class="sxs-lookup"><span data-stu-id="9402f-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="9402f-113">同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9402f-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="9402f-114">您只能有一個`End Function`中的陳述式`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="9402f-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="9402f-115">如需詳細資訊和範例，請參閱 「 傳回的值 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="9402f-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9402f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9402f-116">See also</span></span>

- [<span data-ttu-id="9402f-117">程序</span><span class="sxs-lookup"><span data-stu-id="9402f-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9402f-118">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="9402f-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9402f-119">屬性程序</span><span class="sxs-lookup"><span data-stu-id="9402f-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9402f-120">運算子程序</span><span class="sxs-lookup"><span data-stu-id="9402f-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="9402f-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="9402f-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9402f-122">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9402f-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9402f-123">Return 陳述式</span><span class="sxs-lookup"><span data-stu-id="9402f-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)
- [<span data-ttu-id="9402f-124">如何：建立程序傳回值</span><span class="sxs-lookup"><span data-stu-id="9402f-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="9402f-125">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="9402f-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
