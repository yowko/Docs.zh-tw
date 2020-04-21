---
title: 算術運算子 - C# 參考
description: 了解可使用數字型別執行乘法、除法、餘數、加法和減法運算的 C# 運算子。
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738739"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="ccd9a-103">算術運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ccd9a-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="ccd9a-104">以下運算子使用數值類型的操作數執行算術運算:</span><span class="sxs-lookup"><span data-stu-id="ccd9a-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="ccd9a-105">一元[`++`(增量)、(](#increment-operator-)[`--`遞減)、(](#decrement-operator---)[`+`加號)](#unary-plus-and-minus-operators)和[`-`(減)](#unary-plus-and-minus-operators)運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="ccd9a-106">二進位[`*`(乘法),(](#multiplication-operator-)[`/`除法),(](#division-operator-)[`+`](#addition-operator-)[`%`](#remainder-operator-)[`-`reta)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="ccd9a-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="ccd9a-107">這些運算符由所有[積分](../builtin-types/integral-numeric-types.md)和[浮點](../builtin-types/floating-point-numeric-types.md)數值類型支援。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="ccd9a-108">遞增運算子 ++</span><span class="sxs-lookup"><span data-stu-id="ccd9a-108">Increment operator ++</span></span>

<span data-ttu-id="ccd9a-109">一元遞增運算子 `++` 的運算元遞增量為 1。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="ccd9a-110">運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../programming-guide/indexers/index.md)存取。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="ccd9a-111">遞增運算子支援兩種形式：後置遞增運算子 `x++` 和前置遞增運算子 `++x`。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="ccd9a-112">後置遞增運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-112">Postfix increment operator</span></span>

<span data-ttu-id="ccd9a-113">`x++` 的結果為運算「之前」 \*\* 的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="ccd9a-114">前置遞增運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-114">Prefix increment operator</span></span>

<span data-ttu-id="ccd9a-115">`++x` 的結果為運算「之後」 \*\* 的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="ccd9a-116">遞減運算子 --</span><span class="sxs-lookup"><span data-stu-id="ccd9a-116">Decrement operator --</span></span>

<span data-ttu-id="ccd9a-117">一元遞減運算子 (`--`) 的運算元遞減量為 1。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="ccd9a-118">運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../programming-guide/indexers/index.md)存取。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="ccd9a-119">遞減運算子支援兩種形式：後置遞減運算子 `x--` 和前置遞減運算子 `--x`。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="ccd9a-120">後置遞減運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-120">Postfix decrement operator</span></span>

<span data-ttu-id="ccd9a-121">`x--` 的結果為運算「之前」 \*\* 的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="ccd9a-122">前置遞減運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-122">Prefix decrement operator</span></span>

<span data-ttu-id="ccd9a-123">`--x` 的結果為運算「之後」 \*\* 的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="ccd9a-124">一元加號和減號運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-124">Unary plus and minus operators</span></span>

<span data-ttu-id="ccd9a-125">一元 `+` 運算子會傳回其運算元的值。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="ccd9a-126">一元 `-` 運算子會計算其運算元的負數值。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="ccd9a-127">[ulong](../builtin-types/integral-numeric-types.md)類型不支援一`-`元 運算符。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="ccd9a-128">乘法運算子 \*</span><span class="sxs-lookup"><span data-stu-id="ccd9a-128">Multiplication operator \*</span></span>

