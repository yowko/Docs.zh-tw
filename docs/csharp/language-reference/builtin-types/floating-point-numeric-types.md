---
title: 浮點數值型別 - C# 參考
description: 內建 C# 浮點數型別的概觀
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236051"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="b9776-103">浮點數值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b9776-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="b9776-104">**浮點數型別**是**簡單型別**的子集，並可使用[*常值*](#floating-point-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="b9776-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="b9776-105">所有浮點數型別也是實值型別。</span><span class="sxs-lookup"><span data-stu-id="b9776-105">All floating-point types are also value types.</span></span> <span data-ttu-id="b9776-106">所有浮點數型別都支援[算術](../operators/arithmetic-operators.md)、[比較和等號](../operators/equality-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="b9776-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="b9776-107">浮點數型別的特性</span><span class="sxs-lookup"><span data-stu-id="b9776-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="b9776-108">C# 支援下列預先定義的浮點數型別：</span><span class="sxs-lookup"><span data-stu-id="b9776-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="b9776-109">C# 型別/關鍵字</span><span class="sxs-lookup"><span data-stu-id="b9776-109">C# type/keyword</span></span>|<span data-ttu-id="b9776-110">大概範圍</span><span class="sxs-lookup"><span data-stu-id="b9776-110">Approximate range</span></span>|<span data-ttu-id="b9776-111">精確度</span><span class="sxs-lookup"><span data-stu-id="b9776-111">Precision</span></span>|<span data-ttu-id="b9776-112">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="b9776-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="b9776-113">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="b9776-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="b9776-114">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="b9776-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="b9776-115">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="b9776-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="b9776-116">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="b9776-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="b9776-117">±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="b9776-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="b9776-118">28-29 位數</span><span class="sxs-lookup"><span data-stu-id="b9776-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="b9776-119">在上表中，最左邊欄中的每個 C# 型別關鍵字，都是相對應 .NET 型別的別名。</span><span class="sxs-lookup"><span data-stu-id="b9776-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b9776-120">它們是可互換的。</span><span class="sxs-lookup"><span data-stu-id="b9776-120">They are interchangeable.</span></span> <span data-ttu-id="b9776-121">例如，下列宣告會宣告相同型別的變數：</span><span class="sxs-lookup"><span data-stu-id="b9776-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="b9776-122">每個浮點數型別的預設值都是零 (`0`)。</span><span class="sxs-lookup"><span data-stu-id="b9776-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="b9776-123">每個浮點數型別都有 `MinValue` 與 `MaxValue` 常數，提供該型別的最小與最大有限值。</span><span class="sxs-lookup"><span data-stu-id="b9776-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="b9776-124">`float` 與 `double` 型別也提供表示不是數字和無限值的常數。</span><span class="sxs-lookup"><span data-stu-id="b9776-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="b9776-125">例如，`double` 型別提供下列常數：<xref:System.Double.NaN?displayProperty=nameWithType>、<xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 與 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b9776-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b9776-126">相較於 `float` 與 `double`，因為 `decimal` 型別的精確度較高且範圍較小，所以非常適合財務與金融計算。</span><span class="sxs-lookup"><span data-stu-id="b9776-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="b9776-127">您可以在運算式中混合使用[整數](integral-numeric-types.md)型別與浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="b9776-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="b9776-128">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="b9776-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="b9776-129">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="b9776-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="b9776-130">如果其中一個浮點數型別是 `double`，運算式會評估為 `double` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="b9776-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="b9776-131">如果運算式中沒有 `double` 型別，則運算式會評估為 `float` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="b9776-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="b9776-132">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="b9776-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="b9776-133">正零和負零</span><span class="sxs-lookup"><span data-stu-id="b9776-133">Positive and negative zero</span></span>
- <span data-ttu-id="b9776-134">正無限大和負無限大</span><span class="sxs-lookup"><span data-stu-id="b9776-134">Positive and negative infinity</span></span>
- <span data-ttu-id="b9776-135">非數字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="b9776-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="b9776-136">非零值的有限集合</span><span class="sxs-lookup"><span data-stu-id="b9776-136">The finite set of nonzero values</span></span>

<span data-ttu-id="b9776-137">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="b9776-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="b9776-138">您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。</span><span class="sxs-lookup"><span data-stu-id="b9776-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="b9776-139">浮點數常值</span><span class="sxs-lookup"><span data-stu-id="b9776-139">Floating-point literals</span></span>

<span data-ttu-id="b9776-140">預設會將指派運算子右邊的浮點數值常值視為 `double`。</span><span class="sxs-lookup"><span data-stu-id="b9776-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="b9776-141">您可以使用尾碼，將浮點數或整數常值轉換成特定型別：</span><span class="sxs-lookup"><span data-stu-id="b9776-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="b9776-142">`d` 或 `D` 尾碼會將常值轉換為 `double`。</span><span class="sxs-lookup"><span data-stu-id="b9776-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="b9776-143">`f` 或 `F` 尾碼會將常值轉換為 `float`。</span><span class="sxs-lookup"><span data-stu-id="b9776-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="b9776-144">`m` 或 `M` 尾碼會將常值轉換為 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="b9776-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="b9776-145">下列範例顯示每種尾碼：</span><span class="sxs-lookup"><span data-stu-id="b9776-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="b9776-146">轉換</span><span class="sxs-lookup"><span data-stu-id="b9776-146">Conversions</span></span>

<span data-ttu-id="b9776-147">從 `float` 到 `double` 有隱含轉換 (稱為「擴展轉換」  )，而由於 `float` 值的範圍是 `double` 的適當子集，因此從 `float` 至 `double` 不會失去精確度。</span><span class="sxs-lookup"><span data-stu-id="b9776-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="b9776-148">如果未定義從來源型別到目的地型別的隱含轉換，則必須使用明確轉換，將某種浮點數型別轉換成另一種浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="b9776-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="b9776-149">這稱為「縮小轉換」  。</span><span class="sxs-lookup"><span data-stu-id="b9776-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="b9776-150">因為轉換會導致資料遺失，所以需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="b9776-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="b9776-151">其他浮點數型別和 `decimal` 型別之間沒有隱含轉換，因為 `decimal` 型別的精確度較 `float` 或 `double` 來得高。</span><span class="sxs-lookup"><span data-stu-id="b9776-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="b9776-152">如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="b9776-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="b9776-153">如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="b9776-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9776-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9776-154">See also</span></span>

- [<span data-ttu-id="b9776-155">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b9776-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9776-156">整數型別</span><span class="sxs-lookup"><span data-stu-id="b9776-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="b9776-157">內建型別表</span><span class="sxs-lookup"><span data-stu-id="b9776-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="b9776-158">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="b9776-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="b9776-159">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="b9776-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="b9776-160">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="b9776-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="b9776-161">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="b9776-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="b9776-162">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="b9776-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="b9776-163">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="b9776-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
