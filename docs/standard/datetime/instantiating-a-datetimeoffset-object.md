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
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 3b6e2cc973b9587cc9950ecd6898b8a321a01036

---

# <a name="instantiating-a-datetimeoffset-object"></a>具現化 DateTimeOffset 物件

[System.DateTimeOffset](xref:System.DateTimeOffset) 結構提供數種方式來建立新的 [DateTimeOffset](xref:System.DateTimeOffset) 值。 其中許多項目都直接對應至可用於具現化新 [System.DateTime](xref:System.DateTime) 值的方法，並且具有增強功能可讓您指定日期和時間值與國際標準時間 (UTC) 的位移。 特別的是，您可以使用下列方式來具現化 [DateTimeOffset](xref:System.DateTimeOffset) 值：

* 呼叫 [DateTimeOffset](xref:System.DateTimeOffset) 建構函式。

* 將值隱含地轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。

* 剖析日期和時間的字串表示。

## <a name="date-and-time-literals"></a>日期和時間常值

對於支援它的語言，具現化 [DateTime](xref:System.DateTime) 值的其中一種最常見方式是將日期和時間提供為硬式編碼常值。 例如，下列 Visual Basic 程式碼會建立值為 2008 年 1 月 1 日早上 10:00 的 [DateTime](xref:System.DateTime) 物件。

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

使用支援 [DateTime](xref:System.DateTime) 常值的語言時，也可以使用日期和時間常值來初始化 [DateTimeOffset](xref:System.DateTimeOffset) 值。 例如，下列 Visual Basic 程式碼會建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件。

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

如主控台輸出所顯示，會將當地時區位移指派給使用此方式所建立的 [DateTimeOffset](xref:System.DateTimeOffset) 值。 這表示如果在不同的電腦上執行程式碼，則使用字元常值所指派的 [DateTimeOffset](xref:System.DateTimeOffset) 值不會識別單一時間點。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset 建構函式

[System.DateTimeOffset](xref:System.DateTimeOffset) 類型定義五個建構函式。 其中三項直接對應到 [DateTime](xref:System.DateTime) 建構函式，以及類型為 [System.TimeSpan](xref:System.TimeSpan) 且定義日期和時間與 UTC 之位移的額外參數。 這些可讓您根據其個別日期和時間元件的值來定義 [DateTimeOffset](xref:System.DateTimeOffset) 值。 例如，下列程式碼使用這三個建構函式來具現化具有相同值 7/1/2008 12:05 AM +01:00 的 [DateTimeOffset](xref:System.DateTimeOffset) 物件。

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

請注意，向主控台顯示使用 [PersianCalendar](xref:System.Globalization.PersianCalendar) 物件作為其建構函式之其中一個引數所具現化的 [DateTimeOffset](xref:System.DateTimeOffset) 物件的值時，它會表示為西曆日期，而非波斯曆。 

另兩個建構函式會透過 DateTime 值建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件。 其中第一個具有單一參數，即要轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值的 [DateTime](xref:System.DateTime) 值。 所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移取決於建構函式之單一 [DateTime](xref:System.DateTime) 參數的 [Kind](xref:System.DateTime.Kind) 屬性。 如果它的值為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則位移設定為等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。 否則，它的位移是設定為等於當地時區。 下列範例說明如何使用這個建構函式來具現化代表 UTC 和當地時區的 [DateTimeOffset](xref:System.DateTimeOffset) 物件︰

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
> 呼叫具有單一 [DateTime](xref:System.DateTime) 參數的 [DateTimeOffset](xref:System.DateTimeOffset) 建構函式多載，等於執行 [DateTime](xref:System.DateTime) 值到 [DateTimeOffset](xref:System.DateTimeOffset) 值的隱含轉換。

透過 [DateTime](xref:System.DateTime) 值建立 [DateTimeOffset](xref:System.DateTimeOffset) 物件的第二個建構函式具有兩個參數︰要轉換的 [DateTime](xref:System.DateTime) 值，以及代表日期和時間與 UTC 之位移的 [TimeSpan](xref:System.TimeSpan) 值。 此位移值必須對應到建構函式之第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性，否則會擲回 [System.ArgumentException](xref:System.ArgumentException)。 如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則第二個參數的值必須是 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。 如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Local](xref:System.DateTimeKind.Local)，則第二個參數的值必須是本機系統的時區位移。 如果第一個參數的 [Kind](xref:System.DateTime.Kind) 屬性是 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)，則位移可以是任何有效值。 下列程式碼說明如何呼叫這個建構函式以將 [DateTime](xref:System.DateTime) 轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。

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

## <a name="implicit-type-conversion"></a>隱含類型轉換
 
[System.DateTimeOffset](xref:System.DateTimeOffset) 類型支援一種隱含類型轉換︰從 [System.DateTime](xref:System.DateTime) 值到 [DateTimeOffset](xref:System.DateTimeOffset) 值。 隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。 這樣就可以使用如下所述的程式碼。

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

所產生 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移取決於 DateTime.Kind](xref:System.DateTime.Kind) 屬性值。 如果它的值為 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc)，則位移設定為等於 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。 如果它的值為 [DateTimeKind.Local](xref:System.DateTimeKind.Local) 或 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)，則位移會設定為等於當地時區的位移。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>剖析日期和時間的字串表示

[System.DateTimeOffset](xref:System.DateTimeOffset) 類型支援四種方法，可讓您將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值：

* [Parse](xref:System.DateTimeOffset.Parse(System.String))，會嘗試將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並在轉換失敗時擲回例外狀況。

* [TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@))，會嘗試將日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值，並在轉換失敗時傳回 `false`。

* [ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider))，會嘗試將所指定格式之日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。 方法會在轉換失敗時擲回例外狀況。

* [TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@))，會嘗試將所指定格式之日期和時間的字串表示轉換為 [DateTimeOffset](xref:System.DateTimeOffset) 值。 如果轉換失敗，方法會傳回 `false`。

下列範例說明所有這四個字串轉換方法的呼叫來具現化 [DateTimeOffset](xref:System.DateTimeOffset) 值。

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

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)




<!--HONumber=Nov16_HO3-->


