---
title: "具現化 DateTimeOffset 物件"
description: "具現化 DateTimeOffset 物件"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 476fe67b-6be4-4435-88ab-ced37304f1d1
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 26be324eb5d58b94a71e89aba213f107cf8dfd1e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="instantiating-a-datetimeoffset-object"></a><span data-ttu-id="bad1a-104">具現化 DateTimeOffset 物件</span><span class="sxs-lookup"><span data-stu-id="bad1a-104">Instantiating a DateTimeOffset object</span></span>

<span data-ttu-id="bad1a-105">[System.DateTimeOffset](xref:System.DateTimeOffset) 結構提供數種方式來建立新的 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-105">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure offers a number of ways to create new [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span> <span data-ttu-id="bad1a-106">其中許多項目都直接對應至可用於具現化新 [System.DateTime](xref:System.DateTime) 值的方法，並且具有增強功能可讓您指定日期和時間值與國際標準時間 (UTC) 的位移。</span><span class="sxs-lookup"><span data-stu-id="bad1a-106">Many of them correspond directly to the methods available for instantiating new [System.DateTime](xref:System.DateTime) values, with enhancements that allow you to specify the date and time value's offset from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="bad1a-107">特別的是，您可以使用下列方式來具現化 [DateTimeOffset](xref:System.DateTimeOffset) 值：</span><span class="sxs-lookup"><span data-stu-id="bad1a-107">In particular, you can instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value in the following ways:</span></span>

* <span data-ttu-id="bad1a-108">呼叫 [DateTimeOffset](xref:System.DateTimeOffset) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="bad1a-108">By calling a [DateTimeOffset](xref:System.DateTimeOffset) constructor.</span></span>

* <span data-ttu-id="bad1a-109">將值隱含地轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-109">By implicitly converting a value to [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

* <span data-ttu-id="bad1a-110">剖析日期和時間的字串表示。</span><span class="sxs-lookup"><span data-stu-id="bad1a-110">By parsing the string representation of a date and time.</span></span>

## <a name="date-and-time-literals"></a><span data-ttu-id="bad1a-111">日期和時間常值</span><span class="sxs-lookup"><span data-stu-id="bad1a-111">Date and Time Literals</span></span>

<span data-ttu-id="bad1a-112">對於支援它的語言，具現化 [DateTime](xref:System.DateTime) 值的其中一種最常見方式是將日期和時間提供為硬式編碼常值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-112">For languages that support it, one of the most common ways to instantiate a [DateTime](xref:System.DateTime) value is to provide the date and time as a hard-coded literal value.</span></span> <span data-ttu-id="bad1a-113">例如，下列 Visual Basic 程式碼會建立值為 2008 年 1 月 1 日早上 10:00 的 [DateTime](xref:System.DateTime) 物件。</span><span class="sxs-lookup"><span data-stu-id="bad1a-113">For example, the following Visual Basic code creates a [DateTime](xref:System.DateTime) object whose value is January 1, 2008, at 10:00 AM.</span></span>

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

<span data-ttu-id="bad1a-114">使用支援 [DateTime](xref:System.DateTime) 常值的語言時，也可以使用日期和時間常值來初始化 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-114">[DateTimeOffset](xref:System.DateTimeOffset) values can also be initialized using date and time literals when using languages that support [DateTime](xref:System.DateTime) literals.</span></span> <span data-ttu-id="bad1a-115">例如，下列 Visual Basic 程式碼會建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="bad1a-115">For example, the following Visual Basic code creates a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

<span data-ttu-id="bad1a-116">如主控台輸出所顯示，會將當地時區位移指派給使用此方式所建立的 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-116">As the console output shows, the [DateTimeOffset](xref:System.DateTimeOffset) value created in this way is assigned the offset of the local time zone.</span></span> <span data-ttu-id="bad1a-117">這表示如果在不同的電腦上執行程式碼，則使用字元常值所指派的 [DateTimeOffset](xref:System.DateTimeOffset) 值不會識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="bad1a-117">This means that a [DateTimeOffset](xref:System.DateTimeOffset) value assigned using a character literal does not identify a single point of time if the code is run on different computers.</span></span>

