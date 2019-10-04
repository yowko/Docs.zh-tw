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
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835233"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="db69b-102">AndAlso 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db69b-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="db69b-103">在兩個運算式上執行短路邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="db69b-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db69b-104">語法</span><span class="sxs-lookup"><span data-stu-id="db69b-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="db69b-105">組件</span><span class="sxs-lookup"><span data-stu-id="db69b-105">Parts</span></span>  
  
|<span data-ttu-id="db69b-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="db69b-106">Term</span></span>|<span data-ttu-id="db69b-107">定義</span><span class="sxs-lookup"><span data-stu-id="db69b-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="db69b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="db69b-108">Required.</span></span> <span data-ttu-id="db69b-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="db69b-109">Any `Boolean` expression.</span></span> <span data-ttu-id="db69b-110">結果會是兩個運算式的比較 @no__t 0 的結果。</span><span class="sxs-lookup"><span data-stu-id="db69b-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="db69b-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="db69b-111">Required.</span></span> <span data-ttu-id="db69b-112">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="db69b-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="db69b-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="db69b-113">Required.</span></span> <span data-ttu-id="db69b-114">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="db69b-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db69b-115">備註</span><span class="sxs-lookup"><span data-stu-id="db69b-115">Remarks</span></span>  
 <span data-ttu-id="db69b-116">*如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。</span><span class="sxs-lookup"><span data-stu-id="db69b-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="db69b-117">如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。</span><span class="sxs-lookup"><span data-stu-id="db69b-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="db69b-118">如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="db69b-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="db69b-119">如果兩個運算式都評估為 `True`，`result` 會 `True`。</span><span class="sxs-lookup"><span data-stu-id="db69b-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="db69b-120">下表說明如何判斷 `result`。</span><span class="sxs-lookup"><span data-stu-id="db69b-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="db69b-121">如果`expression1`為</span><span class="sxs-lookup"><span data-stu-id="db69b-121">If `expression1` is</span></span>|<span data-ttu-id="db69b-122">和`expression2`為</span><span class="sxs-lookup"><span data-stu-id="db69b-122">And `expression2` is</span></span>|<span data-ttu-id="db69b-123">@No__t-0 的值為</span><span class="sxs-lookup"><span data-stu-id="db69b-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="db69b-124">（未評估）</span><span class="sxs-lookup"><span data-stu-id="db69b-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="db69b-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="db69b-125">Data Types</span></span>  
 <span data-ttu-id="db69b-126">@No__t-0 運算子只會針對[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來定義。</span><span class="sxs-lookup"><span data-stu-id="db69b-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="db69b-127">Visual Basic 在評估運算式之前，會視需要將每個運算元轉換為 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="db69b-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="db69b-128">如果您將結果指派給數數值型別，Visual Basic 會將它從 `Boolean` 轉換成該類型，如此 `False` 會變成 `0`，而 `True` 會變成 `-1`。</span><span class="sxs-lookup"><span data-stu-id="db69b-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="db69b-129">如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="db69b-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="db69b-130">多載化</span><span class="sxs-lookup"><span data-stu-id="db69b-130">Overloading</span></span>  
 <span data-ttu-id="db69b-131">[And 運算子](../../../visual-basic/language-reference/operators/and-operator.md)和[IsFalse 運算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="db69b-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="db69b-132">多載 `And` 和 @no__t 1 運算子會影響 @no__t 2 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="db69b-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="db69b-133">如果您的程式碼在多載 `And` 和 `IsFalse` 的類別或結構上使用 `AndAlso`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="db69b-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="db69b-134">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="db69b-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db69b-135">範例</span><span class="sxs-lookup"><span data-stu-id="db69b-135">Example</span></span>  
 <span data-ttu-id="db69b-136">下列範例會使用 `AndAlso` 運算子，在兩個運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="db69b-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="db69b-137">結果為 @no__t 0 的值，表示整個子句運算式是否為 true。</span><span class="sxs-lookup"><span data-stu-id="db69b-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="db69b-138">如果第一個運算式 `False`，則不會評估第二個運算式。</span><span class="sxs-lookup"><span data-stu-id="db69b-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="db69b-139">上述範例會分別產生 `True`、`False` 和 `False` 的結果。</span><span class="sxs-lookup"><span data-stu-id="db69b-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="db69b-140">在 `secondCheck` 的計算中，因為第一個運算式已經 `False`，所以不會進行評估。</span><span class="sxs-lookup"><span data-stu-id="db69b-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="db69b-141">不過，第二個運算式會在 `thirdCheck` 的計算中進行評估。</span><span class="sxs-lookup"><span data-stu-id="db69b-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db69b-142">範例</span><span class="sxs-lookup"><span data-stu-id="db69b-142">Example</span></span>  
 <span data-ttu-id="db69b-143">下列範例顯示的 `Function` 程式會在陣列的元素之間搜尋指定的值。</span><span class="sxs-lookup"><span data-stu-id="db69b-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="db69b-144">如果陣列是空的，或超過陣列長度，則 `While` 語句不會針對搜尋值測試陣列元素。</span><span class="sxs-lookup"><span data-stu-id="db69b-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="db69b-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db69b-145">See also</span></span>

- [<span data-ttu-id="db69b-146">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="db69b-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="db69b-147">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="db69b-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="db69b-148">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="db69b-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="db69b-149">And 運算子</span><span class="sxs-lookup"><span data-stu-id="db69b-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="db69b-150">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="db69b-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="db69b-151">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="db69b-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
