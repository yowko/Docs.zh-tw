---
title: double 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 50e11e8547c2887ace677d2c86dcf055326ff9a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708151"
---
# <a name="double-c-reference"></a><span data-ttu-id="4eb66-102">double (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4eb66-102">double (C# Reference)</span></span>

<span data-ttu-id="4eb66-103">`double` 關鍵字表示儲存 64 位元浮點值的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="4eb66-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="4eb66-104">下表顯示 `double` 類型的精確度和大概範圍。</span><span class="sxs-lookup"><span data-stu-id="4eb66-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="4eb66-105">類型</span><span class="sxs-lookup"><span data-stu-id="4eb66-105">Type</span></span>|<span data-ttu-id="4eb66-106">大概範圍</span><span class="sxs-lookup"><span data-stu-id="4eb66-106">Approximate range</span></span>|<span data-ttu-id="4eb66-107">精確度</span><span class="sxs-lookup"><span data-stu-id="4eb66-107">Precision</span></span>|<span data-ttu-id="4eb66-108">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="4eb66-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="4eb66-109">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="4eb66-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="4eb66-110">~15-17 位數</span><span class="sxs-lookup"><span data-stu-id="4eb66-110">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="4eb66-111">常值</span><span class="sxs-lookup"><span data-stu-id="4eb66-111">Literals</span></span>

<span data-ttu-id="4eb66-112">根據預設，指派運算子右邊的實數常值會視為 `double`。</span><span class="sxs-lookup"><span data-stu-id="4eb66-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="4eb66-113">不過，如果您希望整數被視為 `double`，請使用後置字元 d 或 D，例如︰</span><span class="sxs-lookup"><span data-stu-id="4eb66-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="4eb66-114">轉換</span><span class="sxs-lookup"><span data-stu-id="4eb66-114">Conversions</span></span>

<span data-ttu-id="4eb66-115">您可以在一個運算式中混合使用數值整數型別和浮點類型。</span><span class="sxs-lookup"><span data-stu-id="4eb66-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="4eb66-116">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="4eb66-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="4eb66-117">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="4eb66-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="4eb66-118">如果其中一個浮點數類型是 `double`，運算式會評估為 `double` 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯和相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="4eb66-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

- <span data-ttu-id="4eb66-119">若在運算式中沒有 `double` 類型，則會評估為 [float](../../../csharp/language-reference/keywords/float.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯和相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="4eb66-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

 <span data-ttu-id="4eb66-120">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="4eb66-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="4eb66-121">正零和負零。</span><span class="sxs-lookup"><span data-stu-id="4eb66-121">Positive and negative zero.</span></span>

- <span data-ttu-id="4eb66-122">正無限大和負無限大。</span><span class="sxs-lookup"><span data-stu-id="4eb66-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="4eb66-123">非數字值 (NaN)。</span><span class="sxs-lookup"><span data-stu-id="4eb66-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="4eb66-124">非零值的有限集合。</span><span class="sxs-lookup"><span data-stu-id="4eb66-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="4eb66-125">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="4eb66-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="4eb66-126">範例</span><span class="sxs-lookup"><span data-stu-id="4eb66-126">Example</span></span>

<span data-ttu-id="4eb66-127">在下例中，一起新增 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 以得到 `double` 結果。</span><span class="sxs-lookup"><span data-stu-id="4eb66-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="4eb66-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4eb66-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4eb66-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eb66-129">See also</span></span>

- [<span data-ttu-id="4eb66-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4eb66-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="4eb66-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4eb66-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4eb66-132">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="4eb66-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="4eb66-133">預設值表</span><span class="sxs-lookup"><span data-stu-id="4eb66-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)
- [<span data-ttu-id="4eb66-134">內建型別表</span><span class="sxs-lookup"><span data-stu-id="4eb66-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="4eb66-135">浮點型別表</span><span class="sxs-lookup"><span data-stu-id="4eb66-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)
- [<span data-ttu-id="4eb66-136">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="4eb66-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="4eb66-137">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="4eb66-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
