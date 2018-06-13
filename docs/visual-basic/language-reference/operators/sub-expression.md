---
title: Sub 運算式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603531"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="86f1e-102">Sub 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86f1e-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="86f1e-103">宣告的參數和副程式 lambda 運算式定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="86f1e-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f1e-104">語法</span><span class="sxs-lookup"><span data-stu-id="86f1e-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="86f1e-105">組件</span><span class="sxs-lookup"><span data-stu-id="86f1e-105">Parts</span></span>  
  
|<span data-ttu-id="86f1e-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="86f1e-106">Term</span></span>|<span data-ttu-id="86f1e-107">定義</span><span class="sxs-lookup"><span data-stu-id="86f1e-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="86f1e-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="86f1e-108">Optional.</span></span> <span data-ttu-id="86f1e-109">代表程序參數的本機變數名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="86f1e-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="86f1e-110">括號必須要有即使清單是空的。</span><span class="sxs-lookup"><span data-stu-id="86f1e-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="86f1e-111">如需詳細資訊，請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="86f1e-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="86f1e-112">必要。</span><span class="sxs-lookup"><span data-stu-id="86f1e-112">Required.</span></span> <span data-ttu-id="86f1e-113">單一陳述式。</span><span class="sxs-lookup"><span data-stu-id="86f1e-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="86f1e-114">必要。</span><span class="sxs-lookup"><span data-stu-id="86f1e-114">Required.</span></span> <span data-ttu-id="86f1e-115">陳述式的清單。</span><span class="sxs-lookup"><span data-stu-id="86f1e-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86f1e-116">備註</span><span class="sxs-lookup"><span data-stu-id="86f1e-116">Remarks</span></span>  
 <span data-ttu-id="86f1e-117">A *lambda 運算式*沒有名稱的副程式，並執行一或多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="86f1e-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="86f1e-118">您可以使用 lambda 運算式，任何位置，您可以使用委派類型，除了做為引數`RemoveHandler`。</span><span class="sxs-lookup"><span data-stu-id="86f1e-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="86f1e-119">如需委派和 lambda 運算式與委派的使用詳細資訊，請參閱[委派陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)和[寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="86f1e-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="86f1e-120">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="86f1e-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="86f1e-121">Lambda 運算式的語法類似於標準的副程式。</span><span class="sxs-lookup"><span data-stu-id="86f1e-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="86f1e-122">差異如下所示：</span><span class="sxs-lookup"><span data-stu-id="86f1e-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="86f1e-123">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="86f1e-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="86f1e-124">Lambda 運算式不能有修飾詞，例如`Overloads`或`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="86f1e-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="86f1e-125">單行 lambda 運算式的主體必須是陳述式，而不是運算式。</span><span class="sxs-lookup"><span data-stu-id="86f1e-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="86f1e-126">主體可以包含子程序呼叫，但不函式程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="86f1e-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="86f1e-127">在 lambda 運算式中，所有參數必須都指定必須推斷資料型別或所有參數。</span><span class="sxs-lookup"><span data-stu-id="86f1e-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="86f1e-128">選擇性和`ParamArray`參數不允許在 lambda 運算式中。</span><span class="sxs-lookup"><span data-stu-id="86f1e-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="86f1e-129">Lambda 運算式中不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="86f1e-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86f1e-130">範例</span><span class="sxs-lookup"><span data-stu-id="86f1e-130">Example</span></span>  
 <span data-ttu-id="86f1e-131">以下是將值寫入主控台的 lambda 運算式的範例。</span><span class="sxs-lookup"><span data-stu-id="86f1e-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="86f1e-132">此範例顯示這兩個單行或多行 lambda 運算式語法副程式。</span><span class="sxs-lookup"><span data-stu-id="86f1e-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="86f1e-133">如需其他範例，請參閱[Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="86f1e-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="86f1e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86f1e-134">See Also</span></span>  
 [<span data-ttu-id="86f1e-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="86f1e-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="86f1e-136">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="86f1e-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="86f1e-137">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="86f1e-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="86f1e-138">陳述式</span><span class="sxs-lookup"><span data-stu-id="86f1e-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="86f1e-139">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="86f1e-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
