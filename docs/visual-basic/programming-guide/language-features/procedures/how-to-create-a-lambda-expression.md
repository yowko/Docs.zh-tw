---
title: 如何：建立 Lambda 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 1c65841e4c124252cfa41bcd4d0c305a426687ee
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632346"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="3fb8a-102">如何：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fb8a-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="3fb8a-103">*Lambda 運算式*是不具有名稱的函數或副程式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="3fb8a-104">只要委派型別有效，就可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="3fb8a-105">建立單行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="3fb8a-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="3fb8a-106">在可以使用委派類型的任何情況下，輸入關鍵字 `Function`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3fb8a-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="3fb8a-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="3fb8a-108">在括弧中，直接在 `Function`之後，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="3fb8a-109">請注意，您不會在 `Function`之後指定名稱。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="3fb8a-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="3fb8a-111">在 [參數清單] 後面，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="3fb8a-112">運算式評估為的值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="3fb8a-113">您不能使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="3fb8a-114">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="3fb8a-115">或者，也可以透過下列範例來完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="3fb8a-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="3fb8a-116">建立單行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="3fb8a-117">在可以使用委派類型的任何情況下，輸入關鍵字 `Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="3fb8a-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="3fb8a-119">在括弧中，直接在 `Sub`之後，輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="3fb8a-120">請注意，您不會在 `Sub`之後指定名稱。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="3fb8a-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="3fb8a-122">在 [參數清單] 後面，輸入單一語句作為副程式的主體。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="3fb8a-123">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="3fb8a-124">若要建立多行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="3fb8a-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="3fb8a-125">在可以使用委派類型的任何情況下，輸入關鍵字 `Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="3fb8a-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="3fb8a-127">在括弧中，直接在 `Function`之後，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="3fb8a-128">請注意，您不會在 `Function`之後指定名稱。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="3fb8a-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="3fb8a-130">按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-130">Press ENTER.</span></span> <span data-ttu-id="3fb8a-131">系統會自動新增 `End Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="3fb8a-132">在函式主體內，新增下列程式碼以建立運算式並傳回值。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="3fb8a-133">您不能使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="3fb8a-134">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="3fb8a-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="3fb8a-136">在可以使用委派類型的任何情況下，輸入關鍵字 `Sub`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3fb8a-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="3fb8a-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="3fb8a-138">在括弧中，直接在 `Sub`之後，輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="3fb8a-139">請注意，您不會在 `Sub`之後指定名稱。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="3fb8a-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="3fb8a-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="3fb8a-141">按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-141">Press ENTER.</span></span> <span data-ttu-id="3fb8a-142">系統會自動新增 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="3fb8a-143">在函式主體內，新增下列程式碼，以在叫用副程式時執行。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="3fb8a-144">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="3fb8a-145">範例</span><span class="sxs-lookup"><span data-stu-id="3fb8a-145">Example</span></span>  
 <span data-ttu-id="3fb8a-146">Lambda 運算式的常見用法是定義一個函式，該函式可當做參數（其類型為 `Delegate`的引數）傳入。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="3fb8a-147">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A> 方法會傳回本機電腦上執行的進程陣列。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="3fb8a-148">來自 <xref:System.Linq.Enumerable> 類別的 <xref:System.Linq.Enumerable.Where%2A> 方法需要 `Boolean` 委派做為其引數。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="3fb8a-149">範例中的 lambda 運算式用於該目的。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="3fb8a-150">它會針對只有一個執行緒的每個進程傳回 `True`，並在 `filteredList`中選取這些程式。</span><span class="sxs-lookup"><span data-stu-id="3fb8a-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="3fb8a-151">上一個範例相當於下列程式碼，這是以語言整合式查詢（LINQ）語法撰寫的：</span><span class="sxs-lookup"><span data-stu-id="3fb8a-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3fb8a-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fb8a-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="3fb8a-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="3fb8a-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3fb8a-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="3fb8a-156">委派</span><span class="sxs-lookup"><span data-stu-id="3fb8a-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="3fb8a-157">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="3fb8a-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="3fb8a-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="3fb8a-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="3fb8a-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="3fb8a-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