## <a name="datetimeoffset-constructors"></a><span data-ttu-id="bad1a-118">DateTimeOffset 建構函式</span><span class="sxs-lookup"><span data-stu-id="bad1a-118">DateTimeOffset Constructors</span></span>

<span data-ttu-id="bad1a-119">[System.DateTimeOffset](xref:System.DateTimeOffset) 類型定義五個建構函式。</span><span class="sxs-lookup"><span data-stu-id="bad1a-119">The [System.DateTimeOffset](xref:System.DateTimeOffset) type defines five constructors.</span></span> <span data-ttu-id="bad1a-120">其中三項直接對應到 [DateTime](xref:System.DateTime) 建構函式，以及類型為 [System.TimeSpan](xref:System.TimeSpan) 且定義日期和時間與 UTC 之位移的額外參數。</span><span class="sxs-lookup"><span data-stu-id="bad1a-120">Three of them correspond directly to [DateTime](xref:System.DateTime) constructors, with an additional parameter of type [System.TimeSpan](xref:System.TimeSpan) that defines the date and time's offset from UTC.</span></span> <span data-ttu-id="bad1a-121">這些可讓您根據其個別日期和時間元件的值來定義 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-121">These allow you to define a [DateTimeOffset](xref:System.DateTimeOffset) value based on the value of its individual date and time components.</span></span> <span data-ttu-id="bad1a-122">例如，下列程式碼使用這三個建構函式來具現化具有相同值 7/1/2008 12:05 AM +01:00 的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="bad1a-122">For example, the following code uses these three constructors to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects with identical values of 7/1/2008 12:05 AM +01:00.</span></span>

```csharp
DateTimeOffset dateAndTime;

// Instantiate date and time using years, months, days, 
// hours, minutes, and seconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine(dateAndTime);
// Instantiate date and time using years, months, days,
// hours, minutes, seconds, and milliseconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), 
                             dateAndTime.ToString("zzz"));

// Instantiate date and time using number of ticks
// 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = new DateTimeOffset(633452259920000000, new TimeSpan(1, 0, 0));  
Console.WriteLine(dateAndTime);
// The example displays the following output to the console:
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
```

```vb
Dim dateAndTime As DateTimeOffset

' Instantiate date and time using years, months, days, 
' hours, minutes, and seconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine(dateAndTime)
' Instantiate date and time using years, months, days,
' hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using Persian calendar with years,
' months, days, hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(1387, 2, 12, 8, 6, 32, 545, New PersianCalendar, New TimeSpan(1, 0, 0))
' Note that the console output displays the date in the Gregorian
' calendar, not the Persian calendar. 
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using number of ticks
' 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = New DateTimeOffset(633452259920000000, New TimeSpan(1, 0, 0))  
Console.WriteLine(dateAndTime)
' The example displays the following output to the console:
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
```

<span data-ttu-id="bad1a-123">請注意，向主控台顯示使用 [PersianCalendar](xref:System.Globalization.PersianCalendar) 物件作為其建構函式之其中一個引數所具現化的 [DateTimeOffset](xref:System.DateTimeOffset) 物件的值時，它會表示為西曆日期，而非波斯曆。</span><span class="sxs-lookup"><span data-stu-id="bad1a-123">Note that, when the value of the [DateTimeOffset](xref:System.DateTimeOffset) object instantiated using a [PersianCalendar](xref:System.Globalization.PersianCalendar) object as one of the arguments to its constructor is displayed to the console, it is expressed as a date in the Gregorian rather than the Persian calendar.</span></span> 

