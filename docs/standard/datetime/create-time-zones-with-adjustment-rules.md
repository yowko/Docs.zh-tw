---
title: How to：建立具有調整規則的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
ms.openlocfilehash: b7e938581dfde3f1566aa2506302292686c2fc5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278164"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a><span data-ttu-id="3206d-102">How to：建立具有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3206d-102">How to: Create time zones with adjustment rules</span></span>

<span data-ttu-id="3206d-103">應用程式所需的精確時區資訊可能因下列幾個原因而不存在於特定系統上：</span><span class="sxs-lookup"><span data-stu-id="3206d-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="3206d-104">本機系統的登錄中從未定義過時區。</span><span class="sxs-lookup"><span data-stu-id="3206d-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="3206d-105">已從登錄中修改或移除時區的相關資料。</span><span class="sxs-lookup"><span data-stu-id="3206d-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="3206d-106">時區對於特定的歷程記錄期間，沒有時區調整的精確資訊。</span><span class="sxs-lookup"><span data-stu-id="3206d-106">The time zone does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="3206d-107">在這些情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法來定義應用程式所需的時區。</span><span class="sxs-lookup"><span data-stu-id="3206d-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="3206d-108">您可以使用這個方法的多載來建立具有或不含調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="3206d-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="3206d-109">如果時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整。</span><span class="sxs-lookup"><span data-stu-id="3206d-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="3206d-110">（如需這些詞彙的定義，請參閱時區[總覽](time-zone-overview.md)中的「時區詞彙」一節）。</span><span class="sxs-lookup"><span data-stu-id="3206d-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3206d-111">藉由呼叫方法所建立的自訂時間區域 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="3206d-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="3206d-112">相反地，它們只能透過方法呼叫所傳回的物件參考來存取 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3206d-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="3206d-113">本主題說明如何建立具有調整規則的時區。</span><span class="sxs-lookup"><span data-stu-id="3206d-113">This topic shows how to create a time zone with adjustment rules.</span></span> <span data-ttu-id="3206d-114">若要建立不支援日光節約時間調整規則的時區，請參閱[如何：建立沒有調整規則的時區](create-time-zones-without-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="3206d-114">To create a time zone that does not support daylight saving time adjustment rules, see [How to: Create Time Zones Without Adjustment Rules](create-time-zones-without-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a><span data-ttu-id="3206d-115">建立具有浮動調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3206d-115">To create a time zone with floating adjustment rules</span></span>

