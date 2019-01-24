---
title: 函式程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 8b67a6953e7788827ef1ec268f54bddf2f1392c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662253"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="1361a-102">函式程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1361a-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="1361a-103">A`Function`程序是一系列的 Visual Basic 陳述式加上`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1361a-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="1361a-104">`Function`程序執行的工作，然後將控制權傳回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="1361a-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="1361a-105">當它傳回控制項時，它也會傳回值，呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="1361a-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="1361a-106">此程序呼叫時，它的陳述式執行時，每次開始之後的第一個可執行陳述式`Function`陳述式，並與第一個結束`End Function`， `Exit Function`，或`Return`陳述式時發生。</span><span class="sxs-lookup"><span data-stu-id="1361a-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="1361a-107">您可以定義`Function`模組、 類別或結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="1361a-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="1361a-108">它是`Public`根據預設，這表示您可以從任何位置呼叫它可存取模組、 類別或結構定義它的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="1361a-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="1361a-109">A`Function`程序可以取得引數，例如常數、 變數或運算式，這會傳遞給它所呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1361a-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="1361a-110">宣告語法</span><span class="sxs-lookup"><span data-stu-id="1361a-110">Declaration Syntax</span></span>  
 <span data-ttu-id="1361a-111">宣告的語法`Function`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="1361a-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="1361a-112">*修飾詞*可以指定存取層級和多載、 覆寫，將分享，與遮蔽的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1361a-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="1361a-113">如需詳細資訊，請參閱 < [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1361a-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1361a-114">您所進行的相同方式宣告的每個參數[Sub 程序](./sub-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1361a-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="1361a-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="1361a-115">Data Type</span></span>  
 <span data-ttu-id="1361a-116">每個`Function`程序中的資料類型，只要為每個變數。</span><span class="sxs-lookup"><span data-stu-id="1361a-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="1361a-117">此資料型別由`As`子句中的`Function`陳述式，並判斷函式傳回給呼叫程式碼之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1361a-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="1361a-118">下列範例宣告可說明這點。</span><span class="sxs-lookup"><span data-stu-id="1361a-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="1361a-119">如需詳細資訊，請參閱 「 組件 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1361a-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="1361a-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="1361a-120">Returning Values</span></span>  
 <span data-ttu-id="1361a-121">值`Function`程序會傳送回到呼叫端程式碼會呼叫它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1361a-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="1361a-122">程序會傳回此值中有兩種：</span><span class="sxs-lookup"><span data-stu-id="1361a-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="1361a-123">它會使用`Return`陳述式來指定傳回值，並傳回立即控制權傳輸至呼叫端程式。</span><span class="sxs-lookup"><span data-stu-id="1361a-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="1361a-124">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="1361a-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="1361a-125">它將值指派給自己的程序的一或多個陳述式中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="1361a-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="1361a-126">控制項不會傳回給呼叫程式，直到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1361a-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="1361a-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="1361a-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="1361a-128">將傳回的值指派給函式名稱的優點是，控制項不會傳回從程序直到遇到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1361a-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="1361a-129">這可讓您指派的初步的值，並視需要稍後調整它。</span><span class="sxs-lookup"><span data-stu-id="1361a-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="1361a-130">如需有關傳回值的詳細資訊，請參閱[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1361a-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="1361a-131">如需傳回陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1361a-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="1361a-132">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="1361a-132">Calling Syntax</span></span>  
 <span data-ttu-id="1361a-133">您可以叫用`Function`程序包括其名稱和引數是在指派陳述式或運算式的右側。</span><span class="sxs-lookup"><span data-stu-id="1361a-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="1361a-134">您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="1361a-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="1361a-135">如果已不提供任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="1361a-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="1361a-136">呼叫語法`Function`程序如下所示：</span><span class="sxs-lookup"><span data-stu-id="1361a-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="1361a-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="1361a-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="1361a-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span><span class="sxs-lookup"><span data-stu-id="1361a-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="1361a-139">當您呼叫`Function`程序中，您就不必使用它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="1361a-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="1361a-140">如果您不這樣做，函式的所有動作皆都執行，但傳回的值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1361a-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="1361a-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 通常稱為以這種方式。</span><span class="sxs-lookup"><span data-stu-id="1361a-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="1361a-142">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="1361a-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="1361a-143">下列`Function`程序會計算已知值的其他兩個邊直角三角形斜邊的最長的側邊。</span><span class="sxs-lookup"><span data-stu-id="1361a-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="1361a-144">下列範例示範的典型呼叫`hypotenuse`。</span><span class="sxs-lookup"><span data-stu-id="1361a-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1361a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1361a-145">See also</span></span>
- [<span data-ttu-id="1361a-146">程序</span><span class="sxs-lookup"><span data-stu-id="1361a-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1361a-147">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="1361a-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="1361a-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="1361a-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1361a-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="1361a-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1361a-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="1361a-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1361a-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="1361a-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="1361a-152">如何：建立程序傳回值</span><span class="sxs-lookup"><span data-stu-id="1361a-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="1361a-153">如何：從程序傳回值</span><span class="sxs-lookup"><span data-stu-id="1361a-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="1361a-154">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="1361a-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
