---
title: AndAlso 運算子
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
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371930"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="1a361-102">AndAlso 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a361-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="1a361-103">在兩個運算式上執行短路邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="1a361-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a361-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a361-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1a361-105">組件</span><span class="sxs-lookup"><span data-stu-id="1a361-105">Parts</span></span>  
  
|<span data-ttu-id="1a361-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="1a361-106">Term</span></span>|<span data-ttu-id="1a361-107">定義</span><span class="sxs-lookup"><span data-stu-id="1a361-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="1a361-108">必要。</span><span class="sxs-lookup"><span data-stu-id="1a361-108">Required.</span></span> <span data-ttu-id="1a361-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="1a361-109">Any `Boolean` expression.</span></span> <span data-ttu-id="1a361-110">結果是 `Boolean` 兩個運算式比較的結果。</span><span class="sxs-lookup"><span data-stu-id="1a361-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="1a361-111">必要。</span><span class="sxs-lookup"><span data-stu-id="1a361-111">Required.</span></span> <span data-ttu-id="1a361-112">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="1a361-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="1a361-113">必要。</span><span class="sxs-lookup"><span data-stu-id="1a361-113">Required.</span></span> <span data-ttu-id="1a361-114">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="1a361-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a361-115">備註</span><span class="sxs-lookup"><span data-stu-id="1a361-115">Remarks</span></span>  
 <span data-ttu-id="1a361-116">*如果已*編譯的程式碼可以根據另一個運算式的結果，略過一個運算式的評估，則邏輯作業稱為「最少運算」。</span><span class="sxs-lookup"><span data-stu-id="1a361-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="1a361-117">如果第一個運算式評估的結果決定了作業的最後結果，就不需要評估第二個運算式，因為它無法變更最終的結果。</span><span class="sxs-lookup"><span data-stu-id="1a361-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="1a361-118">如果略過的運算式很複雜，或如果它牽涉到程序呼叫，則最少運算可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="1a361-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="1a361-119">如果兩個運算式都評估為 `True` ， `result` 則為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="1a361-120">下表說明如何 `result` 決定。</span><span class="sxs-lookup"><span data-stu-id="1a361-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1a361-121">如果 `expression1` 為 </span><span class="sxs-lookup"><span data-stu-id="1a361-121">If `expression1` is</span></span>|<span data-ttu-id="1a361-122">和 `expression2` 為</span><span class="sxs-lookup"><span data-stu-id="1a361-122">And `expression2` is</span></span>|<span data-ttu-id="1a361-123">的值 `result` 為</span><span class="sxs-lookup"><span data-stu-id="1a361-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="1a361-124">（未評估）</span><span class="sxs-lookup"><span data-stu-id="1a361-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="1a361-125">資料類型</span><span class="sxs-lookup"><span data-stu-id="1a361-125">Data Types</span></span>  
 <span data-ttu-id="1a361-126">`AndAlso`運算子只會針對[布林資料類型](../data-types/boolean-data-type.md)來定義。</span><span class="sxs-lookup"><span data-stu-id="1a361-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="1a361-127">Visual Basic 在評估運算式之前，會視需要將每個運算元轉換成 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="1a361-128">如果您將結果指派給數數值型別，Visual Basic 會將它從轉換 `Boolean` 成該類型， `False` 使變成 `0` ，而成為 `True` `-1` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="1a361-129">如需詳細資訊，請參閱布林型別[轉換](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="1a361-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="1a361-130">多載化</span><span class="sxs-lookup"><span data-stu-id="1a361-130">Overloading</span></span>  
 <span data-ttu-id="1a361-131">[And 運算子](and-operator.md)和[IsFalse 運算子](isfalse-operator.md)可以多載，這表示當運算元具有該類別或結構的類型*時，類別*或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="1a361-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1a361-132">多載 `And` 和 `IsFalse` 運算子會影響運算子的行為 `AndAlso` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="1a361-133">如果您的程式碼在多載 `AndAlso` 和的類別或結構上使用 `And` `IsFalse` ，請確定您瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="1a361-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="1a361-134">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1a361-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a361-135">範例</span><span class="sxs-lookup"><span data-stu-id="1a361-135">Example</span></span>  
 <span data-ttu-id="1a361-136">下列範例會使用 `AndAlso` 運算子，在兩個運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="1a361-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="1a361-137">結果會是一個 `Boolean` 值，表示整個子句運算式是否為 true。</span><span class="sxs-lookup"><span data-stu-id="1a361-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="1a361-138">如果第一個運算式為 `False` ，則不會評估第二個。</span><span class="sxs-lookup"><span data-stu-id="1a361-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="1a361-139">上述範例會 `True` 分別產生、 `False` 和的結果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="1a361-140">在的計算中 `secondCheck` ，因為第一個運算式已經是，所以不會進行評估 `False` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="1a361-141">不過，會在的計算中評估第二個運算式 `thirdCheck` 。</span><span class="sxs-lookup"><span data-stu-id="1a361-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a361-142">範例</span><span class="sxs-lookup"><span data-stu-id="1a361-142">Example</span></span>  
 <span data-ttu-id="1a361-143">下列範例顯示的 `Function` 程式會在陣列的元素之間搜尋指定的值。</span><span class="sxs-lookup"><span data-stu-id="1a361-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="1a361-144">如果陣列是空的，或超過陣列長度，則 `While` 語句不會針對搜尋值測試陣列元素。</span><span class="sxs-lookup"><span data-stu-id="1a361-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="1a361-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a361-145">See also</span></span>

- [<span data-ttu-id="1a361-146">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a361-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="1a361-147">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="1a361-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1a361-148">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="1a361-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1a361-149">And 運算子</span><span class="sxs-lookup"><span data-stu-id="1a361-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="1a361-150">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="1a361-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="1a361-151">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="1a361-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