<span data-ttu-id="bad1a-124">另兩個建構函式會透過 DateTime 值建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件。</span><span class="sxs-lookup"><span data-stu-id="bad1a-124">The other two constructors create a [DateTimeOffset](xref:System.DateTimeOffset) object from a DateTime value.</span></span> <span data-ttu-id="bad1a-125">其中第一個具有單一參數，即要轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值的 [DateTime](xref:System.DateTime) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-125">The first of these has a single parameter, the [DateTime](xref:System.DateTime) value to convert to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="bad1a-126">所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移取決於建構函式之單一 [DateTime](xref:System.DateTime) 參數的 [Kind](xref:System.DateTime.Kind) 屬性。</span><span class="sxs-lookup"><span data-stu-id="bad1a-126">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the [Kind](xref:System.DateTime.Kind) property of the constructor's single [DateTime](xref:System.DateTime) parameter.</span></span> <span data-ttu-id="bad1a-127">如果它的值為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則位移設定為等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。</span><span class="sxs-lookup"><span data-stu-id="bad1a-127">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="bad1a-128">否則，它的位移是設定為等於當地時區。</span><span class="sxs-lookup"><span data-stu-id="bad1a-128">Otherwise, its offset is set equal to that of the local time zone.</span></span> <span data-ttu-id="bad1a-129">下列範例說明如何使用這個建構函式來具現化代表 UTC 和當地時區的 [DateTimeOffset](xref:System.DateTimeOffset) 物件︰</span><span class="sxs-lookup"><span data-stu-id="bad1a-129">The following example illustrates the use of this constructor to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects representing UTC and the local time zone:</span></span>

```csharp
// Declare date; Kind property is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time 
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the offset is TimeSpan.Zero.

// Instantiate a DateTimeOffset value from a UTC time with a zero offset
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a negative offset
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      targetTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM +00:00 failed.

// Instantiate a DateTimeOffset value from a local time
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local, 
// the offset is that of the local time zone.

// Instantiate a DateTimeOffset value from an unspecified time
targetTime = new DateTimeOffset(sourceDate);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Unspecified, 
// the offset is that of the local time zone.
```

```vb
' Declare date; Kind property is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time 
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc, 
' the offset is TimeSpan.Zero.


' Instantiate a DateTimeOffset value from a local time
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Local, 
' the offset is that of the local time zone.

' Instantiate a DateTimeOffset value from an unspecified time
targetTime = New DateTimeOffset(sourceDate)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Unspecified, 
' the offset is that of the local time zone.
```

> [!NOTE]
> <span data-ttu-id="bad1a-130">呼叫具有單一 [DateTime](xref:System.DateTime) 參數的 [DateTimeOffset](xref:System.DateTimeOffset) 建構函式多載，等於執行 [DateTime](xref:System.DateTime) 值到 [DateTimeOffset](xref:System.DateTimeOffset) 值的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="bad1a-130">Calling the overload of the [DateTimeOffset](xref:System.DateTimeOffset) constructor that has a single [DateTime](xref:System.DateTime) parameter is equivalent to performing an implicit conversion of a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

<span data-ttu-id="bad1a-131">透過 [DateTime](xref:System.DateTime) 值建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件的第二個建構函式具有兩個參數︰要轉換的 [DateTime](xref:System.DateTime) 值，以及代表日期和時間與 UTC 之位移的 [TimeSpan](xref:System.TimeSpan) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-131">The second constructor that creates a [DateTimeOffset](xref:System.DateTimeOffset) object from a [DateTime](xref:System.DateTime) value has two parameters: the [DateTime](xref:System.DateTime) value to convert, and a [TimeSpan](xref:System.TimeSpan) value representing the date and time's offset from UTC.</span></span> <span data-ttu-id="bad1a-132">此位移值必須對應到建構函式之第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性，否則會擲回 [System.ArgumentException](xref:System.ArgumentException)。</span><span class="sxs-lookup"><span data-stu-id="bad1a-132">This offset value must correspond to the [Kind](xref:System.DateTime.Kind) property of the constructor's first parameter or an [System.ArgumentException](xref:System.ArgumentException) is thrown.</span></span> <span data-ttu-id="bad1a-133">如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則第二個參數的值必須是 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。</span><span class="sxs-lookup"><span data-stu-id="bad1a-133">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the value of the second parameter must be [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="bad1a-134">如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Local](xref:System.DateTimeKind.Local)，則第二個參數的值必須是本機系統的時區位移。</span><span class="sxs-lookup"><span data-stu-id="bad1a-134">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Local](xref:System.DateTimeKind.Local), the value of the second parameter must be the offset of the local system's time zone.</span></span> <span data-ttu-id="bad1a-135">如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)，則位移可以是任何有效值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-135">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset can be any valid value.</span></span> <span data-ttu-id="bad1a-136">下列程式碼說明如何呼叫這個建構函式以將 [DateTime](xref:System.DateTime) 轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-136">The following code illustrates calls to this constructor to convert [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span>

