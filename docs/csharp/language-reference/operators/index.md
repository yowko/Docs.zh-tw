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
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977375"
---
# <a name="c-operators"></a><span data-ttu-id="bd9b8-102">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-102">C# operators</span></span>

<span data-ttu-id="bd9b8-103">C# 提供許多運算子，也就是指定要在運算式中執行哪些作業 (數學、索引化、函式呼叫等) 的符號。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-103">C# provides many operators, which are symbols that specify which operations (math, indexing, function call, etc.) to perform in an expression.</span></span> <span data-ttu-id="bd9b8-104">您可以[多載](../../programming-guide/statements-expressions-operators/overloadable-operators.md)許多運算子，以便在套用至使用者定義型別時變更它們的意義。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-104">You can [overload](../../programming-guide/statements-expressions-operators/overloadable-operators.md) many operators to change their meaning when applied to a user-defined type.</span></span>

<span data-ttu-id="bd9b8-105">列舉 (`enum`) 型別上通常會允許整數型別上的作業 (例如 `==`、`!=`、`<`、`>`、`&`、`|`)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-105">Operations on integral types (such as `==`, `!=`, `<`, `>`, `&`, `|`) are generally allowed on enumeration (`enum`) types.</span></span>

<span data-ttu-id="bd9b8-106">下列區段列出 C# 運算子，從最高優先順序開始到最低優先順序。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-106">The sections below list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="bd9b8-107">每個區段中的運算子會共用相同的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-107">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="bd9b8-108">主要運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-108">Primary operators</span></span>

<span data-ttu-id="bd9b8-109">這些是最高優先順序的運算子。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-109">These are the highest precedence operators.</span></span>

<span data-ttu-id="bd9b8-110">[x.y](member-access-operator.md) – 成員存取。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-110">[x.y](member-access-operator.md) – member access.</span></span>

<span data-ttu-id="bd9b8-111">[x?.y](null-conditional-operators.md) – null 條件成員存取。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-111">[x?.y](null-conditional-operators.md) – null conditional member access.</span></span> <span data-ttu-id="bd9b8-112">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-112">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="bd9b8-113">[x?[y]](null-conditional-operators.md) - null 條件式索引存取。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-113">[x?[y]](null-conditional-operators.md) - null conditional index access.</span></span> <span data-ttu-id="bd9b8-114">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-114">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="bd9b8-115">[f(x)](invocation-operator.md) – 函式引動過程。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-115">[f(x)](invocation-operator.md) – function invocation.</span></span>

