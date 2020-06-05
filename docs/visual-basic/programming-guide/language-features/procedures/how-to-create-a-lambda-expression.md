---
title: 如何：建立 Lambda 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 7affc84fa501ba98bdfa93835f0b0e381580b9bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388383"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="d6df8-102">如何：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6df8-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="d6df8-103">*Lambda 運算式*是不具有名稱的函數或副程式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="d6df8-104">只要委派型別有效，就可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="d6df8-105">建立單行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="d6df8-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="d6df8-106">在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d6df8-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="d6df8-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="d6df8-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="d6df8-108">在括弧中，緊接在之後 `Function` ，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="d6df8-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="d6df8-109">請注意，您不會在之後指定名稱 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="d6df8-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="d6df8-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="d6df8-111">在 [參數清單] 後面，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="d6df8-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="d6df8-112">運算式評估為的值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d6df8-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="d6df8-113">您不能使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d6df8-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="d6df8-114">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="d6df8-115">或者，也可以透過下列範例來完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="d6df8-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="d6df8-116">建立單行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="d6df8-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="d6df8-117">在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d6df8-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="d6df8-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="d6df8-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="d6df8-119">在括弧中，緊接在之後 `Sub` ，輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="d6df8-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="d6df8-120">請注意，您不會在之後指定名稱 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="d6df8-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="d6df8-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="d6df8-122">在 [參數清單] 後面，輸入單一語句作為副程式的主體。</span><span class="sxs-lookup"><span data-stu-id="d6df8-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="d6df8-123">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="d6df8-124">若要建立多行 lambda 運算式函數</span><span class="sxs-lookup"><span data-stu-id="d6df8-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="d6df8-125">在可以使用委派類型的任何情況下，請輸入關鍵字 `Function` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d6df8-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="d6df8-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="d6df8-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="d6df8-127">在括弧中，緊接在之後 `Function` ，輸入函數的參數。</span><span class="sxs-lookup"><span data-stu-id="d6df8-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="d6df8-128">請注意，您不會在之後指定名稱 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="d6df8-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="d6df8-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="d6df8-130">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d6df8-130">Press ENTER.</span></span> <span data-ttu-id="d6df8-131">`End Function`語句會自動新增。</span><span class="sxs-lookup"><span data-stu-id="d6df8-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="d6df8-132">在函式主體內，新增下列程式碼以建立運算式並傳回值。</span><span class="sxs-lookup"><span data-stu-id="d6df8-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="d6df8-133">您不能使用 `As` 子句來指定傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d6df8-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="d6df8-134">您可以藉由傳入整數引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="d6df8-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="d6df8-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="d6df8-136">在可以使用委派類型的任何情況下，請輸入關鍵字 `Sub` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d6df8-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="d6df8-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="d6df8-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="d6df8-138">在括弧中，緊接在之後 `Sub` ，輸入副程式的參數。</span><span class="sxs-lookup"><span data-stu-id="d6df8-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="d6df8-139">請注意，您不會在之後指定名稱 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="d6df8-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="d6df8-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="d6df8-141">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d6df8-141">Press ENTER.</span></span> <span data-ttu-id="d6df8-142">`End Sub`語句會自動新增。</span><span class="sxs-lookup"><span data-stu-id="d6df8-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="d6df8-143">在函式主體內，新增下列程式碼，以在叫用副程式時執行。</span><span class="sxs-lookup"><span data-stu-id="d6df8-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="d6df8-144">您可以藉由傳入字串引數來呼叫 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d6df8-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="d6df8-145">範例</span><span class="sxs-lookup"><span data-stu-id="d6df8-145">Example</span></span>  
 <span data-ttu-id="d6df8-146">Lambda 運算式的常見用法是定義一個函式，該函式可以當做類型為之參數的引數來傳遞 `Delegate` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="d6df8-147">在下列範例中，方法會傳回在 <xref:System.Diagnostics.Process.GetProcesses%2A> 本機電腦上執行的進程陣列。</span><span class="sxs-lookup"><span data-stu-id="d6df8-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="d6df8-148"><xref:System.Linq.Enumerable.Where%2A>類別中的方法 <xref:System.Linq.Enumerable> 需要 `Boolean` 委派做為其引數。</span><span class="sxs-lookup"><span data-stu-id="d6df8-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="d6df8-149">範例中的 lambda 運算式用於該目的。</span><span class="sxs-lookup"><span data-stu-id="d6df8-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="d6df8-150">它會 `True` 針對只有一個執行緒的每個進程傳回，並在中選取這些程式 `filteredList` 。</span><span class="sxs-lookup"><span data-stu-id="d6df8-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="d6df8-151">上一個範例相當於下列程式碼，這是以語言整合式查詢（LINQ）語法撰寫的：</span><span class="sxs-lookup"><span data-stu-id="d6df8-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d6df8-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6df8-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="d6df8-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d6df8-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="d6df8-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6df8-154">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="d6df8-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6df8-155">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d6df8-156">委派</span><span class="sxs-lookup"><span data-stu-id="d6df8-156">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="d6df8-157">如何：在 Visual Basic 中將程序傳遞至其他程序</span><span class="sxs-lookup"><span data-stu-id="d6df8-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="d6df8-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="d6df8-158">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="d6df8-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="d6df8-159">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