```csharp
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time with a zero offset.
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc,  
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      utcTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value from a local time with 
// the offset of the local time zone
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime, 
                                TimeZoneInfo.Local.GetUtcOffset(localTime));
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local and the offset matches
// that of the local time zone, the call to the constructor succeeds.

// Instantiate a DateTimeOffset value from a local time with a zero offset.
try
{
   targetTime = new DateTimeOffset(localTime, TimeSpan.Zero);
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      localTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value with an arbitary time zone. 
string timeZoneName = "Central Standard Time";
TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). 
                         GetUtcOffset(sourceDate); 
targetTime = new DateTimeOffset(sourceDate, offset);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -05:00
```

```vb
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time with a zero offset.
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime, TimeSpan.Zero)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc,  
' the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
Try
   targetTime = New DateTimeOffset(utcTime, New TimeSpan(-2, 0, 0))
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      utcTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value from a local time with 
' the offset of the local time zone.
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime, _
                                TimeZoneInfo.Local.GetUtcOffset(localTime))
Console.WriteLine(targetTime)
' Because the Kind property is DateTimeKind.Local and the offset matches
' that of the local time zone, the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a local time with a zero offset.
Try
   targetTime = New DateTimeOffset(localTime, TimeSpan.Zero)
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      localTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value with an arbitary time zone. 
Dim timeZoneName As String = "Central Standard Time"
Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). _
                         GetUtcOffset(sourceDate) 
targetTime = New DateTimeOffset(sourceDate, offset)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -05:00
```

## <a name="implicit-type-conversion"></a><span data-ttu-id="bad1a-137">隱含類型轉換</span><span class="sxs-lookup"><span data-stu-id="bad1a-137">Implicit Type Conversion</span></span>
 
<span data-ttu-id="bad1a-138">[System.DateTimeOffset](xref:System.DateTimeOffset) 類型支援一種隱含類型轉換︰從 [System.DateTime](xref:System.DateTime) 值到 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-138">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports one implicit type conversion: from a [System.DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="bad1a-139">隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。</span><span class="sxs-lookup"><span data-stu-id="bad1a-139">(An implicit type conversion is a conversion from one type to another that does not require an explicit cast (in C#) or conversion (in Visual Basic) and that does not lose information.</span></span> <span data-ttu-id="bad1a-140">這樣就可以使用如下所述的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bad1a-140">It makes code like the following possible.</span></span>

```csharp
DateTimeOffset targetTime;

// The Kind property of sourceDate is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
targetTime = sourceDate;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM -07:00

// define a UTC time (Kind property is DateTimeKind.Utc)
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = utcTime;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM +00:00

// Define a local time (Kind property is DateTimeKind.Local)
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = localTime;
Console.WriteLine(targetTime);      
// Displays 5/1/2008 8:30:00 AM -07:00
```

```vb
Dim targetTime As DateTimeOffset

' The Kind property of sourceDate is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
targetTime = sourceDate
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM -07:00

' define a UTC time (Kind property is DateTimeKind.Utc)
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = utcTime
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM +00:00

' Define a local time (Kind property is DateTimeKind.Local)
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = localTime
Console.WriteLine(targetTime)      
' Displays 5/1/2008 8:30:00 AM -07:00
```

<span data-ttu-id="bad1a-141">所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移取決於 DateTime.Kind](xref:System.DateTime.Kind) 屬性值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-141">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the DateTime.Kind](xref:System.DateTime.Kind) property value.</span></span> <span data-ttu-id="bad1a-142">如果它的值為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則位移設定為等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。</span><span class="sxs-lookup"><span data-stu-id="bad1a-142">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="bad1a-143">如果它的值為 [DateTimeKind.Local](xref:System.DateTimeKind.Local) 或 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)，則位移會設定為等於當地時區的位移。</span><span class="sxs-lookup"><span data-stu-id="bad1a-143">If its value is either [DateTimeKind.Local](xref:System.DateTimeKind.Local) or [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset is set equal to that of the local time zone.</span></span>

