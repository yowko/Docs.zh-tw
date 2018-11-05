---
title: float 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: da697aa6f1f429418a69d9f58a13f46a3da9ac74
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187175"
---
# <a name="float-c-reference"></a><span data-ttu-id="f05a3-102">float (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f05a3-102">float (C# Reference)</span></span>

<span data-ttu-id="f05a3-103">`float` 關鍵字表示儲存 32 位元浮點值的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="f05a3-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="f05a3-104">下表顯示 `float` 類型的精確度和大概範圍。</span><span class="sxs-lookup"><span data-stu-id="f05a3-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="f05a3-105">類型</span><span class="sxs-lookup"><span data-stu-id="f05a3-105">Type</span></span>|<span data-ttu-id="f05a3-106">大概範圍</span><span class="sxs-lookup"><span data-stu-id="f05a3-106">Approximate range</span></span>|<span data-ttu-id="f05a3-107">精確度</span><span class="sxs-lookup"><span data-stu-id="f05a3-107">Precision</span></span>|<span data-ttu-id="f05a3-108">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="f05a3-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="f05a3-109">±1.5 x 10<sup>−45</sup> 到 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="f05a3-109">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="f05a3-110">~6-9 位數</span><span class="sxs-lookup"><span data-stu-id="f05a3-110">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="f05a3-111">常值</span><span class="sxs-lookup"><span data-stu-id="f05a3-111">Literals</span></span>

<span data-ttu-id="f05a3-112">根據預設，指派運算子右邊的實數常值會視為 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="f05a3-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="f05a3-113">因此，若要初始化 float 變數，請使用後置字元 `f` 或 `F`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f05a3-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="f05a3-114">如果您在上述宣告中未使用此後置字元，由於您嘗試將 [double](double.md) 值儲存至 `float` 變數，因此會收到編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f05a3-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="f05a3-115">轉換</span><span class="sxs-lookup"><span data-stu-id="f05a3-115">Conversions</span></span>

<span data-ttu-id="f05a3-116">您可以在一個運算式中混合使用數值整數型別和浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f05a3-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="f05a3-117">在此情況下，整數型別會轉換成浮點類型。</span><span class="sxs-lookup"><span data-stu-id="f05a3-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="f05a3-118">運算式的評估會根據下列規則來執行：</span><span class="sxs-lookup"><span data-stu-id="f05a3-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="f05a3-119">如果其中一個浮點數型別是 [double](double.md)，則運算式會評估為 [double](double.md) 或 [bool](bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="f05a3-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md), or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

- <span data-ttu-id="f05a3-120">若在運算式中沒有 [double](double.md) 型別，則運算式會評估為 `float` 或 [bool](bool.md) (在關聯或相等比較中)。</span><span class="sxs-lookup"><span data-stu-id="f05a3-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="f05a3-121">浮點運算式可以包含下列值的集合：</span><span class="sxs-lookup"><span data-stu-id="f05a3-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="f05a3-122">正零和負零</span><span class="sxs-lookup"><span data-stu-id="f05a3-122">Positive and negative zero</span></span>

- <span data-ttu-id="f05a3-123">正無限大和負無限大</span><span class="sxs-lookup"><span data-stu-id="f05a3-123">Positive and negative infinity</span></span>

- <span data-ttu-id="f05a3-124">非數字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="f05a3-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="f05a3-125">非零值的有限集合</span><span class="sxs-lookup"><span data-stu-id="f05a3-125">The finite set of nonzero values</span></span>

<span data-ttu-id="f05a3-126">如需這些值的詳細資訊，請參閱 [IEEE](https://www.ieee.org) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。</span><span class="sxs-lookup"><span data-stu-id="f05a3-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="f05a3-127">範例</span><span class="sxs-lookup"><span data-stu-id="f05a3-127">Example</span></span>

<span data-ttu-id="f05a3-128">在下列範例中，會將一個 [int](int.md)、[short](short.md) 和 `float` 加入數學運算式，以產生 `float` 結果</span><span class="sxs-lookup"><span data-stu-id="f05a3-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="f05a3-129">(請記住，`float` 是 <xref:System.Single?displayProperty=nameWithType> 類型的別名。)請注意，運算式中沒有 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="f05a3-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="f05a3-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f05a3-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f05a3-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05a3-131">See also</span></span>

- <xref:System.Single>  
- [<span data-ttu-id="f05a3-132">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f05a3-132">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="f05a3-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f05a3-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="f05a3-134">轉換和型別轉換</span><span class="sxs-lookup"><span data-stu-id="f05a3-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="f05a3-135">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f05a3-135">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="f05a3-136">整數型別表</span><span class="sxs-lookup"><span data-stu-id="f05a3-136">Integral Types Table</span></span>](integral-types-table.md)  
- [<span data-ttu-id="f05a3-137">內建型別表</span><span class="sxs-lookup"><span data-stu-id="f05a3-137">Built-In Types Table</span></span>](built-in-types-table.md)  
- [<span data-ttu-id="f05a3-138">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f05a3-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="f05a3-139">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="f05a3-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  