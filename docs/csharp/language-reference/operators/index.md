---
title: C# 運算子
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 6380fa4ec99f598be0d01db1061900520e94d5f1
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333404"
---
# <a name="c-operators"></a><span data-ttu-id="122c4-102">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-102">C# operators</span></span>

<span data-ttu-id="122c4-103">C# 提供許多運算子，也就是指定要在運算式中執行哪些作業 (數學、索引化、函式呼叫等) 的符號。</span><span class="sxs-lookup"><span data-stu-id="122c4-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="122c4-104">您可以[多載](../../programming-guide/statements-expressions-operators/overloadable-operators.md)許多運算子，以便在套用至使用者定義型別時變更它們的意義。</span><span class="sxs-lookup"><span data-stu-id="122c4-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="122c4-105">列舉 (`enum`) 型別上通常會允許整數型別上的作業 (例如 `==`、`!=`、`<`、`>`、`&`、`|`)。</span><span class="sxs-lookup"><span data-stu-id="122c4-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="122c4-106">下列區段列出 C# 運算子，從最高優先順序開始到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="122c4-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="122c4-107">每個區段中的運算子會共用相同的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="122c4-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="122c4-108">主要運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-108">Primary operators</span></span>

<span data-ttu-id="122c4-109">這些是最高優先順序的運算子。</span><span class="sxs-lookup"><span data-stu-id="122c4-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="122c4-110">[x.y](member-access-operator.md) – 成員存取。</span><span class="sxs-lookup"><span data-stu-id="122c4-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="122c4-111">[x?.y](null-conditional-operators.md) – null 條件成員存取。</span><span class="sxs-lookup"><span data-stu-id="122c4-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="122c4-112">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="122c4-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="122c4-113">[x?[y]](null-conditional-operators.md) - null 條件式索引存取。</span><span class="sxs-lookup"><span data-stu-id="122c4-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="122c4-114">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="122c4-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="122c4-115">[f(x)](invocation-operator.md) – 函式引動過程。</span><span class="sxs-lookup"><span data-stu-id="122c4-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="122c4-116">[a&#91;x&#93;](index-operator.md) – 彙總物件索引化。</span><span class="sxs-lookup"><span data-stu-id="122c4-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="122c4-117">[x++](increment-operator.md) – 後置遞增。</span><span class="sxs-lookup"><span data-stu-id="122c4-117">[x++](increment-operator.md) – postfix increment.</span></span> <span data-ttu-id="122c4-118">傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="122c4-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="122c4-119">[x--](decrement-operator.md) – 後置遞減。</span><span class="sxs-lookup"><span data-stu-id="122c4-119">[x--](decrement-operator.md) –  postfix decrement.</span></span> <span data-ttu-id="122c4-120">傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="122c4-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="122c4-121">[new](../keywords/new-operator.md) – 型別執行個體化。</span><span class="sxs-lookup"><span data-stu-id="122c4-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="122c4-122">[typeof](../keywords/typeof.md) - 傳回代表運算元的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="122c4-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="122c4-123">[checked](../keywords/checked.md) – 啟動整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="122c4-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="122c4-124">[unchecked](../keywords/unchecked.md) – 停用整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="122c4-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="122c4-125">這是預設編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="122c4-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="122c4-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 產生類型 T 的預設值。</span><span class="sxs-lookup"><span data-stu-id="122c4-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="122c4-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="122c4-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="122c4-128">[sizeof](../keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="122c4-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="122c4-129">[->](dereference-operator.md) – 指標取值結合成員存取。</span><span class="sxs-lookup"><span data-stu-id="122c4-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="122c4-130">一元運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-130">Unary operators</span></span>

<span data-ttu-id="122c4-131">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-132">[+x](addition-operator.md) – 傳回 x 的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="122c4-133">[-x](subtraction-operator.md) – 數值否定。</span><span class="sxs-lookup"><span data-stu-id="122c4-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="122c4-134">[\!x](logical-negation-operator.md) – 邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="122c4-134">[\!x](logical-negation-operator.md) – logical negation.</span></span>

