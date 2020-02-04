---
title: 浮點數值型別 - C# 參考
description: 內建 C# 浮點數型別的概觀
ms.date: 10/22/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 9fde2b28288b58d7da3a4d003ec50af7d7e7a965
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980167"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="5e542-103">浮點數值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5e542-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="5e542-104">**浮點數型別**是**簡單型別**的子集，並可使用[*常值*](#real-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="5e542-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="5e542-105">所有浮點數型別也是實值型別。</span><span class="sxs-lookup"><span data-stu-id="5e542-105">All floating-point types are also value types.</span></span> <span data-ttu-id="5e542-106">所有浮點數數值型別都支援[算術](../operators/arithmetic-operators.md)、比較和[等號](../operators/equality-operators.md)[比較](../operators/comparison-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="5e542-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="5e542-107">浮點數型別的特性</span><span class="sxs-lookup"><span data-stu-id="5e542-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="5e542-108">C# 支援下列預先定義的浮點數型別：</span><span class="sxs-lookup"><span data-stu-id="5e542-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="5e542-109">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="5e542-109">C# type/keyword</span></span>|<span data-ttu-id="5e542-110">大概範圍</span><span class="sxs-lookup"><span data-stu-id="5e542-110">Approximate range</span></span>|<span data-ttu-id="5e542-111">精確度</span><span class="sxs-lookup"><span data-stu-id="5e542-111">Precision</span></span>|<span data-ttu-id="5e542-112">大小</span><span class="sxs-lookup"><span data-stu-id="5e542-112">Size</span></span>|<span data-ttu-id="5e542-113">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="5e542-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="5e542-114">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="5e542-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="5e542-115">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="5e542-115">~6-9 digits</span></span>|<span data-ttu-id="5e542-116">4 個位元組</span><span class="sxs-lookup"><span data-stu-id="5e542-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="5e542-117">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="5e542-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="5e542-118">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="5e542-118">~15-17 digits</span></span>|<span data-ttu-id="5e542-119">8 個位元組</span><span class="sxs-lookup"><span data-stu-id="5e542-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="5e542-120">±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="5e542-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="5e542-121">28-29 位數</span><span class="sxs-lookup"><span data-stu-id="5e542-121">28-29 digits</span></span>|<span data-ttu-id="5e542-122">16 個位元組</span><span class="sxs-lookup"><span data-stu-id="5e542-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="5e542-123">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="5e542-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="5e542-124">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="5e542-124">They are interchangeable.</span></span> <span data-ttu-id="5e542-125">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="5e542-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="5e542-126">每個浮點數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="5e542-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="5e542-127">每個浮點數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大有限值。</span><span class="sxs-lookup"><span data-stu-id="5e542-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="5e542-128">`float` 與 `double` 型別也提供表示不是數字和無限值的常數。</span><span class="sxs-lookup"><span data-stu-id="5e542-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="5e542-129">例如，`double` 型別提供下列常數：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 與 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5e542-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5e542-130">相較於 `float` 與 `double`，因為 `decimal` 型別的精確度較高且範圍較小，所以非常適合財務與金融計算。</span><span class="sxs-lookup"><span data-stu-id="5e542-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="5e542-131">您可以在運算式中混合使用[整數](integral-numeric-types.md)型別與浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="5e542-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="5e542-132">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="5e542-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="5e542-133">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="5e542-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="5e542-134">如果其中一個浮點類型是 `double`，則運算式會評估為 `double`，或在關聯式和相等比較中為[bool](bool.md) 。</span><span class="sxs-lookup"><span data-stu-id="5e542-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="5e542-135">如果運算式中沒有 `double` 類型，則運算式會評估為 `float`，或在關聯式和相等比較中為[bool](bool.md) 。</span><span class="sxs-lookup"><span data-stu-id="5e542-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="5e542-136">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="5e542-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="5e542-137">正零和負零</span><span class="sxs-lookup"><span data-stu-id="5e542-137">Positive and negative zero</span></span>
- <span data-ttu-id="5e542-138">正無限大和負無限大</span><span class="sxs-lookup"><span data-stu-id="5e542-138">Positive and negative infinity</span></span>
- <span data-ttu-id="5e542-139">非數字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="5e542-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="5e542-140">非零值的有限集合</span><span class="sxs-lookup"><span data-stu-id="5e542-140">The finite set of nonzero values</span></span>

<span data-ttu-id="5e542-141">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="5e542-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="5e542-142">您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。</span><span class="sxs-lookup"><span data-stu-id="5e542-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="5e542-143">實際常值</span><span class="sxs-lookup"><span data-stu-id="5e542-143">Real literals</span></span>

<span data-ttu-id="5e542-144">實際常值的類型取決於其後置詞，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5e542-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="5e542-145">不含尾碼或具有 `d` 或 `D` 尾碼的常值屬於類型 `double`</span><span class="sxs-lookup"><span data-stu-id="5e542-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="5e542-146">具有 `f` 或 `F` 尾碼的常值屬於類型 `float`</span><span class="sxs-lookup"><span data-stu-id="5e542-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="5e542-147">具有 `m` 或 `M` 尾碼的常值屬於類型 `decimal`</span><span class="sxs-lookup"><span data-stu-id="5e542-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="5e542-148">下列程式碼示範每個的範例：</span><span class="sxs-lookup"><span data-stu-id="5e542-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="5e542-149">上述範例也會示範如何使用 `_` 做為*數位分隔符號*，從C# 7.0 開始支援。</span><span class="sxs-lookup"><span data-stu-id="5e542-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="5e542-150">您可以使用數位分隔符號搭配所有類型的數值常值。</span><span class="sxs-lookup"><span data-stu-id="5e542-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="5e542-151">您也可以使用科學記號標記法，也就是指定實際常值的指數部分，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5e542-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="5e542-152">轉換</span><span class="sxs-lookup"><span data-stu-id="5e542-152">Conversions</span></span>

<span data-ttu-id="5e542-153">浮點數數值型別之間只有一個隱含轉換：從 `float` 到 `double`。</span><span class="sxs-lookup"><span data-stu-id="5e542-153">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="5e542-154">不過，您可以使用[明確轉換](../operators/type-testing-and-cast.md#cast-operator-)，將任何浮點類型轉換成任何其他浮點類型。</span><span class="sxs-lookup"><span data-stu-id="5e542-154">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="5e542-155">如需詳細資訊，請參閱[內建數值轉換](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="5e542-155">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5e542-156">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5e542-156">C# language specification</span></span>

<span data-ttu-id="5e542-157">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="5e542-157">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5e542-158">浮點類型</span><span class="sxs-lookup"><span data-stu-id="5e542-158">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="5e542-159">Decimal 類型</span><span class="sxs-lookup"><span data-stu-id="5e542-159">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="5e542-160">實際常值</span><span class="sxs-lookup"><span data-stu-id="5e542-160">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="5e542-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e542-161">See also</span></span>

- [<span data-ttu-id="5e542-162">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5e542-162">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5e542-163">內建型別表</span><span class="sxs-lookup"><span data-stu-id="5e542-163">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="5e542-164">整數型別</span><span class="sxs-lookup"><span data-stu-id="5e542-164">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="5e542-165">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="5e542-165">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="5e542-166">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="5e542-166">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
