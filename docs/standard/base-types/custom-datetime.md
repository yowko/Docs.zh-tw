---
title: "自訂日期與時間格式字串"
description: "自訂日期與時間格式字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 45f286f5-92c9-4150-957c-fa6d394bc29b
translationtype: Human Translation
ms.sourcegitcommit: 28625def4199a660fe0ea04ab75f4f65d2e0c9c4
ms.openlocfilehash: 285e4bfd6a53d576ce4538b09a2561065c93e399
ms.lasthandoff: 02/23/2017

---

# <a name="custom-date-and-time-format-strings"></a>自訂日期與時間格式字串

日期和時間格式字串會定義對 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值執行格式化作業後所產生的文字表示。 另外還會定義剖析作業所需日期和時間值的表示，以便成功地將字串轉換成日期和時間。 自訂格式字串是由一個或多個自訂日期和時間格式規範所組成。 任何不是[標準日期和時間格式字串](standard-datetime.md)的字串都會被解譯為自訂日期和時間格式字串。 

自訂日期和時間格式字串可以與 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 值搭配使用。

在格式化作業中，自訂日期和時間格式字串可以搭配日期和時間執行個體的 `ToString` 方法或是支援複合格式的方法使用。 以下範例說明這兩種用法。 

```csharp
DateTime thisDate1 = new DateTime(2011, 6, 10);
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".");

DateTimeOffset thisDate2 = new DateTimeOffset(2011, 6, 10, 15, 24, 16, 
                                              TimeSpan.Zero);
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2); 
// The example displays the following output:
//    Today is June 10, 2011.
//    The current date and time: 06/10/11 15:24:16 +00:00
```

```vb
Dim thisDate1 As Date = #6/10/2011#
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".")

Dim thisDate2 As New DateTimeOffset(2011, 6, 10, 15, 24, 16, TimeSpan.Zero)
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2) 
' The example displays the following output:
'    Today is June 10, 2011.
'    The current date and time: 06/10/11 15:24:16 +00:00
```

在剖析作業中，自訂日期和時間格式字串可以搭配 [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) 和 [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) 方法使用。 這些方法需要輸入字串完全符合特定模式，剖析作業才會成功。 下列範例說明呼叫 [DateTimeOffset.ParseExact(String, String, IFormatProvider)](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) 方法來剖析必須包含日、月和兩位數年的日期。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] dateValues = { "30-12-2011", "12-30-2011", 
                              "30-12-11", "12-30-11" };
      string pattern = "MM-dd-yy";
      DateTime parsedDate;

      foreach (var dateValue in dateValues) {
         if (DateTime.TryParseExact(dateValue, pattern, null, 
                                   DateTimeStyles.None, out parsedDate))
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate);
         else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue);
      }
   }
}
// The example displays the following output:
//    Unable to convert '30-12-2011' to a date and time.
//    Unable to convert '12-30-2011' to a date and time.
//    Unable to convert '30-12-11' to a date and time.
//    Converted '12-30-11' to 12/30/2011.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValues() As String = { "30-12-2011", "12-30-2011", 
                                      "30-12-11", "12-30-11" }
      Dim pattern As String = "MM-dd-yy"
      Dim parsedDate As Date

      For Each dateValue As String In dateValues
         If DateTime.TryParseExact(dateValue, pattern, Nothing, 
                                   DateTimeStyles.None, parsedDate) Then
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate)
         Else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue)
         End If                                                         
      Next
   End Sub
