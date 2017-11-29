---
title: "有效的運算子組合 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="7ecce-102">有效的運算子組合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ecce-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="7ecce-103">複雜運算式可包含許多不同的運算子。</span><span class="sxs-lookup"><span data-stu-id="7ecce-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="7ecce-104">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="7ecce-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="7ecce-105">建立複雜的運算式，例如上述範例中的一個需要瞭解的運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="7ecce-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="7ecce-106">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecce-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="7ecce-107">括號運算式</span><span class="sxs-lookup"><span data-stu-id="7ecce-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="7ecce-108">通常您會想從運算子優先順序所決定以不同順序繼續進行作業。</span><span class="sxs-lookup"><span data-stu-id="7ecce-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="7ecce-109">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="7ecce-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="7ecce-110">上述範例會乘以`z`由`y`，然後將結果以`4`。</span><span class="sxs-lookup"><span data-stu-id="7ecce-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="7ecce-111">但是，如果您想要新增`y`和`4`之前相乘的結果`z`，您可以使用括號覆寫一般運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="7ecce-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="7ecce-112">您可以以括弧括住運算式，強制該運算式要評估第一次，不論運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="7ecce-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="7ecce-113">若要強制執行加法上述的範例，您無法將它改寫下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7ecce-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="7ecce-114">前述範例新增`y`和`4`，然後乘以相加的`z`。</span><span class="sxs-lookup"><span data-stu-id="7ecce-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="7ecce-115">巢狀括號運算式</span><span class="sxs-lookup"><span data-stu-id="7ecce-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="7ecce-116">您可以巢狀括號來覆寫優先順序更進一步的多個層級中的運算式。</span><span class="sxs-lookup"><span data-stu-id="7ecce-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="7ecce-117">最深的巢狀括號括住的運算式會先評估，接著是巢狀最深處，依此類推，最深的巢狀，最後括號外的運算式。</span><span class="sxs-lookup"><span data-stu-id="7ecce-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="7ecce-118">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="7ecce-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="7ecce-119">在上述範例中，`z + 2`會先評估，然後放在括號運算式。</span><span class="sxs-lookup"><span data-stu-id="7ecce-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="7ecce-120">在此範例中，因為其他運算式會以括號括住乘冪，通常具有較高的優先順序高於加法或乘法，是上一次評估。</span><span class="sxs-lookup"><span data-stu-id="7ecce-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ecce-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ecce-121">See Also</span></span>  
 [<span data-ttu-id="7ecce-122">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="7ecce-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="7ecce-123">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="7ecce-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="7ecce-124">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="7ecce-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="7ecce-125">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ecce-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="7ecce-126">布林運算式</span><span class="sxs-lookup"><span data-stu-id="7ecce-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="7ecce-127">數值比較</span><span class="sxs-lookup"><span data-stu-id="7ecce-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="7ecce-128">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="7ecce-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="7ecce-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7ecce-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
