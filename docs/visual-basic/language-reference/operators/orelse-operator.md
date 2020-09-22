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
ms.openlocfilehash: edac3eeaef5d0127f10a0d570ca27c8158806ff3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866723"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="a4ba2-102">OrElse 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ba2-102">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="a4ba2-103">在兩個運算式上執行最少運算內含邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ba2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a4ba2-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a4ba2-105">組件</span><span class="sxs-lookup"><span data-stu-id="a4ba2-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="a4ba2-106">必要。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-106">Required.</span></span> <span data-ttu-id="a4ba2-107">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a4ba2-108">必要。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-108">Required.</span></span> <span data-ttu-id="a4ba2-109">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a4ba2-110">必要。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-110">Required.</span></span> <span data-ttu-id="a4ba2-111">任何 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4ba2-112">備註</span><span class="sxs-lookup"><span data-stu-id="a4ba2-112">Remarks</span></span>  

 <span data-ttu-id="a4ba2-113">如果已編譯的程式碼可以略過一個運算式的評估（視另一個運算式的結果而 *定）* ，則邏輯運算稱為「最少運算」。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="a4ba2-114">如果評估的第一個運算式的結果決定作業的最後結果，則不需要評估第二個運算式，因為它無法變更最後的結果。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="a4ba2-115">如果略過的運算式很複雜，或是牽涉到程序呼叫，則最少運算可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="a4ba2-116">如果任一個或兩個運算式都評估為 `True` ， `result` 就是 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="a4ba2-117">下表說明如何 `result` 決定。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a4ba2-118">如果 `expression1` 為 </span><span class="sxs-lookup"><span data-stu-id="a4ba2-118">If `expression1` is</span></span>|<span data-ttu-id="a4ba2-119">而且 `expression2` 是</span><span class="sxs-lookup"><span data-stu-id="a4ba2-119">And `expression2` is</span></span>|<span data-ttu-id="a4ba2-120">的值 `result` 為</span><span class="sxs-lookup"><span data-stu-id="a4ba2-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="a4ba2-121">未評估 () </span><span class="sxs-lookup"><span data-stu-id="a4ba2-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="a4ba2-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="a4ba2-122">Data Types</span></span>  

 <span data-ttu-id="a4ba2-123">`OrElse`運算子只會定義為[布林資料類型](../data-types/boolean-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-123">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="a4ba2-124">Visual Basic 會在評估運算式之前，視需要將每個運算元轉換成 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="a4ba2-125">如果您將結果指派給數值型別，Visual Basic 會將它從轉換 `Boolean` 成該型別，如此 `False` 就會變成 `0` 和 `True` 成為 `-1` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="a4ba2-126">如需詳細資訊，請參閱布林型別 [轉換](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="a4ba2-127">多載化</span><span class="sxs-lookup"><span data-stu-id="a4ba2-127">Overloading</span></span>  

 <span data-ttu-id="a4ba2-128">可以多載 [Or 運算子](or-operator.md) 和 [IsTrue 運算子](istrue-operator.md) ，這表示當運算元具有該類別或結構的型別 *時，類別*或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-128">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a4ba2-129">多載 `Or` 和 `IsTrue` 運算子會影響運算子的行為 `OrElse` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="a4ba2-130">如果您的程式碼在多載 `OrElse` 和的類別或結構上使用 `Or` `IsTrue` ，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="a4ba2-131">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4ba2-132">範例</span><span class="sxs-lookup"><span data-stu-id="a4ba2-132">Example</span></span>  

 <span data-ttu-id="a4ba2-133">下列範例會使用 `OrElse` 運算子，在兩個運算式上執行邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="a4ba2-134">結果是一個 `Boolean` 值，表示兩個運算式的任一個是否為 true。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="a4ba2-135">如果第一個運算式是 `True` ，則不會評估第二個運算式。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="a4ba2-136">上述範例會 `True` 分別產生、 `True` 和的結果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="a4ba2-137">在的計算中 `firstCheck` ，不會評估第二個運算式，因為第一個運算式已經是 `True` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="a4ba2-138">但是，第二個運算式會在的計算中進行評估 `secondCheck` 。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4ba2-139">範例</span><span class="sxs-lookup"><span data-stu-id="a4ba2-139">Example</span></span>  

 <span data-ttu-id="a4ba2-140">下列範例顯示 `If` `Then` 包含兩個程序呼叫的 ... 語句。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="a4ba2-141">如果第一個呼叫傳回 `True` ，則不會呼叫第二個程式。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="a4ba2-142">如果第二個程式執行的重要工作是在程式碼的這個區段執行時一律執行，這可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="a4ba2-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="a4ba2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4ba2-143">See also</span></span>

- [<span data-ttu-id="a4ba2-144">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ba2-144">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="a4ba2-145">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="a4ba2-145">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a4ba2-146">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="a4ba2-146">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a4ba2-147">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="a4ba2-147">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="a4ba2-148">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="a4ba2-148">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="a4ba2-149">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="a4ba2-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
