---
title: "如何：解決不明確的時間"
description: "如何解決不明確的時間"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f4ab3b4bf3487e70be7e885e9b8a2281927eb30e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="10e77-104">如何：解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="10e77-104">How to: resolve ambiguous times</span></span>

<span data-ttu-id="10e77-105">不明確的時間是指對應到多個國際標準時間 (UTC) 的時間。</span><span class="sxs-lookup"><span data-stu-id="10e77-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="10e77-106">發生時機是往回調整時鐘時間，例如從時區的日光節約時間轉換到其標準時間期間。</span><span class="sxs-lookup"><span data-stu-id="10e77-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="10e77-107">處理不明確的時間時，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="10e77-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="10e77-108">假設如何將時間對應至 UTC。</span><span class="sxs-lookup"><span data-stu-id="10e77-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="10e77-109">例如，您可以假設不明確的時間一律是以時區的標準時間表示。</span><span class="sxs-lookup"><span data-stu-id="10e77-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="10e77-110">如果不明確的時間是使用者所輸入的資料項目，可交由使用者自行解決此不明確狀況。</span><span class="sxs-lookup"><span data-stu-id="10e77-110">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="10e77-111">本文示範如何在假設它代表時區標準時間的情況下解決不明確的時間。</span><span class="sxs-lookup"><span data-stu-id="10e77-111">This article shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="10e77-112">將不明確的時間對應至時區標準時間</span><span class="sxs-lookup"><span data-stu-id="10e77-112">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="10e77-113">呼叫 [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) 或 [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) 方法，以判斷時間是否不明確。</span><span class="sxs-lookup"><span data-stu-id="10e77-113">Call the [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="10e77-114">如果是不明確的時間，請減去時區之 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性所傳回 [TimeSpan](xref:System.TimeSpan) 物件的時間。</span><span class="sxs-lookup"><span data-stu-id="10e77-114">If the time is ambiguous, subtract the time from the [TimeSpan](xref:System.TimeSpan) object returned by the time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span>

3. <span data-ttu-id="10e77-115">呼叫 `static` (在 Visual Basic 中為 `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法，以將 UTC 日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性設定為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)。</span><span class="sxs-lookup"><span data-stu-id="10e77-115">Call the `static` (`Shared` in Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="10e77-116">範例</span><span class="sxs-lookup"><span data-stu-id="10e77-116">Example</span></span>

<span data-ttu-id="10e77-117">下列範例說明如何在假設不明確的 [DateTime](xref:System.DateTime) 代表當地時區標準時間的 UTC 的情況下，將其轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="10e77-117">The following example illustrates how to convert an ambiguous [DateTime](xref:System.DateTime) to UTC by assuming that it represents the local time zone's standard time.</span></span> 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

<span data-ttu-id="10e77-118">此範例包含名為 `ResolveAmbiguousTime` 的方法，可決定傳遞給它的 [DateTime](xref:System.DateTime) 值是否不明確。</span><span class="sxs-lookup"><span data-stu-id="10e77-118">The example consists of a method named `ResolveAmbiguousTime` that determines whether the [DateTime](xref:System.DateTime) value passed to it is ambiguous.</span></span> <span data-ttu-id="10e77-119">如果值不明確，則方法會傳回代表對應 UTC 時間的 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="10e77-119">If the value is ambiguous, the method returns a [DateTime](xref:System.DateTime) value that represents the corresponding UTC time.</span></span> <span data-ttu-id="10e77-120">此方法會將當地時間減去當地時區的 [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性值，來處理這項轉換。</span><span class="sxs-lookup"><span data-stu-id="10e77-120">The method handles this conversion by subtracting the value of the local time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property from the local time.</span></span> 

<span data-ttu-id="10e77-121">一般而言，不明確時間的處理方式是呼叫 [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) 方法來擷取 [TimeSpan](xref:System.TimeSpan) 物件陣列，其中包含不明確時間的可能 UTC 位移。</span><span class="sxs-lookup"><span data-stu-id="10e77-121">Ordinarily, an ambiguous time is handled by calling the [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) method to retrieve an array of [TimeSpan](xref:System.TimeSpan) objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="10e77-122">不過，此範例會進行任意假設，即不明確的時間應該一律對應至時區標準時間。</span><span class="sxs-lookup"><span data-stu-id="10e77-122">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="10e77-123">[BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) 屬性會傳回 UTC 與時區標準時間之間的位移。</span><span class="sxs-lookup"><span data-stu-id="10e77-123">The [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property returns the offset between UTC and a time zone's standard time.</span></span>

## <a name="see-also"></a><span data-ttu-id="10e77-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10e77-124">See Also</span></span>

[<span data-ttu-id="10e77-125">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="10e77-125">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="10e77-126">如何：讓使用者解決不明確的時間</span><span class="sxs-lookup"><span data-stu-id="10e77-126">How to: let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)


