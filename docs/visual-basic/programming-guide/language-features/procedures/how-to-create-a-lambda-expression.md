---
title: "如何：建立 Lambda 運算式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="f0e52-102">如何：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0e52-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="f0e52-103">A *lambda 運算式*函式或副程式，沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="f0e52-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="f0e52-104">Lambda 運算式可用於委派型別無效。</span><span class="sxs-lookup"><span data-stu-id="f0e52-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="f0e52-105">若要建立的單行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="f0e52-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="f0e52-106">在委派類型可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f0e52-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="f0e52-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="f0e52-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="f0e52-108">括號中，直接在之後`Function`，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f0e52-109">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="f0e52-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="f0e52-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="f0e52-111">下列參數清單中，輸入單一運算式做為函式主體。</span><span class="sxs-lookup"><span data-stu-id="f0e52-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="f0e52-112">函數所傳回的值運算式評估為值。</span><span class="sxs-lookup"><span data-stu-id="f0e52-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="f0e52-113">您不使用`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f0e52-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="f0e52-114">Lambda 運算式可以呼叫整數引數中傳遞。</span><span class="sxs-lookup"><span data-stu-id="f0e52-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="f0e52-115">此外，相同的結果便可達成以下範例：</span><span class="sxs-lookup"><span data-stu-id="f0e52-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="f0e52-116">若要建立的單行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="f0e52-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="f0e52-117">在委派類型可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f0e52-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="f0e52-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="f0e52-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="f0e52-119">括號中，直接在之後`Sub`，型別副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f0e52-120">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="f0e52-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="f0e52-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="f0e52-122">下列參數清單中，輸入在單一陳述式做為副程式的主體。</span><span class="sxs-lookup"><span data-stu-id="f0e52-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="f0e52-123">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="f0e52-124">若要建立多行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="f0e52-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="f0e52-125">在委派類型可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f0e52-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="f0e52-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="f0e52-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="f0e52-127">括號中，直接在之後`Function`，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f0e52-128">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="f0e52-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="f0e52-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="f0e52-130">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f0e52-130">Press ENTER.</span></span> <span data-ttu-id="f0e52-131">`End Function`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="f0e52-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="f0e52-132">在函式的主體內，加入下列程式碼，以建立運算式，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="f0e52-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="f0e52-133">您不使用`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f0e52-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="f0e52-134">Lambda 運算式可以呼叫整數引數中傳遞。</span><span class="sxs-lookup"><span data-stu-id="f0e52-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="f0e52-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="f0e52-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="f0e52-136">在委派類型可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f0e52-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="f0e52-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="f0e52-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="f0e52-138">括號中，直接在之後`Sub`，型別副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f0e52-139">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="f0e52-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="f0e52-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="f0e52-141">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f0e52-141">Press ENTER.</span></span> <span data-ttu-id="f0e52-142">`End Sub`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="f0e52-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="f0e52-143">在函式的主體內，加入下列程式碼執行時叫用副程式。</span><span class="sxs-lookup"><span data-stu-id="f0e52-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="f0e52-144">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="f0e52-145">範例</span><span class="sxs-lookup"><span data-stu-id="f0e52-145">Example</span></span>  
 <span data-ttu-id="f0e52-146">Lambda 運算式的常見用法是定義可以做為參數的型別引數傳入的函式`Delegate`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="f0e52-147">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回本機電腦上執行的處理程序的陣列。</span><span class="sxs-lookup"><span data-stu-id="f0e52-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="f0e52-148"><xref:System.Linq.Enumerable.Where%2A>方法從<xref:System.Linq.Enumerable>類別會要求`Boolean`委派為其引數。</span><span class="sxs-lookup"><span data-stu-id="f0e52-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="f0e52-149">在範例中的 lambda 運算式用於此用途。</span><span class="sxs-lookup"><span data-stu-id="f0e52-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="f0e52-150">它會傳回`True`每個處理序只有一個執行緒，且那些中所選`filteredList`。</span><span class="sxs-lookup"><span data-stu-id="f0e52-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="f0e52-151">上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]語法：</span><span class="sxs-lookup"><span data-stu-id="f0e52-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f0e52-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0e52-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="f0e52-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f0e52-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="f0e52-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0e52-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="f0e52-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0e52-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="f0e52-156">委派</span><span class="sxs-lookup"><span data-stu-id="f0e52-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="f0e52-157">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="f0e52-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="f0e52-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0e52-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="f0e52-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="f0e52-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
