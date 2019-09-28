---
title: 函式運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592199"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="d068a-102">函式運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d068a-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="d068a-103">宣告定義函式 lambda 運算式的參數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="d068a-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d068a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d068a-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="d068a-105">組件</span><span class="sxs-lookup"><span data-stu-id="d068a-105">Parts</span></span>  
  
|<span data-ttu-id="d068a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="d068a-106">Term</span></span>|<span data-ttu-id="d068a-107">定義</span><span class="sxs-lookup"><span data-stu-id="d068a-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="d068a-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d068a-108">Optional.</span></span> <span data-ttu-id="d068a-109">本機變數名稱的清單，代表此程式的參數。</span><span class="sxs-lookup"><span data-stu-id="d068a-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="d068a-110">即使清單是空的，括弧也必須存在。</span><span class="sxs-lookup"><span data-stu-id="d068a-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="d068a-111">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d068a-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="d068a-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="d068a-112">Required.</span></span> <span data-ttu-id="d068a-113">單一運算式。</span><span class="sxs-lookup"><span data-stu-id="d068a-113">A single expression.</span></span> <span data-ttu-id="d068a-114">運算式的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d068a-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="d068a-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="d068a-115">Required.</span></span> <span data-ttu-id="d068a-116">使用 `Return` 語句來傳回值的語句清單。</span><span class="sxs-lookup"><span data-stu-id="d068a-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="d068a-117">（請參閱[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)）。傳回值的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d068a-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d068a-118">備註</span><span class="sxs-lookup"><span data-stu-id="d068a-118">Remarks</span></span>  
 <span data-ttu-id="d068a-119">*Lambda 運算式*是沒有名稱的函式，會計算並傳回值。</span><span class="sxs-lookup"><span data-stu-id="d068a-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="d068a-120">您可以在任何可使用委派類型的位置使用 lambda 運算式，但 `RemoveHandler` 的引數除外。</span><span class="sxs-lookup"><span data-stu-id="d068a-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="d068a-121">如需委派的詳細資訊，以及搭配使用 lambda 運算式和委派的用法，請參閱[委派語句](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="d068a-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="d068a-122">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="d068a-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="d068a-123">Lambda 運算式的語法類似于標準函式。</span><span class="sxs-lookup"><span data-stu-id="d068a-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="d068a-124">差異如下：</span><span class="sxs-lookup"><span data-stu-id="d068a-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="d068a-125">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="d068a-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="d068a-126">Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="d068a-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="d068a-127">Lambda 運算式不會使用 `As` 子句來指定函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d068a-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="d068a-128">相反地，型別是從單行 lambda 運算式的主體評估為的值，或多行 lambda 運算式的傳回值推斷而來。</span><span class="sxs-lookup"><span data-stu-id="d068a-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="d068a-129">例如，如果單行 lambda 運算式的主體為 `Where cust.City = "London"`，則其傳回型別會 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="d068a-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="d068a-130">單行 lambda 運算式的主體必須是運算式，而不是語句。</span><span class="sxs-lookup"><span data-stu-id="d068a-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="d068a-131">主體可以包含函式程式的呼叫，而不是對 sub 程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d068a-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="d068a-132">所有參數都必須具有指定的資料類型，否則必須推斷全部。</span><span class="sxs-lookup"><span data-stu-id="d068a-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="d068a-133">不允許選擇性和 Paramarray 參數。</span><span class="sxs-lookup"><span data-stu-id="d068a-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="d068a-134">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="d068a-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d068a-135">範例</span><span class="sxs-lookup"><span data-stu-id="d068a-135">Example</span></span>  
 <span data-ttu-id="d068a-136">下列範例示範兩種建立簡單 lambda 運算式的方式。</span><span class="sxs-lookup"><span data-stu-id="d068a-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="d068a-137">第一個使用 `Dim` 來提供函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="d068a-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="d068a-138">若要呼叫函式，請傳送參數的值。</span><span class="sxs-lookup"><span data-stu-id="d068a-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="d068a-139">範例</span><span class="sxs-lookup"><span data-stu-id="d068a-139">Example</span></span>  
 <span data-ttu-id="d068a-140">或者，您可以同時宣告和執行函數。</span><span class="sxs-lookup"><span data-stu-id="d068a-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="d068a-141">範例</span><span class="sxs-lookup"><span data-stu-id="d068a-141">Example</span></span>  
 <span data-ttu-id="d068a-142">以下是 lambda 運算式的範例，它會遞增其引數並傳回值。</span><span class="sxs-lookup"><span data-stu-id="d068a-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="d068a-143">此範例會顯示函數的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="d068a-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="d068a-144">如需更多範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d068a-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="d068a-145">範例</span><span class="sxs-lookup"><span data-stu-id="d068a-145">Example</span></span>  
 <span data-ttu-id="d068a-146">Lambda 運算式在 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 中的許多查詢運算子，而且可以在以方法為基礎的查詢中明確地使用。</span><span class="sxs-lookup"><span data-stu-id="d068a-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="d068a-147">下列範例顯示一般的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢，然後將查詢轉譯成方法格式。</span><span class="sxs-lookup"><span data-stu-id="d068a-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="d068a-148">如需查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d068a-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="d068a-149">如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子總覽](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d068a-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d068a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d068a-150">See also</span></span>

- [<span data-ttu-id="d068a-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d068a-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d068a-152">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d068a-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d068a-153">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="d068a-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="d068a-154">陳述式</span><span class="sxs-lookup"><span data-stu-id="d068a-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="d068a-155">數值比較</span><span class="sxs-lookup"><span data-stu-id="d068a-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="d068a-156">布林運算式</span><span class="sxs-lookup"><span data-stu-id="d068a-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="d068a-157">If 運算子</span><span class="sxs-lookup"><span data-stu-id="d068a-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="d068a-158">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="d068a-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
