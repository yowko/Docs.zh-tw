---
title: HOW TO：在日期和時間運算中使用時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 053ca2d10deadf58d5bb8b4628fb5dee815d82c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682688"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="1077d-102">HOW TO：在日期和時間運算中使用時區</span><span class="sxs-lookup"><span data-stu-id="1077d-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="1077d-103">一般情況下，當您執行日期和時間設定使用的算術<xref:System.DateTime>或<xref:System.DateTimeOffset>值，結果不會反映任何時區調整規則。</span><span class="sxs-lookup"><span data-stu-id="1077d-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="1077d-104">這是 true 即使的日期和時間值的時區是清楚識別 (例如，當<xref:System.DateTime.Kind%2A>屬性設定為<xref:System.DateTimeKind.Local>)。</span><span class="sxs-lookup"><span data-stu-id="1077d-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="1077d-105">本主題說明如何對屬於特定時區的日期和時間值執行算術運算。</span><span class="sxs-lookup"><span data-stu-id="1077d-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="1077d-106">算術運算的結果將反映時區調整規則。</span><span class="sxs-lookup"><span data-stu-id="1077d-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="1077d-107">將調整規則套用至日期和時間運算</span><span class="sxs-lookup"><span data-stu-id="1077d-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="1077d-108">實作某種方法，以將日期和時間值與所屬時區緊密結合。</span><span class="sxs-lookup"><span data-stu-id="1077d-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="1077d-109">例如，宣告包含日期和時間值及其時區的結構。</span><span class="sxs-lookup"><span data-stu-id="1077d-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="1077d-110">下列範例會使用這種方法來連結<xref:System.DateTime>與其時區的值。</span><span class="sxs-lookup"><span data-stu-id="1077d-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="1077d-111">藉由呼叫轉換為 Coordinated Universal Time (UTC) 的時間<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>方法或<xref:System.TimeZoneInfo.ConvertTime%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="1077d-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="1077d-112">對 UTC 時間執行算術運算。</span><span class="sxs-lookup"><span data-stu-id="1077d-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="1077d-113">將時間從 UTC 轉換為原始時間的相關設定的時區，藉由呼叫<xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="1077d-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="1077d-114">範例</span><span class="sxs-lookup"><span data-stu-id="1077d-114">Example</span></span>

<span data-ttu-id="1077d-115">下列範例將兩個小時三十分鐘新增至 2008 年 3 月 9 日凌晨 1:30</span><span class="sxs-lookup"><span data-stu-id="1077d-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="1077d-116">中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="1077d-116">Central Standard Time.</span></span> <span data-ttu-id="1077d-117">時區轉換為日光節約時間會在三十分鐘後，也就是 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="1077d-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="1077d-118">凌晨 5:00。</span><span class="sxs-lookup"><span data-stu-id="1077d-118">on March 9, 2008.</span></span> <span data-ttu-id="1077d-119">由於本範例依照上一節所列的四個步驟進行，因此會正確回報產生的時間 2008 年 3 月 9 日</span><span class="sxs-lookup"><span data-stu-id="1077d-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="1077d-120">凌晨 5:00。</span><span class="sxs-lookup"><span data-stu-id="1077d-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="1077d-121">兩者<xref:System.DateTime>和<xref:System.DateTimeOffset>其可能所屬的任何時區解除關聯的值。</span><span class="sxs-lookup"><span data-stu-id="1077d-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="1077d-122">若要透過自動套用時區調整規則來執行日期和時間運算，則必須立即識別任何日期和時間值所屬的時區。</span><span class="sxs-lookup"><span data-stu-id="1077d-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="1077d-123">這表示日期和時間及其相關聯時區必須緊密結合。</span><span class="sxs-lookup"><span data-stu-id="1077d-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="1077d-124">有幾個方式可做到這點，包括下列各項︰</span><span class="sxs-lookup"><span data-stu-id="1077d-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="1077d-125">假設應用程式中使用的所有時間都是屬於特定時區。</span><span class="sxs-lookup"><span data-stu-id="1077d-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="1077d-126">雖然適用於某些情況，但是這種方式提供的彈性有限，可攜性也可能有限。</span><span class="sxs-lookup"><span data-stu-id="1077d-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="1077d-127">定義一種類型，而這個類型透過將日期和時間與其相關聯時區都包含為類型的欄位來緊密結合兩者。</span><span class="sxs-lookup"><span data-stu-id="1077d-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="1077d-128">程式碼範例中使用這種方式，以定義將日期和時間以及時區儲存在兩個成員欄位中的結構。</span><span class="sxs-lookup"><span data-stu-id="1077d-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="1077d-129">此範例說明如何在上執行算術運算<xref:System.DateTime>值，使時區調整規則會套用到結果。</span><span class="sxs-lookup"><span data-stu-id="1077d-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="1077d-130">不過，<xref:System.DateTimeOffset>可以輕鬆地使用值。</span><span class="sxs-lookup"><span data-stu-id="1077d-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="1077d-131">下列範例說明如何中原始範例的程式碼可能會使用適用於<xref:System.DateTimeOffset>而不是<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="1077d-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="1077d-132">請注意，如果這個加法只會對<xref:System.DateTimeOffset>值沒有先將它轉換成 UTC，結果會反映正確的點的時間，但其位移不會反映指定時區的時間。</span><span class="sxs-lookup"><span data-stu-id="1077d-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1077d-133">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1077d-133">Compiling the code</span></span>

<span data-ttu-id="1077d-134">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1077d-134">This example requires:</span></span>

* <span data-ttu-id="1077d-135">對 System.Core.dll 的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="1077d-135">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="1077d-136">該<xref:System>命名空間匯入與`using`陳述式 （C# 程式碼所需）。</span><span class="sxs-lookup"><span data-stu-id="1077d-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1077d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1077d-137">See also</span></span>

- [<span data-ttu-id="1077d-138">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="1077d-138">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="1077d-139">使用日期與時間執行算術運算</span><span class="sxs-lookup"><span data-stu-id="1077d-139">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
