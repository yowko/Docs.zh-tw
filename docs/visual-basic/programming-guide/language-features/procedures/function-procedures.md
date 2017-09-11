---
title: "函式程序 (Visual Basic) |Microsoft 文件"
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
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fb36ee41e4b53f6e690ce5d48d34bbfc9f86c177
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="bda93-102">函式程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bda93-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="bda93-103">A`Function`程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式括住`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="bda93-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="bda93-104">`Function`程序執行的工作，然後將控制項傳回呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="bda93-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="bda93-105">當它傳回控制項時，它也會傳回值，呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="bda93-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="bda93-106">此程序呼叫時，其陳述式執行時，每次開始之後的第一個可執行陳述式`Function`陳述式，直到第一個`End Function`， `Exit Function`，或`Return`陳述式時發生。</span><span class="sxs-lookup"><span data-stu-id="bda93-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="bda93-107">您可以定義`Function`模組、 類別或結構中的程序。</span><span class="sxs-lookup"><span data-stu-id="bda93-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="bda93-108">它是`Public`根據預設，這表示您可以從任何位置呼叫它有權存取模組、 類別或結構定義它的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="bda93-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="bda93-109">A`Function`程序可以取得引數，例如常數、 變數或運算式，則呼叫程式碼傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="bda93-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="bda93-110">宣告語法</span><span class="sxs-lookup"><span data-stu-id="bda93-110">Declaration Syntax</span></span>  
 <span data-ttu-id="bda93-111">宣告的語法`Function`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="bda93-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="bda93-112">*修飾詞*可以指定存取層級和多載、 覆寫、 共用、 及遮蔽的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bda93-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="bda93-113">如需詳細資訊，請參閱[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bda93-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="bda93-114">您每個參數宣告相同的方式就如同[Sub 程序](./sub-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="bda93-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="bda93-115">資料類型</span><span class="sxs-lookup"><span data-stu-id="bda93-115">Data Type</span></span>  
 <span data-ttu-id="bda93-116">每個`Function`程序中的資料類型，只是為每個變數。</span><span class="sxs-lookup"><span data-stu-id="bda93-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="bda93-117">此資料型別由指定`As`子句`Function`陳述式，並決定函式會傳回呼叫程式碼的值的資料型別。</span><span class="sxs-lookup"><span data-stu-id="bda93-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="bda93-118">下列範例宣告可說明這點。</span><span class="sxs-lookup"><span data-stu-id="bda93-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="bda93-119">如需詳細資訊，請參閱 「 組件 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bda93-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="bda93-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="bda93-120">Returning Values</span></span>  
 <span data-ttu-id="bda93-121">值`Function`程序會傳送回到呼叫程式碼會呼叫它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="bda93-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="bda93-122">程序會傳回此值中有兩種︰</span><span class="sxs-lookup"><span data-stu-id="bda93-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="bda93-123">它會使用`Return`陳述式來指定傳回值，並傳回控制立即呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="bda93-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="bda93-124">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="bda93-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="bda93-125">它會指派值給自己的函式名稱的程序的一個或多個陳述式中。</span><span class="sxs-lookup"><span data-stu-id="bda93-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="bda93-126">控制項不會傳回給呼叫程式直到`Exit Function`或`End Function`執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="bda93-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="bda93-127">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="bda93-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="bda93-128">將傳回值指派給函式名稱的優點是，控制項不會傳回從程序直到遇到`Exit Function`或`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="bda93-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="bda93-129">這可讓您指派一個基本值，並視需要稍後調整它。</span><span class="sxs-lookup"><span data-stu-id="bda93-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="bda93-130">如需傳回值的詳細資訊，請參閱[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bda93-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="bda93-131">傳回陣列的相關資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bda93-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="bda93-132">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="bda93-132">Calling Syntax</span></span>  
 <span data-ttu-id="bda93-133">您可以叫用`Function`程序包括其名稱和引數是在指派陳述式或運算式的右邊。</span><span class="sxs-lookup"><span data-stu-id="bda93-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="bda93-134">您必須提供值不是選擇性的所有引數，您必須將引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="bda93-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="bda93-135">如果已不提供任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="bda93-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="bda93-136">呼叫語法`Function`程序如下︰</span><span class="sxs-lookup"><span data-stu-id="bda93-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="bda93-137">*左值*`=`*functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="bda93-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="bda93-138">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=`*運算式*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="bda93-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="bda93-139">當您呼叫`Function`程序中，您不需要使用它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="bda93-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="bda93-140">如果不這麼做，會執行的函式的所有動作，但會忽略傳回值。</span><span class="sxs-lookup"><span data-stu-id="bda93-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="bda93-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>通常稱為以這種方式。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="bda93-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="bda93-142">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="bda93-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="bda93-143">下列`Function`程序會計算直角三角形而言，已知值的其他兩邊斜邊的最長邊。</span><span class="sxs-lookup"><span data-stu-id="bda93-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 <span data-ttu-id="bda93-144">[!code-vb[VbVbcnProcedures #&1;](./codesnippet/VisualBasic/function-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bda93-144">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="bda93-145">下列範例會示範一般呼叫`hypotenuse`。</span><span class="sxs-lookup"><span data-stu-id="bda93-145">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 <span data-ttu-id="bda93-146">[!code-vb[VbVbcnProcedures #&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bda93-146">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda93-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bda93-147">See Also</span></span>  
 <span data-ttu-id="bda93-148">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="bda93-149"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-149"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="bda93-150"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="bda93-151"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="bda93-152"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="bda93-153"> [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-153"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="bda93-154"> [如何︰ 建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-154"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="bda93-155"> [如何︰ 從程序傳回值](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bda93-155"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="bda93-156"> [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="bda93-156"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
