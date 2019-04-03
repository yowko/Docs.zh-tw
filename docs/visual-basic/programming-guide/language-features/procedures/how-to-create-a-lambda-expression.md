---
title: HOW TO：建立 Lambda 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 8754049e493ab23b1e7b01d0f315b00bdebf0378
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841416"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="34d54-102">HOW TO：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34d54-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="34d54-103">A *lambda 運算式*函式或副程式，並沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="34d54-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="34d54-104">只要委派型別有效，則可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="34d54-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="34d54-105">若要建立的單行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="34d54-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="34d54-106">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34d54-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="34d54-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="34d54-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="34d54-108">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="34d54-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="34d54-109">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="34d54-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="34d54-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="34d54-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="34d54-111">下列參數清單中，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="34d54-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="34d54-112">運算式評估為值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="34d54-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="34d54-113">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="34d54-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="34d54-114">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="34d54-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4.  <span data-ttu-id="34d54-115">或者，是由下列的範例來完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="34d54-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="34d54-116">若要建立副程式，單行 lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="34d54-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="34d54-117">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="34d54-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="34d54-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="34d54-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="34d54-119">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="34d54-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="34d54-120">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="34d54-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="34d54-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="34d54-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="34d54-122">下列參數清單中，輸入單一陳述式為副程式的內文。</span><span class="sxs-lookup"><span data-stu-id="34d54-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="34d54-123">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="34d54-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="34d54-124">若要建立多行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="34d54-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="34d54-125">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="34d54-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="34d54-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="34d54-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="34d54-127">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="34d54-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="34d54-128">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="34d54-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="34d54-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="34d54-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="34d54-130">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="34d54-130">Press ENTER.</span></span> <span data-ttu-id="34d54-131">`End Function`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="34d54-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="34d54-132">在函式主體中，新增下列程式碼，以建立運算式，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="34d54-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="34d54-133">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="34d54-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="34d54-134">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="34d54-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="34d54-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="34d54-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="34d54-136">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="34d54-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="34d54-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="34d54-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="34d54-138">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="34d54-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="34d54-139">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="34d54-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="34d54-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="34d54-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="34d54-141">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="34d54-141">Press ENTER.</span></span> <span data-ttu-id="34d54-142">`End Sub`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="34d54-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="34d54-143">在函式主體中，新增下列程式碼執行時叫用副程式。</span><span class="sxs-lookup"><span data-stu-id="34d54-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="34d54-144">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="34d54-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="34d54-145">範例</span><span class="sxs-lookup"><span data-stu-id="34d54-145">Example</span></span>  
 <span data-ttu-id="34d54-146">Lambda 運算式的常見用法是定義的函式，可以做為參數的型別引數傳入`Delegate`。</span><span class="sxs-lookup"><span data-stu-id="34d54-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="34d54-147">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回陣列的本機電腦上執行的處理程序。</span><span class="sxs-lookup"><span data-stu-id="34d54-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="34d54-148"><xref:System.Linq.Enumerable.Where%2A>方法，從<xref:System.Linq.Enumerable>類別需要`Boolean`委派作為其引數。</span><span class="sxs-lookup"><span data-stu-id="34d54-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="34d54-149">在範例中的 lambda 運算式用於該目的。</span><span class="sxs-lookup"><span data-stu-id="34d54-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="34d54-150">它會傳回`True`每個處理序具有只有一個執行緒，且在已選取這些`filteredList`。</span><span class="sxs-lookup"><span data-stu-id="34d54-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="34d54-151">上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]語法：</span><span class="sxs-lookup"><span data-stu-id="34d54-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="34d54-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34d54-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="34d54-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="34d54-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="34d54-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="34d54-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="34d54-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="34d54-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="34d54-156">委派</span><span class="sxs-lookup"><span data-stu-id="34d54-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="34d54-157">如何：傳遞至另一個程序，在 Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="34d54-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="34d54-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="34d54-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="34d54-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="34d54-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