End Module
' The example displays the following output:
'    Unable to convert '30-12-2011' to a date and time.
'    Unable to convert '12-30-2011' to a date and time.
'    Unable to convert '30-12-11' to a date and time.
'    Converted '12-30-11' to 12/30/2011.
```

下表說明自訂日期和時間格式規範，並顯示每個格式規範所產生的結果字串。 根據預設，結果字串會反映 en-US 文化特性的格式設定慣例。 如果特定格式規範會產生當地語系化的結果字串，則範例也會註明結果字串適用的文化特性。 如需使用自訂日期和時間格式字串的詳細資訊，請參閱注意一節。

格式規範 | 描述 | 範例
---------------- | ----------- | --------
"d" | 月份天數，從 1 到 31。 | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"dd" | 月份天數，從 01 到 31。 | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"ddd" | 星期幾的縮寫名稱。 | `2019-06-15T13:45:30 -> Mon (en-US)`; `2019-06-15T13:45:30 -> Пн (ru-RU)`; `2019-06-15T13:45:30 -> lun. (fr-FR)`
"dddd" | 星期幾的完整名稱。 | `2019-06-15T13:45:30 -> Monday (en-US)`; `2019-06-15T13:45:30 -> понедельник (ru-RU)`; `2019-06-15T13:45:30 -> lundi (fr-FR)`
"f" | 日期和時間值中的十分之一秒。 | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.05 -> 0` 
"ff" | 日期和時間值中的百分之一秒。 | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> 00`
"fff" | 日期和時間值中的千分之一秒。 | `6/15/2019 13:45:30.617 -> 617`; `6/15/2019 13:45:30.0005 -> 000`
"ffff" | 日期和時間值中的萬分之一秒。 | `2019-06-15T13:45:30.6175000 -> 6175`; `2019-06-15T13:45:30.0000500 -> 0000`
"fffff" | 日期和時間值中的十萬分之一秒。 | `2019-06-15T13:45:30.6175400 -> 61754`; `6/15/2019 13:45:30.000005 -> 00000`
"ffffff" | 日期和時間值中的百萬分之一秒。 | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> 000000`
"fffffff" | 日期和時間值中的千萬分之一秒。 | `2019-06-15T13:45:30.6175425 -> 6175425`;`2019-06-15T13:45:30.0001150 -> 0001150`
"F" | 如果不是零，則為日期和時間值中的十分之一秒。 | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.0500000 -> (no output)`
"FF" | 如果不是零，則為日期和時間值中的百分之一秒。 | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> (no output)`
"FFF" | 如果不是零，則為日期和時間值中的千分之一秒。 | `2019-06-15T13:45:30.6170000 -> 617`; `2019-06-15T13:45:30.0005000 -> (no output)`
"FFFF" | 如果不是零，則為日期和時間值中的萬分之一秒。 | `2019-06-15T13:45:30.5275000 -> 5275`; `2019-06-15T13:45:30.0000500 -> (no output)`
"FFFFF" | 如果不是零，則為日期和時間值中的十萬分之一秒。 | `2019-06-15T13:45:30.6175400 -> 61754`; `2019-06-15T13:45:30.0000050 -> (no output)`
"FFFFFF" | 如果不是零，則為日期和時間值中的百萬分之一秒。 | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> (no output)`
"FFFFFFF" | 如果不是零，則為日期和時間值中的千萬分之一秒。 | `2019-06-15T13:45:30.6175425 -> 6175425`; `2019-06-15T13:45:30.0001150 -> 000115`
"g"、"gg" | 週期或紀元。 | `2019-06-15T13:45:30.6170000 -> A.D.`
"h" | 採用 12 小時制的小時，從 1 到 12。 | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 1`
"hh" | 採用 12 小時制的小時，從 01 到 12。 | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 01`
"H" | 採用 24 小時制的小時，從 0 到 23。 | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 13`
"HH" | 採用 24 小時制的小時，從 00 到 23。 | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 13`
"K" | 時區資訊。 | 使用 [DateTime](xref:System.DateTime) 值︰ `2019-06-15T13:45:30, Kind Unspecified ->`；`2019-06-15T13:45:30, Kind Utc -> Z`；`2019-06-15T13:45:30, Kind Local -> -07:00 (depends on local computer settings)`；使用 [DateTimeOffset](xref:System.DateTimeOffset) 值︰`2019-06-15T01:45:30-07:00 --> -07:00`；`2019-06-15T08:45:30+00:00 --> +00:00`
"m" | 分鐘，從 0 到 59。 | `2019-06-15T01:09:30 -> 9`; `2019-06-15T13:29:30 -> 29`
"mm" | 分鐘，從 00 到 59。 | `2019-06-15T01:09:30 -> 09`; `2019-06-15T01:45:30 -> 45`
"M" | 月份，從 1 到 12。 | `2019-06-15T13:45:30 -> 6`
"MM" | 月份，從 01 到 12。 | `2019-06-15T13:45:30 -> 06`
"MMM" | 月份的縮寫名稱。 | `2019-06-15T13:45:30 -> Jun (en-US)`; `2019-06-15T13:45:30 -> juin (fr-FR)`; `2019-06-15T13:45:30 -> Jun (zu-ZA)`
"MMMM" | 月份的完整名稱。 | `2019-06-15T13:45:30 -> June (en-US)`; `2019-06-15T13:45:30 -> juni (da-DK)`; `2019-06-15T13:45:30 -> uJuni (zu-ZA)`
"s" | 秒數，從 0 到 59。 | `2019-06-15T13:45:09 -> 9`
"ss" | 秒數，從 00 到 59。 | `2019-06-15T13:45:09 -> 09`
"t" | AM/PM 指示項的第一個字元。 | `2019-06-15T13:45:30 -> P (en-US)`; `2019-06-15T13:45:30 -> 午 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"tt" | AM/PM 指示項。 | `2019-06-15T13:45:30 -> PM (en-US)`; `2019-06-15T13:45:30 -> 午後 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"y" | 年份，從 0 到 99。 | `0001-01-01T00:00:00 -> 1`; `0900-01-01T00:00:00 -> 0`; `1900-01-01T00:00:00 -> 0`; `2019-06-15T13:45:30 -> 9`; `2019-06-15T13:45:30 -> 19`
"yy" | 年份，從 00 到 99。 | `0001-01-01T00:00:00 -> 01`; `0900-01-01T00:00:00 -> 00`; `1900-01-01T00:00:00 -> 00`; `2019-06-15T13:45:30 -> 19`
"yyy" | 年份，至少三位數。 | `0001-01-01T00:00:00 -> 001`; `0900-01-01T00:00:00 -> 900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyy" | 以四位數表示的年份。 | `0001-01-01T00:00:00 -> 0001`; `0900-01-01T00:00:00 -> 0900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyyy" | 以五位數表示的年份。 | `0001-01-01T00:00:00 -> 00001`; `2019-06-15T13:45:30 -> 02019`
"z" | 與 UTC 相差的時數，不加上前置零。 | `2019-06-15T13:45:30-07:00 -> -7`
"zz" | 與 UTC 相差的時數，單一位數值會加上前置零。 | `2019-06-15T13:45:30-07:00 -> -07`
"zzz" | 與 UTC 相差的時數和分鐘數。 | `2019-06-15T13:45:30-07:00 -> -07:00`
":" | 時間分隔符號。 | `2019-06-15T13:45:30 -> : (en-US)`; `2019-06-15T13:45:30 -> . (it-IT)`; `2019-06-15T13:45:30 -> : (ja-JP)`
"/" | 日期分隔符號。 | `2019-06-15T13:45:30 -> / (en-US)`; `2019-06-15T13:45:30 -> - (ar-DZ)`; `2019-06-15T13:45:30 -> . (tr-TR)`
"string"、'string' | 常值字串分隔符號。 | `2019-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P`; `2019-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P`
% | 將下列字元定義為自訂格式規範。 | `2019-06-15T13:45:30 (%h) -> 1`
\ | 逸出字元。 | `2019-06-15T13:45:30 (h \h) -> 1 h`
任意字元 | 字元會原封不動地複製到結果字串。 | `2019-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A`

