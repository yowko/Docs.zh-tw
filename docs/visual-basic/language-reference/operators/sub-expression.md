---
title: Sub 運算式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e564fa3f717fc1a9f4e9961d9b3e961912a4d56b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873327"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="ba71d-102">Sub 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba71d-102">Sub Expression (Visual Basic)</span></span>

<span data-ttu-id="ba71d-103">宣告定義副程式 lambda 運算式的參數和程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba71d-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba71d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba71d-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="ba71d-105">組件</span><span class="sxs-lookup"><span data-stu-id="ba71d-105">Parts</span></span>  
  
|<span data-ttu-id="ba71d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ba71d-106">Term</span></span>|<span data-ttu-id="ba71d-107">定義</span><span class="sxs-lookup"><span data-stu-id="ba71d-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="ba71d-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ba71d-108">Optional.</span></span> <span data-ttu-id="ba71d-109">區域變數名稱的清單，這些變數表示程式的參數。</span><span class="sxs-lookup"><span data-stu-id="ba71d-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="ba71d-110">即使清單是空的，也必須有括弧。</span><span class="sxs-lookup"><span data-stu-id="ba71d-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="ba71d-111">如需詳細資訊，請參閱 [Parameter List](../statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="ba71d-111">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="ba71d-112">必要。</span><span class="sxs-lookup"><span data-stu-id="ba71d-112">Required.</span></span> <span data-ttu-id="ba71d-113">單一語句。</span><span class="sxs-lookup"><span data-stu-id="ba71d-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="ba71d-114">必要。</span><span class="sxs-lookup"><span data-stu-id="ba71d-114">Required.</span></span> <span data-ttu-id="ba71d-115">陳述式的清單。</span><span class="sxs-lookup"><span data-stu-id="ba71d-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba71d-116">備註</span><span class="sxs-lookup"><span data-stu-id="ba71d-116">Remarks</span></span>  

 <span data-ttu-id="ba71d-117">*Lambda 運算式*是沒有名稱，且會執行一或多個語句的副程式。</span><span class="sxs-lookup"><span data-stu-id="ba71d-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="ba71d-118">您可以在任何可使用委派類型的位置使用 lambda 運算式，但做為的引數除外 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="ba71d-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="ba71d-119">如需委派的詳細資訊，以及使用 lambda 運算式搭配委派的詳細資訊，請參閱 [委派語句](../statements/delegate-statement.md) 和 [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="ba71d-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="ba71d-120">Lambda 運算式語法</span><span class="sxs-lookup"><span data-stu-id="ba71d-120">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="ba71d-121">Lambda 運算式的語法與標準副程式的語法類似。</span><span class="sxs-lookup"><span data-stu-id="ba71d-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="ba71d-122">差異如下：</span><span class="sxs-lookup"><span data-stu-id="ba71d-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="ba71d-123">Lambda 運算式沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="ba71d-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="ba71d-124">Lambda 運算式不能有修飾詞，例如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="ba71d-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="ba71d-125">單行 lambda 運算式的主體必須是語句，而不是運算式。</span><span class="sxs-lookup"><span data-stu-id="ba71d-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="ba71d-126">本文可能包含對 sub 程式的呼叫，但不包含對函數程式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ba71d-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="ba71d-127">在 lambda 運算式中，所有參數都必須有指定的資料類型，或必須推斷所有參數。</span><span class="sxs-lookup"><span data-stu-id="ba71d-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="ba71d-128">`ParamArray`Lambda 運算式中不允許選擇性和參數。</span><span class="sxs-lookup"><span data-stu-id="ba71d-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="ba71d-129">Lambda 運算式中不允許泛型參數。</span><span class="sxs-lookup"><span data-stu-id="ba71d-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba71d-130">範例</span><span class="sxs-lookup"><span data-stu-id="ba71d-130">Example</span></span>  

 <span data-ttu-id="ba71d-131">以下是將值寫入主控台的 lambda 運算式範例。</span><span class="sxs-lookup"><span data-stu-id="ba71d-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="ba71d-132">此範例會顯示副程式的單行和多行 lambda 運算式語法。</span><span class="sxs-lookup"><span data-stu-id="ba71d-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="ba71d-133">如需更多範例，請參閱 [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ba71d-133">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="ba71d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba71d-134">See also</span></span>

- [<span data-ttu-id="ba71d-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="ba71d-135">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="ba71d-136">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="ba71d-136">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="ba71d-137">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ba71d-137">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="ba71d-138">陳述式</span><span class="sxs-lookup"><span data-stu-id="ba71d-138">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="ba71d-139">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="ba71d-139">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
