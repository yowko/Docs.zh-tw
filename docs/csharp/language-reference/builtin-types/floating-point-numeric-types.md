---
title: 浮點數值型別 - C# 參考
description: 瞭解內置 C# 浮點類型：浮動點、雙數和十進位
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
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77215244"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="d5ffa-103">浮點數值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d5ffa-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="d5ffa-104">*浮點數數值型別*表示實數。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="d5ffa-105">所有浮點數數值型別都是[數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="d5ffa-106">它們也是[簡單的類型](value-types.md#built-in-value-types)，可以使用[文本](#real-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="d5ffa-107">所有浮點數數值型別都支援[算術](../operators/arithmetic-operators.md)、[比較](../operators/comparison-operators.md)和[相等](../operators/equality-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="d5ffa-108">浮點數型別的特性</span><span class="sxs-lookup"><span data-stu-id="d5ffa-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="d5ffa-109">C# 支援下列預先定義的浮點數型別：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="d5ffa-110">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="d5ffa-110">C# type/keyword</span></span>|<span data-ttu-id="d5ffa-111">大概範圍</span><span class="sxs-lookup"><span data-stu-id="d5ffa-111">Approximate range</span></span>|<span data-ttu-id="d5ffa-112">Precision</span><span class="sxs-lookup"><span data-stu-id="d5ffa-112">Precision</span></span>|<span data-ttu-id="d5ffa-113">大小</span><span class="sxs-lookup"><span data-stu-id="d5ffa-113">Size</span></span>|<span data-ttu-id="d5ffa-114">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="d5ffa-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="d5ffa-115">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="d5ffa-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="d5ffa-116">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="d5ffa-116">~6-9 digits</span></span>|<span data-ttu-id="d5ffa-117">4 個位元組</span><span class="sxs-lookup"><span data-stu-id="d5ffa-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="d5ffa-118">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="d5ffa-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="d5ffa-119">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="d5ffa-119">~15-17 digits</span></span>|<span data-ttu-id="d5ffa-120">8 個位元組</span><span class="sxs-lookup"><span data-stu-id="d5ffa-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="d5ffa-121">±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="d5ffa-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="d5ffa-122">28-29 位數</span><span class="sxs-lookup"><span data-stu-id="d5ffa-122">28-29 digits</span></span>|<span data-ttu-id="d5ffa-123">16 個位元組</span><span class="sxs-lookup"><span data-stu-id="d5ffa-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="d5ffa-124">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="d5ffa-125">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-125">They are interchangeable.</span></span> <span data-ttu-id="d5ffa-126">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="d5ffa-127">每個浮點數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="d5ffa-128">每個浮點數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大有限值。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="d5ffa-129">`float` 與 `double` 型別也提供表示不是數字和無限值的常數。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="d5ffa-130">例如，`double` 型別提供下列常數：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 與 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d5ffa-131">相較於 `float` 與 `double`，因為 `decimal` 型別的精確度較高且範圍較小，所以非常適合財務與金融計算。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="d5ffa-132">您可以在運算式中混合[積分](integral-numeric-types.md)類型和`float``double`和 類型。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="d5ffa-133">在這種情況下，積分類型將隱式轉換為其中一個浮點類型，如有必要，`float`該類型將隱式轉換為 。 `double`</span><span class="sxs-lookup"><span data-stu-id="d5ffa-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="d5ffa-134">運算式評估如下：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="d5ffa-135">如果運算式中有`double`類型，則運算式在關係和相等比較`double`[`bool`](bool.md)中計算 到 或 。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="d5ffa-136">如果運算式中沒有`double`類型，則運算式將計算到`float`或`bool`在關係和相等比較中。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="d5ffa-137">您還可以在運算式中混合積分類型和`decimal`類型。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="d5ffa-138">在這種情況下，積分類型隱式轉換為`decimal`類型，運算式在關係和相等比較`decimal``bool`中計算為 或 。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="d5ffa-139">不能將`decimal`類型與 運算式中的`float``double`和 類型混合。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="d5ffa-140">在這種情況下，如果要執行算術、比較或相等操作，則必須顯式將運算元從 類型轉換為`decimal`類型，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="d5ffa-141">您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="d5ffa-142">真實文本</span><span class="sxs-lookup"><span data-stu-id="d5ffa-142">Real literals</span></span>

<span data-ttu-id="d5ffa-143">真實文本的類型由其後綴決定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="d5ffa-144">沒有尾碼或 帶`d`或`D`尾碼的文本的類型`double`</span><span class="sxs-lookup"><span data-stu-id="d5ffa-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="d5ffa-145">帶`f`或`F`尾碼的文本的類型`float`</span><span class="sxs-lookup"><span data-stu-id="d5ffa-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="d5ffa-146">帶`m`或`M`尾碼的文本的類型`decimal`</span><span class="sxs-lookup"><span data-stu-id="d5ffa-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="d5ffa-147">以下代碼演示了每個示例：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="d5ffa-148">前面的示例還顯示`_`用作*數位分隔符號*的用途，該分隔符號支援從 C# 7.0 開始。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="d5ffa-149">您可以將數位分隔符號用於所有類型的數位文本。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="d5ffa-150">您還可以使用科學記數法，即指定真實文本的指數部分，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="d5ffa-151">轉換</span><span class="sxs-lookup"><span data-stu-id="d5ffa-151">Conversions</span></span>

<span data-ttu-id="d5ffa-152">浮點數數值型別之間只有一個隱式轉換：從`float`到`double`。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="d5ffa-153">但是，您可以將任何浮點類型轉換為具有[顯式強制轉換](../operators/type-testing-and-cast.md#cast-operator-)的任何其他浮點類型。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="d5ffa-154">有關詳細資訊，請參閱[內置數位轉換](numeric-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="d5ffa-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d5ffa-155">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d5ffa-155">C# language specification</span></span>

<span data-ttu-id="d5ffa-156">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d5ffa-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d5ffa-157">浮點類型</span><span class="sxs-lookup"><span data-stu-id="d5ffa-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="d5ffa-158">小數類型</span><span class="sxs-lookup"><span data-stu-id="d5ffa-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="d5ffa-159">真實文本</span><span class="sxs-lookup"><span data-stu-id="d5ffa-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="d5ffa-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ffa-160">See also</span></span>

- [<span data-ttu-id="d5ffa-161">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d5ffa-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d5ffa-162">實值型別</span><span class="sxs-lookup"><span data-stu-id="d5ffa-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="d5ffa-163">整數型別</span><span class="sxs-lookup"><span data-stu-id="d5ffa-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="d5ffa-164">標準數位格式字串</span><span class="sxs-lookup"><span data-stu-id="d5ffa-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="d5ffa-165">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="d5ffa-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
