---
title: double 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 4c11065d9354d44c1da8354c6f7b4f52d7b84c10
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47207318"
---
# <a name="double-c-reference"></a><span data-ttu-id="f9ff5-102">double (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f9ff5-102">double (C# Reference)</span></span>

<span data-ttu-id="f9ff5-103">`double` 關鍵字表示儲存 64 位元浮點值的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="f9ff5-104">下表顯示 `double` 類型的精確度和大概範圍。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="f9ff5-105">類型</span><span class="sxs-lookup"><span data-stu-id="f9ff5-105">Type</span></span>|<span data-ttu-id="f9ff5-106">大概範圍</span><span class="sxs-lookup"><span data-stu-id="f9ff5-106">Approximate range</span></span>|<span data-ttu-id="f9ff5-107">精確度</span><span class="sxs-lookup"><span data-stu-id="f9ff5-107">Precision</span></span>|<span data-ttu-id="f9ff5-108">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="f9ff5-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="f9ff5-109">±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="f9ff5-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="f9ff5-110">15-16 位數</span><span class="sxs-lookup"><span data-stu-id="f9ff5-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="f9ff5-111">常值</span><span class="sxs-lookup"><span data-stu-id="f9ff5-111">Literals</span></span>

<span data-ttu-id="f9ff5-112">根據預設，指派運算子右邊的實數常值會視為 `double`。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="f9ff5-113">不過，如果您希望整數被視為 `double`，請使用後置字元 d 或 D，例如︰</span><span class="sxs-lookup"><span data-stu-id="f9ff5-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="f9ff5-114">轉換</span><span class="sxs-lookup"><span data-stu-id="f9ff5-114">Conversions</span></span>

<span data-ttu-id="f9ff5-115">您可以在一個運算式中混合使用數值整數型別和浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="f9ff5-116">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="f9ff5-117">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="f9ff5-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="f9ff5-118">如果其中一個浮點數類型是 `double`，運算式會評估為 `double` 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯和相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

- <span data-ttu-id="f9ff5-119">若在運算式中沒有 `double` 類型，則會評估為 [float](../../../csharp/language-reference/keywords/float.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯和相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

 <span data-ttu-id="f9ff5-120">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="f9ff5-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="f9ff5-121">正零和負零。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-121">Positive and negative zero.</span></span>

- <span data-ttu-id="f9ff5-122">正無限大和負無限大。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="f9ff5-123">非數字值 (NaN)。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="f9ff5-124">非零值的有限集合。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="f9ff5-125">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="f9ff5-126">範例</span><span class="sxs-lookup"><span data-stu-id="f9ff5-126">Example</span></span>

<span data-ttu-id="f9ff5-127">在下例中，一起新增 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 以得到 `double` 結果。</span><span class="sxs-lookup"><span data-stu-id="f9ff5-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="f9ff5-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f9ff5-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f9ff5-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9ff5-129">See Also</span></span>

- [<span data-ttu-id="f9ff5-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f9ff5-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f9ff5-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f9ff5-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f9ff5-132">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f9ff5-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f9ff5-133">預設值表</span><span class="sxs-lookup"><span data-stu-id="f9ff5-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
- [<span data-ttu-id="f9ff5-134">內建型別表</span><span class="sxs-lookup"><span data-stu-id="f9ff5-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="f9ff5-135">浮點型別表</span><span class="sxs-lookup"><span data-stu-id="f9ff5-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
- [<span data-ttu-id="f9ff5-136">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f9ff5-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="f9ff5-137">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f9ff5-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
