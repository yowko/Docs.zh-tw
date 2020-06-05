---
title: 數值比較
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
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403391"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="aa3dd-102">數值比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa3dd-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="aa3dd-103">比較運算子可以用來建立比較數值變數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="aa3dd-104">這些運算式會根據 `Boolean` 比較是否為 true 或 false 傳回值。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="aa3dd-105">這類運算式的範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="aa3dd-106">第一個運算式會評估為 `True` ，因為45大於26。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="aa3dd-107">第二個範例會評估為 `False` ，因為26不大於45。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="aa3dd-108">您也可以用這種方式來比較數值運算式。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="aa3dd-109">您比較的運算式本身可以是複雜的運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="aa3dd-110">前面的複雜運算式包含常值、變數和函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="aa3dd-111">比較運算子兩邊的運算式會進行評估，然後使用比較運算子來比較產生的值 `>=` 。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="aa3dd-112">如果左邊的運算式值大於或等於右邊運算式的值，則整個運算式會評估為， `True` 否則會評估為，否則為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="aa3dd-113">比較值的運算式最常用於結構中 `If...Then` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="aa3dd-114">`=`正負號是比較運算子，也是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="aa3dd-115">做為比較運算子使用時，它會評估左邊的值是否等於右邊的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="aa3dd-116">您也可以在需要值的任何位置使用比較運算式 `Boolean` ，例如 `If` ，在、 `While` 、或語句中，或在 `Loop` `ElseIf` 指派或傳遞值給 `Boolean` 變數時。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="aa3dd-117">在下列範例中，比較運算式所傳回的值會指派給 `Boolean` 變數。</span><span class="sxs-lookup"><span data-stu-id="aa3dd-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="aa3dd-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa3dd-118">See also</span></span>

- [<span data-ttu-id="aa3dd-119">布林運算式</span><span class="sxs-lookup"><span data-stu-id="aa3dd-119">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="aa3dd-120">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="aa3dd-120">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="aa3dd-121">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa3dd-121">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="aa3dd-122">如何：計算數值</span><span class="sxs-lookup"><span data-stu-id="aa3dd-122">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="aa3dd-123">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="aa3dd-123">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
