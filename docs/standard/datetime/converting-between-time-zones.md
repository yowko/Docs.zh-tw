---
title: 在各時區間轉換時間
description: 瞭解如何在 .NET 中將時間從一個時區轉換為另一個時區。 此外，也要瞭解如何轉換具有有限時區感知的 DateTimeOffset 值。
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET], converting
- time zones [.NET], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
ms.openlocfilehash: 3539b3c2b71be331bdea3161b7e8ba6da407cbab
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063829"
---
# <a name="converting-times-between-time-zones"></a><span data-ttu-id="18d67-104">在各時區間轉換時間</span><span class="sxs-lookup"><span data-stu-id="18d67-104">Converting times between time zones</span></span>

<span data-ttu-id="18d67-105">對於使用日期和時間來處理時區差異的任何應用程式，它會變得越來越重要。</span><span class="sxs-lookup"><span data-stu-id="18d67-105">It is becoming increasingly important for any application that works with dates and times to handle differences between time zones.</span></span> <span data-ttu-id="18d67-106">應用程式無法再假設所有時間都是以當地時程表示，也就是從結構中可用的時間 <xref:System.DateTime> 。</span><span class="sxs-lookup"><span data-stu-id="18d67-106">An application can no longer assume that all times can be expressed in the local time, which is the time available from the <xref:System.DateTime> structure.</span></span> <span data-ttu-id="18d67-107">例如，顯示美國東部目前時間的網頁對東亞地區的客戶不具公信力。</span><span class="sxs-lookup"><span data-stu-id="18d67-107">For example, a Web page that displays the current time in the eastern part of the United States will lack credibility to a customer in eastern Asia.</span></span> <span data-ttu-id="18d67-108">本主題說明如何將時間從某個時區轉換為另一個時區，以及如何轉換 <xref:System.DateTimeOffset> 具有有限時區感知的值。</span><span class="sxs-lookup"><span data-stu-id="18d67-108">This topic explains how to convert times from one time zone to another, as well as how to convert <xref:System.DateTimeOffset> values that have limited time zone awareness.</span></span>

## <a name="converting-to-coordinated-universal-time"></a><span data-ttu-id="18d67-109">轉換為國際標準時間</span><span class="sxs-lookup"><span data-stu-id="18d67-109">Converting to Coordinated Universal Time</span></span>