1. <span data-ttu-id="3206d-116">針對每個調整（也就是在特定時間間隔內，每個轉換遠離或回到標準時間），執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="3206d-116">For each adjustment (that is, for each transition away from and back to standard time over a particular time interval), do the following:</span></span>

    1. <span data-ttu-id="3206d-117">定義時區調整的開始轉換時間。</span><span class="sxs-lookup"><span data-stu-id="3206d-117">Define the starting transition time for the time zone adjustment.</span></span>

       <span data-ttu-id="3206d-118">您必須呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> 方法，並傳遞一個 <xref:System.DateTime> 值來定義轉換的時間、定義轉換之月份的整數值、定義轉換發生之周的整數值，以及 <xref:System.DayOfWeek> 定義發生轉換之周間日期的一個值。</span><span class="sxs-lookup"><span data-stu-id="3206d-118">You must call the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method and pass it a <xref:System.DateTime> value that defines the time of the transition, an integer value that defines the month of the transition, an integer value that defines the week on which the transition occurs, and a <xref:System.DayOfWeek> value that defines the day of the week on which the transition occurs.</span></span> <span data-ttu-id="3206d-119">這個方法呼叫會具現化 <xref:System.TimeZoneInfo.TransitionTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="3206d-119">This method call instantiates a <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    2. <span data-ttu-id="3206d-120">定義時區調整的結束轉換時間。</span><span class="sxs-lookup"><span data-stu-id="3206d-120">Define the ending transition time for the time zone adjustment.</span></span> <span data-ttu-id="3206d-121">這需要對方法進行另一個呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3206d-121">This requires another call to the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3206d-122">這個方法呼叫會具現化第二個 <xref:System.TimeZoneInfo.TransitionTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="3206d-122">This method call instantiates a second <xref:System.TimeZoneInfo.TransitionTime> object.</span></span>

    3. <span data-ttu-id="3206d-123">呼叫 <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> 方法，並將調整的有效開始和結束日期、 <xref:System.TimeSpan> 定義轉換中時間量的物件，以及在 <xref:System.TimeZoneInfo.TransitionTime> 日光節約時間發生轉換時定義的兩個物件傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="3206d-123">Call the <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> method and pass it the effective start and end dates of the adjustment, a <xref:System.TimeSpan> object that defines the amount of time in the transition, and the two <xref:System.TimeZoneInfo.TransitionTime> objects that define when the transitions to and from daylight saving time occur.</span></span> <span data-ttu-id="3206d-124">這個方法呼叫會具現化 <xref:System.TimeZoneInfo.AdjustmentRule> 物件。</span><span class="sxs-lookup"><span data-stu-id="3206d-124">This method call instantiates a <xref:System.TimeZoneInfo.AdjustmentRule> object.</span></span>

    4. <span data-ttu-id="3206d-125">將 <xref:System.TimeZoneInfo.AdjustmentRule> 物件指派給物件的陣列 <xref:System.TimeZoneInfo.AdjustmentRule> 。</span><span class="sxs-lookup"><span data-stu-id="3206d-125">Assign the <xref:System.TimeZoneInfo.AdjustmentRule> object to an array of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span>

2. <span data-ttu-id="3206d-126">定義時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3206d-126">Define the time zone's display name.</span></span> <span data-ttu-id="3206d-127">顯示名稱遵循相當標準的格式，其中時區與國際標準時間（UTC）的位移會括在括弧中，後面接著識別時區的字串、時區中的一或多個城市，或時區中的一或多個國家或地區。</span><span class="sxs-lookup"><span data-stu-id="3206d-127">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

3. <span data-ttu-id="3206d-128">定義時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="3206d-128">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="3206d-129">通常，這個字串也會當做時區的識別碼使用。</span><span class="sxs-lookup"><span data-stu-id="3206d-129">Typically, this string is also used as the time zone's identifier.</span></span>

4. <span data-ttu-id="3206d-130">定義時區的日光節約時間名稱。</span><span class="sxs-lookup"><span data-stu-id="3206d-130">Define the name of the time zone's daylight time.</span></span>

5. <span data-ttu-id="3206d-131">如果您想要使用與時區標準名稱不同的識別碼，請定義時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="3206d-131">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

6. <span data-ttu-id="3206d-132">具現化 <xref:System.TimeSpan> 物件，其定義時區與 UTC 的位移。</span><span class="sxs-lookup"><span data-stu-id="3206d-132">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="3206d-133">時間與 UTC 時間較晚的時區具有正位移。</span><span class="sxs-lookup"><span data-stu-id="3206d-133">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="3206d-134">具有早于 UTC 時間的時區具有負位移。</span><span class="sxs-lookup"><span data-stu-id="3206d-134">Time zones with times that are earlier than UTC have a negative offset.</span></span>

7. <span data-ttu-id="3206d-135">呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 方法，以具現化新的時區。</span><span class="sxs-lookup"><span data-stu-id="3206d-135">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="3206d-136">範例</span><span class="sxs-lookup"><span data-stu-id="3206d-136">Example</span></span>

<span data-ttu-id="3206d-137">下列範例會定義美國中部標準時區，其中包含從1918到目前為止的各種時間間隔的調整規則。</span><span class="sxs-lookup"><span data-stu-id="3206d-137">The following example defines a Central Standard Time zone for the United States that includes adjustment rules for a variety of time intervals from 1918 to the present.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