下列各節提供每個自訂日期和時間格式規範的其他資訊。 除非特別註明，否則每個規範都會產生相同的字串表示，無論是與 [DateTime](xref:System.DateTime) 值或 [DateTimeOffset](xref:System.DateTimeOffset) 值搭配使用。 

## <a name="the-d-custom-format-specifier"></a>"d" 自訂格式規範

"d" 自訂格式規範以 1 到 31 的數字來表示月份天數。 單一位數的天數會格式化為沒有前置零的數字。 

如果單獨使用 "d" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "d" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在幾個格式字串中加入 "d" 自訂格式規範。 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15); 

Console.WriteLine(date1.ToString("d, M", 
                  CultureInfo.InvariantCulture)); 
// Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays 29 agosto  
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("d, M", _
                  CultureInfo.InvariantCulture)) 
' Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays 29 agosto 
```

## <a name="the-dd-custom-format-specifier"></a>"dd" 自訂格式規範

"dd" 自訂格式字串以 01 到 31 的數字來表示月份天數。 單一位數的天數會格式化為有前置零的數字。 

下列範例會在自訂格式字串中加入 "dd" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-ddd-custom-format-specifier"></a>"ddd" 自訂格式規範

"ddd" 自訂格式規範表示星期幾的縮寫名稱。 星期幾的當地語系化縮寫名稱是擷取自目前或指定之文化特性的 [DateTimeFormatInfo.AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) 屬性。 

下列範例會在自訂格式字串中加入 "ddd" 自訂格式規範。 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-dddd-custom-format-specifier"></a>"dddd" 自訂格式規範

"dddd" 自訂格式規範 (加上任意個額外的 "d" 規範) 表示星期幾的完整名稱。 星期幾的當地語系化名稱是擷取自目前或指定之文化特性的 [DateTimeFormatInfo.DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) 屬性。 

下列範例會在自訂格式字串中加入 "dddd" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto                                          
```

## <a name="the-f-custom-format-specifier"></a>"f" 自訂格式規範

"f" 自訂格式規範表示秒數的一位有效小數位數，也就是說，它表示日期和時間值中的十分之一秒。

如果單獨使用 "f" 格式規範，而沒有其他格式規範，則會將它解譯為 "f" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

當您使用 "f" 格式規範作為提供給 [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) 或 [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) 方法的一部分格式字串時，"f" 格式規範的數目表示小數秒的最高有效位數，必須存在此位數才能成功剖析字串。

下列範例會在自訂格式字串中加入 "f" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>"ff" 自訂格式規範

"ff" 自訂格式規範表示秒數的兩位有效小數位數，也就是說，它表示日期和時間值中的百分之一秒。 

下列範例會在自訂格式字串中加入 "ff" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>"fff" 自訂格式規範

"fff" 自訂格式規範表示秒數的三位有效小數位數，也就是說，它表示日期和時間值中的千分之一秒。 

下列範例會在自訂格式字串中加入 "fff" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>"ffff" 自訂格式規範

"ffff" 自訂格式規範表示秒數的四位有效小數位數，也就是說，它表示日期和時間值中的萬分之一秒。

雖然時間值的秒數部分可以顯示到萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="the-fffff-custom-format-specifier"></a>"fffff" 自訂格式規範

"fffff" 自訂格式規範表示秒數的五位有效小數位數，也就是說，它表示日期和時間值中的十萬分之一秒。

雖然時間值的秒數部分可以顯示到十萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 

## <a name="the-ffffff-custom-format-specifier"></a>"ffffff" 自訂格式規範

"ffffff" 自訂格式規範表示秒數的六位有效小數位數，也就是說，它表示日期和時間值中的百萬分之一秒。

雖然時間值的秒數部分可以顯示到百萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 

## <a name="the-fffffff-custom-format-specifier"></a>"fffffff" 自訂格式規範

"fffffff" 自訂格式規範表示秒數的七位有效小數位數，也就是說，它表示日期和時間值中的千萬分之一秒。

雖然時間值的秒數部分可以顯示到千萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。 

## <a name="the-f-custom-format-specifier"></a>"F" 自訂格式規範

"F" 自訂格式規範表示秒數的一位有效小數位數，也就是說，它表示日期和時間值中的十分之一秒。 如果數字為零，則不會顯示任何內容。 

