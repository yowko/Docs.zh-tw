---
title: Visual Basic 中的邏輯運算子和位元運算子
ms.date: 07/20/2015
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
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963310"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="cfbe4-102">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-102">Logical and Bitwise Operators in Visual Basic</span></span>
<span data-ttu-id="cfbe4-103">邏輯運算子會`Boolean`比較運算式並`Boolean`傳回結果。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="cfbe4-104">`And`、 、`Or` `Not` 、和運算子是二進位的,因為它們接受兩個運算元,而運算子是一元,因為它採用單一運算元。`Xor` `AndAlso` `OrElse`</span><span class="sxs-lookup"><span data-stu-id="cfbe4-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="cfbe4-105">其中有些運算子也可以在整數值上執行位邏輯運算。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="cfbe4-106">一元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-106">Unary Logical Operator</span></span>  
 <span data-ttu-id="cfbe4-107">[Not 運算子會](../../../../visual-basic/language-reference/operators/not-operator.md)在`Boolean`運算式上執行邏輯*否定*。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-107">The [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="cfbe4-108">它會產生與其運算元相反的邏輯。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="cfbe4-109">如果運算式評估為`True`, `False`則`Not`會傳回; `False`如果運算式`Not`評估為, 則傳回。 `True`</span><span class="sxs-lookup"><span data-stu-id="cfbe4-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="cfbe4-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="cfbe4-111">二元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-111">Binary Logical Operators</span></span>  
 <span data-ttu-id="cfbe4-112">[And 運算子](../../../../visual-basic/language-reference/operators/and-operator.md)會在兩個`Boolean`運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-112">The [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="cfbe4-113">如果兩個運算式都`True`評估為`And` , `True`則會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="cfbe4-114">如果至少有一個運算式評估為`False`, `False`則`And`傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="cfbe4-115">[Or 運算子](../../../../visual-basic/language-reference/operators/or-operator.md)會在兩個`Boolean`運算式上執行邏輯分離或*包含*。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-115">The [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="cfbe4-116">如果任一運算式評估為`True`, 或兩者都評估`True`為, `Or`則`True`會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="cfbe4-117">如果兩個運算式都`True`不`Or`是`False`評估為, 會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="cfbe4-118">[Xor 運算子](../../../../visual-basic/language-reference/operators/xor-operator.md)會在兩個`Boolean`運算式上執行邏輯排除。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-118">The [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="cfbe4-119">如果只有一個運算式評估為`True`(但不是兩者`Xor` `True`), 則會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="cfbe4-120">如果兩個運算式都`True`評估為或同時`False`評估`Xor`為`False`, 會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="cfbe4-121">下列範例說明`And`、 `Or`和`Xor`運算子。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="cfbe4-122">最小運算邏輯作業</span><span class="sxs-lookup"><span data-stu-id="cfbe4-122">Short-Circuiting Logical Operations</span></span>  
 <span data-ttu-id="cfbe4-123">[AndAlso 運算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)與`And`運算子非常類似, 因為它也會在兩個`Boolean`運算式上執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-123">The [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="cfbe4-124">兩者之間的主要差異在於展示最`AndAlso`少運算的行為。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="cfbe4-125">如果`AndAlso`運算式中的第一個運算式評估為`False`, 則不會評估第二個運算式, 因為它無法改變`False`最後的結果`AndAlso` , 並且會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="cfbe4-126">同樣地, [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)會在兩個`Boolean`運算式上執行最少運算邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-126">Similarly, the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="cfbe4-127">如果`OrElse`運算式中的第一個運算式評估為`True`, 則不會評估第二個運算式, 因為它無法改變`True`最後的結果`OrElse` , 並且會傳回。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="cfbe4-128">短路取捨</span><span class="sxs-lookup"><span data-stu-id="cfbe4-128">Short-Circuiting Trade-Offs</span></span>  
 <span data-ttu-id="cfbe4-129">「最少運算」可以藉由不評估無法改變邏輯作業結果的運算式來改善效能。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="cfbe4-130">不過, 如果該運算式執行其他動作, 則最少運算會略過這些動作。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="cfbe4-131">例如, 如果運算式包含對程式的呼叫`Function` , 則不會在縮短運算式時呼叫該程式, 而且中包含的`Function`任何其他程式碼都不會執行。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="cfbe4-132">因此, 函式可能只會偶爾執行, 而且可能無法正確地進行測試。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="cfbe4-133">或程式邏輯可能相依于中`Function`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="cfbe4-134">下列範例說明、 `And` `Or`和其最小運算對應專案之間的差異。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="cfbe4-135">在上述範例中, 請注意, 在呼叫縮短`checkIfValid()`時, 內的某些重要程式碼不會執行。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="cfbe4-136">即使傳回`If` `False`, 第`checkIfValid()`一個語句`12 > 45`也會呼叫`And` , 因為不會有短路。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="cfbe4-137">第二`If`個語句不會`checkIfValid()`呼叫, 因為當`False`傳回`AndAlso`時`12 > 45` , 會將第二個運算式短路。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="cfbe4-138">雖然會`If`傳回`12 < 45` `checkIfValid()` ,`True`但第三個語句`Or`會呼叫, 因為不會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="cfbe4-139">第四`If`個語句不會`checkIfValid()`呼叫, 因為當`True`傳回`OrElse`時`12 < 45` , 會將第二個運算式短路。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="cfbe4-140">位運算</span><span class="sxs-lookup"><span data-stu-id="cfbe4-140">Bitwise Operations</span></span>  
 <span data-ttu-id="cfbe4-141">位運算會以二進位 (基底 2) 形式評估兩個整數值。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="cfbe4-142">它們會比較對應位置的位, 然後根據比較來指派值。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="cfbe4-143">下列範例說明`And`運算子。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="cfbe4-144">上述範例會將的值`x`設定為1。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="cfbe4-145">這會因下列原因而發生:</span><span class="sxs-lookup"><span data-stu-id="cfbe4-145">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="cfbe4-146">這些值會被視為二進位:</span><span class="sxs-lookup"><span data-stu-id="cfbe4-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="cfbe4-147">3 (二進位格式 = 011)</span><span class="sxs-lookup"><span data-stu-id="cfbe4-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="cfbe4-148">5二進位格式 = 101</span><span class="sxs-lookup"><span data-stu-id="cfbe4-148">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="cfbe4-149">`And`運算子會比較二進位標記法, 一次一個二進位位置 (位)。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="cfbe4-150">如果指定位置的兩個位都是 1, 則會將1放在結果中的該位置。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="cfbe4-151">如果任一個位為 0, 則會將0放在結果中的該位置。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="cfbe4-152">在上述範例中, 這種方式如下所示:</span><span class="sxs-lookup"><span data-stu-id="cfbe4-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="cfbe4-153">011 (二進位格式為 3)</span><span class="sxs-lookup"><span data-stu-id="cfbe4-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="cfbe4-154">101 (二進位格式的 5)</span><span class="sxs-lookup"><span data-stu-id="cfbe4-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="cfbe4-155">001 (以二進位形式呈現的結果)</span><span class="sxs-lookup"><span data-stu-id="cfbe4-155">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="cfbe4-156">結果會被視為 decimal。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-156">The result is treated as decimal.</span></span> <span data-ttu-id="cfbe4-157">001值是1的二進位表示, 因此`x` = 1。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="cfbe4-158">位`Or`運算很相似, 不同之處在于如果其中一個或兩個比較的位為 1, 則會將1指派給結果位。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="cfbe4-159">`Xor`如果只有一個比較的位 (不是兩個) 是 1, 則將1指派給結果位。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="cfbe4-160">`Not`接受單一運算元並反轉所有位, 包括符號位, 並將該值指派給結果。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="cfbe4-161">這表示對於帶正負號的正數`Not` , 一律會傳回負值, 而對於負數, `Not`一律會傳回正值或零值。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="cfbe4-162">`AndAlso` 和`OrElse`運算子不支援位運算。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfbe4-163">位運算只能在整數類型上執行。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="cfbe4-164">必須先將浮點值轉換成整數類型, 才能繼續進行位運算。</span><span class="sxs-lookup"><span data-stu-id="cfbe4-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbe4-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfbe4-165">See also</span></span>

- [<span data-ttu-id="cfbe4-166">邏輯/位運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfbe4-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="cfbe4-167">布林運算式</span><span class="sxs-lookup"><span data-stu-id="cfbe4-167">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="cfbe4-168">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-168">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="cfbe4-169">Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-169">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="cfbe4-170">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="cfbe4-170">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [<span data-ttu-id="cfbe4-171">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="cfbe4-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
