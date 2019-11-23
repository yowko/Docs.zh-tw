---
title: OrElse 運算子
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
ms.openlocfilehash: 361de44711c3b41411f2fa1dd81a3dd8db6b01e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348237"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="d2f4a-102">OrElse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2f4a-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="d2f4a-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2f4a-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d2f4a-105">組件</span><span class="sxs-lookup"><span data-stu-id="d2f4a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d2f4a-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-106">Required.</span></span> <span data-ttu-id="d2f4a-107">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="d2f4a-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-108">Required.</span></span> <span data-ttu-id="d2f4a-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d2f4a-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-110">Required.</span></span> <span data-ttu-id="d2f4a-111">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2f4a-112">備註</span><span class="sxs-lookup"><span data-stu-id="d2f4a-112">Remarks</span></span>  
 <span data-ttu-id="d2f4a-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="d2f4a-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="d2f4a-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="d2f4a-116">If either or both expressions evaluate to `True`, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="d2f4a-117">The following table illustrates how `result` is determined.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="d2f4a-118">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="d2f4a-118">If `expression1` is</span></span>|<span data-ttu-id="d2f4a-119">And `expression2` is</span><span class="sxs-lookup"><span data-stu-id="d2f4a-119">And `expression2` is</span></span>|<span data-ttu-id="d2f4a-120">The value of `result` is</span><span class="sxs-lookup"><span data-stu-id="d2f4a-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="d2f4a-121">(not evaluated)</span><span class="sxs-lookup"><span data-stu-id="d2f4a-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="d2f4a-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="d2f4a-122">Data Types</span></span>  
 <span data-ttu-id="d2f4a-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="d2f4a-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="d2f4a-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="d2f4a-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="d2f4a-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="d2f4a-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="d2f4a-127">多載化</span><span class="sxs-lookup"><span data-stu-id="d2f4a-127">Overloading</span></span>  
 <span data-ttu-id="d2f4a-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d2f4a-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="d2f4a-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="d2f4a-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f4a-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2f4a-132">範例</span><span class="sxs-lookup"><span data-stu-id="d2f4a-132">Example</span></span>  
 <span data-ttu-id="d2f4a-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="d2f4a-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="d2f4a-135">If the first expression is `True`, the second is not evaluated.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="d2f4a-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="d2f4a-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="d2f4a-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2f4a-139">範例</span><span class="sxs-lookup"><span data-stu-id="d2f4a-139">Example</span></span>  
 <span data-ttu-id="d2f4a-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="d2f4a-141">If the first call returns `True`, the second procedure is not called.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="d2f4a-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span><span class="sxs-lookup"><span data-stu-id="d2f4a-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d2f4a-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f4a-143">See also</span></span>

- [<span data-ttu-id="d2f4a-144">Logical/Bitwise Operators (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2f4a-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="d2f4a-145">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d2f4a-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d2f4a-146">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d2f4a-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d2f4a-147">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="d2f4a-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="d2f4a-148">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="d2f4a-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="d2f4a-149">Logical and Bitwise Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2f4a-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
