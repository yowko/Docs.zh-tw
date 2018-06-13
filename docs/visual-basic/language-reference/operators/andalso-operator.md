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
ms.openlocfilehash: 549d14cc35d285ac2e4a02a37dd201cc669c5627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604070"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="c7264-102">AndAlso 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7264-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="c7264-103">執行最少運算邏輯結合兩個運算式上。</span><span class="sxs-lookup"><span data-stu-id="c7264-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7264-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7264-104">Syntax</span></span>  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c7264-105">組件</span><span class="sxs-lookup"><span data-stu-id="c7264-105">Parts</span></span>  
  
|<span data-ttu-id="c7264-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c7264-106">Term</span></span>|<span data-ttu-id="c7264-107">定義</span><span class="sxs-lookup"><span data-stu-id="c7264-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="c7264-108">必要。</span><span class="sxs-lookup"><span data-stu-id="c7264-108">Required.</span></span> <span data-ttu-id="c7264-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c7264-109">Any `Boolean` expression.</span></span> <span data-ttu-id="c7264-110">結果是`Boolean`比較兩個運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="c7264-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="c7264-111">必要。</span><span class="sxs-lookup"><span data-stu-id="c7264-111">Required.</span></span> <span data-ttu-id="c7264-112">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c7264-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="c7264-113">必要。</span><span class="sxs-lookup"><span data-stu-id="c7264-113">Required.</span></span> <span data-ttu-id="c7264-114">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c7264-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7264-115">備註</span><span class="sxs-lookup"><span data-stu-id="c7264-115">Remarks</span></span>  
 <span data-ttu-id="c7264-116">邏輯作業即為*最少運算*如果已編譯的程式碼就可以略過運算式的評估，依據另一個運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="c7264-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="c7264-117">如果評估的第一個運算式的結果判斷作業的最終結果，是不必評估第二個運算式，因為它不能變更的最終結果。</span><span class="sxs-lookup"><span data-stu-id="c7264-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="c7264-118">如果近端網址略過的運算式很複雜，或它所涉及的程序呼叫，最少運算可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="c7264-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="c7264-119">如果這兩個運算式評估為`True`，`result`是`True`。</span><span class="sxs-lookup"><span data-stu-id="c7264-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="c7264-120">下表將說明如何`result`決定。</span><span class="sxs-lookup"><span data-stu-id="c7264-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="c7264-121">如果`expression1`是</span><span class="sxs-lookup"><span data-stu-id="c7264-121">If `expression1` is</span></span>|<span data-ttu-id="c7264-122">和`expression2`是</span><span class="sxs-lookup"><span data-stu-id="c7264-122">And `expression2` is</span></span>|<span data-ttu-id="c7264-123">值`result`是</span><span class="sxs-lookup"><span data-stu-id="c7264-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="c7264-124">（不會評估）</span><span class="sxs-lookup"><span data-stu-id="c7264-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="c7264-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="c7264-125">Data Types</span></span>  
 <span data-ttu-id="c7264-126">`AndAlso`僅適用於定義運算子[布林資料型別](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="c7264-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="c7264-127">Visual Basic 會將轉換為所需的每個運算元`Boolean`，並執行作業完全`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="c7264-127">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="c7264-128">如果您將結果指派給數值類型時，Visual Basic 會將轉換從`Boolean`對該類型。</span><span class="sxs-lookup"><span data-stu-id="c7264-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="c7264-129">這可能會產生非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="c7264-129">This could produce unexpected behavior.</span></span> <span data-ttu-id="c7264-130">例如，`5 AndAlso 12`導致`–1`時轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="c7264-130">For example, `5 AndAlso 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c7264-131">多載化</span><span class="sxs-lookup"><span data-stu-id="c7264-131">Overloading</span></span>  
 <span data-ttu-id="c7264-132">[與運算子](../../../visual-basic/language-reference/operators/and-operator.md)和[IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以*多載*，這表示，類別或結構可以重新定義其行為時運算元的類型，類別或結構。</span><span class="sxs-lookup"><span data-stu-id="c7264-132">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c7264-133">多載`And`和`IsFalse`運算子會影響行為`AndAlso`運算子。</span><span class="sxs-lookup"><span data-stu-id="c7264-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="c7264-134">如果您的程式碼使用`AndAlso`上類別或結構的多載`And`和`IsFalse`，確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="c7264-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="c7264-135">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="c7264-135">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7264-136">範例</span><span class="sxs-lookup"><span data-stu-id="c7264-136">Example</span></span>  
 <span data-ttu-id="c7264-137">下列範例會使用`AndAlso`運算子執行邏輯結合兩個運算式上。</span><span class="sxs-lookup"><span data-stu-id="c7264-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="c7264-138">結果是`Boolean`值，表示是否將整個共同運算式為 true。</span><span class="sxs-lookup"><span data-stu-id="c7264-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="c7264-139">如果第一個運算式是`False`，則不會評估第二個。</span><span class="sxs-lookup"><span data-stu-id="c7264-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 <span data-ttu-id="c7264-140">上述範例產生的結果`True`， `False`，和`False`分別。</span><span class="sxs-lookup"><span data-stu-id="c7264-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="c7264-141">在計算`secondCheck`，因為已經是第一個，不會評估第二個運算式`False`。</span><span class="sxs-lookup"><span data-stu-id="c7264-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="c7264-142">不過，第二個運算式會評估的計算`thirdCheck`。</span><span class="sxs-lookup"><span data-stu-id="c7264-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7264-143">範例</span><span class="sxs-lookup"><span data-stu-id="c7264-143">Example</span></span>  
 <span data-ttu-id="c7264-144">下列範例所示`Function`搜尋指定值陣列的項目之間的程序。</span><span class="sxs-lookup"><span data-stu-id="c7264-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="c7264-145">如果陣列是空的或如果尚未超過陣列長度，`While`陳述式不會測試根據搜尋值的陣列項目。</span><span class="sxs-lookup"><span data-stu-id="c7264-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c7264-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7264-146">See Also</span></span>  
 [<span data-ttu-id="c7264-147">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7264-147">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="c7264-148">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="c7264-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="c7264-149">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="c7264-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="c7264-150">And 運算子</span><span class="sxs-lookup"><span data-stu-id="c7264-150">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)  
 [<span data-ttu-id="c7264-151">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="c7264-151">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="c7264-152">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="c7264-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
