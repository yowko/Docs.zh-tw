---
title: "在 DateTime 與 DateTimeOffset 之間轉換"
description: "在 DateTime 與 DateTimeOffset 之間轉換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 2ba70e9ea39148d040bdb46d5e00ea50dcbb8980
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="converting-between-datetime-and-datetimeoffset"></a><span data-ttu-id="0d4e2-104">在 DateTime 與 DateTimeOffset 之間轉換</span><span class="sxs-lookup"><span data-stu-id="0d4e2-104">Converting between DateTime and DateTimeOffset</span></span>

<span data-ttu-id="0d4e2-105">雖然 [System.DateTimeOffset](xref:System.DateTimeOffset) 結構所提供的時區感知程度大於 [System.DateTime](xref:System.DateTime) 結構，但是更常在方法呼叫中使用 [DateTime](xref:System.DateTime) 參數。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-105">Although the [System.DateTimeOffset](xref:System.DateTimeOffset) structure provides a greater degree of time zone awareness than the [System.DateTime](xref:System.DateTime) structure, [DateTime](xref:System.DateTime) parameters are used more commonly in method calls.</span></span> <span data-ttu-id="0d4e2-106">因此，將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值和相反作業的能力特別重要。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-106">Because of this, the ability to convert [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values and vice versa is particularly important.</span></span> <span data-ttu-id="0d4e2-107">本文示範如何盡可能保留最多時區資訊來執行這些轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-107">This article shows how to perform these conversions in a way that preserves as much time zone information as possible.</span></span>

> [!NOTE]
> <span data-ttu-id="0d4e2-108">[DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 類型在呈現時區時間時有一些限制。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-108">Both the [DateTime](xref:System.DateTime) and the [DateTimeOffset](xref:System.DateTimeOffset) types have some limitations when representing times in time zones.</span></span> <span data-ttu-id="0d4e2-109">使用其 [Kind](xref:System.DateTime.Kind) 屬性，[DateTime](xref:System.DateTime) 可以只反映國際標準時間 (UTC) 和系統當地時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-109">With its [Kind](xref:System.DateTime.Kind) property, [DateTime](xref:System.DateTime) is able to reflect only Coordinated Universal Time (UTC) and the system's local time zone.</span></span> <span data-ttu-id="0d4e2-110">[DateTimeOffset](xref:System.DateTimeOffset) 反映時間與 UTC 的位移，但未反映該位移所屬的實際時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-110">[DateTimeOffset](xref:System.DateTimeOffset) reflects a time's offset from UTC, but it does not reflect the actual time zone to which that offset belongs.</span></span> <span data-ttu-id="0d4e2-111">如需時間值以及時區支援的詳細資訊，請參閱[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](choosing-between-datetime.md)。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-111">For details about time values and support for time zones, see [Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="conversions-from-datetime-to-datetimeoffset"></a><span data-ttu-id="0d4e2-112">從 DateTime 到 DateTimeOffset 的轉換</span><span class="sxs-lookup"><span data-stu-id="0d4e2-112">Conversions from DateTime to DateTimeOffset</span></span>

<span data-ttu-id="0d4e2-113">[DateTimeOffset](xref:System.DateTimeOffset) 結構提供兩個對等方式，以執行適用於大部分轉換的 [DateTime](xref:System.DateTime) 到 [DateTimeOffset](xref:System.DateTimeOffset) 轉換：</span><span class="sxs-lookup"><span data-stu-id="0d4e2-113">The [DateTimeOffset](xref:System.DateTimeOffset) structure provides two equivalent ways to perform [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) conversion that are suitable for most conversions:</span></span>

* <span data-ttu-id="0d4e2-114">[DateTimeOffset(DateTime)](xref:System.DateTimeOffset) 建構函式，可根據 [DateTime](xref:System.DateTime) 值來建立新的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-114">The [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) constructor, which creates a new [DateTimeOffset](xref:System.DateTimeOffset) object based on a [DateTime](xref:System.DateTime) value.</span></span>

* <span data-ttu-id="0d4e2-115">隱含轉換運算子，可讓您將 [DateTime](xref:System.DateTime) 值指派給 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-115">The implicit conversion operator, which allows you to assign a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

<span data-ttu-id="0d4e2-116">針對 UTC 和當地 [DateTime](xref:System.DateTime) 值，所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的 [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 屬性會精確地反映 UTC 或當地時區位移。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-116">For UTC and local [DateTime](xref:System.DateTime) values, the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value accurately reflects the UTC or local time zone offset.</span></span> <span data-ttu-id="0d4e2-117">例如，下列程式碼會將 UTC 時間轉換為其對等 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-117">For example, the following code converts a UTC time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> 

```csharp
DateTime utcTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
utcTime1 = DateTime.SpecifyKind(utcTime1, DateTimeKind.Utc);
DateTimeOffset utcTime2 = utcTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  utcTime1, 
                  utcTime1.Kind.ToString(), 
                  utcTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM +00:00
```

```vb
Dim utcTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, _
                                        DateTimeKind.Utc)
Dim utcTime2 As DateTimeOffset = utcTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  utcTime1, _
                  utcTime1.Kind.ToString(), _
                  utcTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM  +00:00
```

<span data-ttu-id="0d4e2-118">在此情況下，`utcTime2` 變數的位移是 00:00。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-118">In this case, the offset of the `utcTime2` variable is 00:00.</span></span> <span data-ttu-id="0d4e2-119">同樣地，下列程式碼會將當地時間轉換為其對等 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-119">Similarly, the following code converts a local time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

```csharp
DateTime localTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
localTime1 = DateTime.SpecifyKind(localTime1, DateTimeKind.Local);
DateTimeOffset localTime2 = localTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  localTime1, 
                  localTime1.Kind.ToString(), 
                  localTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim localTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, DateTimeKind.Local)
Dim localTime2 As DateTimeOffset = localTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  localTime1, _
                  localTime1.Kind.ToString(), _
                  localTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

<span data-ttu-id="0d4e2-120">不過，對於 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [DateTime](xref:System.DateTime) 值，這兩種轉換方法都會產生位移為當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-120">However, for [DateTime](xref:System.DateTime) values whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), these two conversion methods produce a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset is that of the local time zone.</span></span> <span data-ttu-id="0d4e2-121">下列範例會示範以下列時區執行的情況：太平洋標準時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-121">This is shown in the following example, which is run in the U.S. Pacific Standard Time zone.</span></span>

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);  // Kind is DateTimeKind.Unspecified
DateTimeOffset time2 = time1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  time1, 
                  time1.Kind.ToString(), 
                  time2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Dim time2 As DateTimeOffset = time1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  time1, _
                  time1.Kind.ToString(), _
                  time2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

<span data-ttu-id="0d4e2-122">如果 [DateTime](xref:System.DateTime) 值反映當地時區或 UTC 以外的日期和時間，您可以呼叫多載的 [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) 建構函式，以將它轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並保留其時區資訊。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-122">If the [DateTime](xref:System.DateTime) value reflects the date and time in something other than the local time zone or UTC, you can convert it to a [DateTimeOffset](xref:System.DateTimeOffset) value and preserve its time zone information by calling the overloaded [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) constructor.</span></span> <span data-ttu-id="0d4e2-123">例如，下列範例具現化可反映美加中部標準時間的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-123">For example, the following example instantiates a [DateTimeOffset](xref:System.DateTimeOffset) object that reflects Central Standard Time.</span></span>

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);     // Kind is DateTimeKind.Unspecified
try
{
   DateTimeOffset time2 = new DateTimeOffset(time1, 
                  TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)); 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", 
                     time1, 
                     time1.Kind.ToString(), 
                     time2);
}
// Handle exception if time zone is not defined in registry
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to identify target time zone for conversion.");
}
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Try
   Dim time2 As New DateTimeOffset(time1, _
                    TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)) 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", _
                     time1, _
                     time1.Kind.ToString(), _
                     time2)
' Handle exception if time zone is not defined in registry
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to identify target time zone for conversion.")
End Try
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

<span data-ttu-id="0d4e2-124">這個建構函式多載的第二個參數是代表與 UTC 之時間位移的 [System.TimeSpan](xref:System.TimeSpan) 物件，其擷取方式是呼叫時間之對應時區的 [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) 方法。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-124">The second parameter to this constructor overload, a [System.TimeSpan](xref:System.TimeSpan) object that represents the time's offset from UTC, should be retrieved by calling the [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) method of the time's corresponding time zone.</span></span> <span data-ttu-id="0d4e2-125">方法的單一參數是代表要轉換之日期和時間的 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-125">The method's single parameter is the [DateTime](xref:System.DateTime) value that represents the date and time to be converted.</span></span> <span data-ttu-id="0d4e2-126">如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-126">If the time zone supports daylight saving time, this parameter allows the method to determine the appropriate offset for that particular date and time.</span></span>

## <a name="conversions-from-datetimeoffset-to-datetime"></a><span data-ttu-id="0d4e2-127">從 DateTimeOffset 到 DateTime 的轉換</span><span class="sxs-lookup"><span data-stu-id="0d4e2-127">Conversions from DateTimeOffset to DateTime</span></span>

<span data-ttu-id="0d4e2-128">[DateTime](xref:System.DateTime) 屬性最常用於執行 [DateTimeOffset](xref:System.DateTimeOffset) 到 [DateTime](xref:System.DateTime) 轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-128">The [DateTime](xref:System.DateTime) property is most commonly used to perform [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversion.</span></span> <span data-ttu-id="0d4e2-129">不過，它會傳回 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [DateTime](xref:System.DateTime) 值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-129">However, it returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), as the following example illustrates.</span></span> 

```csharp
DateTime baseTime = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset sourceTime;
DateTime targetTime;

// Convert UTC to DateTime value
sourceTime = new DateTimeOffset(baseTime, TimeSpan.Zero);
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert local time to DateTime value
sourceTime = new DateTimeOffset(baseTime, 
                                TimeZoneInfo.Local.GetUtcOffset(baseTime));
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert Central Standard Time to a DateTime value
try
{
   TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime);
   sourceTime = new DateTimeOffset(baseTime, offset);
   targetTime = sourceTime.DateTime;
   Console.WriteLine("{0} converts to {1} {2}", 
                     sourceTime, 
                     targetTime, 
                     targetTime.Kind.ToString());
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.");
} 
// This example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

```vb
Const baseTime As Date = #06/19/2008 7:00AM#
Dim sourceTime As DateTimeOffset
Dim targetTime As Date

' Convert UTC to DateTime value
sourceTime = New DateTimeOffset(baseTime, TimeSpan.Zero)
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert local time to DateTime value
sourceTime = New DateTimeOffset(baseTime, _
                                TimeZoneInfo.Local.GetUtcOffset(baseTime))
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert Central Standard Time to a DateTime value
Try
   Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime)
   sourceTime = New DateTimeOffset(baseTime, offset)
   targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.")
End Try 
' This example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

<span data-ttu-id="0d4e2-130">這表示使用 [DateTime](xref:System.DateTime) 屬性時，轉換會遺失 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之關聯性的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-130">This means that any information about the [DateTimeOffset](xref:System.DateTimeOffset) value's relationship to UTC is lost by the conversion when the [DateTime](xref:System.DateTime) property is used.</span></span> <span data-ttu-id="0d4e2-131">這會影響對應到 UTC 時間或系統當地時間的 [DateTimeOffset](xref:System.DateTimeOffset) 值，原因是 [DateTime](xref:System.DateTime) 結構只會在其 [Kind](xref:System.DateTime.Kind) 屬性中反映這兩個時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-131">This affects [DateTimeOffset](xref:System.DateTimeOffset) values that correspond to UTC time or to the system's local time because the [DateTime](xref:System.DateTime) structure reflects only those two time zones in its [Kind](xref:System.DateTime.Kind) property.</span></span>

<span data-ttu-id="0d4e2-132">若要在將 [DateTimeOffset](xref:System.DateTimeOffset) 轉換為 [DateTime](xref:System.DateTime) 時盡可能保留最多時區資訊，您可以使用 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 和 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-132">To preserve as much time zone information as possible when converting a [DateTimeOffset](xref:System.DateTimeOffset) to a [DateTime](xref:System.DateTime) value, you can use the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) and [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) properties.</span></span> 

## <a name="converting-a-utc-time"></a><span data-ttu-id="0d4e2-133">轉換 UTC 時間</span><span class="sxs-lookup"><span data-stu-id="0d4e2-133">Converting a UTC Time</span></span>

<span data-ttu-id="0d4e2-134">若要表示所轉換的 [DateTime](xref:System.DateTime) 值為 UTC 時間，您可以擷取 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-134">To indicate that a converted [DateTime](xref:System.DateTime) value is the UTC time, you can retrieve the value of the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property.</span></span> <span data-ttu-id="0d4e2-135">它與 [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) 屬性的不同處有兩點：</span><span class="sxs-lookup"><span data-stu-id="0d4e2-135">It differs from the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property in two ways:</span></span>

* <span data-ttu-id="0d4e2-136">它會傳回 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 的 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-136">It returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

* <span data-ttu-id="0d4e2-137">如果 [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 屬性值不等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)，則會將時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-137">If the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property value does not equal [TimeSpan.Zero](xref:System.TimeSpan.Zero), it converts the time to UTC.</span></span>

> [!NOTE]
> <span data-ttu-id="0d4e2-138">如果您的應用程式需要已轉換的 [DateTime](xref:System.DateTime) 值明確地識別單一時間點，則應該考慮使用 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性來處理所有 [DateTimeOffset](xref:System.DateTimeOffset) 到 [DateTime](xref:System.DateTime) 的轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-138">If your application requires that converted [DateTime](xref:System.DateTime) values unambiguously identify a single point in time, you should consider using the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to handle all [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversions.</span></span>

<span data-ttu-id="0d4e2-139">下列程式碼使用 [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性，將位移等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero) 的 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-139">The following code uses the [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset equals [TimeSpan.Zero](xref:System.TimeSpan.Zero) to a [DateTime](xref:System.DateTime) value.</span></span>

```csharp
DateTimeOffset utcTime1 = new DateTimeOffset(2008, 6, 19, 7, 0, 0, TimeSpan.Zero);
DateTime utcTime2 = utcTime1.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

```vb
Dim utcTime1 As New DateTimeOffset(#06/19/2008 7:00AM#, TimeSpan.Zero)
Dim utcTime2 As Date = utcTime1.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

<span data-ttu-id="0d4e2-140">下列程式碼使用 UtcDateTime 屬性，根據 [DateTimeOffset](xref:System.DateTimeOffset) 值來執行時區轉換和類型轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-140">The following code uses the UtcDateTime property to perform both a time zone conversion and a type conversion on a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

```csharp
DateTimeOffset originalTime = new DateTimeOffset(2008, 6, 19, 7, 0, 0, new TimeSpan(5, 0, 0));
DateTime utcTime = originalTime.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalTime, 
                  utcTime, 
                  utcTime.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

```vb
Dim originalTime As New DateTimeOffset(#6/19/2008 7:00AM#, _
                                       New TimeSpan(5, 0, 0))
Dim utcTime As Date = originalTime.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _ 
                  originalTime, _
                  utcTime, _
                  utcTime.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

## <a name="converting-a-local-time"></a><span data-ttu-id="0d4e2-141">轉換當地時間</span><span class="sxs-lookup"><span data-stu-id="0d4e2-141">Converting a Local Time</span></span>

<span data-ttu-id="0d4e2-142">若要表示 [DateTimeOffset](xref:System.DateTimeOffset) 值代表當地時間，您可以將 [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) 屬性所傳回的 [DateTime](xref:System.DateTime) 值傳遞給靜態 [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-142">To indicate that a [DateTimeOffset](xref:System.DateTimeOffset) value represents the local time, you can pass the [DateTime](xref:System.DateTime) value returned by the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property to the static [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method.</span></span> <span data-ttu-id="0d4e2-143">這個方法會傳回傳遞給它的日期和時間作為其第一個參數，但將 [Kind](xref:System.DateTime.Kind) 屬性設定為其第二個參數所指定的值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-143">The method returns the date and time passed to it as its first parameter, but sets the [Kind](xref:System.DateTime.Kind) property to the value specified by its second parameter.</span></span> <span data-ttu-id="0d4e2-144">下列程式碼會在轉換其位移對應至當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值時使用 [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-144">The following code uses the [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset utcTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime utcTime2 = utcTime1.DateTime;
if (utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime))) 
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local);

Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim utcTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim utcTime2 As Date = utcTime1.DateTime
If utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime)) Then
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local)
End If   
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

<span data-ttu-id="0d4e2-145">您也可以使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性，將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為當地 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-145">You can also use the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value to a local [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="0d4e2-146">所傳回 [DateTime](xref:System.DateTime) 值的 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Local](xref:System.DateTimeKind.Local)。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-146">The [Kind](xref:System.DateTime.Kind) property of the returned [DateTime](xref:System.DateTime) value is [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span></span> <span data-ttu-id="0d4e2-147">下列程式碼會在轉換其位移對應至當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值時使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-147">The following code uses the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset localTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime localTime2 = localTime1.LocalDateTime;

Console.WriteLine("{0} converted to {1} {2}", 
                  localTime1, 
                  localTime2, 
                  localTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim localTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim localTime2 As Date = localTime1.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime1, _
                  localTime2, _
                  localTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local 
```

<span data-ttu-id="0d4e2-148">當您使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性擷取 [DateTime](xref:System.DateTime) 值時，屬性的 `get` 存取子會先將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 UTC，然後呼叫 [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) 方法再將它轉換為當地時間。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-148">When you retrieve a [DateTime](xref:System.DateTime) value using the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property, the property's `get` accessor first converts the [DateTimeOffset](xref:System.DateTimeOffset) value to UTC, then converts it to local time by calling the [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) method.</span></span> <span data-ttu-id="0d4e2-149">這表示您可以從 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性擷取值，在您執行類型轉換的同時執行時區轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-149">This means that you can retrieve a value from the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform a time zone conversion at the same time that you perform a type conversion.</span></span> <span data-ttu-id="0d4e2-150">這也表示執行轉換時會套用當地時區的調整規則。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-150">It also means that the local time zone's adjustment rules are applied in performing the conversion.</span></span> <span data-ttu-id="0d4e2-151">下列程式碼說明如何使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性，來執行類型和時區轉換。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-151">The following code illustrates the use of the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform both a type and a time zone conversion.</span></span>

```csharp
DateTimeOffset originalDate;
DateTime localDate;

// Convert time originating in a different time zone
originalDate = new DateTimeOffset(2008, 6, 18, 7, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// Convert time originating in a different time zone 
// so local time zone's adjustment rules are applied
originalDate = new DateTimeOffset(2007, 11, 4, 4, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
//       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

```vb
Dim originalDate As DateTimeOffset
Dim localDate As Date

' Convert time originating in a different time zone
originalDate = New DateTimeOffset(#06/19/2008 7:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' Convert time originating in a different time zone 
' so local time zone's adjustment rules are applied
originalDate = New DateTimeOffset(#11/04/2007 4:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
'       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

## <a name="a-general-purpose-conversion-method"></a><span data-ttu-id="0d4e2-152">一般目的轉換方法</span><span class="sxs-lookup"><span data-stu-id="0d4e2-152">A General-Purpose Conversion Method</span></span>

<span data-ttu-id="0d4e2-153">下列範例定義名為 `ConvertFromDateTimeOffset` 的方法，以將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-153">The following example defines a method named `ConvertFromDateTimeOffset` that converts [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="0d4e2-154">根據其位移，它會判斷 [DateTimeOffset](xref:System.DateTimeOffset) 值是否為 UTC 時間、當地時間或一些其他時間，並據此定義所傳回日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-154">Based on its offset, it determines whether the [DateTimeOffset](xref:System.DateTimeOffset) value is a UTC time, a local time, or some other time, and defines the returned date and time value's [Kind](xref:System.DateTime.Kind) property accordingly.</span></span> 

```csharp
static DateTime ConvertFromDateTimeOffset(DateTimeOffset dateTime)
{
   if (dateTime.Offset.Equals(TimeSpan.Zero))
      return dateTime.UtcDateTime;
   else if (dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime)))
      return DateTime.SpecifyKind(dateTime.DateTime, DateTimeKind.Local);
   else
      return dateTime.DateTime;   
}
```

```vb
Function ConvertFromDateTimeOffset(dateTime As DateTimeOffset) As Date
   If dateTime.Offset.Equals(TimeSpan.Zero) Then
      Return dateTime.UtcDateTime
   ElseIf dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime))
      Return Date.SpecifyKind(dateTime.DateTime, DateTimeKind.Local)
   Else
      Return dateTime.DateTime   
   End If
```

<span data-ttu-id="0d4e2-155">下列範例會呼叫 `ConvertFromDateTimeOffset` 方法來轉換 [DateTimeOffset](xref:System.DateTimeOffset) 値，這些値代表 UTC 時間、當地時間以及美國中央標準時區時間。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-155">The follow example calls the `ConvertFromDateTimeOffset` method to convert [DateTimeOffset](xref:System.DateTimeOffset) values that represent a UTC time, a local time, and a time in the U.S. Central Standard Time zone.</span></span>

```csharp
DateTime timeComponent = new DateTime(2008, 6, 19, 7, 0, 0);
DateTime returnedDate; 

// Convert UTC time
DateTimeOffset utcTime = new DateTimeOffset(timeComponent, TimeSpan.Zero);
returnedDate = ConvertFromDateTimeOffset(utcTime); 
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert local time
DateTimeOffset localTime = new DateTimeOffset(timeComponent, 
                           TimeZoneInfo.Local.GetUtcOffset(timeComponent)); 
returnedDate = ConvertFromDateTimeOffset(localTime);                                          
Console.WriteLine("{0} converted to {1} {2}", 
                  localTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert Central Standard Time
DateTimeOffset cstTime = new DateTimeOffset(timeComponent, 
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent));
returnedDate = ConvertFromDateTimeOffset(cstTime);
Console.WriteLine("{0} converted to {1} {2}", 
                  cstTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());
// The example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
//    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
//    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

```vb
Dim timeComponent As Date = #06/19/2008 7:00AM#
Dim returnedDate As Date 

' Convert UTC time
Dim utcTime As New DateTimeOffset(timeComponent, TimeSpan.Zero)
returnedDate = ConvertFromDateTimeOffset(utcTime) 
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert local time
Dim localTime As New DateTimeOffset(timeComponent, _
                                    TimeZoneInfo.Local.GetUtcOffset(timeComponent)) 
returnedDate = ConvertFromDateTimeOffset(localTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert Central Standard Time
Dim cstTime As New DateTimeOffset(timeComponent, _
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent))
returnedDate = ConvertFromDateTimeOffset(cstTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  cstTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())
' The example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
'    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
'    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

<span data-ttu-id="0d4e2-156">請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰</span><span class="sxs-lookup"><span data-stu-id="0d4e2-156">Note that this code makes two assumptions that, depending on the application and the source of its date and time values, may not always be valid:</span></span>

* <span data-ttu-id="0d4e2-157">它假設位移為 [TimeSpan.Zero](xref:System.TimeSpan.Zero) 的日期和時間值代表 UTC。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-157">It assumes that a date and time value whose offset is [TimeSpan.Zero](xref:System.TimeSpan.Zero) represents UTC.</span></span> <span data-ttu-id="0d4e2-158">事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-158">In fact, UTC is not a time in a particular time zone, but the time in relation to which the times in the world's time zones are standardized.</span></span> <span data-ttu-id="0d4e2-159">時區也可以有 [Zero](xref:System.TimeSpan.Zero) 位移。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-159">Time zones can also have an offset of [Zero](xref:System.TimeSpan.Zero).</span></span>

* <span data-ttu-id="0d4e2-160">它假設位移等於當地時區位移的日期和時間代表當地時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-160">It assumes that a date and time whose offset equals that of the local time zone represents the local time zone.</span></span> <span data-ttu-id="0d4e2-161">因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。</span><span class="sxs-lookup"><span data-stu-id="0d4e2-161">Because date and time values are disassociated from their original time zone, this may not be the case; the date and time can have originated in another time zone with the same offset.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d4e2-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d4e2-162">See Also</span></span>

[<span data-ttu-id="0d4e2-163">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="0d4e2-163">Dates, times, and time zones</span></span>](index.md)