<span data-ttu-id="ccd9a-129">乘法運算子 `*` 會計算其運算元的乘積：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="ccd9a-130">一元 `*` 運算子是一個[指標間接運算子](pointer-related-operators.md#pointer-indirection-operator-)。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="ccd9a-131">除法運算子 /</span><span class="sxs-lookup"><span data-stu-id="ccd9a-131">Division operator /</span></span>

<span data-ttu-id="ccd9a-132">除法運算子 `/` 會將它的左邊運算元除以右邊運算元。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="ccd9a-133">整數除數</span><span class="sxs-lookup"><span data-stu-id="ccd9a-133">Integer division</span></span>

<span data-ttu-id="ccd9a-134">針對整數型別的運算元，`/` 運算子的結果會是整數型別，且等於兩個運算元捨入為零的商：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="ccd9a-135">若要以浮點數的形式取得兩個運算元的商，請使用 `float`、`double` 或 `decimal` 型別：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="ccd9a-136">浮點除數</span><span class="sxs-lookup"><span data-stu-id="ccd9a-136">Floating-point division</span></span>

<span data-ttu-id="ccd9a-137">針對 `float`、`double` 和 `decimal` 型別，`/` 運算子的結果會是兩個運算元的商：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="ccd9a-138">如果其中一個運算元是 `decimal`，則另一個運算元便不可以是 `float` 或 `double`，因為 `float` 或 `double` 都無法隱含轉換為 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="ccd9a-139">您必須明確地將 `float` 或 `double` 運算元轉換為 `decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="ccd9a-140">關於數位型態轉換的詳細資訊,請參考[內建數位轉換](../builtin-types/numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="ccd9a-141">餘數運算子 %</span><span class="sxs-lookup"><span data-stu-id="ccd9a-141">Remainder operator %</span></span>

<span data-ttu-id="ccd9a-142">餘數運算子 `%` 會計算其左邊運算元除以右邊運算元之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="ccd9a-143">整數餘數</span><span class="sxs-lookup"><span data-stu-id="ccd9a-143">Integer remainder</span></span>

<span data-ttu-id="ccd9a-144">對整數型別的運算元來說，`a % b` 的結果是 `a - (a / b) * b` 所產生的值。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="ccd9a-145">非零餘數的正負號與左邊運算元的正負號相同，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="ccd9a-146">使用 <xref:System.Math.DivRem%2A?displayProperty=nameWithType> 方法計算整數除法和餘數結果。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="ccd9a-147">浮點數餘數</span><span class="sxs-lookup"><span data-stu-id="ccd9a-147">Floating-point remainder</span></span>

<span data-ttu-id="ccd9a-148">對於 `float` 和 `double` 運算元，有限 `x` 和 `y` 的 `x % y` 結果是 `z` 值，像是</span><span class="sxs-lookup"><span data-stu-id="ccd9a-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="ccd9a-149">若 `z` 不是零，其正負號與 `x` 的正負號相同。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="ccd9a-150">`z` 的絕對值是由 `|x| - n * |y|` 產生的值，其中 `n` 為最大可能整數，小於或等於 `|x| / |y|`，而 `|x|`和 `|y|`則分別是 `x` 和 `y` 的絕對值。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd9a-151">這種計算剩餘數的方法類似於用於整數操作數的方法,但與 IEEE 754 規範不同。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="ccd9a-152">如果需要符合 IEEE 754 規範的剩餘操作,<xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>請使用方法 。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ccd9a-153">如需在非有限運算元情況中 `%` 運算子的行為，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[餘數運算子](~/_csharplang/spec/expressions.md#remainder-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="ccd9a-154">針對 `decimal` 運算元，餘數運算子 `%` 相當於 <xref:System.Decimal?displayProperty=nameWithType> 型別的[餘數運算子](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>)。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="ccd9a-155">下列範例示範具有浮點運算元的餘數運算子行為：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="ccd9a-156">加法運算子 +</span><span class="sxs-lookup"><span data-stu-id="ccd9a-156">Addition operator +</span></span>

<span data-ttu-id="ccd9a-157">加法運算子 `+` 會計算其運算元的總和：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="ccd9a-158">您還可以使用運算元`+`進行字串串聯和委託組合。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-158">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="ccd9a-159">有關詳細資訊,請參閱[`+`和`+=`運算符](addition-operator.md)文章。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="ccd9a-160">減法運算子 -</span><span class="sxs-lookup"><span data-stu-id="ccd9a-160">Subtraction operator -</span></span>

<span data-ttu-id="ccd9a-161">減法運算子 `-` 會從左邊運算元減去右邊運算元：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="ccd9a-162">您還可以使用`-`運算元進行委託刪除。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-162">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="ccd9a-163">有關詳細資訊,請參閱[`-`和`-=`運算符](subtraction-operator.md)文章。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ccd9a-164">複合指派</span><span class="sxs-lookup"><span data-stu-id="ccd9a-164">Compound assignment</span></span>

<span data-ttu-id="ccd9a-165">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="ccd9a-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ccd9a-166">相當於</span><span class="sxs-lookup"><span data-stu-id="ccd9a-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ccd9a-167">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ccd9a-168">下列範例示範如何搭配算術運算子使用複合指派：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="ccd9a-169">由於[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)的緣故，`op` 作業結果可能無法隱含轉換成 `x` 的 `T` 型別。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="ccd9a-170">在此情況下，如果 `op` 是預先定義的運算子，且作業結果可以明確轉換成 `x` 的 `T` 型別，則形式 `x op= y` 的複合指派運算式相等於 `x = (T)(x op y)`，唯一的不同在於 `x` 只會評估一次。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="ccd9a-171">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="ccd9a-172">您還可以使用與`+=``-=`運算子來訂閱與取消[訂閱事件](../keywords/event.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="ccd9a-173">有關詳細資訊,請參閱[如何訂閱和取消訂閱事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="ccd9a-174">運算子優先順序和關聯性</span><span class="sxs-lookup"><span data-stu-id="ccd9a-174">Operator precedence and associativity</span></span>

<span data-ttu-id="ccd9a-175">下列清單會將算術運算子從最高優先順序開始排序到最低優先順序：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="ccd9a-176">後置遞增 `x++` 和遞減 `x--` 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="ccd9a-177">前置遞增 `++x` 和遞減 `--x` 以及一元 `+` 和 `-` 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="ccd9a-178">乘法類 `*`、`/` 和 `%` 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="ccd9a-179">加法類 `+` 和 `-` 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="ccd9a-180">二元算術運算子都是左向關聯。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="ccd9a-181">亦即，具有相同優先順序層級的運算子會由左至右進行評估。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="ccd9a-182">使用括號 `()` 變更運算子優先順序和關聯性強制執行的評估順序。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="ccd9a-183">有關按優先順序排序的 C# 運算子的完整清單,請參閱[C# 運算符](index.md)一文中的[運算符優先順序](index.md#operator-precedence)部分。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="ccd9a-184">算術溢位和除數為零</span><span class="sxs-lookup"><span data-stu-id="ccd9a-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="ccd9a-185">當算術運算的結果超出可能相關數字型別有限值的範圍之外時，算術運算子的行為取決於其運算元的型別。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="ccd9a-186">整數算術溢位</span><span class="sxs-lookup"><span data-stu-id="ccd9a-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="ccd9a-187">整數除以零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="ccd9a-188">如果整數算術溢位，則溢位檢查內容 (可以是 [checked 或 unchecked](../keywords/checked-and-unchecked.md)) 可控制所產生的行為：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="ccd9a-189">在 checked 內容中，如果常數運算式發生溢位，則會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="ccd9a-190">否則，當運算是在執行階段執行時，就會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="ccd9a-191">在 unchecked 內容中，會捨棄目的型別不適用的高序位位元，以便將結果截斷。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="ccd9a-192">除了 [checked 與 unchecked](../keywords/checked-and-unchecked.md) 陳述式之外，您還可以使用 `checked` 和 `unchecked` 運算子控制評估運算式的溢位檢查內容：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="ccd9a-193">根據預設，*unchecked* 內容中會發生算術運算。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="ccd9a-194">浮點算術溢位</span><span class="sxs-lookup"><span data-stu-id="ccd9a-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="ccd9a-195">具有 `float` 和 `double` 型別的算術運算永遠不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="ccd9a-196">具有這些型別之算術運算的結果可以是代表無限值和非數字的其中一個特殊值：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="ccd9a-197">若是 `decimal` 型別的運算元，算術溢位一律會擲回 <xref:System.OverflowException>，且除數為零一定會擲回 <xref:System.DivideByZeroException>。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="ccd9a-198">四捨五入錯誤</span><span class="sxs-lookup"><span data-stu-id="ccd9a-198">Round-off errors</span></span>

<span data-ttu-id="ccd9a-199">由於實數和浮點算術的浮點表示的一般限制,在具有浮點類型的計算中可能會出現舍入誤差。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="ccd9a-200">亦即，運算式產生的結果可能不同於預期的數學結果。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="ccd9a-201">下列範例將示範幾個這類案例：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="ccd9a-202">有關詳細資訊,請參閱[系統註釋.雙精度](/dotnet/api/system.double#remarks)值、[系統、單一](/dotnet/api/system.single#remarks)或[系統。十進位](/dotnet/api/system.decimal#remarks)參考頁。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ccd9a-203">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="ccd9a-203">Operator overloadability</span></span>

<span data-ttu-id="ccd9a-204">使用者定義的類型可以[重載](operator-overloading.md)`++`一元`+``-``*``/``%``+``--`(、、、 和 ) 和`-`二進位 (、、、和) 算術運算符。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="ccd9a-205">當二元運算子多載時，對應的複合指派運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="ccd9a-206">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="ccd9a-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ccd9a-207">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ccd9a-207">C# language specification</span></span>

<span data-ttu-id="ccd9a-208">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="ccd9a-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ccd9a-209">尾遞減和遞減運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="ccd9a-210">前置遞減運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="ccd9a-211">一元加號運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="ccd9a-212">一元減號運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="ccd9a-213">乘法運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="ccd9a-214">除法運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="ccd9a-215">剩餘運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="ccd9a-216">加法運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="ccd9a-217">減法運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="ccd9a-218">複合指派</span><span class="sxs-lookup"><span data-stu-id="ccd9a-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="ccd9a-219">checked 和 unchecked 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="ccd9a-220">數值升階</span><span class="sxs-lookup"><span data-stu-id="ccd9a-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="ccd9a-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccd9a-221">See also</span></span>

- [<span data-ttu-id="ccd9a-222">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ccd9a-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ccd9a-223">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ccd9a-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="ccd9a-224">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="ccd9a-224">Numerics in .NET</span></span>](../../../standard/numerics.md)
