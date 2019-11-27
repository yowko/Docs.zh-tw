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
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="e5448-102">函式程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5448-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="e5448-103">`Function` 程式是以 `Function` 和 `End Function` 語句括住的一系列 Visual Basic 語句。</span><span class="sxs-lookup"><span data-stu-id="e5448-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="e5448-104">`Function` 程式會執行工作，然後將控制權傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5448-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="e5448-105">當它傳回 control 時，它也會將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5448-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="e5448-106">每次呼叫程式時，其語句都會執行，從 `Function` 語句後面的第一個可執行語句開始，並以遇到的第一個 `End Function`、`Exit Function`或 `Return` 語句為結尾。</span><span class="sxs-lookup"><span data-stu-id="e5448-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="e5448-107">您可以在模組、類別或結構中定義 `Function` 程式。</span><span class="sxs-lookup"><span data-stu-id="e5448-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="e5448-108">預設為 `Public`，這表示您可以從應用程式的任何位置呼叫它，以存取您在其中定義的模組、類別或結構。</span><span class="sxs-lookup"><span data-stu-id="e5448-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="e5448-109">`Function` 程式可以接受引數，例如常數、變數或運算式，由呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="e5448-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="e5448-110">宣告語法</span><span class="sxs-lookup"><span data-stu-id="e5448-110">Declaration Syntax</span></span>  
 <span data-ttu-id="e5448-111">宣告 `Function` 程式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="e5448-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="e5448-112">修飾*詞可以指定*有關多載、覆寫、共用和遮蔽的存取層級和資訊。</span><span class="sxs-lookup"><span data-stu-id="e5448-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="e5448-113">如需詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e5448-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="e5448-114">您可以用與[Sub 程式](./sub-procedures.md)相同的方式宣告每個參數。</span><span class="sxs-lookup"><span data-stu-id="e5448-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="e5448-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="e5448-115">Data Type</span></span>  
 <span data-ttu-id="e5448-116">每個 `Function` 程式都有一種資料類型，就像每個變數一樣。</span><span class="sxs-lookup"><span data-stu-id="e5448-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="e5448-117">這個資料類型是由 `Function` 語句中的 `As` 子句所指定，它會判斷函式傳回給呼叫程式碼之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5448-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="e5448-118">下列範例宣告說明這種情況。</span><span class="sxs-lookup"><span data-stu-id="e5448-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="e5448-119">如需詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)中的「元件」。</span><span class="sxs-lookup"><span data-stu-id="e5448-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="e5448-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5448-120">Returning Values</span></span>  
 <span data-ttu-id="e5448-121">`Function` 程式傳回給呼叫端程式碼的值稱為其傳回值。</span><span class="sxs-lookup"><span data-stu-id="e5448-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="e5448-122">程式會以下列兩種方式的其中一種傳回此值：</span><span class="sxs-lookup"><span data-stu-id="e5448-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="e5448-123">它會使用 `Return` 語句來指定傳回值，並將控制權立即傳回給呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="e5448-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="e5448-124">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="e5448-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="e5448-125">它會在程式的一個或多個語句中，將值指派給它自己的函數名稱。</span><span class="sxs-lookup"><span data-stu-id="e5448-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="e5448-126">在執行 `Exit Function` 或 `End Function` 語句之前，控制項不會回到呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="e5448-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="e5448-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="e5448-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="e5448-128">將傳回值指派給函數名稱的優點是，控制項不會從程式傳回，直到遇到 `Exit Function` 或 `End Function` 語句為止。</span><span class="sxs-lookup"><span data-stu-id="e5448-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="e5448-129">這可讓您指派初步值，並在稍後視需要進行調整。</span><span class="sxs-lookup"><span data-stu-id="e5448-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="e5448-130">如需傳回值的詳細資訊，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e5448-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="e5448-131">如需傳回陣列的詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e5448-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="e5448-132">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="e5448-132">Calling Syntax</span></span>  
 <span data-ttu-id="e5448-133">您可以藉由在指派語句的右邊或運算式中包含其名稱和引數來叫用 `Function` 程式。</span><span class="sxs-lookup"><span data-stu-id="e5448-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="e5448-134">您必須提供所有非選擇性引數的值，而且必須將引數清單括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="e5448-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="e5448-135">如果未提供任何引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="e5448-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="e5448-136">呼叫 `Function` 程式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5448-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="e5448-137">*左*值`=`*functionname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="e5448-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="e5448-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`*expression* `) Then`</span><span class="sxs-lookup"><span data-stu-id="e5448-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="e5448-139">當您呼叫 `Function` 程式時，不需要使用其傳回值。</span><span class="sxs-lookup"><span data-stu-id="e5448-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="e5448-140">如果不這麼做，則會執行函式的所有動作，但會忽略傳回值。</span><span class="sxs-lookup"><span data-stu-id="e5448-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="e5448-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 通常是以這種方式呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5448-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="e5448-142">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="e5448-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="e5448-143">下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值。</span><span class="sxs-lookup"><span data-stu-id="e5448-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="e5448-144">下列範例顯示 `hypotenuse`的一般呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5448-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e5448-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5448-145">See also</span></span>

- [<span data-ttu-id="e5448-146">程序</span><span class="sxs-lookup"><span data-stu-id="e5448-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e5448-147">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="e5448-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e5448-148">屬性程序</span><span class="sxs-lookup"><span data-stu-id="e5448-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e5448-149">運算子程序</span><span class="sxs-lookup"><span data-stu-id="e5448-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e5448-150">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e5448-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e5448-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="e5448-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="e5448-152">如何：建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="e5448-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="e5448-153">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="e5448-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="e5448-154">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="e5448-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