<span data-ttu-id="122c4-135">[~x](bitwise-complement-operator.md) – 位元補數。</span><span class="sxs-lookup"><span data-stu-id="122c4-135">[~x](bitwise-complement-operator.md) – bitwise complement.</span></span>

<span data-ttu-id="122c4-136">[++x](increment-operator.md) – 前置遞增。</span><span class="sxs-lookup"><span data-stu-id="122c4-136">[++x](increment-operator.md) – prefix increment.</span></span> <span data-ttu-id="122c4-137">傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="122c4-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="122c4-138">[--x](decrement-operator.md) – 前置遞減。</span><span class="sxs-lookup"><span data-stu-id="122c4-138">[--x](decrement-operator.md) – prefix decrement.</span></span> <span data-ttu-id="122c4-139">更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。</span><span class="sxs-lookup"><span data-stu-id="122c4-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="122c4-140">[(T)x](invocation-operator.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="122c4-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="122c4-141">[await](../keywords/await.md) – 等候 `Task`。</span><span class="sxs-lookup"><span data-stu-id="122c4-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="122c4-142">[&x](and-operator.md) – 位址。</span><span class="sxs-lookup"><span data-stu-id="122c4-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="122c4-143">[\*x](multiplication-operator.md) – 取值。</span><span class="sxs-lookup"><span data-stu-id="122c4-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="122c4-144">乘法類運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-144">Multiplicative operators</span></span>

<span data-ttu-id="122c4-145">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-145">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-146">[x \* y](multiplication-operator.md) – 乘法。</span><span class="sxs-lookup"><span data-stu-id="122c4-146">[x \* y](multiplication-operator.md) – multiplication.</span></span>

<span data-ttu-id="122c4-147">[x / y](division-operator.md) – 除法。</span><span class="sxs-lookup"><span data-stu-id="122c4-147">[x / y](division-operator.md) – division.</span></span> <span data-ttu-id="122c4-148">如果運算元都是整數，則結果會截斷趨近於零的整數 (例如，`-7 / 2 is -3`)。</span><span class="sxs-lookup"><span data-stu-id="122c4-148">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="122c4-149">[x % y](remainder-operator.md) – 餘數。</span><span class="sxs-lookup"><span data-stu-id="122c4-149">[x % y](remainder-operator.md) – remainder.</span></span> <span data-ttu-id="122c4-150">如果運算元都是整數，這會傳回 x 除以 y 的餘數。</span><span class="sxs-lookup"><span data-stu-id="122c4-150">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="122c4-151">若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。</span><span class="sxs-lookup"><span data-stu-id="122c4-151">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="122c4-152">加法類運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-152">Additive operators</span></span>

<span data-ttu-id="122c4-153">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-153">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-154">[x + y](addition-operator.md) – 加法。</span><span class="sxs-lookup"><span data-stu-id="122c4-154">[x + y](addition-operator.md) – addition.</span></span>

<span data-ttu-id="122c4-155">[x – y](subtraction-operator.md) – 減法。</span><span class="sxs-lookup"><span data-stu-id="122c4-155">[x – y](subtraction-operator.md) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="122c4-156">移位運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-156">Shift operators</span></span>

<span data-ttu-id="122c4-157">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-157">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-158">[x <\<  y](left-shift-operator.md) – 位元向左移位並使用右邊的零填滿。</span><span class="sxs-lookup"><span data-stu-id="122c4-158">[x <\<  y](left-shift-operator.md) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="122c4-159">[x >> y](right-shift-operator.md) – 位元向右移位。</span><span class="sxs-lookup"><span data-stu-id="122c4-159">[x >> y](right-shift-operator.md) – shift bits right.</span></span> <span data-ttu-id="122c4-160">如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。</span><span class="sxs-lookup"><span data-stu-id="122c4-160">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="122c4-161">如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。</span><span class="sxs-lookup"><span data-stu-id="122c4-161">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="122c4-162">關係和類型測試運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-162">Relational and type-testing operators</span></span>

<span data-ttu-id="122c4-163">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-163">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-164">[x \< y](less-than-operator.md) – 小於 (如果 x 小於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="122c4-164">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="122c4-165">[x > y](greater-than-operator.md) – 大於 (如果 x 大於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="122c4-165">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="122c4-166">[x \<= y](less-than-equal-operator.md) – 小於或等於。</span><span class="sxs-lookup"><span data-stu-id="122c4-166">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="122c4-167">[x >= y](greater-than-equal-operator.md) – 大於或等於。</span><span class="sxs-lookup"><span data-stu-id="122c4-167">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="122c4-168">[is](../keywords/is.md) – 型別相容性。</span><span class="sxs-lookup"><span data-stu-id="122c4-168">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="122c4-169">如果評估的左運算元可以轉換成右運算元中指定的類型 (靜態類型)，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="122c4-169">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="122c4-170">[as](../keywords/as.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="122c4-170">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="122c4-171">傳回的左運算元轉型為右運算元指定的類型 (靜態類型)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="122c4-171">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="122c4-172">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-172">Equality operators</span></span>

<span data-ttu-id="122c4-173">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-173">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-174">[x == y](equality-comparison-operator.md) – 相等。</span><span class="sxs-lookup"><span data-stu-id="122c4-174">[x == y](equality-comparison-operator.md) – equality.</span></span> <span data-ttu-id="122c4-175">根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 (識別測試)。</span><span class="sxs-lookup"><span data-stu-id="122c4-175">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="122c4-176">不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。</span><span class="sxs-lookup"><span data-stu-id="122c4-176">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="122c4-177">[x != y](not-equal-operator.md) – 不等於。</span><span class="sxs-lookup"><span data-stu-id="122c4-177">[x != y](not-equal-operator.md) – not equal.</span></span> <span data-ttu-id="122c4-178">請參閱 `==` 的註解。</span><span class="sxs-lookup"><span data-stu-id="122c4-178">See comment for `==`.</span></span> <span data-ttu-id="122c4-179">如果類型多載 `==`，則它必須多載 `!=`。</span><span class="sxs-lookup"><span data-stu-id="122c4-179">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="122c4-180">邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-180">Logical AND operator</span></span>

<span data-ttu-id="122c4-181">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-181">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-182">[x & y](and-operator.md) – 邏輯或位元 AND。</span><span class="sxs-lookup"><span data-stu-id="122c4-182">[x & y](and-operator.md) – logical or bitwise AND.</span></span> <span data-ttu-id="122c4-183">您通常可以將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="122c4-183">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="122c4-184">邏輯 XOR 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-184">Logical XOR operator</span></span>

<span data-ttu-id="122c4-185">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-185">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-186">[x ^ y](xor-operator.md) – 邏輯或位元 XOR。</span><span class="sxs-lookup"><span data-stu-id="122c4-186">[x ^ y](xor-operator.md) – logical or bitwise XOR.</span></span> <span data-ttu-id="122c4-187">您通常可以將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="122c4-187">You can generally use this with integer types and `enum` types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="122c4-188">邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-188">Logical OR operator</span></span>

<span data-ttu-id="122c4-189">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-190">[x &#124; y](or-operator.md) – 邏輯或位元 OR。</span><span class="sxs-lookup"><span data-stu-id="122c4-190">[x &#124; y](or-operator.md) – logical or bitwise OR.</span></span> <span data-ttu-id="122c4-191">您通常可以將整數類型和 `enum` 類型搭配使用。</span><span class="sxs-lookup"><span data-stu-id="122c4-191">You can generally use this with integer types and `enum` types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="122c4-192">條件 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-192">Conditional AND operator</span></span>

<span data-ttu-id="122c4-193">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-193">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-194">[x && y](conditional-and-operator.md) – 邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="122c4-194">[x && y](conditional-and-operator.md) – logical AND.</span></span> <span data-ttu-id="122c4-195">如果第一個運算元評估為 false，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="122c4-195">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="122c4-196">條件 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-196">Conditional OR operator</span></span>

<span data-ttu-id="122c4-197">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-197">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-198">[x &#124;&#124; y](conditional-or-operator.md) – 邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="122c4-198">[x &#124;&#124; y](conditional-or-operator.md) – logical OR.</span></span> <span data-ttu-id="122c4-199">如果第一個運算元評估為 true，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="122c4-199">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="122c4-200">Null 聯合運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-200">Null-coalescing operator</span></span>

<span data-ttu-id="122c4-201">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-201">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-202">[x ?? y](null-coalescing-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="122c4-202">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="122c4-203">條件運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-203">Conditional operator</span></span>

<span data-ttu-id="122c4-204">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-204">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-205">[t ? x : y](conditional-operator.md) - 如果測試 `t` 評估為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="122c4-205">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="122c4-206">指派和 Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-206">Assignment and Lambda operators</span></span>

<span data-ttu-id="122c4-207">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="122c4-207">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="122c4-208">[x = y](assignment-operator.md) – 指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-208">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="122c4-209">[x += y](addition-assignment-operator.md) – 遞增。</span><span class="sxs-lookup"><span data-stu-id="122c4-209">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="122c4-210">將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-210">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="122c4-211">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以新增。</span><span class="sxs-lookup"><span data-stu-id="122c4-211">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="122c4-212">[x -= y](subtraction-assignment-operator.md) – 遞減。</span><span class="sxs-lookup"><span data-stu-id="122c4-212">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="122c4-213">將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-213">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="122c4-214">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以移除。</span><span class="sxs-lookup"><span data-stu-id="122c4-214">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler</span></span>

<span data-ttu-id="122c4-215">[x \*= y](multiplication-assignment-operator.md) – 乘法指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-215">[x \*= y](multiplication-assignment-operator.md) – multiplication assignment.</span></span> <span data-ttu-id="122c4-216">將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-216">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-217">[x /= y](division-assignment-operator.md) – 除法指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-217">[x /= y](division-assignment-operator.md) – division assignment.</span></span> <span data-ttu-id="122c4-218">將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-218">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-219">[x %= y](remainder-assignment-operator.md) – 餘數指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-219">[x %= y](remainder-assignment-operator.md) – remainder assignment.</span></span> <span data-ttu-id="122c4-220">將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-220">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-221">[x &= y](and-assignment-operator.md) – AND 指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-221">[x &= y](and-assignment-operator.md) – AND assignment.</span></span> <span data-ttu-id="122c4-222">將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-222">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-223">[x &#124;= y](or-assignment-operator.md) – OR 指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-223">[x &#124;= y](or-assignment-operator.md) – OR assignment.</span></span> <span data-ttu-id="122c4-224">將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-224">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-225">[x ^= y](xor-assignment-operator.md) – XOR 指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-225">[x ^= y](xor-assignment-operator.md) – XOR assignment.</span></span> <span data-ttu-id="122c4-226">將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-226">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-227">[x <<= y](left-shift-assignment-operator.md) – 左移指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-227">[x <<= y](left-shift-assignment-operator.md) – left-shift assignment.</span></span> <span data-ttu-id="122c4-228">將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-228">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-229">[x >>= y](right-shift-assignment-operator.md) – 右移指派。</span><span class="sxs-lookup"><span data-stu-id="122c4-229">[x >>= y](right-shift-assignment-operator.md) – right-shift assignment.</span></span> <span data-ttu-id="122c4-230">將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="122c4-230">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="122c4-231">[=>](lambda-operator.md) – lambda 宣告。</span><span class="sxs-lookup"><span data-stu-id="122c4-231">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="arithmetic-overflow"></a><span data-ttu-id="122c4-232">算術溢位</span><span class="sxs-lookup"><span data-stu-id="122c4-232">Arithmetic overflow</span></span>

<span data-ttu-id="122c4-233">算術運算子 ([+](addition-operator.md)、[-](subtraction-operator.md)、[\*](multiplication-operator.md)、[/](division-operator.md)) 可產生數值型別所涉及之可能值範圍以外的結果。</span><span class="sxs-lookup"><span data-stu-id="122c4-233">The arithmetic operators ([+](addition-operator.md), [-](subtraction-operator.md), [\*](multiplication-operator.md), [/](division-operator.md)) can produce results that are outside the range of possible values for the numeric type involved.</span></span> <span data-ttu-id="122c4-234">您應該參考特定運算子一節以取得詳細資料，但一般而言：</span><span class="sxs-lookup"><span data-stu-id="122c4-234">You should refer to the section on a particular operator for details, but in general:</span></span>

- <span data-ttu-id="122c4-235">整數算術溢位可能會擲回 <xref:System.OverflowException> 或捨棄結果的最高有效位元。</span><span class="sxs-lookup"><span data-stu-id="122c4-235">Integer arithmetic overflow either throws an <xref:System.OverflowException> or discards the most significant bits of the result.</span></span> <span data-ttu-id="122c4-236">整數除以零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="122c4-236">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

   <span data-ttu-id="122c4-237">發生整數溢位時，會發生的事取決於執行內容，可以是 [checked 或 unchecked](../keywords/checked-and-unchecked.md)。</span><span class="sxs-lookup"><span data-stu-id="122c4-237">When integer overflow occurs, what happens depends on the execution context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md).</span></span> <span data-ttu-id="122c4-238">在 checked 內容中，會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="122c4-238">In a checked context, an <xref:System.OverflowException> is thrown.</span></span> <span data-ttu-id="122c4-239">在 unchecked 內容中，會捨棄結果的最高有效位元並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="122c4-239">In an unchecked context, the most significant bits of the result are discarded and execution continues.</span></span> <span data-ttu-id="122c4-240">因此，C# 可讓您選擇處理或忽略溢位。</span><span class="sxs-lookup"><span data-stu-id="122c4-240">Thus, C# gives you the choice of handling or ignoring overflow.</span></span> <span data-ttu-id="122c4-241">根據預設，*unchecked* 內容中會發生算術運算。</span><span class="sxs-lookup"><span data-stu-id="122c4-241">By default, arithmetic operations occur in an *unchecked* context.</span></span>

   <span data-ttu-id="122c4-242">除了算術運算之外，整數類資料型別至整數類資料型別的轉換可能會造成溢位 (例如，當您將 [long](../keywords/long.md) 轉換為 [int](../keywords/int.md) 時)，且有可能受 checked 或 unchecked 執行的限制。</span><span class="sxs-lookup"><span data-stu-id="122c4-242">In addition to the arithmetic operations, integral-type to integral-type casts can cause overflow (such as when you cast a [long](../keywords/long.md) to an [int](../keywords/int.md)), and are subject to checked or unchecked execution.</span></span> <span data-ttu-id="122c4-243">不過，位元運算子和移位運算子永遠不會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="122c4-243">However, bitwise operators and shift operators never cause overflow.</span></span>

- <span data-ttu-id="122c4-244">浮點算術溢位或除以零永遠不會擲回例外狀況，因為浮點類型以 IEEE 754 為基礎，所以具有代表無限與 NaN (而非數字) 的佈建。</span><span class="sxs-lookup"><span data-stu-id="122c4-244">Floating-point arithmetic overflow or division by zero never throws an exception, because floating-point types are based on IEEE 754 and so have provisions for representing infinity and NaN (Not a Number).</span></span>

- <span data-ttu-id="122c4-245">[十進位](../keywords/decimal.md)算術溢位一律會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="122c4-245">[Decimal](../keywords/decimal.md) arithmetic overflow always throws an <xref:System.OverflowException>.</span></span> <span data-ttu-id="122c4-246">十進位除以零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="122c4-246">Decimal division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="122c4-247">另請參閱</span><span class="sxs-lookup"><span data-stu-id="122c4-247">See also</span></span>

- [<span data-ttu-id="122c4-248">C# 參考</span><span class="sxs-lookup"><span data-stu-id="122c4-248">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="122c4-249">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="122c4-249">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="122c4-250">C#</span><span class="sxs-lookup"><span data-stu-id="122c4-250">C#</span></span>](../../index.md)
- [<span data-ttu-id="122c4-251">多載運算子</span><span class="sxs-lookup"><span data-stu-id="122c4-251">Overloadable Operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="122c4-252">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="122c4-252">C# Keywords</span></span>](../keywords/index.md)