<span data-ttu-id="18d67-110">國際標準時間 (UTC) 是高精確度且不可部分完成的時間標準。</span><span class="sxs-lookup"><span data-stu-id="18d67-110">Coordinated Universal Time (UTC) is a high-precision, atomic time standard.</span></span> <span data-ttu-id="18d67-111">世界的時區會以從 UTC 的正面或負位移來表示。</span><span class="sxs-lookup"><span data-stu-id="18d67-111">The world's time zones are expressed as positive or negative offsets from UTC.</span></span> <span data-ttu-id="18d67-112">因此，UTC 提供一種無時區或時區中性時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-112">Thus, UTC provides a kind of time-zone free or time-zone neutral time.</span></span> <span data-ttu-id="18d67-113">跨電腦的日期和時間可攜性十分重要時，建議使用 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-113">The use of UTC time is recommended when a date and time's portability across computers is important.</span></span> <span data-ttu-id="18d67-114"> (如需使用日期和時間的詳細資訊和其他最佳做法，請參閱 [.NET Framework 中使用 DateTime 的編碼最佳作法](/previous-versions/dotnet/articles/ms973825(v=msdn.10))。 ) 將個別時區轉換成 UTC，可讓時間比較輕鬆。</span><span class="sxs-lookup"><span data-stu-id="18d67-114">(For details and other best practices using dates and times, see [Coding best practices using DateTime in the .NET Framework](/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) Converting individual time zones to UTC makes time comparisons easy.</span></span>

> [!NOTE]
> <span data-ttu-id="18d67-115">您也可以將 <xref:System.DateTimeOffset> 結構序列化，以明確地表示單一時間點。</span><span class="sxs-lookup"><span data-stu-id="18d67-115">You can also serialize a <xref:System.DateTimeOffset> structure to unambiguously represent a single point in time.</span></span> <span data-ttu-id="18d67-116">因為 <xref:System.DateTimeOffset> 物件會儲存日期和時間值以及其與 utc 的位移，所以一律會以 utc 的關聯性表示特定時間點。</span><span class="sxs-lookup"><span data-stu-id="18d67-116">Because <xref:System.DateTimeOffset> objects store a date and time value along with its offset from UTC, they always represent a particular point in time in relationship to UTC.</span></span>

<span data-ttu-id="18d67-117">將時間轉換為 UTC 的最簡單方式，就是 `static` `Shared` 在 Visual Basic) 方法中呼叫 (<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="18d67-117">The easiest way to convert a time to UTC is to call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="18d67-118">方法所執行的確切轉換取決於 `dateTime` 參數的 <xref:System.DateTime.Kind%2A> 屬性值，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="18d67-118">The exact conversion performed by the method depends on the value of the `dateTime` parameter's <xref:System.DateTime.Kind%2A> property, as the following table shows.</span></span>

| `DateTime.Kind`            | <span data-ttu-id="18d67-119">轉換</span><span class="sxs-lookup"><span data-stu-id="18d67-119">Conversion</span></span>                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | <span data-ttu-id="18d67-120">將當地時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="18d67-120">Converts local time to UTC.</span></span>                                                    |
| `DateTimeKind.Unspecified` | <span data-ttu-id="18d67-121">假設 `dateTime` 參數是當地時間，並將當地時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="18d67-121">Assumes the `dateTime` parameter is local time and converts local time to UTC.</span></span> |
| `DateTimeKind.Utc`         | <span data-ttu-id="18d67-122">傳回未變更的 `dateTime` 參數。</span><span class="sxs-lookup"><span data-stu-id="18d67-122">Returns the `dateTime` parameter unchanged.</span></span>                                    |

<span data-ttu-id="18d67-123">下列程式碼會將目前當地時間轉換為 UTC，並將結果顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="18d67-123">The following code converts the current local time to UTC and displays the result to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

<span data-ttu-id="18d67-124">如果日期和時間值不是當地時間或 UTC，此 <xref:System.DateTime.ToUniversalTime%2A> 方法可能會傳回錯誤的結果。</span><span class="sxs-lookup"><span data-stu-id="18d67-124">If the date and time value does not represent either the local time or UTC, the <xref:System.DateTime.ToUniversalTime%2A> method will likely return an erroneous result.</span></span> <span data-ttu-id="18d67-125">不過，您可以使用 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> 方法，從指定的時區轉換日期和時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-125">However, you can use the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> method to convert the date and time from a specified time zone.</span></span> <span data-ttu-id="18d67-126"> (如需有關如何取得 <xref:System.TimeZoneInfo> 代表目的地時區之物件的詳細資訊，請參閱 [尋找本機系統上定義的時區](finding-the-time-zones-on-local-system.md)) 。下列程式碼會使用 <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> 方法將東部標準時間轉換成 UTC。</span><span class="sxs-lookup"><span data-stu-id="18d67-126">(For details on retrieving a <xref:System.TimeZoneInfo> object that represents the destination time zone, see [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md).) The following code uses the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> method to convert Eastern Standard Time to UTC.</span></span>

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

<span data-ttu-id="18d67-127">請注意， <xref:System.ArgumentException> 如果 <xref:System.DateTime> 物件的 <xref:System.DateTime.Kind%2A> 屬性和時區不符，則這個方法會擲回。</span><span class="sxs-lookup"><span data-stu-id="18d67-127">Note that this method throws an <xref:System.ArgumentException> if the <xref:System.DateTime> object's <xref:System.DateTime.Kind%2A> property and the time zone are mismatched.</span></span> <span data-ttu-id="18d67-128">如果 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType> <xref:System.TimeZoneInfo> ，但物件不代表本地時區，或 <xref:System.DateTime.Kind%2A> 屬性為 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> 但物件不 <xref:System.TimeZoneInfo> 相等， <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType> 則會發生不相符的情況。</span><span class="sxs-lookup"><span data-stu-id="18d67-128">A mismatch occurs if the <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Local?displayProperty=nameWithType> but the <xref:System.TimeZoneInfo> object does not represent the local time zone, or if the <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> but the <xref:System.TimeZoneInfo> object does not equal <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="18d67-129">所有這些方法都採用 <xref:System.DateTime> 值作為參數，並傳回 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="18d67-129">All of these methods take <xref:System.DateTime> values as parameters and return a <xref:System.DateTime> value.</span></span> <span data-ttu-id="18d67-130">針對 <xref:System.DateTimeOffset> 值， <xref:System.DateTimeOffset> 結構具有 <xref:System.DateTimeOffset.ToUniversalTime%2A> 實例方法，可將目前實例的日期和時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="18d67-130">For <xref:System.DateTimeOffset> values, the <xref:System.DateTimeOffset> structure has a <xref:System.DateTimeOffset.ToUniversalTime%2A> instance method that converts the date and time of the current instance to UTC.</span></span> <span data-ttu-id="18d67-131">下列範例會呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A> 方法，將當地時間和數個其他時間轉換成國際標準時間 (UTC) 。</span><span class="sxs-lookup"><span data-stu-id="18d67-131">The following example calls the <xref:System.DateTimeOffset.ToUniversalTime%2A> method to convert a local time and several other times to Coordinated Universal Time (UTC).</span></span>

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a><span data-ttu-id="18d67-132">將 UTC 轉換為指定的時區</span><span class="sxs-lookup"><span data-stu-id="18d67-132">Converting UTC to a designated time zone</span></span>

<span data-ttu-id="18d67-133">若要將 UTC 轉換為當地時間，請參閱後面的「將 UTC 轉換為當地時間」一節。</span><span class="sxs-lookup"><span data-stu-id="18d67-133">To convert UTC to local time, see the "Converting UTC to Local Time" section that follows.</span></span> <span data-ttu-id="18d67-134">若要將 UTC 轉換為您指定的任何時區時間，請呼叫 <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="18d67-134">To convert UTC to the time in any time zone that you designate, call the <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> method.</span></span> <span data-ttu-id="18d67-135">此方法接受兩個參數：</span><span class="sxs-lookup"><span data-stu-id="18d67-135">The method takes two parameters:</span></span>

- <span data-ttu-id="18d67-136">要轉換的 UTC。</span><span class="sxs-lookup"><span data-stu-id="18d67-136">The UTC to convert.</span></span> <span data-ttu-id="18d67-137">這必須是 <xref:System.DateTime> <xref:System.DateTime.Kind%2A> 屬性設定為或的值 `Unspecified` `Utc` 。</span><span class="sxs-lookup"><span data-stu-id="18d67-137">This must be a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is set to `Unspecified` or `Utc`.</span></span>

- <span data-ttu-id="18d67-138">要將 UTC 轉換為的時區。</span><span class="sxs-lookup"><span data-stu-id="18d67-138">The time zone to convert the UTC to.</span></span>

<span data-ttu-id="18d67-139">下列程式碼會將 UTC 轉換為美加中部標準時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-139">The following code converts UTC to Central Standard Time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a><span data-ttu-id="18d67-140">將 UTC 轉換為當地時間</span><span class="sxs-lookup"><span data-stu-id="18d67-140">Converting UTC to local time</span></span>

<span data-ttu-id="18d67-141">若要將 UTC 轉換為當地時間，請呼叫 <xref:System.DateTime.ToLocalTime%2A> <xref:System.DateTime> 您要轉換其時間之物件的方法。</span><span class="sxs-lookup"><span data-stu-id="18d67-141">To convert UTC to local time, call the <xref:System.DateTime.ToLocalTime%2A> method of the <xref:System.DateTime> object whose time you want to convert.</span></span> <span data-ttu-id="18d67-142">方法的確切行為取決於物件屬性的值 <xref:System.DateTime.Kind%2A> ，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="18d67-142">The exact behavior of the method depends on the value of the object's <xref:System.DateTime.Kind%2A> property, as the following table shows.</span></span>

| `DateTime.Kind`            | <span data-ttu-id="18d67-143">轉換</span><span class="sxs-lookup"><span data-stu-id="18d67-143">Conversion</span></span>                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <span data-ttu-id="18d67-144">傳回未變更的 <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="18d67-144">Returns the <xref:System.DateTime> value unchanged.</span></span>                                      |
| `DateTimeKind.Unspecified` | <span data-ttu-id="18d67-145">假設 <xref:System.DateTime> 值為 utc，並將 utc 轉換為當地時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-145">Assumes that the <xref:System.DateTime> value is UTC and converts the UTC to local time.</span></span> |
| `DateTimeKind.Utc`         | <span data-ttu-id="18d67-146">將 <xref:System.DateTime> 值轉換為本地時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-146">Converts the <xref:System.DateTime> value to local time.</span></span>                                 |

> [!NOTE]
> <span data-ttu-id="18d67-147"><xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>方法的行為與方法相同 `DateTime.ToLocalTime` 。</span><span class="sxs-lookup"><span data-stu-id="18d67-147">The <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> method behaves identically to the `DateTime.ToLocalTime` method.</span></span> <span data-ttu-id="18d67-148">它會採用單一參數，也就是要轉換的日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="18d67-148">It takes a single parameter, which is the date and time value to convert.</span></span>

<span data-ttu-id="18d67-149">您也可以使用 `static` `Shared` Visual Basic) 方法中的 (，將任何指定時區的時間轉換為當地時間 <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="18d67-149">You can also convert the time in any designated time zone to local time by using the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="18d67-150">下一節將討論這項技術。</span><span class="sxs-lookup"><span data-stu-id="18d67-150">This technique is discussed in the next section.</span></span>

## <a name="converting-between-any-two-time-zones"></a><span data-ttu-id="18d67-151">在兩個時區之間轉換</span><span class="sxs-lookup"><span data-stu-id="18d67-151">Converting between any two time zones</span></span>

<span data-ttu-id="18d67-152">您可以使用 `static` `Shared` 類別的 Visual Basic) 方法中的下列兩個 (之一，在任何兩個時區之間進行轉換 <xref:System.TimeZoneInfo> ：</span><span class="sxs-lookup"><span data-stu-id="18d67-152">You can convert between any two time zones by using either of the following two `static` (`Shared` in Visual Basic) methods of the <xref:System.TimeZoneInfo> class:</span></span>

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  <span data-ttu-id="18d67-153">這個方法的參數是要轉換的日期和時間值、 `TimeZoneInfo` 代表日期和時間值時區的物件，以及 `TimeZoneInfo` 代表要將日期和時間值轉換成之時區的物件。</span><span class="sxs-lookup"><span data-stu-id="18d67-153">This method's parameters are the date and time value to convert, a `TimeZoneInfo` object that represents the time zone of the date and time value, and a `TimeZoneInfo` object that represents the time zone to convert the date and time value to.</span></span>

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  <span data-ttu-id="18d67-154">這個方法的參數是要轉換的日期和時間值、日期和時間值時區的識別碼，以及要將日期和時間值轉換成的時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="18d67-154">This method's parameters are the date and time value to convert, the identifier of the date and time value's time zone, and the identifier of the time zone to convert the date and time value to.</span></span>

<span data-ttu-id="18d67-155">這兩種方法都需要 <xref:System.DateTime.Kind%2A> 轉換日期和時間值的屬性，以及 <xref:System.TimeZoneInfo> 代表其時區的物件或時區識別碼彼此對應。</span><span class="sxs-lookup"><span data-stu-id="18d67-155">Both methods require that the <xref:System.DateTime.Kind%2A> property of the date and time value to convert and the <xref:System.TimeZoneInfo> object or time zone identifier that represents its time zone correspond to one another.</span></span> <span data-ttu-id="18d67-156">否則會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="18d67-156">Otherwise, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="18d67-157">例如，如果 `Kind` 日期和時間值的屬性為 `DateTimeKind.Local` ，則如果 `TimeZoneInfo` 傳遞做為參數的物件不等於，則會擲回例外狀況 `TimeZoneInfo.Local` 。</span><span class="sxs-lookup"><span data-stu-id="18d67-157">For example, if the `Kind` property of the date and time value is `DateTimeKind.Local`, an exception is thrown if the `TimeZoneInfo` object passed as a parameter to the method is not equal to `TimeZoneInfo.Local`.</span></span> <span data-ttu-id="18d67-158">如果以參數形式傳遞給方法的識別碼不等於，也會擲回例外狀況 `TimeZoneInfo.Local.Id` 。</span><span class="sxs-lookup"><span data-stu-id="18d67-158">An exception is also thrown if the identifier passed as a parameter to the method is not equal to `TimeZoneInfo.Local.Id`.</span></span>

<span data-ttu-id="18d67-159">下列範例會使用 <xref:System.TimeZoneInfo.ConvertTime%2A> 方法，從夏威夷標準時間轉換為當地時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-159">The following example uses the <xref:System.TimeZoneInfo.ConvertTime%2A> method to convert from Hawaiian Standard Time to local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a><span data-ttu-id="18d67-160">轉換 DateTimeOffset 值</span><span class="sxs-lookup"><span data-stu-id="18d67-160">Converting DateTimeOffset values</span></span>

<span data-ttu-id="18d67-161">物件所代表的日期和時間值 <xref:System.DateTimeOffset> 不是完全時區感知，因為物件在具現化時與其時區解除關聯。</span><span class="sxs-lookup"><span data-stu-id="18d67-161">Date and time values represented by <xref:System.DateTimeOffset> objects are not fully time-zone aware because the object is disassociated from its time zone at the time it is instantiated.</span></span> <span data-ttu-id="18d67-162">不過，在許多情況下，應用程式只需要根據與 UTC 的兩個不同位移來轉換日期和時間，而不是根據特定時區的時間。</span><span class="sxs-lookup"><span data-stu-id="18d67-162">However, in many cases an application simply needs to convert a date and time based on two different offsets from UTC rather than on the time in particular time zones.</span></span> <span data-ttu-id="18d67-163">若要執行這種轉換，您可以呼叫目前實例的 <xref:System.DateTimeOffset.ToOffset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="18d67-163">To perform this conversion, you can call the current instance's <xref:System.DateTimeOffset.ToOffset%2A> method.</span></span> <span data-ttu-id="18d67-164">方法的單一參數是方法要傳回之新日期和時間值的位移。</span><span class="sxs-lookup"><span data-stu-id="18d67-164">The method's single parameter is the offset of the new date and time value that the method is to return.</span></span>

<span data-ttu-id="18d67-165">例如，如果網頁使用者要求的日期和時間已知且序列化為字串 (格式為 MM/dd/yyyy hh:mm:ss zzzz)，則下列 `ReturnTimeOnServer` 方法會將這個日期和時間值轉換為 Web 伺服器上的時間和日期。</span><span class="sxs-lookup"><span data-stu-id="18d67-165">For example, if the date and time of a user request for a Web page is known and is serialized as a string in the format MM/dd/yyyy hh:mm:ss zzzz, the following `ReturnTimeOnServer` method converts this date and time value to the date and time on the Web server.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]

