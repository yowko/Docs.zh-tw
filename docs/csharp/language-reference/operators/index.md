---
title: C# 運算子
ms.date: 04/30/2019
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
ms.openlocfilehash: c6b83779a630c6d797968d79635793e229751f93
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833265"
---
# <a name="c-operators"></a><span data-ttu-id="421a3-102">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-102">C# operators</span></span>

<span data-ttu-id="421a3-103">C# 提供內建型別支援的數個預先定義運算子。</span><span class="sxs-lookup"><span data-stu-id="421a3-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="421a3-104">例如，[算術運算子](arithmetic-operators.md)會執行含內建數值型別運算元的算術運算，而[布林邏輯運算子](boolean-logical-operators.md)會執行含 [bool](../keywords/bool.md) 運算元的邏輯運算。</span><span class="sxs-lookup"><span data-stu-id="421a3-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="421a3-105">使用者定義型別可以多載特定運算子，以定義該型別運算元的對應行為。</span><span class="sxs-lookup"><span data-stu-id="421a3-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="421a3-106">如需詳細資訊，請參閱[運算子](../keywords/operator.md)關鍵字文章。</span><span class="sxs-lookup"><span data-stu-id="421a3-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="421a3-107">下面各節列出 C# 運算子，從最高優先順序開始列到最低。</span><span class="sxs-lookup"><span data-stu-id="421a3-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="421a3-108">每個區段中的運算子會共用相同的優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="421a3-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="421a3-109">主要運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-109">Primary operators</span></span>