<span data-ttu-id="3206d-138">在此範例中建立的時區有多個調整規則。</span><span class="sxs-lookup"><span data-stu-id="3206d-138">The time zone created in this example has multiple adjustment rules.</span></span> <span data-ttu-id="3206d-139">請務必小心，以確保任何調整規則的有效開始和結束日期不會與另一個調整規則的日期重迭。</span><span class="sxs-lookup"><span data-stu-id="3206d-139">Care must be taken to ensure that the effective start and end dates of any adjustment rule do not overlap with the dates of another adjustment rule.</span></span> <span data-ttu-id="3206d-140">如果有重迭， <xref:System.InvalidTimeZoneException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="3206d-140">If there is an overlap, an <xref:System.InvalidTimeZoneException> is thrown.</span></span>

<span data-ttu-id="3206d-141">對於浮動調整規則，值5會傳遞至方法的 `week` 參數， <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 以指出轉換會在特定月份的最後一周發生。</span><span class="sxs-lookup"><span data-stu-id="3206d-141">For floating adjustment rules, the value 5 is passed to the `week` parameter of the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method to indicate that the transition occurs on the last week of a particular month.</span></span>

<span data-ttu-id="3206d-142">在建立 <xref:System.TimeZoneInfo.AdjustmentRule> 要在方法呼叫中使用的物件陣列 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> 時，程式碼可以將陣列初始化為要為時區建立的調整數目所需的大小。</span><span class="sxs-lookup"><span data-stu-id="3206d-142">In creating the array of <xref:System.TimeZoneInfo.AdjustmentRule> objects to use in the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> method call, the code could initialize the array to the size required by the number of adjustments to be created for the time zone.</span></span> <span data-ttu-id="3206d-143">相反地，此程式碼範例會呼叫 <xref:System.Collections.Generic.List%601.Add%2A> 方法，以將每個調整規則新增至物件的泛型 <xref:System.Collections.Generic.List%601> 集合 <xref:System.TimeZoneInfo.AdjustmentRule> 。</span><span class="sxs-lookup"><span data-stu-id="3206d-143">Instead, this code example calls the <xref:System.Collections.Generic.List%601.Add%2A> method to add each adjustment rule to a generic <xref:System.Collections.Generic.List%601> collection of <xref:System.TimeZoneInfo.AdjustmentRule> objects.</span></span> <span data-ttu-id="3206d-144">然後，程式碼會呼叫 <xref:System.Collections.Generic.List%601.CopyTo%2A> 方法，將這個集合的成員複製到陣列。</span><span class="sxs-lookup"><span data-stu-id="3206d-144">The code then calls the <xref:System.Collections.Generic.List%601.CopyTo%2A> method to copy the members of this collection to the array.</span></span>

<span data-ttu-id="3206d-145">此範例也會使用 <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> 方法來定義固定日期的調整。</span><span class="sxs-lookup"><span data-stu-id="3206d-145">The example also uses the <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> method to define fixed-date adjustments.</span></span> <span data-ttu-id="3206d-146">這類似于呼叫 <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> 方法，不同之處在于它只需要時間、月份和轉換參數的日期。</span><span class="sxs-lookup"><span data-stu-id="3206d-146">This is similar to calling the <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> method, except that it requires only the time, month, and day of the transition parameters.</span></span>

<span data-ttu-id="3206d-147">您可以使用下列程式碼來測試此範例：</span><span class="sxs-lookup"><span data-stu-id="3206d-147">The example can be tested using code such as the following:</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a><span data-ttu-id="3206d-148">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3206d-148">Compiling the code</span></span>

<span data-ttu-id="3206d-149">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3206d-149">This example requires:</span></span>

- <span data-ttu-id="3206d-150">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="3206d-150">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="3206d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3206d-151">See also</span></span>

- [<span data-ttu-id="3206d-152">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="3206d-152">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="3206d-153">時區總覽</span><span class="sxs-lookup"><span data-stu-id="3206d-153">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="3206d-154">如何：建立沒有調整規則的時區</span><span class="sxs-lookup"><span data-stu-id="3206d-154">How to: Create time zones without adjustment rules</span></span>](create-time-zones-without-adjustment-rules.md)