<span data-ttu-id="bd9b8-116">[a&#91;x&#93;](index-operator.md) – 彙總物件索引化。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-116">[a&#91;x&#93;](index-operator.md) – aggregate object indexing.</span></span>

<span data-ttu-id="bd9b8-117">[x++](arithmetic-operators.md#increment-operator-) – 後置遞增。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-117">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="bd9b8-118">傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-118">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="bd9b8-119">[x--](arithmetic-operators.md#decrement-operator---) – 後置遞減。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-119">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="bd9b8-120">傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-120">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="bd9b8-121">[new](../keywords/new-operator.md) – 型別執行個體化。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-121">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="bd9b8-122">[typeof](../keywords/typeof.md) - 傳回代表運算元的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-122">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="bd9b8-123">[checked](../keywords/checked.md) – 啟動整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-123">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="bd9b8-124">[unchecked](../keywords/unchecked.md) – 停用整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-124">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="bd9b8-125">這是預設編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-125">This is the default compiler behavior.</span></span>

<span data-ttu-id="bd9b8-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 產生類型 T 的預設值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-126">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="bd9b8-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-127">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="bd9b8-128">[sizeof](../keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-128">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="bd9b8-129">[->](dereference-operator.md) – 指標取值結合成員存取。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-129">[->](dereference-operator.md) – pointer dereferencing combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="bd9b8-130">一元運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-130">Unary operators</span></span>

<span data-ttu-id="bd9b8-131">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-131">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-132">[+x](addition-operator.md) – 傳回 x 的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-132">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="bd9b8-133">[-x](subtraction-operator.md) – 數值否定。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-133">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="bd9b8-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – 邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-134">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="bd9b8-135">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – 位元補數。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-135">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="bd9b8-136">[++x](arithmetic-operators.md#increment-operator-) – 前置遞增。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-136">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="bd9b8-137">傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-137">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="bd9b8-138">[--x](arithmetic-operators.md#decrement-operator---) – 前置遞減。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-138">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="bd9b8-139">更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-139">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="bd9b8-140">[(T)x](invocation-operator.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-140">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="bd9b8-141">[await](../keywords/await.md) – 等候 `Task`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-141">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="bd9b8-142">[&x](and-operator.md) – 位址。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-142">[&x](and-operator.md) – address of.</span></span>

<span data-ttu-id="bd9b8-143">[\*x](multiplication-operator.md) – 取值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-143">[\*x](multiplication-operator.md) – dereferencing.</span></span>

<span data-ttu-id="bd9b8-144">[true 運算子](../keywords/true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true` 以指出運算元必然為 true。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-144">[true operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="bd9b8-145">[false 運算子](../keywords/true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true`，以指出運算元必然為 false。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-145">[false operator](../keywords/true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="bd9b8-146">乘法類運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-146">Multiplicative operators</span></span>

<span data-ttu-id="bd9b8-147">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-147">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – 乘法。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-148">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="bd9b8-149">[x / y](arithmetic-operators.md#division-operator-) – 除法。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-149">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="bd9b8-150">如果運算元都是整數，則結果會截斷趨近於零的整數 (例如，`-7 / 2 is -3`)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-150">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="bd9b8-151">[x % y](arithmetic-operators.md#remainder-operator-) – 餘數。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-151">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="bd9b8-152">如果運算元都是整數，這會傳回 x 除以 y 的餘數。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-152">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="bd9b8-153">若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-153">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="bd9b8-154">加法類運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-154">Additive operators</span></span>

<span data-ttu-id="bd9b8-155">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-155">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-156">[x + y](arithmetic-operators.md#addition-operator-) – 加法。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-156">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="bd9b8-157">[x – y](arithmetic-operators.md#subtraction-operator--) – 減法。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-157">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="bd9b8-158">移位運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-158">Shift operators</span></span>

<span data-ttu-id="bd9b8-159">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-159">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-160">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – 位元向左移位並使用右邊的零填滿。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-160">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="bd9b8-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – 位元向右移位。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-161">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="bd9b8-162">如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-162">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="bd9b8-163">如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-163">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="bd9b8-164">關係和類型測試運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-164">Relational and type-testing operators</span></span>

<span data-ttu-id="bd9b8-165">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-165">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-166">[x \< y](less-than-operator.md) – 小於 (如果 x 小於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-166">[x \< y](less-than-operator.md) – less than (true if x is less than y).</span></span>

<span data-ttu-id="bd9b8-167">[x > y](greater-than-operator.md) – 大於 (如果 x 大於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-167">[x > y](greater-than-operator.md) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="bd9b8-168">[x \<= y](less-than-equal-operator.md) – 小於或等於。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-168">[x \<= y](less-than-equal-operator.md) – less than or equal to.</span></span>

<span data-ttu-id="bd9b8-169">[x >= y](greater-than-equal-operator.md) – 大於或等於。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-169">[x >= y](greater-than-equal-operator.md) – greater than or equal to.</span></span>

<span data-ttu-id="bd9b8-170">[is](../keywords/is.md) – 型別相容性。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-170">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="bd9b8-171">如果評估的左運算元可以轉換成右運算元中指定的類型 (靜態類型)，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-171">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="bd9b8-172">[as](../keywords/as.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-172">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="bd9b8-173">傳回的左運算元轉型為右運算元指定的類型 (靜態類型)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-173">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="bd9b8-174">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-174">Equality operators</span></span>

<span data-ttu-id="bd9b8-175">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-175">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-176">[x == y](equality-operators.md#equality-operator-) – 相等。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-176">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="bd9b8-177">根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 (識別測試)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-177">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="bd9b8-178">不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-178">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="bd9b8-179">[x != y](equality-operators.md#inequality-operator-) – 不等於。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-179">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="bd9b8-180">請參閱 `==` 的註解。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-180">See comment for `==`.</span></span> <span data-ttu-id="bd9b8-181">如果類型多載 `==`，則它必須多載 `!=`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-181">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="bd9b8-182">邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-182">Logical AND operator</span></span>

<span data-ttu-id="bd9b8-183">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-183">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-184">`x & y` – `bool` 運算元的 [邏輯 AND](boolean-logical-operators.md#logical-and-operator-)，或整數型別之運算元的 [位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-184">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="bd9b8-185">邏輯 XOR 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-185">Logical XOR operator</span></span>

<span data-ttu-id="bd9b8-186">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-187">`x ^ y` – `bool` 運算元的 [邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-)，或整數型別之運算元的 [位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-187">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="bd9b8-188">邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-188">Logical OR operator</span></span>

<span data-ttu-id="bd9b8-189">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-190">`x | y` – `bool` 運算元的 [邏輯 OR](boolean-logical-operators.md#logical-or-operator-)，或整數型別之運算元的 [位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-190">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="bd9b8-191">條件 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-191">Conditional AND operator</span></span>

<span data-ttu-id="bd9b8-192">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-193">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-193">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="bd9b8-194">如果第一個運算元評估為 false，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-194">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="bd9b8-195">條件 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-195">Conditional OR operator</span></span>

<span data-ttu-id="bd9b8-196">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-196">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-197">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-197">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="bd9b8-198">如果第一個運算元評估為 true，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-198">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="bd9b8-199">Null 聯合運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-199">Null-coalescing operator</span></span>

<span data-ttu-id="bd9b8-200">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-200">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-201">[x ?? y](null-coalescing-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-201">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="bd9b8-202">條件運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-202">Conditional operator</span></span>

<span data-ttu-id="bd9b8-203">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-204">[t ? x : y](conditional-operator.md) - 如果測試 `t` 評估為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-204">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="bd9b8-205">指派和 Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-205">Assignment and Lambda operators</span></span>

<span data-ttu-id="bd9b8-206">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-206">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="bd9b8-207">[x = y](assignment-operator.md) – 指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-207">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="bd9b8-208">[x += y](addition-assignment-operator.md) – 遞增。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-208">[x += y](addition-assignment-operator.md) – increment.</span></span> <span data-ttu-id="bd9b8-209">將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-209">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="bd9b8-210">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以新增。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-210">If `x` designates an `event`, then `y` must be an appropriate function that C# adds as an event handler.</span></span>

<span data-ttu-id="bd9b8-211">[x -= y](subtraction-assignment-operator.md) – 遞減。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-211">[x -= y](subtraction-assignment-operator.md) – decrement.</span></span> <span data-ttu-id="bd9b8-212">將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-212">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="bd9b8-213">如果 `x` 指定 `event`，則 `y` 必須是適當的函式，其中會將 C# 視為事件處理常式予以移除。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-213">If `x` designates an `event`, then `y` must be an appropriate function that C# removes as an event handler.</span></span>

<span data-ttu-id="bd9b8-214">[x \*= y](arithmetic-operators.md#compound-assignment) – 乘法指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-214">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="bd9b8-215">將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-215">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-216">[x /= y](arithmetic-operators.md#compound-assignment) – 除法指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-216">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="bd9b8-217">將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-217">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-218">[x %= y](arithmetic-operators.md#compound-assignment) – 餘數指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-218">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="bd9b8-219">將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-219">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-220">[x &= y](boolean-logical-operators.md#compound-assignment) – AND 指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-220">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="bd9b8-221">將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-221">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR 指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-222">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="bd9b8-223">將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-223">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-224">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR 指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-224">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="bd9b8-225">將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-225">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-226">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – 左移指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-226">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="bd9b8-227">將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-227">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-228">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – 右移指派。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-228">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="bd9b8-229">將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-229">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="bd9b8-230">[=>](lambda-operator.md) – lambda 宣告。</span><span class="sxs-lookup"><span data-stu-id="bd9b8-230">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd9b8-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd9b8-231">See also</span></span>

- [<span data-ttu-id="bd9b8-232">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bd9b8-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bd9b8-233">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bd9b8-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bd9b8-234">C#</span><span class="sxs-lookup"><span data-stu-id="bd9b8-234">C#</span></span>](../../index.md)
- [<span data-ttu-id="bd9b8-235">多載運算子</span><span class="sxs-lookup"><span data-stu-id="bd9b8-235">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="bd9b8-236">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bd9b8-236">C# Keywords</span></span>](../keywords/index.md)