<span data-ttu-id="421a3-110">這些是最高優先順序的運算子。</span><span class="sxs-lookup"><span data-stu-id="421a3-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="421a3-111">[x.y](member-access-operators.md#member-access-operator-) – 成員存取。</span><span class="sxs-lookup"><span data-stu-id="421a3-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="421a3-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null 條件成員存取。</span><span class="sxs-lookup"><span data-stu-id="421a3-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="421a3-113">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="421a3-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="421a3-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - Null 條件式陣列項目，或型別索引子存取。</span><span class="sxs-lookup"><span data-stu-id="421a3-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="421a3-115">如果左運算元評估為 `null`，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="421a3-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="421a3-116">[f(x)](member-access-operators.md#invocation-operator-) – 方法呼叫，或委派叫用。</span><span class="sxs-lookup"><span data-stu-id="421a3-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="421a3-117">[&#91;x&#93;](member-access-operators.md#indexer-operator-) – 陣列項目，或型別索引子存取。</span><span class="sxs-lookup"><span data-stu-id="421a3-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="421a3-118">[x++](arithmetic-operators.md#increment-operator-) – 後置遞增。</span><span class="sxs-lookup"><span data-stu-id="421a3-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="421a3-119">傳回 x 的值，然後利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="421a3-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="421a3-120">[x--](arithmetic-operators.md#decrement-operator---) – 後置遞減。</span><span class="sxs-lookup"><span data-stu-id="421a3-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="421a3-121">傳回 x 的值，然後利用小於 x 值的值 (通常會減去整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="421a3-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="421a3-122">[new](../keywords/new-operator.md) – 型別執行個體化。</span><span class="sxs-lookup"><span data-stu-id="421a3-122">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="421a3-123">[typeof](../keywords/typeof.md) - 傳回代表運算元的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="421a3-123">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="421a3-124">[checked](../keywords/checked.md) – 啟動整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="421a3-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="421a3-125">[unchecked](../keywords/unchecked.md) – 停用整數作業的溢位檢查。</span><span class="sxs-lookup"><span data-stu-id="421a3-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="421a3-126">這是預設編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="421a3-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="421a3-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) - 產生類型 T 的預設值。</span><span class="sxs-lookup"><span data-stu-id="421a3-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="421a3-128">[nameof](../keywords/nameof.md) - 取得變數、型別或成員的簡單 (未限定) 名稱，作為常數字串。</span><span class="sxs-lookup"><span data-stu-id="421a3-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="421a3-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – 宣告並傳回委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="421a3-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="421a3-130">[sizeof](../keywords/sizeof.md) – 傳回型別運算元的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="421a3-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="421a3-131">[stackalloc](stackalloc.md) -　配置堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="421a3-131">[stackalloc](stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="421a3-132">[->](pointer-related-operators.md#pointer-member-access-operator--) - 指標間接取值結合成員存取。</span><span class="sxs-lookup"><span data-stu-id="421a3-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="421a3-133">一元運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-133">Unary operators</span></span>

<span data-ttu-id="421a3-134">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-135">[+x](addition-operator.md) – 傳回 x 的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="421a3-136">[-x](subtraction-operator.md) – 數值否定。</span><span class="sxs-lookup"><span data-stu-id="421a3-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="421a3-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – 邏輯否定。</span><span class="sxs-lookup"><span data-stu-id="421a3-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="421a3-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – 位元補數。</span><span class="sxs-lookup"><span data-stu-id="421a3-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="421a3-139">[++x](arithmetic-operators.md#increment-operator-) – 前置遞增。</span><span class="sxs-lookup"><span data-stu-id="421a3-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="421a3-140">傳回 x 的值之前，利用大於 x 值的值 (通常會加上整數 1) 更新儲存位置。</span><span class="sxs-lookup"><span data-stu-id="421a3-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="421a3-141">[--x](arithmetic-operators.md#decrement-operator---) – 前置遞減。</span><span class="sxs-lookup"><span data-stu-id="421a3-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="421a3-142">更新儲存體位置之後，傳回 x 減一的 x 值 (通常減去整數 1)。</span><span class="sxs-lookup"><span data-stu-id="421a3-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="421a3-143">[(T)x](invocation-operator.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="421a3-143">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="421a3-144">[await](../keywords/await.md) – 等候 `Task`。</span><span class="sxs-lookup"><span data-stu-id="421a3-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="421a3-145">[&x](pointer-related-operators.md#address-of-operator-) - 變數的位址。</span><span class="sxs-lookup"><span data-stu-id="421a3-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="421a3-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) - 指標間接取值或取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="421a3-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="421a3-147">[true 運算子](true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true` 以指出運算元必然為 true。</span><span class="sxs-lookup"><span data-stu-id="421a3-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="421a3-148">[false 運算子](true-false-operators.md) - 傳回 [bool](../keywords/bool.md) 值 `true`，以指出運算元必然為 false。</span><span class="sxs-lookup"><span data-stu-id="421a3-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="421a3-149">乘法類運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-149">Multiplicative operators</span></span>

<span data-ttu-id="421a3-150">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – 乘法。</span><span class="sxs-lookup"><span data-stu-id="421a3-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="421a3-152">[x / y](arithmetic-operators.md#division-operator-) – 除法。</span><span class="sxs-lookup"><span data-stu-id="421a3-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="421a3-153">如果運算元都是整數，則結果會截斷趨近於零的整數 (例如，`-7 / 2 is -3`)。</span><span class="sxs-lookup"><span data-stu-id="421a3-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="421a3-154">[x % y](arithmetic-operators.md#remainder-operator-) – 餘數。</span><span class="sxs-lookup"><span data-stu-id="421a3-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="421a3-155">如果運算元都是整數，這會傳回 x 除以 y 的餘數。</span><span class="sxs-lookup"><span data-stu-id="421a3-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="421a3-156">若為 `q = x / y` 和 `r = x % y`，則為 `x = q * y + r`。</span><span class="sxs-lookup"><span data-stu-id="421a3-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="421a3-157">加法類運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-157">Additive operators</span></span>

<span data-ttu-id="421a3-158">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-159">[x + y](arithmetic-operators.md#addition-operator-) – 加法。</span><span class="sxs-lookup"><span data-stu-id="421a3-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="421a3-160">[x – y](arithmetic-operators.md#subtraction-operator--) – 減法。</span><span class="sxs-lookup"><span data-stu-id="421a3-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="421a3-161">移位運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-161">Shift operators</span></span>

<span data-ttu-id="421a3-162">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – 位元向左移位並使用右邊的零填滿。</span><span class="sxs-lookup"><span data-stu-id="421a3-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="421a3-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – 位元向右移位。</span><span class="sxs-lookup"><span data-stu-id="421a3-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="421a3-165">如果左運算元是 `int` 或 `long`，則以正負號位元填入左位元。</span><span class="sxs-lookup"><span data-stu-id="421a3-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="421a3-166">如果左運算元是 `uint` 或 `ulong`，則以零填入左位元。</span><span class="sxs-lookup"><span data-stu-id="421a3-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="421a3-167">關係和類型測試運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-167">Relational and type-testing operators</span></span>

<span data-ttu-id="421a3-168">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-169">[x \< y](comparison-operators.md#less-than-operator-) – 小於 (如果 x 小於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="421a3-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="421a3-170">[x > y](comparison-operators.md#greater-than-operator-) – 大於 (如果 x 大於 y，則為 true)。</span><span class="sxs-lookup"><span data-stu-id="421a3-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="421a3-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – 小於或等於。</span><span class="sxs-lookup"><span data-stu-id="421a3-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="421a3-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – 大於或等於。</span><span class="sxs-lookup"><span data-stu-id="421a3-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="421a3-173">[is](../keywords/is.md) – 型別相容性。</span><span class="sxs-lookup"><span data-stu-id="421a3-173">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="421a3-174">如果評估的左運算元可以轉換成右運算元中指定的類型 (靜態類型)，則傳回 true。</span><span class="sxs-lookup"><span data-stu-id="421a3-174">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="421a3-175">[as](../keywords/as.md) – 型別轉換。</span><span class="sxs-lookup"><span data-stu-id="421a3-175">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="421a3-176">傳回的左運算元轉型為右運算元指定的類型 (靜態類型)，但 `as` 傳回 `null`，其中 `(T)x` 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="421a3-176">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="421a3-177">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-177">Equality operators</span></span>

<span data-ttu-id="421a3-178">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-179">[x == y](equality-operators.md#equality-operator-) – 相等。</span><span class="sxs-lookup"><span data-stu-id="421a3-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="421a3-180">根據預設，對於 `string` 以外的參考類型，這會傳回參考相等 (識別測試)。</span><span class="sxs-lookup"><span data-stu-id="421a3-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="421a3-181">不過，類型可以多載 `==`，因此如果您的目的是要測試識別，最好使用 `object` 上的 `ReferenceEquals` 方法。</span><span class="sxs-lookup"><span data-stu-id="421a3-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="421a3-182">[x != y](equality-operators.md#inequality-operator-) – 不等於。</span><span class="sxs-lookup"><span data-stu-id="421a3-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="421a3-183">請參閱 `==` 的註解。</span><span class="sxs-lookup"><span data-stu-id="421a3-183">See comment for `==`.</span></span> <span data-ttu-id="421a3-184">如果類型多載 `==`，則它必須多載 `!=`。</span><span class="sxs-lookup"><span data-stu-id="421a3-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="421a3-185">邏輯 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-185">Logical AND operator</span></span>

<span data-ttu-id="421a3-186">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-187">`x & y` – `bool` 運算元的 [邏輯 AND](boolean-logical-operators.md#logical-and-operator-)，或整數型別之運算元的 [位元邏輯 AND](bitwise-and-shift-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="421a3-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="421a3-188">邏輯 XOR 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-188">Logical XOR operator</span></span>

<span data-ttu-id="421a3-189">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-190">`x ^ y` – `bool` 運算元的 [邏輯 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-)，或整數型別之運算元的 [位元邏輯 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="421a3-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="421a3-191">邏輯 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-191">Logical OR operator</span></span>

<span data-ttu-id="421a3-192">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-193">`x | y` – `bool` 運算元的 [邏輯 OR](boolean-logical-operators.md#logical-or-operator-)，或整數型別之運算元的 [位元邏輯 OR](bitwise-and-shift-operators.md#logical-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="421a3-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="421a3-194">條件 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-194">Conditional AND operator</span></span>

<span data-ttu-id="421a3-195">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 邏輯 AND。</span><span class="sxs-lookup"><span data-stu-id="421a3-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="421a3-197">如果第一個運算元評估為 false，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="421a3-197">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="421a3-198">條件 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-198">Conditional OR operator</span></span>

<span data-ttu-id="421a3-199">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 邏輯 OR。</span><span class="sxs-lookup"><span data-stu-id="421a3-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="421a3-201">如果第一個運算元評估為 true，C# 就不會評估第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="421a3-201">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="421a3-202">Null 聯合運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-202">Null-coalescing operator</span></span>

<span data-ttu-id="421a3-203">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-204">[x ?? y](null-coalescing-operator.md) – 如果非 `null` 則傳回 `x`，否則會傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="421a3-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="421a3-205">條件運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-205">Conditional operator</span></span>

<span data-ttu-id="421a3-206">此運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-207">[t ? x : y](conditional-operator.md) - 如果測試 `t` 評估為 true，則會評估並傳回 `x`，否則會評估並傳回 `y`。</span><span class="sxs-lookup"><span data-stu-id="421a3-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="421a3-208">指派和 Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-208">Assignment and lambda operators</span></span>

<span data-ttu-id="421a3-209">這些運算子具有的優先順序高於下一個區段且低於前一個區段。</span><span class="sxs-lookup"><span data-stu-id="421a3-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="421a3-210">[x = y](assignment-operator.md) – 指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="421a3-211">[x += y](arithmetic-operators.md#compound-assignment) – 遞增。</span><span class="sxs-lookup"><span data-stu-id="421a3-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="421a3-212">將 `y` 的值加上 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="421a3-213">如果 `x` 指定 [event](../keywords/event.md)，則 `y` 必須是 C# 視為事件處理常式新增的適當方法。</span><span class="sxs-lookup"><span data-stu-id="421a3-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="421a3-214">[x -= y](arithmetic-operators.md#compound-assignment) – 遞減。</span><span class="sxs-lookup"><span data-stu-id="421a3-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="421a3-215">將 `x` 的值減去 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="421a3-216">如果 `x` 指定 [event](../keywords/event.md)，則 `y` 必須是 C# 視為事件處理常式移除的適當方法。</span><span class="sxs-lookup"><span data-stu-id="421a3-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="421a3-217">[x \*= y](arithmetic-operators.md#compound-assignment) – 乘法指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="421a3-218">將 `y` 的值乘以 `x` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-219">[x /= y](arithmetic-operators.md#compound-assignment) – 除法指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="421a3-220">將 `x` 的值除以 `y` 的值，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-221">[x %= y](arithmetic-operators.md#compound-assignment) – 餘數指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="421a3-222">將 `x` 的值除以 `y` 的值，將餘數儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND 指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="421a3-224">將 `y` 的值和 `x` 的值進行 AND 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR 指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="421a3-226">將 `y` 的值和 `x` 的值進行 OR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR 指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="421a3-228">將 `y` 的值和 `x` 的值進行 XOR 處理，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – 左移指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="421a3-230">將 `x` 的值向左移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – 右移指派。</span><span class="sxs-lookup"><span data-stu-id="421a3-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="421a3-232">將 `x` 的值向右移 `y` 個空格，將結果儲存在 `x`，並傳回新的值。</span><span class="sxs-lookup"><span data-stu-id="421a3-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="421a3-233">[=>](lambda-operator.md) – lambda 宣告。</span><span class="sxs-lookup"><span data-stu-id="421a3-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="421a3-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="421a3-234">See also</span></span>

- [<span data-ttu-id="421a3-235">C# 參考</span><span class="sxs-lookup"><span data-stu-id="421a3-235">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="421a3-236">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="421a3-236">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="421a3-237">C#</span><span class="sxs-lookup"><span data-stu-id="421a3-237">C#</span></span>](../../index.md)
- [<span data-ttu-id="421a3-238">多載運算子</span><span class="sxs-lookup"><span data-stu-id="421a3-238">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="421a3-239">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="421a3-239">C# Keywords</span></span>](../keywords/index.md)
