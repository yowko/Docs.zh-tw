---
title: "如何︰ 建立 Lambda 運算式 (Visual Basic) |Microsoft 文件"
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
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.openlocfilehash: edd475490dce81ff9cca32b5f9a5090d99f4d80d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="c55f1-102">如何：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c55f1-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="c55f1-103">A *lambda 運算式*函式或不含名稱的副程式。</span><span class="sxs-lookup"><span data-stu-id="c55f1-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="c55f1-104">只要委派型別有效，可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c55f1-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="c55f1-105">若要建立的單行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="c55f1-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="c55f1-106">在委派型別可以用在任何情況下，輸入關鍵字`Function`，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="c55f1-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="c55f1-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="c55f1-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="c55f1-108">在括號內，緊接`Function`，類型函式的參數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="c55f1-109">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="c55f1-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="c55f1-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="c55f1-111">下列參數清單中，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="c55f1-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="c55f1-112">運算式評估為值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="c55f1-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="c55f1-113">您不使用`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c55f1-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="c55f1-114">[!code-vb[VbVbalrLambdas #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-114">[!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span></span>  
  
     <span data-ttu-id="c55f1-115">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="c55f1-116">[!code-vb[VbVbalrLambdas #&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-116">[!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span></span>  
  
4.  <span data-ttu-id="c55f1-117">此外，相同的結果被透過下列的範例︰</span><span class="sxs-lookup"><span data-stu-id="c55f1-117">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     <span data-ttu-id="c55f1-118">[!code-vb[VbVbalrLambdas #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-118">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="c55f1-119">若要建立單行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="c55f1-119">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="c55f1-120">在委派型別可以用在任何情況下，輸入關鍵字`Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c55f1-120">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="c55f1-121">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="c55f1-121">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="c55f1-122">在括號內，緊接`Sub`，型別副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-122">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="c55f1-123">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-123">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="c55f1-124">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="c55f1-124">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="c55f1-125">下列參數清單中，輸入單一陳述式做為副程式的主體。</span><span class="sxs-lookup"><span data-stu-id="c55f1-125">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     <span data-ttu-id="c55f1-126">[!code-vb[VbVbalrLambdas #&17;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-126">[!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span></span>  
  
     <span data-ttu-id="c55f1-127">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-127">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="c55f1-128">[!code-vb[VbVbalrLambdas #&18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-128">[!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="c55f1-129">若要建立多行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="c55f1-129">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="c55f1-130">在委派型別可以用在任何情況下，輸入關鍵字`Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c55f1-130">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="c55f1-131">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="c55f1-131">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="c55f1-132">在括號內，緊接`Function`，類型函式的參數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-132">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="c55f1-133">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-133">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="c55f1-134">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="c55f1-134">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="c55f1-135">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c55f1-135">Press ENTER.</span></span> <span data-ttu-id="c55f1-136">`End Function`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="c55f1-136">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="c55f1-137">在函式的主體內，新增下列程式碼來建立運算式，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="c55f1-137">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="c55f1-138">您不使用`As`子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c55f1-138">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="c55f1-139">[!code-vb[VbVbalrLambdas #&19;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-139">[!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span></span>  
  
     <span data-ttu-id="c55f1-140">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-140">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="c55f1-141">[!code-vb[VbVbalrLambdas #&20;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-141">[!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="c55f1-142">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="c55f1-142">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="c55f1-143">在委派型別可以用在任何情況下，輸入關鍵字`Sub`，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="c55f1-143">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="c55f1-144">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="c55f1-144">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="c55f1-145">在括號內，緊接`Sub`，型別副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-145">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="c55f1-146">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-146">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="c55f1-147">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="c55f1-147">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="c55f1-148">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="c55f1-148">Press ENTER.</span></span> <span data-ttu-id="c55f1-149">`End Sub`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="c55f1-149">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="c55f1-150">在函式主體，加入下列程式碼來叫用副程式時執行。</span><span class="sxs-lookup"><span data-stu-id="c55f1-150">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     <span data-ttu-id="c55f1-151">[!code-vb[VbVbalrLambdas #&21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-151">[!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span></span>  
  
     <span data-ttu-id="c55f1-152">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="c55f1-152">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="c55f1-153">[!code-vb[VbVbalrLambdas #&22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-153">[!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c55f1-154">範例</span><span class="sxs-lookup"><span data-stu-id="c55f1-154">Example</span></span>  
 <span data-ttu-id="c55f1-155">定義可以做為參數的型別引數傳入的函式的 lambda 運算式的常見用法是`Delegate`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-155">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="c55f1-156">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回本機電腦上執行的處理程序的陣列。</xref:System.Diagnostics.Process.GetProcesses%2A></span><span class="sxs-lookup"><span data-stu-id="c55f1-156">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="c55f1-157"><xref:System.Linq.Enumerable.Where%2A>方法從<xref:System.Linq.Enumerable>類別需要`Boolean`委派做為引數。</xref:System.Linq.Enumerable> </xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="c55f1-157">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="c55f1-158">在範例中的 lambda 運算式用來達成目的。</span><span class="sxs-lookup"><span data-stu-id="c55f1-158">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="c55f1-159">它會傳回`True`每個處理序只有一個執行緒，且那些中所選`filteredList`。</span><span class="sxs-lookup"><span data-stu-id="c55f1-159">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 <span data-ttu-id="c55f1-160">[!code-vb[VbVbalrLambdas #&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-160">[!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span></span>  
  
 <span data-ttu-id="c55f1-161">上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]語法︰</span><span class="sxs-lookup"><span data-stu-id="c55f1-161">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] syntax:</span></span>  
  
 <span data-ttu-id="c55f1-162">[!code-vb[VbVbalrLambdas #&11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="c55f1-162">[!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55f1-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c55f1-163">See Also</span></span>  
 <span data-ttu-id="c55f1-164"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="c55f1-164"><xref:System.Linq.Enumerable></span></span>   
<span data-ttu-id="c55f1-165"> [Lambda 運算式](./lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-165"> [Lambda Expressions](./lambda-expressions.md) </span></span>  
<span data-ttu-id="c55f1-166"> [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-166"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="c55f1-167"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-167"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="c55f1-168"> [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-168"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="c55f1-169"> [如何︰ 將傳遞至另一個程序，在 Visual Basic 中的程序](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-169"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="c55f1-170"> [Delegate 陳述式](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c55f1-170"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="c55f1-171"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="c55f1-171"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
