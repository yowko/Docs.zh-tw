---
title: 數值比較 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649603"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="ef296-102">數值比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef296-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="ef296-103">比較運算子可用來建構比較數值變數的值的運算式。</span><span class="sxs-lookup"><span data-stu-id="ef296-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="ef296-104">這些運算式會傳回`Boolean`值根據是否比較為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="ef296-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="ef296-105">這類運算式的範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="ef296-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="ef296-106">第一個運算式會評估為`True`，因為 45 大於 26。</span><span class="sxs-lookup"><span data-stu-id="ef296-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="ef296-107">第二個範例評估結果為`False`，因為 26 不大於 45。</span><span class="sxs-lookup"><span data-stu-id="ef296-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="ef296-108">您也可以比較這種方式中的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="ef296-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="ef296-109">比較運算式本身可能是複雜的運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef296-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="ef296-110">先前的複雜運算式包含常值、 變數和函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="ef296-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="ef296-111">比較運算子的兩邊運算式會評估，並產生的值會再使用比較`>=`比較運算子。</span><span class="sxs-lookup"><span data-stu-id="ef296-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="ef296-112">如果左側運算式的值是否大於或等於右運算式的值，整個運算式評估為`True`; 否則其評估結果為`False`。</span><span class="sxs-lookup"><span data-stu-id="ef296-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="ef296-113">比較值的運算式最常用於`If...Then`語法結構，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef296-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="ef296-114">`=`號是比較運算子，以及指派運算子。</span><span class="sxs-lookup"><span data-stu-id="ef296-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="ef296-115">當做比較運算子使用時，它會評估在左邊的值是否等於右邊的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef296-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="ef296-116">您也可以隨處使用比較運算式`Boolean`值是所需，例如`If`， `While`， `Loop`，或`ElseIf`陳述式，或是當您指派給或傳遞值至`Boolean`變數。</span><span class="sxs-lookup"><span data-stu-id="ef296-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="ef296-117">下列範例中，在比較運算式所傳回的值指派給`Boolean`變數。</span><span class="sxs-lookup"><span data-stu-id="ef296-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ef296-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef296-118">See Also</span></span>  
 [<span data-ttu-id="ef296-119">布林運算式</span><span class="sxs-lookup"><span data-stu-id="ef296-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="ef296-120">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ef296-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="ef296-121">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="ef296-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="ef296-122">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="ef296-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="ef296-123">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="ef296-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
