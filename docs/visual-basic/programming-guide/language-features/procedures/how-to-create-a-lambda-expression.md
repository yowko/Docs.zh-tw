---
title: HOW TO：建立 Lambda 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665932"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="7518f-102">HOW TO：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7518f-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="7518f-103">A *lambda 運算式*函式或副程式，並沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="7518f-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="7518f-104">只要委派型別有效，則可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="7518f-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="7518f-105">若要建立的單行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="7518f-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="7518f-106">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7518f-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="7518f-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="7518f-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="7518f-108">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="7518f-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="7518f-109">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="7518f-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="7518f-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="7518f-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="7518f-111">下列參數清單中，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="7518f-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="7518f-112">運算式評估為值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="7518f-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="7518f-113">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7518f-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="7518f-114">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="7518f-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="7518f-115">或者，是由下列的範例來完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="7518f-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="7518f-116">若要建立副程式，單行 lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="7518f-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="7518f-117">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7518f-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="7518f-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="7518f-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="7518f-119">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="7518f-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="7518f-120">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="7518f-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="7518f-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="7518f-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="7518f-122">下列參數清單中，輸入單一陳述式為副程式的內文。</span><span class="sxs-lookup"><span data-stu-id="7518f-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="7518f-123">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="7518f-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="7518f-124">若要建立多行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="7518f-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="7518f-125">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7518f-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="7518f-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="7518f-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="7518f-127">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="7518f-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="7518f-128">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="7518f-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="7518f-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="7518f-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="7518f-130">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7518f-130">Press ENTER.</span></span> <span data-ttu-id="7518f-131">`End Function`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="7518f-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="7518f-132">在函式主體中，新增下列程式碼，以建立運算式，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="7518f-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="7518f-133">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7518f-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="7518f-134">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="7518f-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="7518f-135">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="7518f-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="7518f-136">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7518f-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="7518f-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="7518f-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="7518f-138">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="7518f-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="7518f-139">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="7518f-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="7518f-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="7518f-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="7518f-141">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7518f-141">Press ENTER.</span></span> <span data-ttu-id="7518f-142">`End Sub`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="7518f-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="7518f-143">在函式主體中，新增下列程式碼執行時叫用副程式。</span><span class="sxs-lookup"><span data-stu-id="7518f-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="7518f-144">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="7518f-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="7518f-145">範例</span><span class="sxs-lookup"><span data-stu-id="7518f-145">Example</span></span>  
 <span data-ttu-id="7518f-146">Lambda 運算式的常見用法是定義的函式，可以做為參數的型別引數傳入`Delegate`。</span><span class="sxs-lookup"><span data-stu-id="7518f-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="7518f-147">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回陣列的本機電腦上執行的處理程序。</span><span class="sxs-lookup"><span data-stu-id="7518f-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="7518f-148"><xref:System.Linq.Enumerable.Where%2A>方法，從<xref:System.Linq.Enumerable>類別需要`Boolean`委派作為其引數。</span><span class="sxs-lookup"><span data-stu-id="7518f-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="7518f-149">在範例中的 lambda 運算式用於該目的。</span><span class="sxs-lookup"><span data-stu-id="7518f-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="7518f-150">它會傳回`True`每個處理序具有只有一個執行緒，且在已選取這些`filteredList`。</span><span class="sxs-lookup"><span data-stu-id="7518f-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="7518f-151">上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]語法：</span><span class="sxs-lookup"><span data-stu-id="7518f-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7518f-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7518f-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="7518f-153">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="7518f-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="7518f-154">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="7518f-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7518f-155">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="7518f-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7518f-156">委派</span><span class="sxs-lookup"><span data-stu-id="7518f-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="7518f-157">如何：傳遞至另一個程序，在 Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="7518f-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="7518f-158">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="7518f-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="7518f-159">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="7518f-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
