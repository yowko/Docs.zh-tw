---
title: "如何： 建立有調整規則的時區"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75e1867e810090bf35a0dfc7def5785747f94382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="166b0-102">如何： 建立有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="166b0-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="166b0-103">為應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：</span><span class="sxs-lookup"><span data-stu-id="166b0-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="166b0-104">時區永遠不會在本機系統登錄中已定義。</span><span class="sxs-lookup"><span data-stu-id="166b0-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="166b0-105">已經修改或移除登錄中時區的相關資料。</span><span class="sxs-lookup"><span data-stu-id="166b0-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="166b0-106">時區並沒有特定的歷程記錄期間時區調整的正確資訊。</span><span class="sxs-lookup"><span data-stu-id="166b0-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="166b0-107">在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。</span><span class="sxs-lookup"><span data-stu-id="166b0-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="166b0-108">您可以使用這個方法的多載來建立具有或沒有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="166b0-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="166b0-109">如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。</span><span class="sxs-lookup"><span data-stu-id="166b0-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="166b0-110">(如需這些詞彙的定義，請參閱 < 時區詞彙 」 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)</span><span class="sxs-lookup"><span data-stu-id="166b0-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="166b0-111">藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會加入至登錄。</span><span class="sxs-lookup"><span data-stu-id="166b0-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="166b0-112">相反地，他們可以只透過存取所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="166b0-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="166b0-113">本主題示範如何建立有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="166b0-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="166b0-114">若要建立不支援日光節約時間調整規則的時區，請參閱[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="166b0-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="166b0-115">若要建立採用浮動調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="166b0-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="166b0-116">每個調整 （也就是，針對每個轉換遠離和一段特定時間間隔回標準時間），執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="166b0-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="166b0-117">定義時區調整開始轉換的時間。</span><span class="sxs-lookup"><span data-stu-id="166b0-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="166b0-118">您必須呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法並將它傳遞<xref:System.DateTime>值，其定義的轉換、 定義轉換的月份的整數值、 整數值，定義轉換發生的當週的時間和<xref:System.DayOfWeek>定義轉換發生的一週天數的值。</span><span class="sxs-lookup"><span data-stu-id="166b0-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="166b0-119">這個方法呼叫會具現化<xref:System.TimeZoneInfo.TransitionTime>物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="166b0-120">定義結束轉換的時區調整的時間。</span><span class="sxs-lookup"><span data-stu-id="166b0-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="166b0-121">這需要另一個呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="166b0-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="166b0-122">這個方法呼叫會具現化第二個<xref:System.TimeZoneInfo.TransitionTime>物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="166b0-123">呼叫<xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A>方法並將它傳遞的有效開始和結束日期的調整，<xref:System.TimeSpan>物件，在轉換中，以及兩個定義的時間量<xref:System.TimeZoneInfo.TransitionTime>物件，以定義何時套用日光節約時間來回轉換發生時間。</span><span class="sxs-lookup"><span data-stu-id="166b0-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="166b0-124">這個方法呼叫會具現化<xref:System.TimeZoneInfo.AdjustmentRule>物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="166b0-125">指派<xref:System.TimeZoneInfo.AdjustmentRule>物件的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="166b0-126">定義時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="166b0-126">Define the time zone's display name.</span></span> <span data-ttu-id="166b0-127">顯示名稱會遵循國際標準時間 (UTC) 時區的位移加上括弧和後面的字串，識別時區，一或多個時區中，或其中一個城市的多個 cou 相當標準格式ntries 或時區中的區域。</span><span class="sxs-lookup"><span data-stu-id="166b0-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="166b0-128">定義時區標準時間名稱。</span><span class="sxs-lookup"><span data-stu-id="166b0-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="166b0-129">一般而言，這個字串也做時區的識別項。</span><span class="sxs-lookup"><span data-stu-id="166b0-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="166b0-130">定義時區的日光節約時間名稱。</span><span class="sxs-lookup"><span data-stu-id="166b0-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="166b0-131">如果您想要使用不同的識別項與時區的標準名稱，定義時區識別項。</span><span class="sxs-lookup"><span data-stu-id="166b0-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="166b0-132">具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="166b0-133">較晚於 UTC 的時區有正面的位移。</span><span class="sxs-lookup"><span data-stu-id="166b0-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="166b0-134">時間早於 UTC 的時區有了負數的位移。</span><span class="sxs-lookup"><span data-stu-id="166b0-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="166b0-135">呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法來具現化新的時區。</span><span class="sxs-lookup"><span data-stu-id="166b0-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="166b0-136">範例</span><span class="sxs-lookup"><span data-stu-id="166b0-136">Example</span></span>

<span data-ttu-id="166b0-137">下列範例會定義包含各種不同的時間間隔從 1918年至目前的調整規則的美國中部標準時區。</span><span class="sxs-lookup"><span data-stu-id="166b0-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="166b0-138">此範例中所建立的時區有多項調整規則。</span><span class="sxs-lookup"><span data-stu-id="166b0-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="166b0-139">小心以確保的有效開始和結束日期的任何調整規則未重疊的另一項調整規則的日期。</span><span class="sxs-lookup"><span data-stu-id="166b0-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="166b0-140">如果沒有重疊，<xref:System.InvalidTimeZoneException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="166b0-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="166b0-141">5 的值傳遞至浮點調整規則，`week`參數<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，以表示轉換發生在特定月份的最後一週。</span><span class="sxs-lookup"><span data-stu-id="166b0-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="166b0-142">在中建立的陣列<xref:System.TimeZoneInfo.AdjustmentRule>物件中使用<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType>方法呼叫的程式碼可以初始化數個調整時區建立所需的大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="166b0-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="166b0-143">相反地，這個程式碼範例會呼叫<xref:System.Collections.Generic.List%601.Add%2A>方法，將每個調整規則加入至泛型<xref:System.Collections.Generic.List%601>集合<xref:System.TimeZoneInfo.AdjustmentRule>物件。</span><span class="sxs-lookup"><span data-stu-id="166b0-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="166b0-144">然後程式碼會呼叫<xref:System.Collections.Generic.List%601.CopyTo%2A>方法，將此集合的成員複製到陣列。</span><span class="sxs-lookup"><span data-stu-id="166b0-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="166b0-145">此範例也會使用<xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A>方法，以定義固定日期調整。</span><span class="sxs-lookup"><span data-stu-id="166b0-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="166b0-146">這是類似於呼叫<xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>方法，但是它需要只時間、 月和日轉換參數。</span><span class="sxs-lookup"><span data-stu-id="166b0-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="166b0-147">可以使用下列程式碼來測試範例：</span><span class="sxs-lookup"><span data-stu-id="166b0-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="166b0-148">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="166b0-148">Compiling the code</span></span>

<span data-ttu-id="166b0-149">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="166b0-149">This example requires:</span></span>

* <span data-ttu-id="166b0-150">對 system.core.dll 的參考無法加入至專案。</span><span class="sxs-lookup"><span data-stu-id="166b0-150">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="166b0-151">應該是匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="166b0-151">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="166b0-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="166b0-152">See also</span></span>

<span data-ttu-id="166b0-153">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="166b0-153">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)</span></span>
