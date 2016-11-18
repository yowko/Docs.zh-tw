---
title: "在 DateTime 與 DateTimeOffset 之間轉換"
description: "在 DateTime 與 DateTimeOffset 之間轉換"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 99ec9d8c433025bbc5122fe3ea364fe84f33a1f8

---

# <a name="converting-between-datetime-and-datetimeoffset"></a>在 DateTime 與 DateTimeOffset 之間轉換

雖然 [System.DateTimeOffset](xref:System.DateTimeOffset) 結構所提供的時區感知程度大於 [System.DateTime](xref:System.DateTime) 結構，但是更常在方法呼叫中使用 [DateTime](xref:System.DateTime) 參數。 因此，將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值和相反作業的能力特別重要。 本文示範如何盡可能保留最多時區資訊來執行這些轉換。

> [!NOTE]
> [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 類型在呈現時區時間時有一些限制。 使用其 [Kind](xref:System.DateTime.Kind) 屬性，[DateTime](xref:System.DateTime) 可以只反映國際標準時間 (UTC) 和系統當地時區。 [DateTimeOffset](xref:System.DateTimeOffset) 反映時間與 UTC 的位移，但未反映該位移所屬的實際時區。 如需時間值以及時區支援的詳細資訊，請參閱[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](choosing-between-datetime.md)。

## <a name="conversions-from-datetime-to-datetimeoffset"></a>從 DateTime 到 DateTimeOffset 的轉換

[DateTimeOffset](xref:System.DateTimeOffset) 結構提供兩個對等方式，以執行適用於大部分轉換的 [DateTime](xref:System.DateTime) 到 [DateTimeOffset](xref:System.DateTimeOffset) 轉換：

* [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) 建構函式，可根據 [DateTime](xref:System.DateTime) 值來建立新的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。

* 隱含轉換運算子，可讓您將 [DateTime](xref:System.DateTime) 值指派給 [DateTimeOffset](xref:System.DateTimeOffset) 物件。

針對 UTC 和當地 [DateTime](xref:System.DateTime) 值，所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的 [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 屬性會精確地反映 UTC 或當地時區位移。 例如，下列程式碼會將 UTC 時間轉換為其對等 [DateTimeOffset](xref:System.DateTimeOffset) 值。 

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

在此情況下，`utcTime2` 變數的位移是 00:00。 同樣地，下列程式碼會將當地時間轉換為其對等 [DateTimeOffset](xref:System.DateTimeOffset) 值。

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

不過，對於 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [DateTime](xref:System.DateTime) 值，這兩種轉換方法都會產生位移為當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值。 下列範例會示範以下列時區執行的情況：太平洋標準時區。

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

如果 [DateTime](xref:System.DateTime) 值反映當地時區或 UTC 以外的日期和時間，您可以呼叫多載的 [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) 建構函式，以將它轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並保留其時區資訊。 例如，下列範例具現化可反映美加中部標準時間的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。

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

這個建構函式多載的第二個參數是代表與 UTC 之時間位移的 [System.TimeSpan](xref:System.TimeSpan) 物件，其擷取方式是呼叫時間之對應時區的 [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) 方法。 方法的單一參數是代表要轉換之日期和時間的 [DateTime](xref:System.DateTime) 值。 如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。

## <a name="conversions-from-datetimeoffset-to-datetime"></a>從 DateTimeOffset 到 DateTime 的轉換

[DateTime](xref:System.DateTime) 屬性最常用於執行 [DateTimeOffset](xref:System.DateTimeOffset) 到 [DateTime](xref:System.DateTime) 轉換。 不過，它會傳回 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [DateTime](xref:System.DateTime) 值，如下列範例所示。 

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

這表示使用 [DateTime](xref:System.DateTime) 屬性時，轉換會遺失 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之關聯性的任何資訊。 這會影響對應到 UTC 時間或系統當地時間的 [DateTimeOffset](xref:System.DateTimeOffset) 值，原因是 [DateTime](xref:System.DateTime) 結構只會在其 [Kind](xref:System.DateTime.Kind) 屬性中反映這兩個時區。

若要在將 [DateTimeOffset](xref:System.DateTimeOffset) 轉換為 [DateTime](xref:System.DateTime) 時盡可能保留最多時區資訊，您可以使用 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 和 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性。 

## <a name="converting-a-utc-time"></a>轉換 UTC 時間

若要表示所轉換的 [DateTime](xref:System.DateTime) 值為 UTC 時間，您可以擷取 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性的值。 它與 [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) 屬性的不同處有兩點：

* 它會傳回 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 的 [DateTime](xref:System.DateTime) 值。

* 如果 [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 屬性值不等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)，則會將時間轉換為 UTC。

> [!NOTE]
> 如果您的應用程式需要已轉換的 [DateTime](xref:System.DateTime) 值明確地識別單一時間點，則應該考慮使用 [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性來處理所有 [DateTimeOffset](xref:System.DateTimeOffset) 到 [DateTime](xref:System.DateTime) 的轉換。

下列程式碼使用 [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) 屬性，將位移等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero) 的 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值。

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

下列程式碼使用 UtcDateTime 屬性，根據 [DateTimeOffset](xref:System.DateTimeOffset) 值來執行時區轉換和類型轉換。

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

## <a name="converting-a-local-time"></a>轉換當地時間

若要表示 [DateTimeOffset](xref:System.DateTimeOffset) 值代表當地時間，您可以將 [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) 屬性所傳回的 [DateTime](xref:System.DateTime) 值傳遞給靜態 [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法。 這個方法會傳回傳遞給它的日期和時間作為其第一個參數，但將 [Kind](xref:System.DateTime.Kind) 屬性設定為其第二個參數所指定的值。 下列程式碼會在轉換其位移對應至當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值時使用 [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) 方法。

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

您也可以使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性，將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為當地 [DateTime](xref:System.DateTime) 值。 所傳回 [DateTime](xref:System.DateTime) 值的 [Kind](xref:System.DateTime.Kind) 屬性為 [DateTimeKind.Local](xref:System.DateTimeKind.Local)。 下列程式碼會在轉換其位移對應至當地時區位移的 [DateTimeOffset](xref:System.DateTimeOffset) 值時使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性。

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

當您使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性擷取 [DateTime](xref:System.DateTime) 值時，屬性的 `get` 存取子會先將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 UTC，然後呼叫 [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) 方法再將它轉換為當地時間。 這表示您可以從 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性擷取值，在您執行類型轉換的同時執行時區轉換。 這也表示執行轉換時會套用當地時區的調整規則。 下列程式碼說明如何使用 [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) 屬性，來執行類型和時區轉換。

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

## <a name="a-generalpurpose-conversion-method"></a>一般目的轉換方法

下列範例定義名為 `ConvertFromDateTimeOffset` 的方法，以將 [DateTimeOffset](xref:System.DateTimeOffset) 值轉換為 [DateTime](xref:System.DateTime) 值。 根據其位移，它會判斷 [DateTimeOffset](xref:System.DateTimeOffset) 值是否為 UTC 時間、當地時間或一些其他時間，並據此定義所傳回日期和時間值的 [Kind](xref:System.DateTime.Kind) 屬性。 

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

下列範例會呼叫 `ConvertFromDateTimeOffset` 方法來轉換 [DateTimeOffset](xref:System.DateTimeOffset) 値，這些値代表 UTC 時間、當地時間以及美國中央標準時區時間。

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

請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰

* 它假設位移為 [TimeSpan.Zero](xref:System.TimeSpan.Zero) 的日期和時間值代表 UTC。 事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。 時區也可以有 [Zero](xref:System.TimeSpan.Zero) 位移。

* 它假設位移等於當地時區位移的日期和時間代表當地時區。 因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)







<!--HONumber=Nov16_HO3-->


