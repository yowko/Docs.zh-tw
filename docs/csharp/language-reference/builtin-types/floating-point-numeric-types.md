---
title: 浮點數值型別 - C# 參考
description: 瞭解內建 C# 浮點型態:浮動點、雙數和十進制
ms.date: 02/10/2020
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
ms.openlocfilehash: a277215d438b5f6b0bbbef72e5e0121b6ce41990
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121474"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="aac0e-103">浮點數值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="aac0e-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="aac0e-104">*浮點數值類型*表示實數。</span><span class="sxs-lookup"><span data-stu-id="aac0e-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="aac0e-105">所有浮點數值類型都是[值類型](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="aac0e-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="aac0e-106">它們也是[簡單的類型](value-types.md#built-in-value-types),可以使用[文本](#real-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="aac0e-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="aac0e-107">所有浮點數值類型都支援[算術](../operators/arithmetic-operators.md)、[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算符。</span><span class="sxs-lookup"><span data-stu-id="aac0e-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="aac0e-108">浮點數型別的特性</span><span class="sxs-lookup"><span data-stu-id="aac0e-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="aac0e-109">C# 支援下列預先定義的浮點數型別：</span><span class="sxs-lookup"><span data-stu-id="aac0e-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="aac0e-110">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="aac0e-110">C# type/keyword</span></span>|<span data-ttu-id="aac0e-111">大概範圍</span><span class="sxs-lookup"><span data-stu-id="aac0e-111">Approximate range</span></span>|<span data-ttu-id="aac0e-112">Precision</span><span class="sxs-lookup"><span data-stu-id="aac0e-112">Precision</span></span>|<span data-ttu-id="aac0e-113">大小</span><span class="sxs-lookup"><span data-stu-id="aac0e-113">Size</span></span>|<span data-ttu-id="aac0e-114">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="aac0e-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="aac0e-115">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="aac0e-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="aac0e-116">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="aac0e-116">~6-9 digits</span></span>|<span data-ttu-id="aac0e-117">4 個位元組</span><span class="sxs-lookup"><span data-stu-id="aac0e-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="aac0e-118">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="aac0e-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="aac0e-119">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="aac0e-119">~15-17 digits</span></span>|<span data-ttu-id="aac0e-120">8 個位元組</span><span class="sxs-lookup"><span data-stu-id="aac0e-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="aac0e-121">±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="aac0e-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="aac0e-122">28-29 位數</span><span class="sxs-lookup"><span data-stu-id="aac0e-122">28-29 digits</span></span>|<span data-ttu-id="aac0e-123">16 個位元組</span><span class="sxs-lookup"><span data-stu-id="aac0e-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="aac0e-124">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="aac0e-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="aac0e-125">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="aac0e-125">They are interchangeable.</span></span> <span data-ttu-id="aac0e-126">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="aac0e-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="aac0e-127">每個浮點數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="aac0e-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="aac0e-128">每個浮點數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大有限值。</span><span class="sxs-lookup"><span data-stu-id="aac0e-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="aac0e-129">`float` 與 `double` 型別也提供表示不是數字和無限值的常數。</span><span class="sxs-lookup"><span data-stu-id="aac0e-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="aac0e-130">例如，`double` 型別提供下列常數：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 與 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="aac0e-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="aac0e-131">相較於 `float` 與 `double`，因為 `decimal` 型別的精確度較高且範圍較小，所以非常適合財務與金融計算。</span><span class="sxs-lookup"><span data-stu-id="aac0e-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="aac0e-132">您可以在運算式中混合[積分](integral-numeric-types.md)類型和`float``double`和類型。</span><span class="sxs-lookup"><span data-stu-id="aac0e-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="aac0e-133">在這種情況下,積分類型將隱式轉換為其中一個浮點類型,如有必要,`float`該類型將隱式轉換為`double`。</span><span class="sxs-lookup"><span data-stu-id="aac0e-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="aac0e-134">運算式評估如下：</span><span class="sxs-lookup"><span data-stu-id="aac0e-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="aac0e-135">如果表示式中有`double`類型,則表示式在關係與相等`double`[`bool`](bool.md)比較 中計算到或 。</span><span class="sxs-lookup"><span data-stu-id="aac0e-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="aac0e-136">如果運算式中沒有`double`類型,則運算式將計算到`float``bool`或在關係和相等比較中。</span><span class="sxs-lookup"><span data-stu-id="aac0e-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="aac0e-137">您還可以在運算式中混合積分類型和`decimal`類型。</span><span class="sxs-lookup"><span data-stu-id="aac0e-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="aac0e-138">在這種情況下,積分類型隱式轉換為`decimal`類型,運算式在關係和相等比較`decimal``bool`中計算為或 。</span><span class="sxs-lookup"><span data-stu-id="aac0e-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="aac0e-139">不能將`decimal`類型與 運算式`float``double`中的和類型混合。</span><span class="sxs-lookup"><span data-stu-id="aac0e-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="aac0e-140">在這種情況下,如果要執行算術、比較或相等操作,則必須顯式將操作數從 類型轉換`decimal`為 類型,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="aac0e-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="aac0e-141">您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。</span><span class="sxs-lookup"><span data-stu-id="aac0e-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="aac0e-142">真實文字</span><span class="sxs-lookup"><span data-stu-id="aac0e-142">Real literals</span></span>

<span data-ttu-id="aac0e-143">真實文本的類型由其後綴決定,如下所示:</span><span class="sxs-lookup"><span data-stu-id="aac0e-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="aac0e-144">沒有尾尾或`d`包含`D`後的文字的類型`double`</span><span class="sxs-lookup"><span data-stu-id="aac0e-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="aac0e-145">以`f`文字`F`的文字的類型`float`</span><span class="sxs-lookup"><span data-stu-id="aac0e-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="aac0e-146">以`m`文字`M`的文字的類型`decimal`</span><span class="sxs-lookup"><span data-stu-id="aac0e-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="aac0e-147">以下代碼展示每個範例:</span><span class="sxs-lookup"><span data-stu-id="aac0e-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="aac0e-148">前面的範例還顯示`_`用作*數位分隔符*的用途,該分隔符支援從 C# 7.0 開始。</span><span class="sxs-lookup"><span data-stu-id="aac0e-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="aac0e-149">您可以將數字分隔符用於所有類型的數字文本。</span><span class="sxs-lookup"><span data-stu-id="aac0e-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="aac0e-150">您還可以使用科學記數法,即指定真實文本的指數部分,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="aac0e-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="aac0e-151">轉換</span><span class="sxs-lookup"><span data-stu-id="aac0e-151">Conversions</span></span>

<span data-ttu-id="aac0e-152">浮點數值類型之間只有一個隱式轉換:從`float`到`double`。</span><span class="sxs-lookup"><span data-stu-id="aac0e-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="aac0e-153">但是,您可以將任何浮點類型轉換為具有[顯式強制轉換](../operators/type-testing-and-cast.md#cast-expression)的任何其他浮點類型。</span><span class="sxs-lookup"><span data-stu-id="aac0e-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="aac0e-154">有關詳細資訊,請參閱[內建數位轉換](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="aac0e-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aac0e-155">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="aac0e-155">C# language specification</span></span>

<span data-ttu-id="aac0e-156">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="aac0e-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="aac0e-157">浮點型態</span><span class="sxs-lookup"><span data-stu-id="aac0e-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="aac0e-158">小數型別</span><span class="sxs-lookup"><span data-stu-id="aac0e-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="aac0e-159">真實文字</span><span class="sxs-lookup"><span data-stu-id="aac0e-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="aac0e-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aac0e-160">See also</span></span>

- [<span data-ttu-id="aac0e-161">C# 參考</span><span class="sxs-lookup"><span data-stu-id="aac0e-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aac0e-162">值類型</span><span class="sxs-lookup"><span data-stu-id="aac0e-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="aac0e-163">整數型別</span><span class="sxs-lookup"><span data-stu-id="aac0e-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="aac0e-164">標準數值格式字串</span><span class="sxs-lookup"><span data-stu-id="aac0e-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="aac0e-165">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="aac0e-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
