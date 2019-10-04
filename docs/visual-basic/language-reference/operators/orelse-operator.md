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
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835237"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="40dd5-102">OrElse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40dd5-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="40dd5-103">在兩個運算式上執行最少運算（含）運算邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="40dd5-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40dd5-104">語法</span><span class="sxs-lookup"><span data-stu-id="40dd5-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="40dd5-105">組件</span><span class="sxs-lookup"><span data-stu-id="40dd5-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="40dd5-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="40dd5-106">Required.</span></span> <span data-ttu-id="40dd5-107">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="40dd5-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="40dd5-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="40dd5-108">Required.</span></span> <span data-ttu-id="40dd5-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="40dd5-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="40dd5-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="40dd5-110">Required.</span></span> <span data-ttu-id="40dd5-111">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="40dd5-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40dd5-112">備註</span><span class="sxs-lookup"><span data-stu-id="40dd5-112">Remarks</span></span>  
 <span data-ttu-id="40dd5-113">*如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。</span><span class="sxs-lookup"><span data-stu-id="40dd5-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="40dd5-114">如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。</span><span class="sxs-lookup"><span data-stu-id="40dd5-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="40dd5-115">如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="40dd5-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="40dd5-116">如果任一個或兩個運算式評估為 `True`，`result` 會 `True`。</span><span class="sxs-lookup"><span data-stu-id="40dd5-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="40dd5-117">下表說明如何判斷 `result`。</span><span class="sxs-lookup"><span data-stu-id="40dd5-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="40dd5-118">如果`expression1`為</span><span class="sxs-lookup"><span data-stu-id="40dd5-118">If `expression1` is</span></span>|<span data-ttu-id="40dd5-119">和`expression2`為</span><span class="sxs-lookup"><span data-stu-id="40dd5-119">And `expression2` is</span></span>|<span data-ttu-id="40dd5-120">@No__t-0 的值為</span><span class="sxs-lookup"><span data-stu-id="40dd5-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="40dd5-121">（未評估）</span><span class="sxs-lookup"><span data-stu-id="40dd5-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="40dd5-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="40dd5-122">Data Types</span></span>  
 <span data-ttu-id="40dd5-123">@No__t-0 運算子只會針對[布林資料類型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)來定義。</span><span class="sxs-lookup"><span data-stu-id="40dd5-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="40dd5-124">Visual Basic 在評估運算式之前，會視需要將每個運算元轉換為 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="40dd5-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="40dd5-125">如果您將結果指派給數數值型別，Visual Basic 會將它從 `Boolean` 轉換成該類型，如此 `False` 會變成 `0`，而 `True` 會變成 `-1`。</span><span class="sxs-lookup"><span data-stu-id="40dd5-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="40dd5-126">如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="40dd5-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="40dd5-127">多載化</span><span class="sxs-lookup"><span data-stu-id="40dd5-127">Overloading</span></span>  
 <span data-ttu-id="40dd5-128">[Or 運算子](../../../visual-basic/language-reference/operators/or-operator.md)和[IsTrue 運算子](../../../visual-basic/language-reference/operators/istrue-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="40dd5-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="40dd5-129">多載 `Or` 和 @no__t 1 運算子會影響 @no__t 2 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="40dd5-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="40dd5-130">如果您的程式碼在多載 `Or` 和 `IsTrue` 的類別或結構上使用 `OrElse`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="40dd5-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="40dd5-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="40dd5-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40dd5-132">範例</span><span class="sxs-lookup"><span data-stu-id="40dd5-132">Example</span></span>  
 <span data-ttu-id="40dd5-133">下列範例會使用 `OrElse` 運算子，在兩個運算式上執行邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="40dd5-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="40dd5-134">結果為 @no__t 0 的值，表示兩個運算式的其中一個是否為 true。</span><span class="sxs-lookup"><span data-stu-id="40dd5-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="40dd5-135">如果第一個運算式 `True`，則不會評估第二個運算式。</span><span class="sxs-lookup"><span data-stu-id="40dd5-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="40dd5-136">上述範例會分別產生 `True`、`True` 和 `False` 的結果。</span><span class="sxs-lookup"><span data-stu-id="40dd5-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="40dd5-137">在 `firstCheck` 的計算中，因為第一個運算式已經 `True`，所以不會進行評估。</span><span class="sxs-lookup"><span data-stu-id="40dd5-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="40dd5-138">不過，第二個運算式會在 `secondCheck` 的計算中進行評估。</span><span class="sxs-lookup"><span data-stu-id="40dd5-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40dd5-139">範例</span><span class="sxs-lookup"><span data-stu-id="40dd5-139">Example</span></span>  
 <span data-ttu-id="40dd5-140">下列範例顯示包含兩個程序呼叫的 `If` ... @no__t 1 語句。</span><span class="sxs-lookup"><span data-stu-id="40dd5-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="40dd5-141">如果第一次呼叫傳回 `True`，則不會呼叫第二個程式。</span><span class="sxs-lookup"><span data-stu-id="40dd5-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="40dd5-142">如果第二個程式執行程式碼的這個區段時一定要執行的重要工作，這可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="40dd5-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="40dd5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40dd5-143">See also</span></span>

- [<span data-ttu-id="40dd5-144">邏輯/位運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="40dd5-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="40dd5-145">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="40dd5-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="40dd5-146">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="40dd5-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="40dd5-147">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="40dd5-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="40dd5-148">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="40dd5-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="40dd5-149">Visual Basic 中的邏輯和位運算子</span><span class="sxs-lookup"><span data-stu-id="40dd5-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
