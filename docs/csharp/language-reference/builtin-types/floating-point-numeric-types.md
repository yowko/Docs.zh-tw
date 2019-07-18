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
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664188"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="5709b-103">浮點數值型別 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5709b-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="5709b-104">**浮點數型別**是**簡單型別**的子集，並可使用[*常值*](#floating-point-literals)初始化。</span><span class="sxs-lookup"><span data-stu-id="5709b-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="5709b-105">所有浮點數型別也是實值型別。</span><span class="sxs-lookup"><span data-stu-id="5709b-105">All floating-point types are also value types.</span></span> <span data-ttu-id="5709b-106">所有浮點數型別都支援[算術](../operators/arithmetic-operators.md)、[比較和等號](../operators/equality-operators.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="5709b-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="5709b-107">下表顯示浮點數型別的精確度和大概範圍：</span><span class="sxs-lookup"><span data-stu-id="5709b-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="5709b-108">類型</span><span class="sxs-lookup"><span data-stu-id="5709b-108">Type</span></span>|<span data-ttu-id="5709b-109">大概範圍</span><span class="sxs-lookup"><span data-stu-id="5709b-109">Approximate range</span></span>|<span data-ttu-id="5709b-110">精確度</span><span class="sxs-lookup"><span data-stu-id="5709b-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="5709b-111">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="5709b-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="5709b-112">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="5709b-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="5709b-113">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="5709b-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="5709b-114">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="5709b-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="5709b-115">±1.0 x 10<sup>-28</sup> 到 ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="5709b-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="5709b-116">28-29 位數</span><span class="sxs-lookup"><span data-stu-id="5709b-116">28-29 digits</span></span>|  

<span data-ttu-id="5709b-117">所有浮點數型別的預設值為 `0`。</span><span class="sxs-lookup"><span data-stu-id="5709b-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="5709b-118">每個浮點數型別都有名為 `MinValue` 和 `MaxValue` 的常數，為該型別的最小值和最大值。</span><span class="sxs-lookup"><span data-stu-id="5709b-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="5709b-119">`float` 和 `double` 型別還有 `PositiveInfinity`、`NegativeInfinity` 和 `NaN` (亦即「非數字」) 等額外常數。</span><span class="sxs-lookup"><span data-stu-id="5709b-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="5709b-120">`decimal` 型別包含 `Zero`、`One` 和 `MinusOne` 的常數。</span><span class="sxs-lookup"><span data-stu-id="5709b-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="5709b-121">相較於 `float` 和 `double`，`decimal` 型別的精確度較高且範圍較小，因此非常適合財務和金融計算。</span><span class="sxs-lookup"><span data-stu-id="5709b-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="5709b-122">您可以在運算式中混合使用整數型別和浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="5709b-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="5709b-123">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="5709b-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="5709b-124">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="5709b-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="5709b-125">如果其中一個浮點數型別是 `double`，運算式會評估為 `double` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="5709b-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="5709b-126">如果運算式中沒有 `double` 型別，則運算式會評估為 `float` 或 [bool](../keywords/bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="5709b-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="5709b-127">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="5709b-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="5709b-128">正零和負零</span><span class="sxs-lookup"><span data-stu-id="5709b-128">Positive and negative zero</span></span>
- <span data-ttu-id="5709b-129">正無限大和負無限大</span><span class="sxs-lookup"><span data-stu-id="5709b-129">Positive and negative infinity</span></span>
- <span data-ttu-id="5709b-130">非數字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="5709b-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="5709b-131">非零值的有限集合</span><span class="sxs-lookup"><span data-stu-id="5709b-131">The finite set of nonzero values</span></span>

<span data-ttu-id="5709b-132">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="5709b-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="5709b-133">您可以使用[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)或[自訂數值格式字串](../../../standard/base-types/custom-numeric-format-strings.md)，設定浮點數值格式。</span><span class="sxs-lookup"><span data-stu-id="5709b-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="5709b-134">浮點數常值</span><span class="sxs-lookup"><span data-stu-id="5709b-134">Floating-point literals</span></span>

<span data-ttu-id="5709b-135">預設會將指派運算子右邊的浮點數值常值視為 `double`。</span><span class="sxs-lookup"><span data-stu-id="5709b-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="5709b-136">您可以使用尾碼，將浮點數或整數常值轉換成特定型別：</span><span class="sxs-lookup"><span data-stu-id="5709b-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="5709b-137">`d` 或 `D` 尾碼會將常值轉換為 `double`。</span><span class="sxs-lookup"><span data-stu-id="5709b-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="5709b-138">`f` 或 `F` 尾碼會將常值轉換為 `float`。</span><span class="sxs-lookup"><span data-stu-id="5709b-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="5709b-139">`m` 或 `M` 尾碼會將常值轉換為 `decimal`。</span><span class="sxs-lookup"><span data-stu-id="5709b-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="5709b-140">下列範例顯示每種尾碼：</span><span class="sxs-lookup"><span data-stu-id="5709b-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="5709b-141">轉換</span><span class="sxs-lookup"><span data-stu-id="5709b-141">Conversions</span></span>

<span data-ttu-id="5709b-142">從 `float` 到 `double` 有隱含轉換 (稱為「擴展轉換」  )，而由於 `float` 值的範圍是 `double` 的適當子集，因此從 `float` 至 `double` 不會失去精確度。</span><span class="sxs-lookup"><span data-stu-id="5709b-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="5709b-143">如果未定義從來源型別到目的地型別的隱含轉換，則必須使用明確轉換，將某種浮點數型別轉換成另一種浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="5709b-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="5709b-144">這稱為「縮小轉換」  。</span><span class="sxs-lookup"><span data-stu-id="5709b-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="5709b-145">因為轉換會導致資料遺失，所以需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="5709b-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="5709b-146">其他浮點數型別和 `decimal` 型別之間沒有隱含轉換，因為 `decimal` 型別的精確度較 `float` 或 `double` 來得高。</span><span class="sxs-lookup"><span data-stu-id="5709b-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="5709b-147">如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="5709b-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="5709b-148">如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../keywords/explicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="5709b-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5709b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5709b-149">See also</span></span>

- [<span data-ttu-id="5709b-150">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5709b-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5709b-151">整數型別</span><span class="sxs-lookup"><span data-stu-id="5709b-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="5709b-152">預設值表</span><span class="sxs-lookup"><span data-stu-id="5709b-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="5709b-153">格式化數值結果表</span><span class="sxs-lookup"><span data-stu-id="5709b-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="5709b-154">內建型別表</span><span class="sxs-lookup"><span data-stu-id="5709b-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="5709b-155">.NET 中的數值</span><span class="sxs-lookup"><span data-stu-id="5709b-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="5709b-156">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="5709b-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="5709b-157">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="5709b-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="5709b-158">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="5709b-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="5709b-159">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="5709b-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
