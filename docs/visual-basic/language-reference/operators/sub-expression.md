---
title: Sub 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d284e629ea0b0a4e9b6eb9e098612bb07c38723b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350904"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="71b0a-102">Sub 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71b0a-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="71b0a-103">宣告定義副程式 lambda 運算式的參數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="71b0a-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="71b0a-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="71b0a-105">組件</span><span class="sxs-lookup"><span data-stu-id="71b0a-105">Parts</span></span>  
  
|<span data-ttu-id="71b0a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="71b0a-106">Term</span></span>|<span data-ttu-id="71b0a-107">定義</span><span class="sxs-lookup"><span data-stu-id="71b0a-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="71b0a-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="71b0a-108">Optional.</span></span> <span data-ttu-id="71b0a-109">本機變數名稱的清單，代表程式的參數。</span><span class="sxs-lookup"><span data-stu-id="71b0a-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="71b0a-110">即使清單是空的，括弧也必須存在。</span><span class="sxs-lookup"><span data-stu-id="71b0a-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="71b0a-111">如需詳細資訊，請參閱 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="71b0a-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="71b0a-112">必要。</span><span class="sxs-lookup"><span data-stu-id="71b0a-112">Required.</span></span> <span data-ttu-id="71b0a-113">單一語句。</span><span class="sxs-lookup"><span data-stu-id="71b0a-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="71b0a-114">必要。</span><span class="sxs-lookup"><span data-stu-id="71b0a-114">Required.</span></span> <span data-ttu-id="71b0a-115">陳述式的清單。</span><span class="sxs-lookup"><span data-stu-id="71b0a-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71b0a-116">備註</span><span class="sxs-lookup"><span data-stu-id="71b0a-116">Remarks</span></span>  
 <span data-ttu-id="71b0a-117">*Lambda 運算式*是沒有名稱，且會執行一或多個語句的副程式。</span><span class="sxs-lookup"><span data-stu-id="71b0a-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="71b0a-118">除了 `RemoveHandler`的引數之外，您可以在任何可使用委派類型的位置使用 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="71b0a-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="71b0a-119">如需委派的詳細資訊，以及搭配使用 lambda 運算式和委派的用法，請參閱[委派語句](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="71b0a-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="71b0a-120">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="71b0a-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="71b0a-121">Lambda 運算式的語法與標準副程式類似。</span><span class="sxs-lookup"><span data-stu-id="71b0a-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="71b0a-122">差異如下：</span><span class="sxs-lookup"><span data-stu-id="71b0a-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="71b0a-123">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="71b0a-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="71b0a-124">Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides`。</span><span class="sxs-lookup"><span data-stu-id="71b0a-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="71b0a-125">單行 lambda 運算式的主體必須是語句，而不是運算式。</span><span class="sxs-lookup"><span data-stu-id="71b0a-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="71b0a-126">主體可以包含 sub 程式的呼叫，而不是函式呼叫的呼叫。</span><span class="sxs-lookup"><span data-stu-id="71b0a-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="71b0a-127">在 lambda 運算式中，所有參數都必須具有指定的資料類型，否則必須推斷所有的參數。</span><span class="sxs-lookup"><span data-stu-id="71b0a-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="71b0a-128">Lambda 運算式中不允許選擇性和 `ParamArray` 參數。</span><span class="sxs-lookup"><span data-stu-id="71b0a-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="71b0a-129">Lambda 運算式中不允許使用泛型參數。</span><span class="sxs-lookup"><span data-stu-id="71b0a-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71b0a-130">範例</span><span class="sxs-lookup"><span data-stu-id="71b0a-130">Example</span></span>  
 <span data-ttu-id="71b0a-131">以下是將值寫入主控台的 lambda 運算式範例。</span><span class="sxs-lookup"><span data-stu-id="71b0a-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="71b0a-132">此範例會顯示副程式的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="71b0a-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="71b0a-133">如需更多範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="71b0a-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="71b0a-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="71b0a-134">See also</span></span>

- [<span data-ttu-id="71b0a-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="71b0a-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="71b0a-136">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="71b0a-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="71b0a-137">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="71b0a-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="71b0a-138">陳述式</span><span class="sxs-lookup"><span data-stu-id="71b0a-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="71b0a-139">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="71b0a-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
