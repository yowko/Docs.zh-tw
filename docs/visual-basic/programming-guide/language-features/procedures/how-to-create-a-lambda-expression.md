---
title: HOW TO：建立 Lambda 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344542"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="f8e38-102">HOW TO：建立 Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8e38-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="f8e38-103">A *lambda 運算式*函式或副程式，並沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="f8e38-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="f8e38-104">只要委派型別有效，則可以使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="f8e38-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="f8e38-105">若要建立的單行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="f8e38-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="f8e38-106">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f8e38-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="f8e38-107">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-107">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f8e38-108">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-108">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. <span data-ttu-id="f8e38-109">下列參數清單中，輸入單一運算式做為函式的主體。</span><span class="sxs-lookup"><span data-stu-id="f8e38-109">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="f8e38-110">運算式評估為值是函式所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="f8e38-110">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="f8e38-111">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f8e38-111">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="f8e38-112">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-112">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="f8e38-113">或者，是由下列的範例來完成相同的結果：</span><span class="sxs-lookup"><span data-stu-id="f8e38-113">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="f8e38-114">若要建立副程式，單行 lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f8e38-114">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="f8e38-115">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f8e38-115">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="f8e38-116">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="f8e38-116">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f8e38-117">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-117">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. <span data-ttu-id="f8e38-118">下列參數清單中，輸入單一陳述式為副程式的內文。</span><span class="sxs-lookup"><span data-stu-id="f8e38-118">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="f8e38-119">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-119">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="f8e38-120">若要建立多行 lambda 運算式函式</span><span class="sxs-lookup"><span data-stu-id="f8e38-120">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="f8e38-121">在委派型別可以使用其中任何情況下，輸入關鍵字`Function`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f8e38-121">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="f8e38-122">在括號內，直接在之後`Function`，型別函式的參數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-122">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f8e38-123">請注意，您不指定的名稱之後`Function`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-123">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. <span data-ttu-id="f8e38-124">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f8e38-124">Press ENTER.</span></span> <span data-ttu-id="f8e38-125">`End Function`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="f8e38-125">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="f8e38-126">在函式主體中，新增下列程式碼，以建立運算式，並傳回值。</span><span class="sxs-lookup"><span data-stu-id="f8e38-126">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="f8e38-127">您不使用`As`子句，以指定的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="f8e38-127">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="f8e38-128">Lambda 運算式可以呼叫傳入整數引數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-128">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="f8e38-129">若要建立多行 lambda 運算式副程式</span><span class="sxs-lookup"><span data-stu-id="f8e38-129">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="f8e38-130">在委派型別可以使用其中任何情況下，輸入關鍵字`Sub`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f8e38-130">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="f8e38-131">在括號內，直接在之後`Sub`，型別參數的副程式。</span><span class="sxs-lookup"><span data-stu-id="f8e38-131">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f8e38-132">請注意，您不指定的名稱之後`Sub`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-132">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. <span data-ttu-id="f8e38-133">請按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f8e38-133">Press ENTER.</span></span> <span data-ttu-id="f8e38-134">`End Sub`陳述式會自動加入。</span><span class="sxs-lookup"><span data-stu-id="f8e38-134">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="f8e38-135">在函式主體中，新增下列程式碼執行時叫用副程式。</span><span class="sxs-lookup"><span data-stu-id="f8e38-135">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="f8e38-136">Lambda 運算式可以呼叫傳入的字串引數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-136">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="f8e38-137">範例</span><span class="sxs-lookup"><span data-stu-id="f8e38-137">Example</span></span>  
 <span data-ttu-id="f8e38-138">Lambda 運算式的常見用法是定義的函式，可以做為參數的型別引數傳入`Delegate`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-138">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="f8e38-139">在下列範例中，<xref:System.Diagnostics.Process.GetProcesses%2A>方法會傳回陣列的本機電腦上執行的處理程序。</span><span class="sxs-lookup"><span data-stu-id="f8e38-139">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="f8e38-140"><xref:System.Linq.Enumerable.Where%2A>方法，從<xref:System.Linq.Enumerable>類別需要`Boolean`委派作為其引數。</span><span class="sxs-lookup"><span data-stu-id="f8e38-140">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="f8e38-141">在範例中的 lambda 運算式用於該目的。</span><span class="sxs-lookup"><span data-stu-id="f8e38-141">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="f8e38-142">它會傳回`True`每個處理序具有只有一個執行緒，且在已選取這些`filteredList`。</span><span class="sxs-lookup"><span data-stu-id="f8e38-142">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="f8e38-143">上述範例相當於下列程式碼，以撰寫[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]語法：</span><span class="sxs-lookup"><span data-stu-id="f8e38-143">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="f8e38-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8e38-144">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="f8e38-145">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f8e38-145">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="f8e38-146">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8e38-146">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="f8e38-147">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8e38-147">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f8e38-148">委派</span><span class="sxs-lookup"><span data-stu-id="f8e38-148">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="f8e38-149">HOW TO：傳遞至另一個程序，在 Visual Basic 中的程序</span><span class="sxs-lookup"><span data-stu-id="f8e38-149">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="f8e38-150">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8e38-150">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f8e38-151">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="f8e38-151">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
