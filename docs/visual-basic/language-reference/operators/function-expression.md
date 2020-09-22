---
title: 函式運算式
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 719969be23a6d94f22a1d86cb4ad3f37e4c3b254
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873415"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="d5ffb-102">函式運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5ffb-102">Function Expression (Visual Basic)</span></span>

<span data-ttu-id="d5ffb-103">宣告定義函數 lambda 運算式的參數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ffb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5ffb-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="d5ffb-105">組件</span><span class="sxs-lookup"><span data-stu-id="d5ffb-105">Parts</span></span>  
  
|<span data-ttu-id="d5ffb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="d5ffb-106">Term</span></span>|<span data-ttu-id="d5ffb-107">定義</span><span class="sxs-lookup"><span data-stu-id="d5ffb-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="d5ffb-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-108">Optional.</span></span> <span data-ttu-id="d5ffb-109">區域變數名稱的清單，這些變數表示此程式的參數。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="d5ffb-110">即使清單是空的，也必須有括弧。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="d5ffb-111">請參閱 [參數清單](../statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-111">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="d5ffb-112">必要。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-112">Required.</span></span> <span data-ttu-id="d5ffb-113">單一運算式。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-113">A single expression.</span></span> <span data-ttu-id="d5ffb-114">運算式的型別是函數的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="d5ffb-115">必要。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-115">Required.</span></span> <span data-ttu-id="d5ffb-116">使用語句傳回值的語句清單 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="d5ffb-117"> (請參閱 [Return 語句](../statements/return-statement.md)。 ) 傳回值的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-117">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5ffb-118">備註</span><span class="sxs-lookup"><span data-stu-id="d5ffb-118">Remarks</span></span>  

 <span data-ttu-id="d5ffb-119">*Lambda 運算式*是沒有名稱的函式，其會計算並傳回值。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="d5ffb-120">除了做為的引數以外，您可以在任何可使用委派類型的位置使用 lambda 運算式 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="d5ffb-121">如需委派的詳細資訊，以及使用 lambda 運算式搭配委派的詳細資訊，請參閱 [委派語句](../statements/delegate-statement.md) 和 [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="d5ffb-122">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="d5ffb-122">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="d5ffb-123">Lambda 運算式的語法與標準函式的語法類似。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="d5ffb-124">差異如下：</span><span class="sxs-lookup"><span data-stu-id="d5ffb-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="d5ffb-125">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="d5ffb-126">Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="d5ffb-127">Lambda 運算式不使用 `As` 子句來指定函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="d5ffb-128">相反地，型別是從單行 lambda 運算式的主體評估為的值，或是多行 lambda 運算式的傳回值推斷而來。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="d5ffb-129">例如，如果單行 lambda 運算式的主體是 `Where cust.City = "London"` ，其傳回型別為 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="d5ffb-130">單行 lambda 運算式的主體必須是運算式，而非語句。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="d5ffb-131">本文可能包含對函數程式的呼叫，但不包含對 sub 程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="d5ffb-132">所有參數都必須有指定的資料類型，或全部都必須加以推斷。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="d5ffb-133">不允許選擇性和 Paramarray 參數。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="d5ffb-134">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5ffb-135">範例</span><span class="sxs-lookup"><span data-stu-id="d5ffb-135">Example</span></span>  

 <span data-ttu-id="d5ffb-136">下列範例示範兩種建立簡單 lambda 運算式的方式。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="d5ffb-137">第一個使用 `Dim` 來提供函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="d5ffb-138">若要呼叫函式，請將參數的值傳送給。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="d5ffb-139">範例</span><span class="sxs-lookup"><span data-stu-id="d5ffb-139">Example</span></span>  

 <span data-ttu-id="d5ffb-140">或者，您也可以同時宣告和執行函數。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="d5ffb-141">範例</span><span class="sxs-lookup"><span data-stu-id="d5ffb-141">Example</span></span>  

 <span data-ttu-id="d5ffb-142">以下是 lambda 運算式的範例，它會遞增其引數並傳回值。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="d5ffb-143">此範例會顯示函數的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="d5ffb-144">如需更多範例，請參閱 [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-144">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="d5ffb-145">範例</span><span class="sxs-lookup"><span data-stu-id="d5ffb-145">Example</span></span>  

 <span data-ttu-id="d5ffb-146">Lambda 運算式在語言整合查詢中有許多查詢運算子 (LINQ) ，而且可以在以方法為基礎的查詢中明確地使用。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="d5ffb-147">下列範例顯示一般 LINQ 查詢，然後將查詢轉譯成方法格式。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="d5ffb-148">如需查詢方法的詳細資訊，請參閱 [查詢](../queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-148">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="d5ffb-149">如需標準查詢運算子的詳細資訊，請參閱 [標準查詢運算子總覽](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffb-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ffb-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ffb-150">See also</span></span>

- [<span data-ttu-id="d5ffb-151">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="d5ffb-151">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="d5ffb-152">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d5ffb-152">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d5ffb-153">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="d5ffb-153">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="d5ffb-154">陳述式</span><span class="sxs-lookup"><span data-stu-id="d5ffb-154">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="d5ffb-155">數值比較</span><span class="sxs-lookup"><span data-stu-id="d5ffb-155">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="d5ffb-156">布林運算式</span><span class="sxs-lookup"><span data-stu-id="d5ffb-156">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="d5ffb-157">If 運算子</span><span class="sxs-lookup"><span data-stu-id="d5ffb-157">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="d5ffb-158">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="d5ffb-158">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
