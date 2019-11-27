---
title: 有效的運算子組合
ms.date: 07/20/2015
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
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348975"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="e7a2f-102">有效的運算子組合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7a2f-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="e7a2f-103">複雜運算式可以包含許多不同的運算子。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="e7a2f-104">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="e7a2f-105">在上述範例中建立複雜運算式，需要徹底瞭解運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="e7a2f-106">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../../visual-basic/language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="e7a2f-107">括號運算式</span><span class="sxs-lookup"><span data-stu-id="e7a2f-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="e7a2f-108">您通常會想要以不同于運算子優先順序的順序來繼續作業。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="e7a2f-109">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="e7a2f-110">上述範例會 `y`將 `z` 相乘，然後將結果新增至 `4`。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="e7a2f-111">但是，如果您想要加入 `y` 並 `4`，然後再將結果乘以 `z`，您可以使用括弧來覆寫正常的運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="e7a2f-112">藉由將運算式括在括弧中，您會強制先評估該運算式，而不論運算子優先順序為何。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="e7a2f-113">若要強制前面的範例先執行加法，您可以重寫它，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="e7a2f-114">上述範例會新增 `y` 和 `4`，然後將該總和乘以 `z`。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="e7a2f-115">嵌套的括號運算式</span><span class="sxs-lookup"><span data-stu-id="e7a2f-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="e7a2f-116">您可以在多個括弧層級中嵌套運算式，以便更進一步覆寫優先順序。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="e7a2f-117">最深嵌套在括弧中的運算式會先進行評估，然後再進行下一個最深的嵌套，依此類推，最後再加上最小的嵌套，最後再加上括弧以外的運算式。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="e7a2f-118">說明如下例。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="e7a2f-119">在上述範例中，會先評估 `z + 2`，然後再評估其他的括號運算式。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="e7a2f-120">乘冪（通常具有高於加法或乘法的優先順序）會在此範例中最後評估，因為其他運算式會括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="e7a2f-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a2f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a2f-121">See also</span></span>

- [<span data-ttu-id="e7a2f-122">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="e7a2f-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="e7a2f-123">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="e7a2f-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="e7a2f-124">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="e7a2f-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="e7a2f-125">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e7a2f-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="e7a2f-126">布林運算式</span><span class="sxs-lookup"><span data-stu-id="e7a2f-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="e7a2f-127">數值比較</span><span class="sxs-lookup"><span data-stu-id="e7a2f-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="e7a2f-128">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="e7a2f-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="e7a2f-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e7a2f-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
