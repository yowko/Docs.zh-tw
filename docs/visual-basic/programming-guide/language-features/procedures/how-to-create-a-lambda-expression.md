---
title: 如何：建立 Lambda 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: cc2de38f7375848d104edff6f419656d9caa9cb2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071920"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="34f9f-102">如何：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34f9f-102">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="34f9f-103">*Lambda 運算式*是沒有名稱的函數或副程式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="34f9f-104">只要委派型別是有效的，就可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="34f9f-105">若要建立單行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="34f9f-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="34f9f-106">在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34f9f-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="34f9f-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="34f9f-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="34f9f-108">在括弧中，直接 `Function` 輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="34f9f-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="34f9f-109">請注意，您不會在之後指定名稱 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="34f9f-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="34f9f-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="34f9f-111">在參數清單之後，輸入單一運算式作為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="34f9f-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="34f9f-112">運算式評估為的值是函數所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="34f9f-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="34f9f-113">您不使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="34f9f-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="34f9f-114">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="34f9f-115">另外，下列範例也會完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="34f9f-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="34f9f-116">若要建立單行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="34f9f-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="34f9f-117">在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="34f9f-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="34f9f-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="34f9f-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="34f9f-119">在括弧中，直接 `Sub` 輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="34f9f-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="34f9f-120">請注意，您不會在之後指定名稱 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="34f9f-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="34f9f-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="34f9f-122">在參數清單之後，輸入單一語句作為副程式的主體。</span><span class="sxs-lookup"><span data-stu-id="34f9f-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="34f9f-123">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="34f9f-124">若要建立多行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="34f9f-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="34f9f-125">在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="34f9f-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="34f9f-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="34f9f-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="34f9f-127">在括弧中，直接 `Function` 輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="34f9f-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="34f9f-128">請注意，您不會在之後指定名稱 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="34f9f-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="34f9f-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="34f9f-130">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="34f9f-130">Press ENTER.</span></span> <span data-ttu-id="34f9f-131">`End Function`系統會自動加入語句。</span><span class="sxs-lookup"><span data-stu-id="34f9f-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="34f9f-132">在函式主體中，加入下列程式碼以建立運算式並傳回值。</span><span class="sxs-lookup"><span data-stu-id="34f9f-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="34f9f-133">您不使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="34f9f-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="34f9f-134">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="34f9f-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="34f9f-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="34f9f-136">在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34f9f-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="34f9f-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="34f9f-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="34f9f-138">在括弧中，直接 `Sub` 輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="34f9f-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="34f9f-139">請注意，您不會在之後指定名稱 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="34f9f-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="34f9f-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="34f9f-141">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="34f9f-141">Press ENTER.</span></span> <span data-ttu-id="34f9f-142">`End Sub`系統會自動加入語句。</span><span class="sxs-lookup"><span data-stu-id="34f9f-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="34f9f-143">在函式主體中，加入下列程式碼，以在叫用副程式時執行。</span><span class="sxs-lookup"><span data-stu-id="34f9f-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="34f9f-144">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34f9f-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="34f9f-145">範例</span><span class="sxs-lookup"><span data-stu-id="34f9f-145">Example</span></span>  

 <span data-ttu-id="34f9f-146">Lambda 運算式的常見用法是定義一個函式，這個函式可以當做型別為之參數的引數傳遞 `Delegate` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="34f9f-147">在下列範例中，方法會傳回在 <xref:System.Diagnostics.Process.GetProcesses%2A> 本機電腦上執行之進程的陣列。</span><span class="sxs-lookup"><span data-stu-id="34f9f-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="34f9f-148"><xref:System.Linq.Enumerable.Where%2A>類別中的方法 <xref:System.Linq.Enumerable> 需要 `Boolean` 委派做為其引數。</span><span class="sxs-lookup"><span data-stu-id="34f9f-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="34f9f-149">此範例中的 lambda 運算式會用於該用途。</span><span class="sxs-lookup"><span data-stu-id="34f9f-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="34f9f-150">它會 `True` 針對只有一個執行緒的每個進程傳回，而且在中選取這些程式 `filteredList` 。</span><span class="sxs-lookup"><span data-stu-id="34f9f-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="34f9f-151">上述範例相當於下列程式碼，這是以語言整合查詢 (LINQ) 語法所撰寫：</span><span class="sxs-lookup"><span data-stu-id="34f9f-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="34f9f-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34f9f-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="34f9f-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="34f9f-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="34f9f-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="34f9f-154">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="34f9f-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="34f9f-155">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="34f9f-156">委派</span><span class="sxs-lookup"><span data-stu-id="34f9f-156">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="34f9f-157">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="34f9f-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="34f9f-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="34f9f-158">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="34f9f-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="34f9f-159">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
