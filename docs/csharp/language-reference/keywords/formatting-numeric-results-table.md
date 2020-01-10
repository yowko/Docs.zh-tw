---
title: 格式化數值結果表 - C# 參考
description: 深入了解 C# 標準數值格式字串
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: eb93f0a4f3c66e9f7b295366a77b9fb099fc3a1e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713502"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="444ec-103">格式化數值結果表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="444ec-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="444ec-104">下表顯示用來格式化數值結果的支援格式規範。</span><span class="sxs-lookup"><span data-stu-id="444ec-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="444ec-105">最後一個資料行中的格式化結果會對應至 "en-US" <xref:System.Globalization.CultureInfo>。</span><span class="sxs-lookup"><span data-stu-id="444ec-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="444ec-106">格式規範</span><span class="sxs-lookup"><span data-stu-id="444ec-106">Format specifier</span></span>|<span data-ttu-id="444ec-107">描述</span><span class="sxs-lookup"><span data-stu-id="444ec-107">Description</span></span>|<span data-ttu-id="444ec-108">範例</span><span class="sxs-lookup"><span data-stu-id="444ec-108">Examples</span></span>|<span data-ttu-id="444ec-109">結果</span><span class="sxs-lookup"><span data-stu-id="444ec-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="444ec-110">C 或 c</span><span class="sxs-lookup"><span data-stu-id="444ec-110">C or c</span></span>|<span data-ttu-id="444ec-111">貨幣</span><span class="sxs-lookup"><span data-stu-id="444ec-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="444ec-112">\\$2.50</span><span class="sxs-lookup"><span data-stu-id="444ec-112">\\$2.50</span></span><br /><br /> <span data-ttu-id="444ec-113">（\\$2.50）</span><span class="sxs-lookup"><span data-stu-id="444ec-113">(\\$2.50)</span></span>|  
|<span data-ttu-id="444ec-114">D 或 d</span><span class="sxs-lookup"><span data-stu-id="444ec-114">D or d</span></span>|<span data-ttu-id="444ec-115">Decimal</span><span class="sxs-lookup"><span data-stu-id="444ec-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="444ec-116">00025</span><span class="sxs-lookup"><span data-stu-id="444ec-116">00025</span></span>|  
|<span data-ttu-id="444ec-117">E 或 e</span><span class="sxs-lookup"><span data-stu-id="444ec-117">E or e</span></span>|<span data-ttu-id="444ec-118">指數</span><span class="sxs-lookup"><span data-stu-id="444ec-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="444ec-119">2.50E+005</span><span class="sxs-lookup"><span data-stu-id="444ec-119">2.50E+005</span></span>|  
|<span data-ttu-id="444ec-120">F 或 f</span><span class="sxs-lookup"><span data-stu-id="444ec-120">F or f</span></span>|<span data-ttu-id="444ec-121">固定點</span><span class="sxs-lookup"><span data-stu-id="444ec-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="444ec-122">2.50</span><span class="sxs-lookup"><span data-stu-id="444ec-122">2.50</span></span><br /><br /> <span data-ttu-id="444ec-123">3</span><span class="sxs-lookup"><span data-stu-id="444ec-123">3</span></span>|  
|<span data-ttu-id="444ec-124">G 或 g</span><span class="sxs-lookup"><span data-stu-id="444ec-124">G or g</span></span>|<span data-ttu-id="444ec-125">一般</span><span class="sxs-lookup"><span data-stu-id="444ec-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="444ec-126">2.5</span><span class="sxs-lookup"><span data-stu-id="444ec-126">2.5</span></span>|  
|<span data-ttu-id="444ec-127">N 或 n</span><span class="sxs-lookup"><span data-stu-id="444ec-127">N or n</span></span>|<span data-ttu-id="444ec-128">數字</span><span class="sxs-lookup"><span data-stu-id="444ec-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="444ec-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="444ec-129">2,500,000.00</span></span>|  
|<span data-ttu-id="444ec-130">P 或 p</span><span class="sxs-lookup"><span data-stu-id="444ec-130">P or p</span></span>|<span data-ttu-id="444ec-131">百分比</span><span class="sxs-lookup"><span data-stu-id="444ec-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="444ec-132">25.00%</span><span class="sxs-lookup"><span data-stu-id="444ec-132">25.00%</span></span>|  
|<span data-ttu-id="444ec-133">R 或 r</span><span class="sxs-lookup"><span data-stu-id="444ec-133">R or r</span></span>|<span data-ttu-id="444ec-134">來回</span><span class="sxs-lookup"><span data-stu-id="444ec-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="444ec-135">2.5</span><span class="sxs-lookup"><span data-stu-id="444ec-135">2.5</span></span>|  
|<span data-ttu-id="444ec-136">X 或 x</span><span class="sxs-lookup"><span data-stu-id="444ec-136">X or x</span></span>|<span data-ttu-id="444ec-137">十六進位</span><span class="sxs-lookup"><span data-stu-id="444ec-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="444ec-138">FA</span><span class="sxs-lookup"><span data-stu-id="444ec-138">FA</span></span><br /><br /> <span data-ttu-id="444ec-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="444ec-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="444ec-140">備註</span><span class="sxs-lookup"><span data-stu-id="444ec-140">Remarks</span></span>

