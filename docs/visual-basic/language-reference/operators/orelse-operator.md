---
title: OrElse 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860148"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="6ed08-102">OrElse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ed08-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="6ed08-103">執行最少運算的兩個運算式上的內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="6ed08-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed08-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ed08-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="6ed08-105">組件</span><span class="sxs-lookup"><span data-stu-id="6ed08-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6ed08-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="6ed08-106">Required.</span></span> <span data-ttu-id="6ed08-107">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="6ed08-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="6ed08-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="6ed08-108">Required.</span></span> <span data-ttu-id="6ed08-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="6ed08-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="6ed08-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="6ed08-110">Required.</span></span> <span data-ttu-id="6ed08-111">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="6ed08-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ed08-112">備註</span><span class="sxs-lookup"><span data-stu-id="6ed08-112">Remarks</span></span>  
 <span data-ttu-id="6ed08-113">邏輯作業即所謂*最少運算*如果編譯的程式碼就可以略過運算式的評估，根據另一個運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="6ed08-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="6ed08-114">如果評估的第一個運算式的結果判斷作業的最終結果，則不需要評估第二個運算式，因為它不能變更的最終結果。</span><span class="sxs-lookup"><span data-stu-id="6ed08-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="6ed08-115">如果已略過的運算式很複雜，或如果它包含程序呼叫，則最少運算可提升效能。</span><span class="sxs-lookup"><span data-stu-id="6ed08-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="6ed08-116">如果任一個或兩個運算式都評估為`True`，`result`是`True`。</span><span class="sxs-lookup"><span data-stu-id="6ed08-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="6ed08-117">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="6ed08-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="6ed08-118">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="6ed08-118">If `expression1` is</span></span>|<span data-ttu-id="6ed08-119">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="6ed08-119">And `expression2` is</span></span>|<span data-ttu-id="6ed08-120">值`result`是</span><span class="sxs-lookup"><span data-stu-id="6ed08-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="6ed08-121">（不會評估）</span><span class="sxs-lookup"><span data-stu-id="6ed08-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="6ed08-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ed08-122">Data Types</span></span>  
 <span data-ttu-id="6ed08-123">`OrElse`僅適用於定義運算子[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="6ed08-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="6ed08-124">Visual Basic 會將轉換為所需的每一個運算元`Boolean`之前評估運算式。</span><span class="sxs-lookup"><span data-stu-id="6ed08-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="6ed08-125">如果您將結果指派給數值類型時，Visual Basic 會將它從`Boolean`為該類型，`False`會變成`0`並`True`會變成`-1`。</span><span class="sxs-lookup"><span data-stu-id="6ed08-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="6ed08-126">如需詳細資訊，請參閱[布林類型轉換](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="6ed08-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="6ed08-127">多載化</span><span class="sxs-lookup"><span data-stu-id="6ed08-127">Overloading</span></span>  
 <span data-ttu-id="6ed08-128">[或運算子](../../../visual-basic/language-reference/operators/or-operator.md)並[IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別的型別或結構。</span><span class="sxs-lookup"><span data-stu-id="6ed08-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6ed08-129">多載`Or`並`IsTrue`運算子會影響的行為`OrElse`運算子。</span><span class="sxs-lookup"><span data-stu-id="6ed08-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="6ed08-130">如果您的程式碼會使用`OrElse`上類別或結構，多載`Or`和`IsTrue`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="6ed08-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="6ed08-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="6ed08-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ed08-132">範例</span><span class="sxs-lookup"><span data-stu-id="6ed08-132">Example</span></span>  
 <span data-ttu-id="6ed08-133">下列範例會使用`OrElse`上兩個運算式執行邏輯分離的運算子。</span><span class="sxs-lookup"><span data-stu-id="6ed08-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="6ed08-134">結果是`Boolean`值，表示其中兩個運算式是否為 true。</span><span class="sxs-lookup"><span data-stu-id="6ed08-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="6ed08-135">如果第一個運算式為`True`，則不會評估第二個。</span><span class="sxs-lookup"><span data-stu-id="6ed08-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="6ed08-136">上述範例產生的結果`True`， `True`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="6ed08-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="6ed08-137">計算`firstCheck`，因為已經是第一，不會評估第二個運算式`True`。</span><span class="sxs-lookup"><span data-stu-id="6ed08-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="6ed08-138">不過，第二個運算式評估的計算`secondCheck`。</span><span class="sxs-lookup"><span data-stu-id="6ed08-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ed08-139">範例</span><span class="sxs-lookup"><span data-stu-id="6ed08-139">Example</span></span>  
 <span data-ttu-id="6ed08-140">下列範例所示`If`...`Then`包含兩個程序呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ed08-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="6ed08-141">如果第一次呼叫傳回`True`，不會呼叫第二個程序。</span><span class="sxs-lookup"><span data-stu-id="6ed08-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="6ed08-142">如果第二個程序執行的重要工作，應該一律在這段程式碼執行時才執行，這可能產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="6ed08-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="6ed08-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ed08-143">See also</span></span>

- [<span data-ttu-id="6ed08-144">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ed08-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="6ed08-145">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="6ed08-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6ed08-146">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="6ed08-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6ed08-147">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="6ed08-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="6ed08-148">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="6ed08-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="6ed08-149">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="6ed08-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