## <a name="parsing-the-string-representation-of-a-date-and-time"></a><span data-ttu-id="bad1a-144">剖析日期和時間的字串表示</span><span class="sxs-lookup"><span data-stu-id="bad1a-144">Parsing the String Representation of a Date and Time</span></span>

<span data-ttu-id="bad1a-145">[System.DateTimeOffset](xref:System.DateTimeOffset) 類型支援四種方法，可讓您將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值：</span><span class="sxs-lookup"><span data-stu-id="bad1a-145">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports four methods that allow you to convert the string representation of a date and time into a [DateTimeOffset](xref:System.DateTimeOffset) value:</span></span>

* <span data-ttu-id="bad1a-146">[Parse](xref:System.DateTimeOffset.Parse(System.String))，會嘗試將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並在轉換失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bad1a-146">[Parse](xref:System.DateTimeOffset.Parse(System.String)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="bad1a-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@))，會嘗試將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並在轉換失敗時傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="bad1a-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and returns `false` if the conversion fails.</span></span>

* <span data-ttu-id="bad1a-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider))，會嘗試將所指定格式之日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="bad1a-149">方法會在轉換失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bad1a-149">The method throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="bad1a-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@))，會嘗試將所指定格式之日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="bad1a-151">如果轉換失敗，方法會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="bad1a-151">The method returns `false` if the conversion fails.</span></span>

<span data-ttu-id="bad1a-152">下列範例說明所有這四個字串轉換方法的呼叫來具現化 [DateTimeOffset](xref:System.DateTimeOffset) 值。</span><span class="sxs-lookup"><span data-stu-id="bad1a-152">The following example illustrates calls to each of these four string conversion methods to instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

```csharp
string timeString; 
DateTimeOffset targetTime;

timeString = "05/01/2008 8:30 AM +01:00";
try
{
   targetTime = DateTimeOffset.Parse(timeString);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "05/01/2008 8:30 AM";
if (DateTimeOffset.TryParse(timeString, out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);   

timeString = "Thursday, 01 May 2008 08:30";
try
{
   targetTime = DateTimeOffset.ParseExact(timeString, "f", 
                CultureInfo.InvariantCulture);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "Thursday, 01 May 2008 08:30 +02:00";
string formatString; 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern +
                " " +
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern +
                " zzz"; 
if (DateTimeOffset.TryParseExact(timeString, 
                                formatString, 
                                CultureInfo.InvariantCulture, 
                                DateTimeStyles.AllowLeadingWhite, 
                                out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);
// The example displays the following output to the console:
//    5/1/2008 8:30:00 AM +01:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM +02:00
```

```vb
Dim timeString As String 
Dim targetTime As DateTimeOffset

timeString = "05/01/2008 8:30 AM +01:00"
Try
   targetTime = DateTimeOffset.Parse(timeString)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "05/01/2008 8:30 AM"
If DateTimeOffset.TryParse(timeString, targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)   
End If

timeString = "Thursday, 01 May 2008 08:30"
Try
   targetTime = DateTimeOffset.ParseExact(timeString, "f", _
                CultureInfo.InvariantCulture)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "Thursday, 01 May 2008 08:30 +02:00"
Dim formatString As String 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern & _
                " " & _
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern & _
                " zzz" 
If DateTimeOffset.TryParseExact(timeString, _
                                formatString, _
                                CultureInfo.InvariantCulture, _
                                DateTimeStyles.AllowLeadingWhite, _
                                targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)
End If      
' The example displays the following output to the console:
'    5/1/2008 8:30:00 AM +01:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM +02:00
```

## <a name="see-also"></a><span data-ttu-id="bad1a-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bad1a-153">See Also</span></span>

[<span data-ttu-id="bad1a-154">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="bad1a-154">Dates, times, and time zones</span></span>](index.md)


