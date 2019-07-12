---
title: AndAlso 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 1cb4d372d3ac228f29c6fa45f124796e5dfb6709
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859891"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="61183-102">AndAlso 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61183-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="61183-103">執行最少運算邏輯結合兩個運算式上。</span><span class="sxs-lookup"><span data-stu-id="61183-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61183-104">語法</span><span class="sxs-lookup"><span data-stu-id="61183-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="61183-105">組件</span><span class="sxs-lookup"><span data-stu-id="61183-105">Parts</span></span>  
  
|<span data-ttu-id="61183-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="61183-106">Term</span></span>|<span data-ttu-id="61183-107">定義</span><span class="sxs-lookup"><span data-stu-id="61183-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="61183-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="61183-108">Required.</span></span> <span data-ttu-id="61183-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="61183-109">Any `Boolean` expression.</span></span> <span data-ttu-id="61183-110">結果是`Boolean`比較兩個運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="61183-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="61183-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="61183-111">Required.</span></span> <span data-ttu-id="61183-112">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="61183-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="61183-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="61183-113">Required.</span></span> <span data-ttu-id="61183-114">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="61183-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61183-115">備註</span><span class="sxs-lookup"><span data-stu-id="61183-115">Remarks</span></span>  
 <span data-ttu-id="61183-116">邏輯作業即所謂*最少運算*如果編譯的程式碼就可以略過運算式的評估，根據另一個運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="61183-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="61183-117">如果評估的第一個運算式的結果判斷作業的最終結果，則不需要評估第二個運算式，因為它不能變更的最終結果。</span><span class="sxs-lookup"><span data-stu-id="61183-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="61183-118">如果已略過的運算式很複雜，或如果它包含程序呼叫，則最少運算可提升效能。</span><span class="sxs-lookup"><span data-stu-id="61183-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="61183-119">如果這兩個運算式都評估為`True`，`result`是`True`。</span><span class="sxs-lookup"><span data-stu-id="61183-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="61183-120">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="61183-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="61183-121">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="61183-121">If `expression1` is</span></span>|<span data-ttu-id="61183-122">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="61183-122">And `expression2` is</span></span>|<span data-ttu-id="61183-123">值`result`是</span><span class="sxs-lookup"><span data-stu-id="61183-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="61183-124">（不會評估）</span><span class="sxs-lookup"><span data-stu-id="61183-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="61183-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="61183-125">Data Types</span></span>  
 <span data-ttu-id="61183-126">`AndAlso`僅適用於定義運算子[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="61183-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="61183-127">Visual Basic 會將轉換為所需的每一個運算元`Boolean`之前評估運算式。</span><span class="sxs-lookup"><span data-stu-id="61183-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="61183-128">如果您將結果指派給數值類型時，Visual Basic 會將它從`Boolean`為該類型，`False`會變成`0`並`True`會變成`-1`。</span><span class="sxs-lookup"><span data-stu-id="61183-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="61183-129">如需詳細資訊，請參閱[布林類型轉換](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="61183-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="61183-130">多載化</span><span class="sxs-lookup"><span data-stu-id="61183-130">Overloading</span></span>  
 <span data-ttu-id="61183-131">[與運算子](../../../visual-basic/language-reference/operators/and-operator.md)並[IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以是*多載*，這表示，類別或結構可以重新定義其行為時運算元的類型，類別或結構。</span><span class="sxs-lookup"><span data-stu-id="61183-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="61183-132">多載`And`並`IsFalse`運算子會影響的行為`AndAlso`運算子。</span><span class="sxs-lookup"><span data-stu-id="61183-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="61183-133">如果您的程式碼會使用`AndAlso`上類別或結構，多載`And`和`IsFalse`，務必了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="61183-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="61183-134">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="61183-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61183-135">範例</span><span class="sxs-lookup"><span data-stu-id="61183-135">Example</span></span>  
 <span data-ttu-id="61183-136">下列範例會使用`AndAlso`運算子執行邏輯結合兩個運算式上。</span><span class="sxs-lookup"><span data-stu-id="61183-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="61183-137">結果是`Boolean`表示整個優先運算式的值為 true。</span><span class="sxs-lookup"><span data-stu-id="61183-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="61183-138">如果第一個運算式為`False`，則不會評估第二個。</span><span class="sxs-lookup"><span data-stu-id="61183-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="61183-139">上述範例產生的結果`True`， `False`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="61183-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="61183-140">計算`secondCheck`，因為已經是第一，不會評估第二個運算式`False`。</span><span class="sxs-lookup"><span data-stu-id="61183-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="61183-141">不過，第二個運算式評估的計算`thirdCheck`。</span><span class="sxs-lookup"><span data-stu-id="61183-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61183-142">範例</span><span class="sxs-lookup"><span data-stu-id="61183-142">Example</span></span>  
 <span data-ttu-id="61183-143">下列範例所示`Function`搜尋指定的值陣列的項目之間的程序。</span><span class="sxs-lookup"><span data-stu-id="61183-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="61183-144">如果陣列是空的或如果已超過陣列長度，`While`陳述式不會測試針對搜尋值的陣列項目。</span><span class="sxs-lookup"><span data-stu-id="61183-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="61183-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61183-145">See also</span></span>

- [<span data-ttu-id="61183-146">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61183-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="61183-147">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="61183-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="61183-148">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="61183-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="61183-149">And 運算子</span><span class="sxs-lookup"><span data-stu-id="61183-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="61183-150">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="61183-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="61183-151">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="61183-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
