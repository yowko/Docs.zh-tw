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
ms.openlocfilehash: 9ba6be8e1dd03c0589f712b0e9b39258953cd223
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077081"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="170ff-102">有效的運算子組合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="170ff-102">Efficient Combination of Operators (Visual Basic)</span></span>

<span data-ttu-id="170ff-103">複雜運算式可包含許多不同的運算子。</span><span class="sxs-lookup"><span data-stu-id="170ff-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="170ff-104">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="170ff-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="170ff-105">若要建立複雜的運算式（例如上述範例中的運算式），必須徹底瞭解運算子優先順序的規則。</span><span class="sxs-lookup"><span data-stu-id="170ff-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="170ff-106">如需詳細資訊，請參閱 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="170ff-106">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="170ff-107">括號運算式</span><span class="sxs-lookup"><span data-stu-id="170ff-107">Parenthetical Expressions</span></span>  

 <span data-ttu-id="170ff-108">通常您會想要以運算子優先順序所決定的不同順序來繼續執行作業。</span><span class="sxs-lookup"><span data-stu-id="170ff-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="170ff-109">請思考一下下列範例。</span><span class="sxs-lookup"><span data-stu-id="170ff-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="170ff-110">上述範例會乘以 `z` `y` ，然後將結果加入至 `4` 。</span><span class="sxs-lookup"><span data-stu-id="170ff-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="170ff-111">但是，如果您想要在將 `y` `4` 結果相乘之前加入 `z` ，則可以使用括弧覆寫一般運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="170ff-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="170ff-112">藉由將運算式括在括弧中，您就可以強制先評估運算式，而不考慮運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="170ff-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="170ff-113">若要強制上述範例先執行加法，您可以如下列範例所示重寫它。</span><span class="sxs-lookup"><span data-stu-id="170ff-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="170ff-114">上述範例會新增 `y` 和 `4` ，然後將該總和乘以 `z` 。</span><span class="sxs-lookup"><span data-stu-id="170ff-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="170ff-115">嵌套括號運算式</span><span class="sxs-lookup"><span data-stu-id="170ff-115">Nested Parenthetical Expressions</span></span>  

 <span data-ttu-id="170ff-116">您可以在多個括弧層級中嵌套運算式，更進一步覆寫優先順序。</span><span class="sxs-lookup"><span data-stu-id="170ff-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="170ff-117">最深層嵌套在括弧中的運算式會先進行評估，然後再以最深的嵌套方式進行評估，最後再進行最深的嵌套，最後是括弧外的運算式。</span><span class="sxs-lookup"><span data-stu-id="170ff-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="170ff-118">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="170ff-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="170ff-119">在上述範例中， `z + 2` 會先評估另一個括號運算式。</span><span class="sxs-lookup"><span data-stu-id="170ff-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="170ff-120">通常優先順序高於加法或乘法的乘冪會在此範例中最後評估，因為其他運算式會以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="170ff-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="170ff-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="170ff-121">See also</span></span>

- [<span data-ttu-id="170ff-122">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="170ff-122">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="170ff-123">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="170ff-123">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="170ff-124">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="170ff-124">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="170ff-125">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="170ff-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="170ff-126">布林運算式</span><span class="sxs-lookup"><span data-stu-id="170ff-126">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="170ff-127">數值比較</span><span class="sxs-lookup"><span data-stu-id="170ff-127">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="170ff-128">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="170ff-128">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="170ff-129">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="170ff-129">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
