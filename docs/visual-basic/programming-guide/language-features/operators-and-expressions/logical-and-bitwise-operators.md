---
title: "Visual Basic 中的邏輯運算子和位元運算子"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba48f722a11e93f82ae99aa407c3096a964e5ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="aacd0-102">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-102">Logical and Bitwise Operators in Visual Basic</span></span>
<span data-ttu-id="aacd0-103">邏輯運算子會比較`Boolean`運算式並傳回`Boolean`結果。</span><span class="sxs-lookup"><span data-stu-id="aacd0-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="aacd0-104">`And`， `Or`， `AndAlso`， `OrElse`，和`Xor`運算子是*二進位*由於它們會採用兩個運算元，而`Not`運算子是*一元*因為它會採用單一運算元。</span><span class="sxs-lookup"><span data-stu-id="aacd0-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="aacd0-105">其中某些運算子也可以執行位元整數值上的邏輯作業。</span><span class="sxs-lookup"><span data-stu-id="aacd0-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="aacd0-106">一元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-106">Unary Logical Operator</span></span>  
 <span data-ttu-id="aacd0-107">[Not 運算子](../../../../visual-basic/language-reference/operators/not-operator.md)執行邏輯*否定*上`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-107">The [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="aacd0-108">它會產生其運算元的相反邏輯。</span><span class="sxs-lookup"><span data-stu-id="aacd0-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="aacd0-109">如果運算式評估為`True`，然後`Not`傳回`False`; 如果運算式評估為`False`，然後`Not`傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="aacd0-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="aacd0-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="aacd0-111">二元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-111">Binary Logical Operators</span></span>  
 <span data-ttu-id="aacd0-112">[與運算子](../../../../visual-basic/language-reference/operators/and-operator.md)執行邏輯*搭配*在兩個`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-112">The [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="aacd0-113">如果這兩個運算式評估為`True`，然後`And`傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="aacd0-114">如果至少一個運算式評估為`False`，然後`And`傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="aacd0-115">[或運算子](../../../../visual-basic/language-reference/operators/or-operator.md)執行邏輯*分離*或*包含*在兩個`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-115">The [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="aacd0-116">如果任一個運算式評估為`True`，或兩者都評估為`True`，然後`Or`傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="aacd0-117">如果兩個運算式判斷值為`True`，`Or`傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="aacd0-118">[Xor 運算子](../../../../visual-basic/language-reference/operators/xor-operator.md)執行邏輯*排除*在兩個`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-118">The [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="aacd0-119">如果只有一個運算式評估為`True`，但非兩者`Xor`傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="aacd0-120">如果這兩個運算式評估為`True`或兩者都評估為`False`，`Xor`傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="aacd0-121">下列範例說明`And`， `Or`，和`Xor`運算子。</span><span class="sxs-lookup"><span data-stu-id="aacd0-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="aacd0-122">最少運算邏輯作業</span><span class="sxs-lookup"><span data-stu-id="aacd0-122">Short-Circuiting Logical Operations</span></span>  
 <span data-ttu-id="aacd0-123">[AndAlso 運算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)非常類似於`And`運算子，它也會在兩個執行邏輯結合`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-123">The [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="aacd0-124">兩者之間的主要差異在於`AndAlso`表現*最少運算*行為。</span><span class="sxs-lookup"><span data-stu-id="aacd0-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="aacd0-125">如果中的第一個運算式`AndAlso`運算式評估為`False`，則它無法改變的最終結果，因為不會評估第二個運算式和`AndAlso`傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="aacd0-126">同樣地， [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)執行最少運算邏輯分離，在兩個`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-126">Similarly, the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="aacd0-127">如果中的第一個運算式`OrElse`運算式評估為`True`，則它無法改變的最終結果，因為不會評估第二個運算式和`OrElse`傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="aacd0-128">最少運算的取捨</span><span class="sxs-lookup"><span data-stu-id="aacd0-128">Short-Circuiting Trade-Offs</span></span>  
 <span data-ttu-id="aacd0-129">最少運算可以改善效能，不會評估運算式，無法變更邏輯作業的結果。</span><span class="sxs-lookup"><span data-stu-id="aacd0-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="aacd0-130">不過，如果該運算式會執行其他動作，最少運算會略過這些動作。</span><span class="sxs-lookup"><span data-stu-id="aacd0-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="aacd0-131">例如，如果運算式包括呼叫`Function`程序中，如果運算式是最少運算，和任何額外的程式碼包含在程序不會呼叫`Function`不會執行。</span><span class="sxs-lookup"><span data-stu-id="aacd0-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="aacd0-132">因此，函式可能會偶爾才會執行，而且可能不正確地測試。</span><span class="sxs-lookup"><span data-stu-id="aacd0-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="aacd0-133">程式邏輯可能會相依於中的程式碼或`Function`。</span><span class="sxs-lookup"><span data-stu-id="aacd0-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="aacd0-134">下列範例說明之間的差異`And`， `Or`，及其最少運算的對應。</span><span class="sxs-lookup"><span data-stu-id="aacd0-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 <span data-ttu-id="aacd0-135">在上述範例中，請注意，某些重要的程式碼內`checkIfValid()`呼叫最少運算時不會執行。</span><span class="sxs-lookup"><span data-stu-id="aacd0-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="aacd0-136">第一個`If`陳述式會呼叫`checkIfValid()`即使`12 > 45`傳回`False`，因為`And`不最短路徑。</span><span class="sxs-lookup"><span data-stu-id="aacd0-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="aacd0-137">第二個`If`陳述式不會呼叫`checkIfValid()`，因為當`12 > 45`傳回`False`， `AndAlso` short-circuits 第二個運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="aacd0-138">第三個`If`陳述式會呼叫`checkIfValid()`即使`12 < 45`傳回`True`，因為`Or`不最短路徑。</span><span class="sxs-lookup"><span data-stu-id="aacd0-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="aacd0-139">第四個`If`陳述式不會呼叫`checkIfValid()`，因為當`12 < 45`傳回`True`， `OrElse` short-circuits 第二個運算式。</span><span class="sxs-lookup"><span data-stu-id="aacd0-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="aacd0-140">位元運算</span><span class="sxs-lookup"><span data-stu-id="aacd0-140">Bitwise Operations</span></span>  
 <span data-ttu-id="aacd0-141">位元運算的評估結果 (基底 2) 的二進位格式的兩個整數值。</span><span class="sxs-lookup"><span data-stu-id="aacd0-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="aacd0-142">這些比較對應位置的位元，並接著指派根據比較結果的值。</span><span class="sxs-lookup"><span data-stu-id="aacd0-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="aacd0-143">下列範例說明`And`運算子。</span><span class="sxs-lookup"><span data-stu-id="aacd0-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 <span data-ttu-id="aacd0-144">上述範例中設定的值`x`設為 1。</span><span class="sxs-lookup"><span data-stu-id="aacd0-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="aacd0-145">發生這種情況，原因如下：</span><span class="sxs-lookup"><span data-stu-id="aacd0-145">This happens for the following reasons:</span></span>  
  
-   <span data-ttu-id="aacd0-146">值會被視為二進位：</span><span class="sxs-lookup"><span data-stu-id="aacd0-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="aacd0-147">以二進位形式的 3 = 011</span><span class="sxs-lookup"><span data-stu-id="aacd0-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="aacd0-148">以二進位形式的 5 = 101</span><span class="sxs-lookup"><span data-stu-id="aacd0-148">5 in binary form = 101</span></span>  
  
-   <span data-ttu-id="aacd0-149">`And`運算子比較的二進位表示法，一次一個二進位位置 （位元）。</span><span class="sxs-lookup"><span data-stu-id="aacd0-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="aacd0-150">如果指定的位置兩個位元都是 1，1 會在結果中的那個位置中。</span><span class="sxs-lookup"><span data-stu-id="aacd0-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="aacd0-151">如果其中一個位元為 0，0 會在結果中的那個位置中。</span><span class="sxs-lookup"><span data-stu-id="aacd0-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="aacd0-152">在上述範例中可以這麼做，如下所示：</span><span class="sxs-lookup"><span data-stu-id="aacd0-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="aacd0-153">011 (3 二進位格式)</span><span class="sxs-lookup"><span data-stu-id="aacd0-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="aacd0-154">101 (5 二進位格式)</span><span class="sxs-lookup"><span data-stu-id="aacd0-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="aacd0-155">001 （結果，以二進位格式）</span><span class="sxs-lookup"><span data-stu-id="aacd0-155">001 (The result, in binary form)</span></span>  
  
-   <span data-ttu-id="aacd0-156">結果會被視為十進位。</span><span class="sxs-lookup"><span data-stu-id="aacd0-156">The result is treated as decimal.</span></span> <span data-ttu-id="aacd0-157">001 的值是 1 的二進位表示法因此`x`= 1。</span><span class="sxs-lookup"><span data-stu-id="aacd0-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="aacd0-158">位元`Or`作業很類似，不同之處在於如果一個或兩個比較的位元為 1 1 指派給結果位元。</span><span class="sxs-lookup"><span data-stu-id="aacd0-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="aacd0-159">`Xor`如果只有其中一個比較 （非兩者） 位元為 1，將 1 指派的結果位元。</span><span class="sxs-lookup"><span data-stu-id="aacd0-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="aacd0-160">`Not`使用單一運算元反轉所有位元，包括正負號位元，並將該值指派給結果。</span><span class="sxs-lookup"><span data-stu-id="aacd0-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="aacd0-161">這表示針對簽署正數，`Not`一律會傳回一個負數值，並為負數，`Not`一律會傳回正或零值。</span><span class="sxs-lookup"><span data-stu-id="aacd0-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="aacd0-162">`AndAlso`和`OrElse`運算子不支援位元運算。</span><span class="sxs-lookup"><span data-stu-id="aacd0-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aacd0-163">只有整數類資料型別，可以執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="aacd0-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="aacd0-164">浮點值必須轉換成整數類資料類型，然後才可以繼續執行位元運算。</span><span class="sxs-lookup"><span data-stu-id="aacd0-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aacd0-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aacd0-165">See Also</span></span>  
 [<span data-ttu-id="aacd0-166">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aacd0-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="aacd0-167">布林運算式</span><span class="sxs-lookup"><span data-stu-id="aacd0-167">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="aacd0-168">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-168">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="aacd0-169">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-169">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="aacd0-170">在 Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="aacd0-170">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="aacd0-171">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="aacd0-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
