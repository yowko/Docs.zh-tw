---
title: "格式化數值結果表 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="f0bd2-102">格式化數值結果表 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f0bd2-102">Formatting Numeric Results Table (C# Reference)</span></span>
<span data-ttu-id="f0bd2-103">您可以使用 <xref:System.String.Format%2A?displayProperty=fullName> 方法，或透過會呼叫 `String.Format` 的 <xref:System.Console.Write%2A?displayProperty=fullName> 或 <xref:System.Console.WriteLine%2A?displayProperty=fullName> 方法格式化數值結果。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-103">You can format numeric results by using the <xref:System.String.Format%2A?displayProperty=fullName> method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> or <xref:System.Console.WriteLine%2A?displayProperty=fullName> method, which calls `String.Format`.</span></span> <span data-ttu-id="f0bd2-104">使用格式字串來指定格式。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-104">The format is specified by using format strings.</span></span> <span data-ttu-id="f0bd2-105">下表包含支援的標準格式字串。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-105">The following table contains the supported standard format strings.</span></span> <span data-ttu-id="f0bd2-106">格式字串的格式如下︰`Axx`，其中 `A` 是格式規範，而 `xx` 是有效位數規範。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-106">The format string takes the following form: `Axx`, where `A` is the format specifier and `xx` is the precision specifier.</span></span> <span data-ttu-id="f0bd2-107">格式規範控制套用到數值之格式的類型，而有效位數規範控制格式化輸出的有效位數或小數位數。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-107">The format specifier controls the type of formatting applied to the numeric value, and the precision specifier controls the number of significant digits or decimal places of the formatted output.</span></span> <span data-ttu-id="f0bd2-108">有效位數規範的值範圍是從 0 到 99。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-108">The value of the precision specifier ranges from 0 to 99.</span></span>  
  
 <span data-ttu-id="f0bd2-109">如需標準和自訂格式字串的詳細資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-109">For more information about standard and custom formatting strings, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="f0bd2-110">如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="f0bd2-110">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
|<span data-ttu-id="f0bd2-111">格式規範</span><span class="sxs-lookup"><span data-stu-id="f0bd2-111">Format Specifier</span></span>|<span data-ttu-id="f0bd2-112">描述</span><span class="sxs-lookup"><span data-stu-id="f0bd2-112">Description</span></span>|<span data-ttu-id="f0bd2-113">範例</span><span class="sxs-lookup"><span data-stu-id="f0bd2-113">Examples</span></span>|<span data-ttu-id="f0bd2-114">輸出</span><span class="sxs-lookup"><span data-stu-id="f0bd2-114">Output</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="f0bd2-115">C 或 c</span><span class="sxs-lookup"><span data-stu-id="f0bd2-115">C or c</span></span>|<span data-ttu-id="f0bd2-116">貨幣</span><span class="sxs-lookup"><span data-stu-id="f0bd2-116">Currency</span></span>|<span data-ttu-id="f0bd2-117">Console.Write("{0:C}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-117">Console.Write("{0:C}", 2.5);</span></span><br /><br /> <span data-ttu-id="f0bd2-118">Console.Write("{0:C}", -2.5);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-118">Console.Write("{0:C}", -2.5);</span></span>|<span data-ttu-id="f0bd2-119">$2.50</span><span class="sxs-lookup"><span data-stu-id="f0bd2-119">$2.50</span></span><br /><br /> <span data-ttu-id="f0bd2-120">($2.50)</span><span class="sxs-lookup"><span data-stu-id="f0bd2-120">($2.50)</span></span>|  
|<span data-ttu-id="f0bd2-121">D 或 d</span><span class="sxs-lookup"><span data-stu-id="f0bd2-121">D or d</span></span>|<span data-ttu-id="f0bd2-122">Decimal</span><span class="sxs-lookup"><span data-stu-id="f0bd2-122">Decimal</span></span>|<span data-ttu-id="f0bd2-123">Console.Write("{0:D5}", 25);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-123">Console.Write("{0:D5}", 25);</span></span>|<span data-ttu-id="f0bd2-124">00025</span><span class="sxs-lookup"><span data-stu-id="f0bd2-124">00025</span></span>|  
|<span data-ttu-id="f0bd2-125">E 或 e</span><span class="sxs-lookup"><span data-stu-id="f0bd2-125">E or e</span></span>|<span data-ttu-id="f0bd2-126">科學記號</span><span class="sxs-lookup"><span data-stu-id="f0bd2-126">Scientific</span></span>|<span data-ttu-id="f0bd2-127">Console.Write("{0:E}", 250000);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-127">Console.Write("{0:E}", 250000);</span></span>|<span data-ttu-id="f0bd2-128">2.500000E+005</span><span class="sxs-lookup"><span data-stu-id="f0bd2-128">2.500000E+005</span></span>|  
|<span data-ttu-id="f0bd2-129">F 或 f</span><span class="sxs-lookup"><span data-stu-id="f0bd2-129">F or f</span></span>|<span data-ttu-id="f0bd2-130">固定點</span><span class="sxs-lookup"><span data-stu-id="f0bd2-130">Fixed-point</span></span>|<span data-ttu-id="f0bd2-131">Console.Write("{0:F2}", 25);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-131">Console.Write("{0:F2}", 25);</span></span><br /><br /> <span data-ttu-id="f0bd2-132">Console.Write("{0:F0}", 25);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-132">Console.Write("{0:F0}", 25);</span></span>|<span data-ttu-id="f0bd2-133">25.00</span><span class="sxs-lookup"><span data-stu-id="f0bd2-133">25.00</span></span><br /><br /> <span data-ttu-id="f0bd2-134">25</span><span class="sxs-lookup"><span data-stu-id="f0bd2-134">25</span></span>|  
|<span data-ttu-id="f0bd2-135">G 或 g</span><span class="sxs-lookup"><span data-stu-id="f0bd2-135">G or g</span></span>|<span data-ttu-id="f0bd2-136">一般</span><span class="sxs-lookup"><span data-stu-id="f0bd2-136">General</span></span>|<span data-ttu-id="f0bd2-137">Console.Write("{0:G}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-137">Console.Write("{0:G}", 2.5);</span></span>|<span data-ttu-id="f0bd2-138">2.5</span><span class="sxs-lookup"><span data-stu-id="f0bd2-138">2.5</span></span>|  
|<span data-ttu-id="f0bd2-139">N 或 n</span><span class="sxs-lookup"><span data-stu-id="f0bd2-139">N or n</span></span>|<span data-ttu-id="f0bd2-140">數字</span><span class="sxs-lookup"><span data-stu-id="f0bd2-140">Number</span></span>|<span data-ttu-id="f0bd2-141">Console.Write("{0:N}", 2500000);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-141">Console.Write("{0:N}", 2500000);</span></span>|<span data-ttu-id="f0bd2-142">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="f0bd2-142">2,500,000.00</span></span>|  
|<span data-ttu-id="f0bd2-143">X 或 x</span><span class="sxs-lookup"><span data-stu-id="f0bd2-143">X or x</span></span>|<span data-ttu-id="f0bd2-144">十六進位</span><span class="sxs-lookup"><span data-stu-id="f0bd2-144">Hexadecimal</span></span>|<span data-ttu-id="f0bd2-145">Console.Write("{0:X}", 250);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-145">Console.Write("{0:X}", 250);</span></span><br /><br /> <span data-ttu-id="f0bd2-146">Console.Write("{0:X}", 0xffff);</span><span class="sxs-lookup"><span data-stu-id="f0bd2-146">Console.Write("{0:X}", 0xffff);</span></span>|<span data-ttu-id="f0bd2-147">FA</span><span class="sxs-lookup"><span data-stu-id="f0bd2-147">FA</span></span><br /><br /> <span data-ttu-id="f0bd2-148">FFFF</span><span class="sxs-lookup"><span data-stu-id="f0bd2-148">FFFF</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0bd2-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0bd2-149">See Also</span></span>  
 <span data-ttu-id="f0bd2-150">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f0bd2-150">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f0bd2-151">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f0bd2-151">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f0bd2-152">[標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="f0bd2-152">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="f0bd2-153">[類型的參考表](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="f0bd2-153">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 [<span data-ttu-id="f0bd2-154">string</span><span class="sxs-lookup"><span data-stu-id="f0bd2-154">string</span></span>](../../../csharp/language-reference/keywords/string.md)

