---
title: 邏輯運算子和位元運算子
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
ms.openlocfilehash: c15b9337f262563941699c0ff8fe5219ca6a5c93
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085993"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="825f1-102">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="825f1-102">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="825f1-103">邏輯運算子會比較 `Boolean` 運算式並傳回 `Boolean` 結果。</span><span class="sxs-lookup"><span data-stu-id="825f1-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="825f1-104">`And`、、 `Or` `AndAlso` 、 `OrElse` 和 `Xor` 運算子是*二元*的，因為它們採用兩個運算元，而 `Not` 運算子是*一元*，因為它採用單一運算元。</span><span class="sxs-lookup"><span data-stu-id="825f1-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="825f1-105">其中某些運算子也可以對整數值執行位邏輯運算。</span><span class="sxs-lookup"><span data-stu-id="825f1-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="825f1-106">一元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="825f1-106">Unary Logical Operator</span></span>  

 <span data-ttu-id="825f1-107">[Not 運算子會](../../../language-reference/operators/not-operator.md)對運算式*negation*執行邏輯否定 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-107">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="825f1-108">它會產生相對於其運算元的邏輯。</span><span class="sxs-lookup"><span data-stu-id="825f1-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="825f1-109">如果運算式評估為 `True` ，則會 `Not` 傳回 `False` ; 如果運算式評估為 `False` ，則 `Not` `True` 會傳回。</span><span class="sxs-lookup"><span data-stu-id="825f1-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="825f1-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="825f1-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="825f1-111">二元邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="825f1-111">Binary Logical Operators</span></span>  

 <span data-ttu-id="825f1-112">[And 運算子](../../../language-reference/operators/and-operator.md)會在兩個運算式上執行邏輯*結合* `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-112">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="825f1-113">如果兩個運算式都評估為 `True` ，則會傳回 `And` `True` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="825f1-114">如果至少有一個運算式評估為 `False` ，則會傳回 `And` `False` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="825f1-115">[Or 運算子](../../../language-reference/operators/or-operator.md)會在兩個運算式上*執行邏輯分離*或*包含* `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-115">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="825f1-116">如果任一個運算式評估為 `True` ，或兩者都評估為 `True` ，則會傳回 `Or` `True` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="825f1-117">如果兩個運算式都未評估為，就會傳回 `True` `Or` `False` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="825f1-118">[Xor 運算子](../../../language-reference/operators/xor-operator.md)會在兩個運算式上執行邏輯*排除* `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-118">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="825f1-119">如果只有一個運算式評估為 `True` （但不是兩者），則會傳回 `Xor` `True` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="825f1-120">如果兩個運算式都評估為 `True` 或兩者都評估為，則會傳回 `False` `Xor` `False` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="825f1-121">下列範例說明 `And` 、 `Or` 和 `Xor` 運算子。</span><span class="sxs-lookup"><span data-stu-id="825f1-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="825f1-122">短路邏輯作業</span><span class="sxs-lookup"><span data-stu-id="825f1-122">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="825f1-123">[AndAlso 運算子](../../../language-reference/operators/andalso-operator.md)與運算子非常類似 `And` ，因為它也會在兩個運算式上執行邏輯結合 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-123">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="825f1-124">兩者之間的主要差異在於 `AndAlso` 展現 *短路* 行為。</span><span class="sxs-lookup"><span data-stu-id="825f1-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="825f1-125">如果運算式中的第一個運算式 `AndAlso` 評估為 `False` ，則不會評估第二個運算式，因為它無法改變最後的結果，而且會傳回 `AndAlso` `False` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="825f1-126">同樣地， [OrElse 運算子](../../../language-reference/operators/orelse-operator.md) 會在兩個運算式上執行最少運算邏輯分離 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-126">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="825f1-127">如果運算式中的第一個運算式 `OrElse` 評估為 `True` ，則不會評估第二個運算式，因為它無法改變最後的結果，而且會傳回 `OrElse` `True` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="825f1-128">短路取捨</span><span class="sxs-lookup"><span data-stu-id="825f1-128">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="825f1-129">最少運算可以藉由不評估無法改變邏輯運算結果的運算式，來改善效能。</span><span class="sxs-lookup"><span data-stu-id="825f1-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="825f1-130">但是，如果該運算式執行其他動作，則會略過這些動作。</span><span class="sxs-lookup"><span data-stu-id="825f1-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="825f1-131">例如，如果運算式包含對程式的呼叫，則 `Function` 不會在運算式縮短時呼叫該程式，而且所包含的任何其他程式碼都不會 `Function` 執行。</span><span class="sxs-lookup"><span data-stu-id="825f1-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="825f1-132">因此，函式可能只會偶爾執行，而且可能無法正確地進行測試。</span><span class="sxs-lookup"><span data-stu-id="825f1-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="825f1-133">或者，程式邏輯可能相依于中的程式碼 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="825f1-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="825f1-134">下列範例說明 `And` 、 `Or` 和它們的短路對應專案之間的差異。</span><span class="sxs-lookup"><span data-stu-id="825f1-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="825f1-135">在上述範例中，請注意，不會在 `checkIfValid()` 呼叫縮短時執行內的一些重要程式碼。</span><span class="sxs-lookup"><span data-stu-id="825f1-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="825f1-136">第一個 `If` 語句 `checkIfValid()` 會呼叫，即使傳回，也是一樣 `12 > 45` `False` ，因為不 `And` 會短路。</span><span class="sxs-lookup"><span data-stu-id="825f1-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="825f1-137">第二個 `If` 語句不會呼叫 `checkIfValid()` ，因為當傳回時 `12 > 45` ，會 `False` `AndAlso` 將第二個運算式縮短。</span><span class="sxs-lookup"><span data-stu-id="825f1-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="825f1-138">第三個 `If` 語句 `checkIfValid()` 會呼叫，即使傳回，也是一樣 `12 < 45` `True` ，因為不 `Or` 會短路。</span><span class="sxs-lookup"><span data-stu-id="825f1-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="825f1-139">第四個 `If` 語句不會呼叫 `checkIfValid()` ，因為當傳回時 `12 < 45` ，會 `True` `OrElse` 將第二個運算式縮短。</span><span class="sxs-lookup"><span data-stu-id="825f1-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="825f1-140">位運算</span><span class="sxs-lookup"><span data-stu-id="825f1-140">Bitwise Operations</span></span>  

 <span data-ttu-id="825f1-141">位運算會以二進位 (基底 2) 形式來評估兩個整數值。</span><span class="sxs-lookup"><span data-stu-id="825f1-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="825f1-142">它們會比較對應位置的位，然後根據比較來指派值。</span><span class="sxs-lookup"><span data-stu-id="825f1-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="825f1-143">下列範例說明 `And` 運算子。</span><span class="sxs-lookup"><span data-stu-id="825f1-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="825f1-144">上述範例會將的值設定 `x` 為1。</span><span class="sxs-lookup"><span data-stu-id="825f1-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="825f1-145">發生此問題的原因如下：</span><span class="sxs-lookup"><span data-stu-id="825f1-145">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="825f1-146">這些值會視為二進位：</span><span class="sxs-lookup"><span data-stu-id="825f1-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="825f1-147">3二進位格式 = 011</span><span class="sxs-lookup"><span data-stu-id="825f1-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="825f1-148">5（二進位格式 = 101）</span><span class="sxs-lookup"><span data-stu-id="825f1-148">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="825f1-149">`And`運算子會比較二進位標記法，一個二進位位置 (位) 一次。</span><span class="sxs-lookup"><span data-stu-id="825f1-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="825f1-150">如果指定位置的兩個位都是1，則會在結果中將1放在該位置。</span><span class="sxs-lookup"><span data-stu-id="825f1-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="825f1-151">如果任一個位為0，則結果中會將0放在該位置。</span><span class="sxs-lookup"><span data-stu-id="825f1-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="825f1-152">在上述範例中，這會以下面方式運作：</span><span class="sxs-lookup"><span data-stu-id="825f1-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="825f1-153">binary 格式的 011 (3) </span><span class="sxs-lookup"><span data-stu-id="825f1-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="825f1-154">101 (5 二進位格式) </span><span class="sxs-lookup"><span data-stu-id="825f1-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="825f1-155">001 (結果，以二進位格式) </span><span class="sxs-lookup"><span data-stu-id="825f1-155">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="825f1-156">結果會被視為 decimal。</span><span class="sxs-lookup"><span data-stu-id="825f1-156">The result is treated as decimal.</span></span> <span data-ttu-id="825f1-157">值001是1的二進位標記法，因此 `x` = 1。</span><span class="sxs-lookup"><span data-stu-id="825f1-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="825f1-158">位 `Or` 運算很類似，不同之處在于如果其中一或兩個比較的位為1，則會將1指派給結果位。</span><span class="sxs-lookup"><span data-stu-id="825f1-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="825f1-159">`Xor` 如果只有一個比較的位 (不是兩個) 都是1，則會將1指派給結果位。</span><span class="sxs-lookup"><span data-stu-id="825f1-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="825f1-160">`Not` 採用單一運算元並反轉所有位（包括正負號位），並將該值指派給結果。</span><span class="sxs-lookup"><span data-stu-id="825f1-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="825f1-161">這表示對於帶正負號的正數，一律會傳回 `Not` 負值，而針對負數，一律會傳回 `Not` 正值或零值。</span><span class="sxs-lookup"><span data-stu-id="825f1-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="825f1-162">`AndAlso`和 `OrElse` 運算子不支援位運算。</span><span class="sxs-lookup"><span data-stu-id="825f1-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="825f1-163">位運算只能在整數類型上執行。</span><span class="sxs-lookup"><span data-stu-id="825f1-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="825f1-164">必須先將浮點值轉換成整數類資料類型，然後才能繼續進行位運算。</span><span class="sxs-lookup"><span data-stu-id="825f1-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825f1-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="825f1-165">See also</span></span>

- [<span data-ttu-id="825f1-166">邏輯/位元運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="825f1-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="825f1-167">布林運算式</span><span class="sxs-lookup"><span data-stu-id="825f1-167">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="825f1-168">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="825f1-168">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="825f1-169">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="825f1-169">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="825f1-170">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="825f1-170">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="825f1-171">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="825f1-171">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
