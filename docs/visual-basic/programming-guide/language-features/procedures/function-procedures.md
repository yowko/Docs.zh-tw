---
title: 函式程序
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341093"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="76c28-102">函式程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76c28-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="76c28-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span><span class="sxs-lookup"><span data-stu-id="76c28-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="76c28-104">The `Function` procedure performs a task and then returns control to the calling code.</span><span class="sxs-lookup"><span data-stu-id="76c28-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="76c28-105">When it returns control, it also returns a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="76c28-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="76c28-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span><span class="sxs-lookup"><span data-stu-id="76c28-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="76c28-107">You can define a `Function` procedure in a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="76c28-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="76c28-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span><span class="sxs-lookup"><span data-stu-id="76c28-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="76c28-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span><span class="sxs-lookup"><span data-stu-id="76c28-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="76c28-110">宣告語法</span><span class="sxs-lookup"><span data-stu-id="76c28-110">Declaration Syntax</span></span>  
 <span data-ttu-id="76c28-111">The syntax for declaring a `Function` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="76c28-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="76c28-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span><span class="sxs-lookup"><span data-stu-id="76c28-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="76c28-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76c28-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="76c28-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="76c28-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="76c28-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="76c28-115">Data Type</span></span>  
 <span data-ttu-id="76c28-116">Every `Function` procedure has a data type, just as every variable does.</span><span class="sxs-lookup"><span data-stu-id="76c28-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="76c28-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span><span class="sxs-lookup"><span data-stu-id="76c28-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="76c28-118">The following sample declarations illustrate this.</span><span class="sxs-lookup"><span data-stu-id="76c28-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="76c28-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76c28-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="76c28-120">Returning Values</span><span class="sxs-lookup"><span data-stu-id="76c28-120">Returning Values</span></span>  
 <span data-ttu-id="76c28-121">The value a `Function` procedure sends back to the calling code is called its return value.</span><span class="sxs-lookup"><span data-stu-id="76c28-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="76c28-122">The procedure returns this value in one of two ways:</span><span class="sxs-lookup"><span data-stu-id="76c28-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="76c28-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span><span class="sxs-lookup"><span data-stu-id="76c28-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="76c28-124">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="76c28-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="76c28-125">It assigns a value to its own function name in one or more statements of the procedure.</span><span class="sxs-lookup"><span data-stu-id="76c28-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="76c28-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span><span class="sxs-lookup"><span data-stu-id="76c28-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="76c28-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="76c28-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="76c28-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="76c28-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="76c28-129">This allows you to assign a preliminary value and adjust it later if necessary.</span><span class="sxs-lookup"><span data-stu-id="76c28-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="76c28-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="76c28-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="76c28-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="76c28-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="76c28-132">Calling Syntax</span><span class="sxs-lookup"><span data-stu-id="76c28-132">Calling Syntax</span></span>  
 <span data-ttu-id="76c28-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span><span class="sxs-lookup"><span data-stu-id="76c28-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="76c28-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="76c28-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="76c28-135">If no arguments are supplied, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="76c28-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="76c28-136">The syntax for a call to a `Function` procedure is as follows:</span><span class="sxs-lookup"><span data-stu-id="76c28-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="76c28-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="76c28-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="76c28-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span><span class="sxs-lookup"><span data-stu-id="76c28-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="76c28-139">When you call a `Function` procedure, you do not have to use its return value.</span><span class="sxs-lookup"><span data-stu-id="76c28-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="76c28-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span><span class="sxs-lookup"><span data-stu-id="76c28-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="76c28-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span><span class="sxs-lookup"><span data-stu-id="76c28-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="76c28-142">Illustration of Declaration and Call</span><span class="sxs-lookup"><span data-stu-id="76c28-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="76c28-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span><span class="sxs-lookup"><span data-stu-id="76c28-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="76c28-144">The following example shows a typical call to `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="76c28-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="76c28-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="76c28-145">See also</span></span>

- [<span data-ttu-id="76c28-146">程序</span><span class="sxs-lookup"><span data-stu-id="76c28-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="76c28-147">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="76c28-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="76c28-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="76c28-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="76c28-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="76c28-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="76c28-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="76c28-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="76c28-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="76c28-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="76c28-152">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="76c28-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="76c28-153">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="76c28-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="76c28-154">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="76c28-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
