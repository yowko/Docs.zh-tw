---
title: "函式運算式 (Visual Basic) |Microsoft 文件"
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
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: c379ed1694f72243ccb8367d5b820803b4fcf190
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="b6e68-102">函式運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6e68-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="b6e68-103">宣告的參數和函式的 lambda 運算式定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6e68-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e68-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6e68-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="b6e68-105">組件</span><span class="sxs-lookup"><span data-stu-id="b6e68-105">Parts</span></span>  
  
|<span data-ttu-id="b6e68-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="b6e68-106">Term</span></span>|<span data-ttu-id="b6e68-107">定義</span><span class="sxs-lookup"><span data-stu-id="b6e68-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="b6e68-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="b6e68-108">Optional.</span></span> <span data-ttu-id="b6e68-109">本機變數的名稱，表示此程序的參數清單。</span><span class="sxs-lookup"><span data-stu-id="b6e68-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="b6e68-110">括號必須存在，即使清單是空的。</span><span class="sxs-lookup"><span data-stu-id="b6e68-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="b6e68-111">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e68-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="b6e68-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="b6e68-112">Required.</span></span> <span data-ttu-id="b6e68-113">單一運算式。</span><span class="sxs-lookup"><span data-stu-id="b6e68-113">A single expression.</span></span> <span data-ttu-id="b6e68-114">運算式的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b6e68-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="b6e68-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="b6e68-115">Required.</span></span> <span data-ttu-id="b6e68-116">使用傳回值的陳述式清單`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6e68-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="b6e68-117">(請參閱[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。)傳回值的類型是函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b6e68-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6e68-118">備註</span><span class="sxs-lookup"><span data-stu-id="b6e68-118">Remarks</span></span>  
 <span data-ttu-id="b6e68-119">A *lambda 運算式*是函式不會計算並傳回值的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6e68-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="b6e68-120">您可以使用 lambda 運算式任何地方使用委派類型，除了做為引數`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="b6e68-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="b6e68-121">如需委派和使用委派 lambda 運算式的詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e68-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="b6e68-122">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="b6e68-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="b6e68-123">Lambda 運算式的語法類似於標準函式。</span><span class="sxs-lookup"><span data-stu-id="b6e68-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="b6e68-124">差異如下︰</span><span class="sxs-lookup"><span data-stu-id="b6e68-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="b6e68-125">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="b6e68-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="b6e68-126">Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="b6e68-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="b6e68-127">不使用 lambda 運算式`As`子句來指定函式的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b6e68-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="b6e68-128">相反地，來自單行 lambda 運算式的主體，所評估的值或多行 lambda 運算式的傳回值推斷型別。</span><span class="sxs-lookup"><span data-stu-id="b6e68-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="b6e68-129">例如，如果單行 lambda 運算式的主體是`Where cust.City = "London"`，其傳回型別是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="b6e68-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="b6e68-130">單行 lambda 運算式的主體必須是運算式，而不是陳述式。</span><span class="sxs-lookup"><span data-stu-id="b6e68-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="b6e68-131">主體可以包含呼叫的函式程序，但不呼叫 sub 程序。</span><span class="sxs-lookup"><span data-stu-id="b6e68-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="b6e68-132">必須推斷資料型別或所有必須指定所有參數。</span><span class="sxs-lookup"><span data-stu-id="b6e68-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="b6e68-133">不允許選用和參數陣列參數。</span><span class="sxs-lookup"><span data-stu-id="b6e68-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="b6e68-134">不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="b6e68-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e68-135">範例</span><span class="sxs-lookup"><span data-stu-id="b6e68-135">Example</span></span>  
 <span data-ttu-id="b6e68-136">下列範例示範兩種方式建立簡單的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="b6e68-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="b6e68-137">第一個使用`Dim`提供函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6e68-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="b6e68-138">若要呼叫的函式，您傳送參數的值。</span><span class="sxs-lookup"><span data-stu-id="b6e68-138">To call the function, you send in a value for the parameter.</span></span>  
  
 <span data-ttu-id="b6e68-139">[!code-vb[VbVbalrLambdas #&1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6e68-139">[!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span></span>  
  
 <span data-ttu-id="b6e68-140">[!code-vb[VbVbalrLambdas #&2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6e68-140">[!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e68-141">範例</span><span class="sxs-lookup"><span data-stu-id="b6e68-141">Example</span></span>  
 <span data-ttu-id="b6e68-142">或者，您可以宣告和函式執行一次。</span><span class="sxs-lookup"><span data-stu-id="b6e68-142">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 <span data-ttu-id="b6e68-143">[!code-vb[VbVbalrLambdas #&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6e68-143">[!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e68-144">範例</span><span class="sxs-lookup"><span data-stu-id="b6e68-144">Example</span></span>  
 <span data-ttu-id="b6e68-145">以下是遞增其引數和傳回值的 lambda 運算式的範例。</span><span class="sxs-lookup"><span data-stu-id="b6e68-145">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="b6e68-146">函式的兩個單行或多行 lambda 運算式語法範例。</span><span class="sxs-lookup"><span data-stu-id="b6e68-146">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="b6e68-147">如需詳細資訊，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e68-147">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="b6e68-148">[!code-vb[VbVbalrLambdas #&14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6e68-148">[!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e68-149">範例</span><span class="sxs-lookup"><span data-stu-id="b6e68-149">Example</span></span>  
 <span data-ttu-id="b6e68-150">Lambda 運算式為基礎的查詢運算子，在許多[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]，並可以在以方法為基礎的查詢中明確地使用。</span><span class="sxs-lookup"><span data-stu-id="b6e68-150">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="b6e68-151">下列範例示範典型[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]後面接著的查詢轉譯成方法格式的查詢。</span><span class="sxs-lookup"><span data-stu-id="b6e68-151">The following example shows a typical [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="b6e68-152">如需查詢方法的詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e68-152">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="b6e68-153">如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。</span><span class="sxs-lookup"><span data-stu-id="b6e68-153">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e68-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e68-154">See Also</span></span>  
 <span data-ttu-id="b6e68-155">[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-155">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="b6e68-156"> [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-156"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="b6e68-157"> [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="b6e68-158"> [陳述式](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-158"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="b6e68-159"> [值的比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-159"> [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="b6e68-160"> [布林運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-160"> [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="b6e68-161"> [如果運算子](../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b6e68-161"> [If Operator](../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="b6e68-162"> [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="b6e68-162"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