如果單獨使用 "F" 格式規範，而沒有其他格式規範，則會將它解譯為 "F" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

與 [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) 或 [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) 方法搭配使用的 "F" 格式規範數目，表示小數秒的最高有效位數上限，要成功剖析字串就不能超過此位數。

下列範例會在自訂格式字串中加入 "F" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>"FF" 自訂格式規範

"FF" 自訂格式規範表示秒數的兩位有效小數位數，也就是說，它表示日期和時間值中的百分之一秒。 不過，結尾的零或兩個零的數字都不會顯示。 

下列範例會在自訂格式字串中加入 "FF" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>"FFF" 自訂格式規範

"FFF" 自訂格式規範表示秒數的三位有效小數位數，也就是說，它表示日期和時間值中的千分之一秒。 不過，結尾的零或三個零的數字都不會顯示。 

下列範例會在自訂格式字串中加入 "FFF" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
````

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>"FFFF" 自訂格式規範

"FFFF" 自訂格式規範表示秒數的四位有效小數位數，也就是說，它表示日期和時間值中的萬分之一秒。 不過，結尾的零或四個零的數字都不會顯示。

雖然時間值的秒數部分可以顯示到萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" 自訂格式規範

"FFFFF" 自訂格式規範表示秒數的五位有效小數位數，也就是說，它表示日期和時間值中的十萬分之一秒。 不過，結尾的零或五個零的數字都不會顯示。

雖然時間值的秒數部分可以顯示到十萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" 自訂格式規範

"FFFFFF" 自訂格式規範表示秒數的六位有效小數位數，也就是說，它表示日期和時間值中的百萬分之一秒。 不過，結尾的零或六個零的數字都不會顯示。

雖然時間值的秒數部分可以顯示到百萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" 自訂格式規範

"FFFFFFF" 自訂格式規範表示秒數的七位有效小數位數，也就是說，它表示日期和時間值中的千萬分之一秒。 不過，結尾的零或七個零的數字都不會顯示。

雖然時間值的秒數部分可以顯示到千萬分之一秒，但該值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="the-g-or-gg-custom-format-specifier"></a>"g" 或 "gg" 自訂格式規範

"g" 或 "gg" 自訂格式規範 (加上任意個額外的 "g" 規範) 表示時期或時代，例如 A.D.。 如果要格式化的日期沒有關聯的時期或時代字串，則格式化作業會忽略這個規範。 

如果單獨使用 "g" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "g" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "g" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(70, 08, 04);

Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.InvariantCulture));
// Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));                         
// Displays 08/04/0070 ap. J.-C.
```

```vb
Dim date1 As Date = #08/04/0070#

Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.InvariantCulture))
' Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))                         
' Displays 08/04/0070 ap. J.-C.
```

## <a name="the-h-custom-format-specifier"></a>"h" 自訂格式規範

"h" 自訂格式規範以 1 到 12 的數字來表示小時，也就是以 12 小時制來表示小時，從午夜或中午開始計算整點時數。 午夜後的特定小時與下午的相同小時會難以區分。 小時是不進位的，而且單一位數的小時會格式化為沒有前置零的數字。 例如，假設時間為上午或下午 5:43，則此自訂格式規範會顯示 "5"。 

如果單獨使用 "h" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "h" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-hh-custom-format-specifier"></a>"hh" 自訂格式規範

"hh" 自訂格式規範 (加上任意個額外的 "h" 規範) 以 01 到 12 的數字來表示小時，也就是以 12 小時制來表示小時，從午夜或中午開始計算整點時數。 午夜後的特定小時與下午的相同小時會難以區分。 小時是不進位的，而且單一位數的小時會格式化為有前置零的數字。 例如，假設時間為上午或下午 5:43，則此格式規範會顯示 "05"。

下列範例會在自訂格式字串中加入 "hh" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-h-custom-format-specifier"></a>"H" 自訂格式規範

"H" 自訂格式規範以 0 到 23 的數字來表示小時，也就是採用以零為起始的 24 小時制來表示小時，從午夜開始計算時數。 單一位數的小時會格式化為沒有前置零的數字。 

如果單獨使用 "H" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "H" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("H:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 6:09:01 
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("H:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 6:09:01 
```

## <a name="the-hh-custom-format-specifier"></a>"HH" 自訂格式規範

"HH" 自訂格式規範 (加上任意個額外的 "H" 規範) 以 00 到 23 的數字來表示小時，也就是採用以零為起始的 24 小時制來表示小時，從午夜開始計算時數。 單一位數的小時會格式化為具有前置零的數字。 

