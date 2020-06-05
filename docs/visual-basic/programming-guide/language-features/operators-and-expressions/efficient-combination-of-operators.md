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
ms.openlocfilehash: 3088072646278dac13e4d483cb4f99297eaad9ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403468"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="a3abf-102">有效的運算子組合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3abf-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="a3abf-103">複雜運算式可以包含許多不同的運算子。</span><span class="sxs-lookup"><span data-stu-id="a3abf-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="a3abf-104">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="a3abf-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="a3abf-105">在上述範例中建立複雜運算式，需要徹底瞭解運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="a3abf-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="a3abf-106">如需詳細資訊，請參閱[Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="a3abf-106">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="a3abf-107">括號運算式</span><span class="sxs-lookup"><span data-stu-id="a3abf-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="a3abf-108">您通常會想要以不同于運算子優先順序的順序來繼續作業。</span><span class="sxs-lookup"><span data-stu-id="a3abf-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="a3abf-109">請思考一下下列範例。</span><span class="sxs-lookup"><span data-stu-id="a3abf-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="a3abf-110">上述範例會 `z` 將乘以 `y` ，然後將結果新增至 `4` 。</span><span class="sxs-lookup"><span data-stu-id="a3abf-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="a3abf-111">但是，如果您想要 `y` 在 `4` 乘以結果之前加入和 `z` ，您可以使用括弧來覆寫一般運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="a3abf-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="a3abf-112">藉由將運算式括在括弧中，您會強制先評估該運算式，而不論運算子優先順序為何。</span><span class="sxs-lookup"><span data-stu-id="a3abf-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="a3abf-113">若要強制前面的範例先執行加法，您可以重寫它，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a3abf-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="a3abf-114">上述範例會加入 `y` 和 `4` ，然後將總和乘以 `z` 。</span><span class="sxs-lookup"><span data-stu-id="a3abf-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="a3abf-115">嵌套的括號運算式</span><span class="sxs-lookup"><span data-stu-id="a3abf-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="a3abf-116">您可以在多個括弧層級中嵌套運算式，以便更進一步覆寫優先順序。</span><span class="sxs-lookup"><span data-stu-id="a3abf-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="a3abf-117">最深嵌套在括弧中的運算式會先進行評估，然後再進行下一個最深的嵌套，依此類推，最後再加上最小的嵌套，最後再加上括弧以外的運算式。</span><span class="sxs-lookup"><span data-stu-id="a3abf-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="a3abf-118">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="a3abf-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="a3abf-119">在上述範例中， `z + 2` 會先評估，然後再評估其他的括號運算式。</span><span class="sxs-lookup"><span data-stu-id="a3abf-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="a3abf-120">乘冪（通常具有高於加法或乘法的優先順序）會在此範例中最後評估，因為其他運算式會括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="a3abf-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3abf-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3abf-121">See also</span></span>

- [<span data-ttu-id="a3abf-122">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="a3abf-122">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="a3abf-123">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3abf-123">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="a3abf-124">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="a3abf-124">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="a3abf-125">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3abf-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="a3abf-126">布林運算式</span><span class="sxs-lookup"><span data-stu-id="a3abf-126">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="a3abf-127">數值比較</span><span class="sxs-lookup"><span data-stu-id="a3abf-127">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="a3abf-128">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="a3abf-128">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="a3abf-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="a3abf-129">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