<span data-ttu-id="444ec-141">您可以使用格式規範來建立格式字串。</span><span class="sxs-lookup"><span data-stu-id="444ec-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="444ec-142">格式字串的格式如下：`Axx`，其中</span><span class="sxs-lookup"><span data-stu-id="444ec-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="444ec-143">`A` 是格式規範，可控制套用到數值的格式化類型。</span><span class="sxs-lookup"><span data-stu-id="444ec-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="444ec-144">`xx` 是有效位數規範，會影響格式化輸出中的位數。</span><span class="sxs-lookup"><span data-stu-id="444ec-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="444ec-145">有效位數規範的值範圍是從 0 到 99。</span><span class="sxs-lookup"><span data-stu-id="444ec-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="444ec-146">僅整數類型可支援十進位 ("D" 或 "d") 和十六進位 ("X" 或 "x") 格式規範。</span><span class="sxs-lookup"><span data-stu-id="444ec-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="444ec-147">僅 <xref:System.Single>、<xref:System.Double> 和 <xref:System.Numerics.BigInteger> 類型支援來回行程 ("R" 或 "r") 格式規範。</span><span class="sxs-lookup"><span data-stu-id="444ec-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="444ec-148">標準數值格式字串受到下列各項支援：</span><span class="sxs-lookup"><span data-stu-id="444ec-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="444ec-149">所有數值類型之 `ToString` 方法的一些多載。</span><span class="sxs-lookup"><span data-stu-id="444ec-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="444ec-150">例如，您可以將數值格式字串提供給 <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> 和 <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="444ec-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="444ec-151">.NET [複合格式化功能](../../../standard/base-types/composite-formatting.md)，可受到 <xref:System.String.Format%2A?displayProperty=nameWithType> 之類的方法支援。</span><span class="sxs-lookup"><span data-stu-id="444ec-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="444ec-152">[插入字串](../tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="444ec-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="444ec-153">如需詳細資訊，請參閱[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="444ec-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="444ec-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="444ec-154">See also</span></span>

- [<span data-ttu-id="444ec-155">C# 參考</span><span class="sxs-lookup"><span data-stu-id="444ec-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="444ec-156">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="444ec-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="444ec-157">格式化類型</span><span class="sxs-lookup"><span data-stu-id="444ec-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="444ec-158">複合格式</span><span class="sxs-lookup"><span data-stu-id="444ec-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="444ec-159">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="444ec-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="444ec-160">string</span><span class="sxs-lookup"><span data-stu-id="444ec-160">string</span></span>](../builtin-types/reference-types.md)
