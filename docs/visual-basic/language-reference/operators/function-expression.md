---
title: 函式運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529632"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="7bcb8-102">函式運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcb8-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="7bcb8-103">宣告參數與定義的函式的 lambda 運算式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bcb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="7bcb8-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="7bcb8-105">組件</span><span class="sxs-lookup"><span data-stu-id="7bcb8-105">Parts</span></span>  
  
|<span data-ttu-id="7bcb8-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="7bcb8-106">Term</span></span>|<span data-ttu-id="7bcb8-107">定義</span><span class="sxs-lookup"><span data-stu-id="7bcb8-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="7bcb8-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-108">Optional.</span></span> <span data-ttu-id="7bcb8-109">本機變數的名稱，表示此程序參數的清單。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="7bcb8-110">括號必須要有即使清單是空的。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="7bcb8-111">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="7bcb8-112">必要。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-112">Required.</span></span> <span data-ttu-id="7bcb8-113">在單一運算式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-113">A single expression.</span></span> <span data-ttu-id="7bcb8-114">運算式的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="7bcb8-115">必要。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-115">Required.</span></span> <span data-ttu-id="7bcb8-116">陳述式會使用傳回值的清單`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="7bcb8-117">(請參閱[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。)傳回值的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bcb8-118">備註</span><span class="sxs-lookup"><span data-stu-id="7bcb8-118">Remarks</span></span>  
 <span data-ttu-id="7bcb8-119">A *lambda 運算式*是函式不會計算並傳回值的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="7bcb8-120">您可以使用 lambda 運算式任何地方使用委派類型，除非做為引數`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="7bcb8-121">如需委派和 lambda 運算式與委派使用的詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)並[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="7bcb8-122">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="7bcb8-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="7bcb8-123">Lambda 運算式的語法類似於標準函式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="7bcb8-124">差異如下所示：</span><span class="sxs-lookup"><span data-stu-id="7bcb8-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="7bcb8-125">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="7bcb8-126">Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="7bcb8-127">不使用 lambda 運算式`As`子句來指定函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="7bcb8-128">相反地，從單行 lambda 運算式的主體，所評估的值或多行 lambda 運算式的傳回值推斷型別。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="7bcb8-129">例如，單行 lambda 運算式的主體是否`Where cust.City = "London"`，其傳回類型是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="7bcb8-130">單行 lambda 運算式的主體必須是運算式，不是陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="7bcb8-131">主體可以包含的函式程序的呼叫，但不是呼叫子函數程序。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="7bcb8-132">可能是所有的參數必須必須推斷資料類型或全部指定。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="7bcb8-133">不允許 Optional 和 Paramarray 參數。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="7bcb8-134">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcb8-135">範例</span><span class="sxs-lookup"><span data-stu-id="7bcb8-135">Example</span></span>  
 <span data-ttu-id="7bcb8-136">下列範例顯示兩種方式可建立簡單的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="7bcb8-137">第一個範例使用`Dim`提供函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="7bcb8-138">若要呼叫的函式，您將會傳送參數的值。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7bcb8-139">範例</span><span class="sxs-lookup"><span data-stu-id="7bcb8-139">Example</span></span>  
 <span data-ttu-id="7bcb8-140">或者，您可以宣告，並在同一時間執行的函式。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="7bcb8-141">範例</span><span class="sxs-lookup"><span data-stu-id="7bcb8-141">Example</span></span>  
 <span data-ttu-id="7bcb8-142">以下是遞增其引數和傳回值的 lambda 運算式的範例。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="7bcb8-143">此範例會顯示函式的這兩個單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="7bcb8-144">如需其他範例，請參閱 < [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="7bcb8-145">範例</span><span class="sxs-lookup"><span data-stu-id="7bcb8-145">Example</span></span>  
 <span data-ttu-id="7bcb8-146">Lambda 運算式為基礎的查詢運算子，在許多[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]，並可以在以方法為基礎的查詢中明確使用。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="7bcb8-147">下列範例示範典型[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]後面接著的查詢轉譯成方法格式的查詢。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="7bcb8-148">如需有關查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="7bcb8-149">如需有關標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7bcb8-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bcb8-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bcb8-150">See Also</span></span>  
 [<span data-ttu-id="7bcb8-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="7bcb8-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="7bcb8-152">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="7bcb8-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="7bcb8-153">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="7bcb8-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="7bcb8-154">陳述式</span><span class="sxs-lookup"><span data-stu-id="7bcb8-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="7bcb8-155">數值比較</span><span class="sxs-lookup"><span data-stu-id="7bcb8-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="7bcb8-156">布林運算式</span><span class="sxs-lookup"><span data-stu-id="7bcb8-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="7bcb8-157">If 運算子</span><span class="sxs-lookup"><span data-stu-id="7bcb8-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="7bcb8-158">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="7bcb8-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
