---
title: 位元與移位運算子 - C# 參考
description: 了解針對整數型別運算元執行位元邏輯或移位作業的 C# 運算子。
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 65f7e2db176b408c9768ce73e297008c4b4c83d8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880608"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="573d4-103">位元與移位運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="573d4-103">Bitwise and shift operators (C# Reference)</span></span>

<span data-ttu-id="573d4-104">下列運算子會針對[整數型別](../keywords/integral-types-table.md)的運算元執行位元或移位作業：</span><span class="sxs-lookup"><span data-stu-id="573d4-104">The following operators perform bitwise or shift operations with operands of the [integral types](../keywords/integral-types-table.md):</span></span>

- <span data-ttu-id="573d4-105">一元 [`~`(位元補充)](#bitwise-complement-operator-) 運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="573d4-106">二元 [`<<` (左移)](#left-shift-operator-) 及 [`>>` (右移)](#right-shift-operator-) 移位運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="573d4-107">二元 [`&` (邏輯 AND)](#logical-and-operator-)、[`|` (邏輯 OR)](#logical-or-operator-)，以及 [`^` (邏輯互斥 OR)](#logical-exclusive-or-operator-) 運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="573d4-108">這些運算子已針對 `int`、`uint`、`long` 和 `ulong` 型別進行定義。</span><span class="sxs-lookup"><span data-stu-id="573d4-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="573d4-109">當兩個運算元都是其他整數型別 (`sbyte`、`byte`、`short`、`ushort` 或 `char`) 時，它們的值會轉換成 `int` 型別，而這也是作業的結果型別。</span><span class="sxs-lookup"><span data-stu-id="573d4-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="573d4-110">當運算元屬於不同的整數型別時，它們的值都會轉換成範圍最接近的整數型別。</span><span class="sxs-lookup"><span data-stu-id="573d4-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="573d4-111">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)一節。</span><span class="sxs-lookup"><span data-stu-id="573d4-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="573d4-112">`&`、`|` 和 `^` 運算子也已針對 `bool` 型別的運算元進行定義。</span><span class="sxs-lookup"><span data-stu-id="573d4-112">The `&`, `|`, and `^` operators are also defined for the operands of the `bool` type.</span></span> <span data-ttu-id="573d4-113">如需詳細資訊，請參閱[布林邏輯運算子](boolean-logical-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="573d4-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="573d4-114">位元和移位運算子一律不會導致溢位，並會在[受檢查內容及未受檢查](../keywords/checked-and-unchecked.md)內容中產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="573d4-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="573d4-115">位元補充運算子 ~</span><span class="sxs-lookup"><span data-stu-id="573d4-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="573d4-116">`~` 運算子會透過反轉每個位元，產生其運算元的位元補充：</span><span class="sxs-lookup"><span data-stu-id="573d4-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="573d4-117">您也可以使用 `~` 符號來宣告完成項。</span><span class="sxs-lookup"><span data-stu-id="573d4-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="573d4-118">如需詳細資訊，請參閱[完成項](../../programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="573d4-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="573d4-119">左移運算子 \<\<</span><span class="sxs-lookup"><span data-stu-id="573d4-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="573d4-120">`<<` 運算子會將其第一個運算元左移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="573d4-120">The `<<` operator shifts its first operand left by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="573d4-121">左移作業會捨棄位於結果型別範圍外的高位位元，並將低位的空位元位置設為零，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="573d4-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="573d4-122">由於移位運算子僅針對 `int`、`uint`、`long` 和 `ulong` 型別進行定義，所以作業的結果一律會包含至少 32 個位元。</span><span class="sxs-lookup"><span data-stu-id="573d4-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="573d4-123">第一個運算元是另一個整數型別 (`sbyte`、`byte`、`short`、`ushort` 或 `char`)，其值會轉換成 `int` 型別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="573d4-123">If the first operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="573d4-124">如需 `<<` 運算子第二個運算元如何定義移位計數的資訊，請參閱[移位運算子的移位計數](#shift-count-of-the-shift-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="573d4-124">For information about how the second operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="573d4-125">右移運算子 >></span><span class="sxs-lookup"><span data-stu-id="573d4-125">Right-shift operator >></span></span>

<span data-ttu-id="573d4-126">`>>` 運算子會將其第一個運算元右移第二個運算元所定義的位元數。</span><span class="sxs-lookup"><span data-stu-id="573d4-126">The `>>` operator shifts its first operand right by the number of bits defined by its second operand.</span></span>

<span data-ttu-id="573d4-127">右移作業會捨棄低位位元，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="573d4-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="573d4-128">會根據第一個運算元的類型來設定高位空位元位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="573d4-128">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="573d4-129">若第一個運算元的型別為 [int](../keywords/int.md) 或 [long](../keywords/long.md)，則右移運算元會執行*算術*位移：第一個運算元之最高有效位元 (正負號位元) 的值會傳播到高為空位元位置。</span><span class="sxs-lookup"><span data-stu-id="573d4-129">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="573d4-130">也就是說，若第一個運算元不是負值且在為負值時被設定為一，則高位空位元位置會被設定為零。</span><span class="sxs-lookup"><span data-stu-id="573d4-130">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="573d4-131">若第一個運算元的型別為 [uint](../keywords/uint.md) 或 [ulong](../keywords/ulong.md)，則右移運算子會執行*邏輯*位移：高位空位元位置一律會被設定為零。</span><span class="sxs-lookup"><span data-stu-id="573d4-131">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="573d4-132">如需 `>>` 運算子第二個運算元如何定義移位計數的資訊，請參閱[移位運算子的移位計數](#shift-count-of-the-shift-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="573d4-132">For information about how the second operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-amp"></a><span data-ttu-id="573d4-133">邏輯 AND 運算子 &amp;</span><span class="sxs-lookup"><span data-stu-id="573d4-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="573d4-134">`&` 運算子會計算其運算元的位元邏輯 AND：</span><span class="sxs-lookup"><span data-stu-id="573d4-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="573d4-135">針對 `bool` 型別的運算元，`&` 運算子會計算其運算元的[邏輯 AND](boolean-logical-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="573d4-135">For the operands of the `bool` type, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="573d4-136">一元的 `&` 運算子是 [address-of 運算子](pointer-related-operators.md#address-of-operator-)。</span><span class="sxs-lookup"><span data-stu-id="573d4-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="573d4-137">邏輯互斥 OR 運算子 ^</span><span class="sxs-lookup"><span data-stu-id="573d4-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="573d4-138">`^` 運算子會計算其運算元的位元邏輯互斥 OR，也稱為位元邏輯 XOR：</span><span class="sxs-lookup"><span data-stu-id="573d4-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="573d4-139">針對 `bool` 型別的運算元，`^` 運算子會計算其運算元的[邏輯互斥 OR](boolean-logical-operators.md#logical-exclusive-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="573d4-139">For the operands of the `bool` type, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="573d4-140">邏輯 OR 運算子 |</span><span class="sxs-lookup"><span data-stu-id="573d4-140">Logical OR operator |</span></span>

<span data-ttu-id="573d4-141">`|` 運算子會計算其運算元的位元邏輯 OR：</span><span class="sxs-lookup"><span data-stu-id="573d4-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="573d4-142">針對 `bool` 型別的運算元，`|` 運算子會計算其運算元的[邏輯 OR](boolean-logical-operators.md#logical-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="573d4-142">For the operands of the `bool` type, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="573d4-143">複合指派</span><span class="sxs-lookup"><span data-stu-id="573d4-143">Compound assignment</span></span>

<span data-ttu-id="573d4-144">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="573d4-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="573d4-145">相當於</span><span class="sxs-lookup"><span data-stu-id="573d4-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="573d4-146">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="573d4-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="573d4-147">下列範例會示範使用位元及移位運算子進行複合指派的方式：</span><span class="sxs-lookup"><span data-stu-id="573d4-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="573d4-148">由於[數值升階](~/_csharplang/spec/expressions.md#numeric-promotions)的緣故，`op` 作業結果可能無法隱含轉換成 `x` 的 `T` 型別。</span><span class="sxs-lookup"><span data-stu-id="573d4-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="573d4-149">在此情況下，如果 `op` 是預先定義的運算子，且作業結果可以明確轉換成 `x` 的 `T` 型別，則形式 `x op= y` 的複合指派運算式相等於 `x = (T)(x op y)`，唯一的不同在於 `x` 只會評估一次。</span><span class="sxs-lookup"><span data-stu-id="573d4-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="573d4-150">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="573d4-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="573d4-151">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="573d4-151">Operator precedence</span></span>

<span data-ttu-id="573d4-152">下列清單會從優先順序最高位元及移位運算子依序排序到優先順序最低的運算子：</span><span class="sxs-lookup"><span data-stu-id="573d4-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="573d4-153">位元補充運算子 `~`</span><span class="sxs-lookup"><span data-stu-id="573d4-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="573d4-154">移位運算子 `<<` 和 `>>`</span><span class="sxs-lookup"><span data-stu-id="573d4-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="573d4-155">邏輯 AND 運算子 `&`</span><span class="sxs-lookup"><span data-stu-id="573d4-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="573d4-156">邏輯互斥 OR 運算子 `^`</span><span class="sxs-lookup"><span data-stu-id="573d4-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="573d4-157">邏輯 OR 運算子 `|`</span><span class="sxs-lookup"><span data-stu-id="573d4-157">Logical OR operator `|`</span></span>

<span data-ttu-id="573d4-158">使用括號 `()` 來變更由運算子優先順序所強制執行的評估順序：</span><span class="sxs-lookup"><span data-stu-id="573d4-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="573d4-159">如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="573d4-159">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="573d4-160">移位運算子的移位計數</span><span class="sxs-lookup"><span data-stu-id="573d4-160">Shift count of the shift operators</span></span>

<span data-ttu-id="573d4-161">針對移位運算子 `<<` 和 `>>`，第二個運算元的型別必須是 [int](../keywords/int.md) 或具有[預先定義隱含數值轉換](../keywords/implicit-numeric-conversions-table.md)至 `int` 的型別。</span><span class="sxs-lookup"><span data-stu-id="573d4-161">For the shift operators `<<` and `>>`, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="573d4-162">針對 `x << count` 和 `x >> count` 運算式，實際的移位計數取決於 `x` 的型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="573d4-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="573d4-163">若 `x` 的型別是 [int](../keywords/int.md) 或 [uint](../keywords/uint.md)，則移位計數會由第二個運算元低位的「五個」位元定義。</span><span class="sxs-lookup"><span data-stu-id="573d4-163">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is defined by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="573d4-164">也就是說，位移計數是從 `count & 0x1F` (或 `count & 0b_1_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="573d4-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="573d4-165">若 `x` 的型別是 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md)，則移位計數會由第二個運算元低位的「六個」位元定義。</span><span class="sxs-lookup"><span data-stu-id="573d4-165">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is defined by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="573d4-166">也就是說，位移計數是從 `count & 0x3F` (或 `count & 0b_11_1111`) 所計算。</span><span class="sxs-lookup"><span data-stu-id="573d4-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="573d4-167">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="573d4-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="573d4-168">列舉邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-168">Enumeration logical operators</span></span>

<span data-ttu-id="573d4-169">`~`、`&`、`|` 和 `^` 運算子也已針對任何[列舉](../keywords/enum.md)型別進行定義。</span><span class="sxs-lookup"><span data-stu-id="573d4-169">The `~`, `&`, `|`, and `^` operators are also defined for any [enumeration](../keywords/enum.md) type.</span></span> <span data-ttu-id="573d4-170">針對相同列舉型別的運算元，邏輯作業會在基礎整數型別的對應值上執行。</span><span class="sxs-lookup"><span data-stu-id="573d4-170">For the operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="573d4-171">例如，針對任何基礎型別為 `U` 列舉型別 `T` 的 `x` 和 `y`，`x & y` 運算式會產生與 `(T)((U)x & (U)y)` 運算式相同結果。</span><span class="sxs-lookup"><span data-stu-id="573d4-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="573d4-172">您通常會搭配使用 [Flags](xref:System.FlagsAttribute) 屬性定義的列舉型別使用位元邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="573d4-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="573d4-173">如需詳細資訊，請參閱[列舉型別](../../programming-guide/enumeration-types.md)文章中的[作為位元旗標的列舉型別](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags)一節。</span><span class="sxs-lookup"><span data-stu-id="573d4-173">For more information, see the [Enumeration types as bit flags](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../../programming-guide/enumeration-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="573d4-174">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="573d4-174">Operator overloadability</span></span>

<span data-ttu-id="573d4-175">使用者定義型別可以[多載](../keywords/operator.md) `~`、`<<`、`>>`、`&`、`|` 和 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="573d4-175">A user-defined type can [overload](../keywords/operator.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="573d4-176">當二元運算子多載時，對應的複合指派運算子也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="573d4-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="573d4-177">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="573d4-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="573d4-178">若使用者定義型別 `T` 多載了 `<<` 或 `>>` 運算子，則第一個運算元的型別必須是 `T`，第二個運算元的型別必須是 `int`。</span><span class="sxs-lookup"><span data-stu-id="573d4-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="573d4-179">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="573d4-179">C# language specification</span></span>

<span data-ttu-id="573d4-180">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="573d4-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="573d4-181">位元補充運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="573d4-182">移位運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="573d4-183">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="573d4-184">複合指派</span><span class="sxs-lookup"><span data-stu-id="573d4-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="573d4-185">數值升階</span><span class="sxs-lookup"><span data-stu-id="573d4-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="573d4-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="573d4-186">See also</span></span>

- [<span data-ttu-id="573d4-187">C# 參考</span><span class="sxs-lookup"><span data-stu-id="573d4-187">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="573d4-188">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="573d4-188">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="573d4-189">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-189">C# Operators</span></span>](index.md)
- [<span data-ttu-id="573d4-190">布林值邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="573d4-190">Boolean logical operators</span></span>](boolean-logical-operators.md)