下列範例會在自訂格式字串中加入 "HH" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("HH:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01                        
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("HH:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01
```

## <a name="the-k-custom-format-specifier"></a>"K" 自訂格式規範

"K" 自訂格式規範表示日期和時間值的時區資訊。 與 [DateTime](xref:System.DateTime) 值搭配使用這個格式規範時，結果字串會由 [DateTime.Kind](xref:System.DateTime.Kind) 屬性的值定義： 
 
* 若為當地時區 ([DateTimeKind.Local](xref:System.DateTimeKind.Local) 的 [DateTime.Kind](xref:System.DateTime.Kind) 屬性值)，此規範相當於 "zzz" 規範，所產生的結果字串會包含當地時間與國際標準時間 (UTC) 之間的時差，例如 "-07:00"。 

* 若為 UTC 時間 ([DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 的 [DateTime.Kind](xref:System.DateTime.Kind) 屬性值)，結果字串會包含 "Z" 字元來表示 UTC 日期。 

* 若為未指定時區的時間 ([DateTime.Kind](xref:System.DateTime.Kind) 屬性等於 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的時間)，結果就相當於 [String.Empty](xref:System.String#System_String_Empty)。 

若為 [DateTimeOffset](xref:System.DateTimeOffset) 值，"K" 格式規範相當於 "zz" 格式規範，所產生的結果字串會包含 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之間的時差。 

如果單獨使用 "K" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會顯示美國太平洋時區中，"K" 自訂格式規範與各種 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 值搭配使用所產生的結果字串。

```csharp
Console.WriteLine(DateTime.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTime.UtcNow.ToString("%K"));
// Displays Z      
Console.WriteLine("'{0}'", 
                  DateTime.SpecifyKind(DateTime.Now, 
                       DateTimeKind.Unspecified).ToString("%K"));
// Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"));
// Displays +00:00
Console.WriteLine(new DateTimeOffset(2008, 5, 1, 6, 30, 0, 
                      new TimeSpan(5, 0, 0)).ToString("%K"));
// Displays +05:00  
```

```vb
Console.WriteLine(Date.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(Date.UtcNow.ToString("%K"))
' Displays Z      
Console.WriteLine("'{0}'", _
                  Date.SpecifyKind(Date.Now, _
                                   DateTimeKind.Unspecified). _
                  ToString("%K"))
' Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"))
' Displays +00:00
Console.WriteLine(New DateTimeOffset(2008, 5, 1, 6, 30, 0, _
                                     New TimeSpan(5, 0, 0)). _
                  ToString("%K"))
' Displays +05:00 
```

## <a name="the-m-custom-format-specifier"></a>"m" 自訂格式規範

"m" 自訂格式規範以 0 到 59 的數字來表示分鐘。 分鐘表示自上個整點以來已經過的完整分鐘數。 單一位數的分鐘會格式化為沒有前置零的數字。 

如果單獨使用 "m" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "m" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。 

下列範例會在自訂格式字串中加入 "m" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-mm-custom-format-specifier"></a>"mm" 自訂格式規範

"mm" 自訂格式規範 (加上任意個額外的 "m" 規範) 以 00 到 59 的數字來表示分鐘。 分鐘表示自上個整點以來已經過的完整分鐘數。 單一位數的分鐘會格式化為具有前置零的數字。 

下列範例會在自訂格式字串中加入 "mm" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-m-custom-format-specifier"></a>"M" 自訂格式規範

"M" 自訂格式規範以 1 到 12 的數字來表示月份 (如果是有 13 個月的行事曆則從 1 到 13)。 單一位數的月份會格式化為沒有前置零的數字。 

如果單獨使用 "M" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "M" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "M" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 18);
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("nl-NL")));                       
// Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("lv-LV")));                        
// Displays (8) Aug, augusts
```

```vb
Dim date1 As Date = #8/18/2008#
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("nl-NL")))                        
' Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("lv-LV")))                        
' Displays (8) Aug, augusts 
```

## <a name="the-mm-custom-format-specifier"></a>"MM" 自訂格式規範

"MM" 自訂格式規範以 01 到 12 的數字來表示月份 (如果是有 13 個月的行事曆則從 1 到 13)。 單一位數的月份會格式化為有前置零的數字。 

下列範例會在自訂格式字串中加入 "MM" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-mmm-custom-format-specifier"></a>"MMM" 自訂格式規範

"MMM" 自訂格式規範表示月份的縮寫名稱。 月份的當地語系化縮寫名稱是擷取自目前或指定之文化特性的 [DateTimeFormatInfo.AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) 屬性。

下列範例會在自訂格式字串中加入 "MMM" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-mmmm-custom-format-specifier"></a>"MMMM" 自訂格式規範

"MMMM" 自訂格式規範表示月份的完整名稱。 月份的當地語系化名稱是擷取自目前或指定之文化特性的 [DateTimeFormatInfo.MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) 屬性。 

下列範例會在自訂格式字串中加入 "MMMM" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto 
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto  
```

## <a name="the-s-custom-format-specifier"></a>"s" 自訂格式規範

"s" 自訂格式規範以 0 到 59 的數字來表示秒數。 結果表示自上個分鐘以來已經過的完整秒數。 單一位數的秒數會格式化為沒有前置零的數字。 

如果單獨使用 "s" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "s" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。 

下列範例會在自訂格式字串中加入 "s" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-ss-custom-format-specifier"></a>"ss" 自訂格式規範

"ss" 自訂格式規範 (加上任意個額外的 "s" 規範) 以 00 到 59 的數字來表示秒數。 結果表示自上個分鐘以來已經過的完整秒數。 單一位數的秒數會格式化為具有前置零的數字。 

下列範例會在自訂格式字串中加入 "ss" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-t-custom-format-specifier"></a>"t" 自訂格式規範

"t" 自訂格式規範表示 AM/PM 指示項的第一個字元。 適當的當地語系化指示項是擷取自目前或特定文化特性的 [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) 或 [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) 屬性。 AM 指示項用於從 0:00:00 (午夜) 到 11:59:59.999 為止的所有時間。 PM 指示項用於從 12:00:00 (中午) 到 23:59:59.999 為止的所有時間。 

如果單獨使用 "t" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "t" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "t" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-tt-custom-format-specifier"></a>"tt" 自訂格式規範

"tt" 自訂格式規範 (加上任意個額外的 "t" 規範) 表示整個 AM/PM 指示項。 適當的當地語系化指示項是擷取自目前或特定文化特性的 [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) 或 [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) 屬性。 AM 指示項用於從 0:00:00 (午夜) 到 11:59:59.999 為止的所有時間。 PM 指示項用於從 12:00:00 (中午) 到 23:59:59.999 為止的所有時間。

對於需要特別強調 AM 與 PM 的語言，請務必使用 "tt" 規範。 其中一種就是日文，日文的 AM 和 PM 指示項的第二個字元 (非第一個字元) 不同。

下列範例會在自訂格式字串中加入 "tt" 自訂格式規範。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-y-custom-format-specifier"></a>"y" 自訂格式規範

"y" 自訂格式規範以一位或兩位數來表示年份。 如果年份超過兩個位數，結果中只會出現兩個低位數字。 如果兩位數年份的第一個數字以零開始 (例如 2008)，則會格式化為沒有前置零的數字。 

如果單獨使用 "y" 格式規範，而沒有其他自訂格式規範，則會將它解譯為 "y" 標準日期和時間格式規範。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

下列範例會在自訂格式字串中加入 "y" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yy-custom-format-specifier"></a>"yy" 自訂格式規範

"yy" 自訂格式規範以兩位數來表示年份。 如果年份超過兩個位數，結果中只會出現兩個低位數字。 如果兩位數年份少於兩個有效位數，則會以前置零填補此數字來產生兩位數。

在剖析作業中，使用 "yy" 自訂格式規範所剖析的兩位數年份，是根據格式提供者現行曆法的 [Calendar.TwoDigitYearMax](xref:System.Globalization.Calendar.TwoDigitYearMax) 屬性進行解譯。 下列範例會使用 en-US 文化特性的預設西曆 (在此案例中為目前的文化特性)，剖析具有兩位數年份之日期的字串表示。 接著它會將目前文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件變更為使用已修改 [TwoDigitYearMax](xref:System.Globalization.GregorianCalendar.TwoDigitYearMax) 屬性的 [GregorianCalendar](xref:System.Globalization.GregorianCalendar) 物件。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fmt = "dd-MMM-yy";
      string value = "24-Jan-49";

      Calendar cal = (Calendar) CultureInfo.CurrentCulture.Calendar.Clone();
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
      Console.WriteLine();

      cal.TwoDigitYearMax = 2099;
      CultureInfo culture = (CultureInfo) CultureInfo.CurrentCulture.Clone();
      culture.DateTimeFormat.Calendar = cal;
      Thread.CurrentThread.CurrentCulture = culture;

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
   }
}
// The example displays the following output:
//       Two Digit Year Range: 1930 - 2029
//       1/24/1949
//       
//       Two Digit Year Range: 2000 - 2099
//       1/24/2049
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fmt As String = "dd-MMM-yy"
      Dim value As String = "24-Jan-49"

      Dim cal As Calendar = CType(CultureInfo.CurrentCulture.Calendar.Clone(), Calendar)
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
      Console.WriteLine()

      cal.TwoDigitYearMax = 2099
      Dim culture As CultureInfo = CType(CultureInfo.CurrentCulture.Clone(), CultureInfo)
      culture.DateTimeFormat.Calendar = cal
      Thread.CurrentThread.CurrentCulture = culture

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Two Digit Year Range: 1930 - 2029
'       1/24/1949
'       
'       Two Digit Year Range: 2000 - 2099
'       1/24/2049
```

下列範例會在自訂格式字串中加入 "yy" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyy-custom-format-specifier"></a>"yyy" 自訂格式規範

"yyy" 自訂格式規範以最少三位數來表示年份。 如果年份超過三個有效位數，它們會包含在結果字串中。 如果年份少於三個位數，則會以前置零填補此數字來產生三位數。

> [!NOTE]
> 對於可具有五位數年份的泰國佛教曆法，此格式規範會顯示全部有效位數。

下列範例會在自訂格式字串中加入 "yyy" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010      
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-yyyy-custom-format-specifier"></a>"yyyy" 自訂格式規範

"yyyy" 自訂格式規範以最少四位數來表示年份。 如果年份超過四個有效位數，它們會包含在結果字串中。 如果年份少於四個位數，則會以前置零填補此數字，以產生四個位數。

> [!NOTE]
> 對於可具有五位數年份的泰國佛教曆法，此格式規範會顯示全部有效位數。

下列範例會在自訂格式字串中加入 "yyyy" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyyyy-custom-format-specifier"></a>"yyyyy" 自訂格式規範

"yyyyy" 自訂格式規範 (加上任意個額外的 "y" 規範) 以最少五位數來表示年份。 如果年份超過五個有效位數，它們會包含在結果字串中。 如果年份少於五位數，則會以前置零填補此數字來產生五位數。

如果有更多 "y" 規範，則會視需要以前置零填補此數字，以產生該 "y" 規範數目的位數。 

下列範例會在自訂格式字串中加入 "yyyyy" 自訂格式規範。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-z-custom-format-specifier"></a>"z" 自訂格式規範

搭配 [DateTime](xref:System.DateTime) 值使用時，"z" 自訂格式規範表示本機作業系統時區與國際標準時間 (UTC) 之間的時差 (帶正負號)，以小時為單位。 它不會反映執行個體的 [DateTime.Kind](xref:System.DateTime.Kind) 屬性值。 因此，不建議將 "z" 格式規範搭配 [DateTime](xref:System.DateTime) 值使用。

搭配 [DateTimeOffset](xref:System.DateTimeOffset) 值使用時，此格式規範表示 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之間的時差，以小時為單位。 

顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為沒有前置零的數字。 

如果單獨使用 "z" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。 

下列範例會在自訂格式字串中加入 "z" 自訂格式規範。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zz-custom-format-specifier"></a>"zz" 自訂格式規範

搭配 [DateTime](xref:System.DateTime) 值使用時，"zz" 自訂格式規範表示本機作業系統時區與國際標準時間 (UTC) 之間的時差 (帶正負號)，以小時為單位。 它不會反映執行個體的 [DateTime.Kind](xref:System.DateTime.Kind) 屬性值。 因此，不建議將 "zz" 格式規範搭配 [DateTime](xref:System.DateTime) 值使用。

搭配 [DateTimeOffset](xref:System.DateTimeOffset) 值使用時，此格式規範表示 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之間的時差，以小時為單位。

顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為有前置零的數字。 

下列範例會在自訂格式字串中加入 "zz" 自訂格式規範。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zzz-custom-format-specifier"></a>"zzz" 自訂格式規範

搭配 [DateTime](xref:System.DateTime) 值使用時，"zzz" 自訂格式規範表示本機作業系統時區與國際標準時間 (UTC) 之間的時差 (帶正負號)，以小時為單位。 它不會反映執行個體的 [DateTime.Kind](xref:System.DateTime.Kind) 屬性值。 因此，不建議將 "zzz" 格式規範搭配 [DateTime](xref:System.DateTime) 值使用。

搭配 [DateTimeOffset](xref:System.DateTimeOffset) 值使用時，此格式規範表示 [DateTimeOffset](xref:System.DateTimeOffset) 值與 UTC 之間的時差，以小時為單位。

顯示時差時，一定會有前置正負號。 加號 (+) 表示早於 UTC 的時數，減號 (-) 表示晚於 UTC 的時數。 單一位數的時差會格式化為有前置零的數字。 

下列範例會在自訂格式字串中加入 "zzz" 自訂格式規範。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the--custom-format-specifier"></a>":" 自訂格式規範

":" 自訂格式規範表示時間分隔符號，用於區別時、分、秒。 

如果單獨使用 ":" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

## <a name="the--custom-format-specifier"></a>"/" 自訂格式規範

"/" 自訂格式規範表示日期分隔符號，用於區別年、月、日。 

如果單獨使用 "/" 格式規範，而沒有其他自訂格式規範，則會將它解譯為標準日期和時間格式規範，並擲回 [FormatException](xref:System.FormatException)。 如需如何使用單一格式規範的詳細資訊，請參閱本主題後文的[使用單一自訂格式規範](#using-single-custom-format-specifiers)。

## <a name="character-literals"></a>字元常值

自訂日期和時間格式字串中的下列字元是保留字元，一律會解譯為格式字元；若是 "、'、/ 和 \,，則解譯為特殊字元。 

  |   |   |   |      
- | - | - | - | -
F | H | K | M | d
f | G | h | m | 秒
Y | Y | z | % | :
/ | " | ' | \ |
  |   |   |   |
  
所有其他字元一律會解譯為字元常值，並在格式化作業中，原封不動地包含在結果字串中。 在剖析作業中，它們必須完全符合輸入字串中的字元；這項比較會區分大小寫。 

下列範例包含常值字元 "PST" (太平洋標準時間) 和 "PDT" (太平洋日光節約時間)，以表示格式字串中的當地時區。 請注意，此字串會包含在結果字串中，而且包含當地時區字串的字串也會成功剖析。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String[] formats = { "dd MMM yyyy hh:mm tt PST", 
                           "dd MMM yyyy hh:mm tt PDT" };
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(formats[1]));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm PST";
      DateTime newDate;
      if (DateTime.TryParseExact(value, formats, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim formats() As String = { "dd MMM yyyy hh:mm tt PST", 
                                  "dd MMM yyyy hh:mm tt PDT" }
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(formats(1)))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm PST"
      Dim newDate As Date
      If Date.TryParseExact(value, formats, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM PDT
'       12/25/2016 12:00:00 PM
```

您可以使用兩種方式來指定將字元解譯為常值字元，而不是保留字元，以便包含在結果字串中，或在輸入字串中成功剖析：

* 將每個保留字元逸出。 如需詳細資訊，請參閱[使用逸出字元](#using-the-escape-character)。 
  
  下列範例包含常值字元 "pst" (太平洋標準時間)，以表示格式字串中的當地時區。 由於 "s" 與 "t" 是自訂格式字串，因此必須逸出這兩個字元才能解譯為字元常值。 
  
```csharp
using System;
using System.Globalization;

public class Example
{
  public static void Main()
  {
      String format = "dd MMM yyyy hh:mm tt p\\s\\t";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                  DateTimeStyles.None, out newDate)) 
          Console.WriteLine(newDate);
      else
          Console.WriteLine("Unable to parse '{0}'", value);
  }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt p\s\t" 
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```
  
* 以雙引號或單引號括住整個常值字串。 下列範例類似上一個範例，不同之處在於 "pst" 會以雙引號括住，以表示整個分隔的字串都應該解譯為字元常值。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String format = "dd MMM yyyy hh:mm tt \"pst\"";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt ""pst"""  
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```

## <a name="notes"></a>備註


### <a name="using-single-custom-format-specifiers"></a>使用單一自訂格式規範

自訂日期和時間格式字串是由兩個或多個字元所組成。 日期和時間格式化方法會將任何單一字元字串解譯為標準日期和時間格式字串。 如果這些方法無法將該字元辨識為有效的格式規範，則會擲回 [FormatException](xref:System.FormatException)。 例如，僅由規範 "h" 所組成的格式字串會解譯為標準日期和時間字串。 不過，在這種特殊情形下會擲回例外狀況，因為並沒有 "h" 標準日期和時間格式規範。 

若要使用任何自訂日期和時間格式規範做為格式字串中的唯一規範 (也就是單獨使用 "d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":" 或 "/" 自訂格式規範)，請在規範之前或之後加上一個空格，或在單一自訂日期和時間規範之前加上一個百分比 ("%") 格式規範。

例如，"`%h`" 會解譯為自訂日期和時間格式字串，該字串會顯示由目前日期和時間值所表示的小時。 您也可以使用 " h" 或 "h " 格式字串，然而這會在結果字串中的小時旁邊加上空格。 下列範例示範這三個格式字串。


```csharp
DateTime dat1 = new DateTime(2009, 6, 15, 13, 45, 0);

Console.WriteLine("'{0:%h}'", dat1);
Console.WriteLine("'{0: h}'", dat1);
Console.WriteLine("'{0:h }'", dat1);
// The example displays the following output:
//       '1'
//       ' 1'
//       '1 '
```

```vb
Dim dat1 As Date = #6/15/2009 1:45PM#

Console.WriteLine("'{0:%h}'", dat1)
Console.WriteLine("'{0: h}'", dat1)
Console.WriteLine("'{0:h }'", dat1)
' The example displays the following output:
'       '1'
'       ' 1'
'       '1 '
```

### <a name="using-the-escape-character"></a>使用逸出字元

格式字串中的 "d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":" 或 "/" 字元會解譯為自訂格式規範，而不是常值字元。 若要避免將字元解譯為格式規範，您可以在前面加上反斜線 (\)，這是逸出字元。 逸出字元表示接下來的字元是字元常值，應該原封不動地放入結果字串中。

若要在結果字串中加上反斜線，您必須再加上一個反斜線 (變成 `\\`)，才能將反斜線解譯為常值。

> [!NOTE]
> 某些編譯器 (例如 C# 編譯器) 也可能會將單一反斜線字元解譯為逸出字元。 為了確保字串在格式化時能夠正確獲得解譯，您可以在字串前面加上逐字字串常值字元 (@ 字元)，或在每個反斜線前面再加上一個反斜線字元。 下列 C# 範例示範這兩種做法。

下列範例會使用逸出字元，以避免格式化作業將 "h" 和 "m" 字元解譯為格式規範。 

```csharp
DateTime date = new DateTime(2009, 06, 15, 13, 45, 30, 90);
string fmt1 = "h \\h m \\m";
string fmt2 = @"h \h m \m";

Console.WriteLine("{0} ({1}) -> {2}", date, fmt1, date.ToString(fmt1));
Console.WriteLine("{0} ({1}) -> {2}", date, fmt2, date.ToString(fmt2));
// The example displays the following output:
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
```

```vb
Dim date1 As Date = #6/15/2009 13:45#
Dim fmt As String = "h \h m \m"

Console.WriteLine("{0} ({1}) -> {2}", date1, fmt, date1.ToString(fmt))
' The example displays the following output:
'       6/15/2009 1:45:00 PM (h \h m \m) -> 1 h 45 m 
```

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo 屬性

格式會受到目前 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件屬性的影響，而此物件是由目前執行緒文化特性隱含提供或由叫用格式之方法的 [IFormatProvider](xref:System.IFormatProvider) 參數明確提供。 在 [IFormatProvider](xref:System.IFormatProvider) 參數中，您應該指定表示文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或指定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 

許多自訂日期和時間格式規範所產生的結果字串，也取決於目前 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的屬性。 您的應用程式可以變更對應的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 屬性，藉此變更某些自訂日期和時間格式規範所產生的結果。 例如，"ddd" 格式規範會將 [AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) 字串陣列中找到的縮寫星期幾名稱加入結果字串。 同樣地，"MMMM" 格式規範會將 [MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) 字串陣列中找到的完整月份名稱加入結果字串。

## <a name="see-also"></a>請參閱

[System.DateTime](xref:System.DateTime)

[System.IFormatProvider](xref:System.IFormatProvider)

[格式化類型](formatting-types.md)

[標準日期與時間格式字串](standard-datetime.md)