<span data-ttu-id="18d67-166">如果將字串 "9/1/2007 5:32:07 -05:00" 傳遞給這個方法，代表時區中的日期和時間比 UTC 早五個小時，就會傳回 9/1/2007 3:32:07 AM -07:00，代表伺服器位於美國「太平洋標準時間」時區。</span><span class="sxs-lookup"><span data-stu-id="18d67-166">If the method is passed the string "9/1/2007 5:32:07 -05:00", which represents the date and time in a time zone five hours earlier than UTC, it returns 9/1/2007 3:32:07 AM -07:00 for a server located in the U.S. Pacific Standard Time zone.</span></span>

<span data-ttu-id="18d67-167"><xref:System.TimeZoneInfo>類別也包含方法的多載 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> ，此方法會使用值來執行時區轉換 <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> 。</span><span class="sxs-lookup"><span data-stu-id="18d67-167">The <xref:System.TimeZoneInfo> class also includes an overload of the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method that performs time zone conversions with <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> values.</span></span> <span data-ttu-id="18d67-168">方法的參數是 <xref:System.DateTimeOffset> 值，以及轉換時間的時區的參考。</span><span class="sxs-lookup"><span data-stu-id="18d67-168">The method's parameters are a <xref:System.DateTimeOffset> value and a reference to the time zone to which the time is to be converted.</span></span> <span data-ttu-id="18d67-169">方法呼叫會傳回 <xref:System.DateTimeOffset> 值。</span><span class="sxs-lookup"><span data-stu-id="18d67-169">The method call returns a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="18d67-170">例如， `ReturnTimeOnServer` 上一個範例中的方法可以重寫，如下所示，以呼叫 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="18d67-170">For example, the `ReturnTimeOnServer` method in the previous example could be rewritten as follows to call the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> method.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a><span data-ttu-id="18d67-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18d67-171">See also</span></span>

- <xref:System.TimeZoneInfo>
- [<span data-ttu-id="18d67-172">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="18d67-172">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="18d67-173">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="18d67-173">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
