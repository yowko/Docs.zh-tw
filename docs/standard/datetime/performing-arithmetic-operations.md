---
title: "使用日期和時間執行算術運算"
description: "使用日期和時間執行算術運算"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 64fbb3b25d5959ac1dd781d2076775560d926e1a

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a>使用日期和時間執行算術運算

雖然 [System.DateTime](xref:System.DateTime) 和 [System.DateTimeOffset](xref:System.DateTimeOffset) 結構提供對其值執行算術運算的成員，但是算術運算的結果非常不同。 本文會檢查這些差異、將它們與日期和時間資料的時區感知程度產生關聯，以及討論如何使用日期和時間資料來執行完全時區感知運算。

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>使用 DateTime 值的比較和算術運算

[System.DateTime](xref:System.DateTime) 值具有有限時區感知程度。 [DateTime.Kind](xref:System.DateTime.Kind) 屬性允許將 [System.DateTimeKind](xref:System.DateTimeKind) 值指派給日期和時間，指出它是否代表當地時間、國際標準時間 (UTC) 或未指定時區的時間。 不過，對 [DateTime](xref:System.DateTime) 值比較或執行日期和時間運算時，會忽略這個有限時區資訊。 下列範例會比較目前當地時間與目前 UTC 時間，以說明這點。

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

[DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) 方法會報告當地時間早於 (或晚於) UTC 時間，接著減法運算會指出 UTC 與當地時間之間的時差，以美國太平洋標準時間時區系統來說相差七個小時。 但因為這兩個值提供單一時間點的不同表示，所以在此情況下，此時間間隔很明顯地完全歸因於當地時區與 UTC 的位移。 

一般來說，[DateTimeKind](xref:System.DateTimeKind) 屬性不會影響 [DateTime](xref:System.DateTime) 比較和算術方法所傳回的結果 (如兩個相同時間點的比較所指出)，但是可能會影響這些結果的解譯。 例如: 

* 針對 [DateTimeKind](xref:System.DateTimeKind) 屬性等於 [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 的兩個日期和時間值所執行的任何算術運算結果，會反映兩個值的實際時間間隔。 同樣地，兩個這類日期和時間值的比較會精確地反映時間的關聯性。

* 針對 [DateTimeKind](xref:System.DateTimeKind) 屬性等於 [DateTimeKind.Local](xref:System.DateTimeKind.Local) 的兩個日期和時間值或具有不同 [DateTimeKind](xref:System.DateTimeKind) 屬性值的兩個日期和時間值所執行的任何算術或比較運算結果，會反映兩個值的時鐘時間差異。 

* 當地日期和時間值的算術或比較作業不會考慮特定值是不明確或無效，也不會考慮當地時區與日光節約時間之轉換所產生的任何調整規則的影響。

* 任何比較或計算 UTC 與當地時間之差異的作業，都會在結果中包含等於當地時區與 UTC 之位移的時間間隔。 

* 任何比較或計算未指定時間與 UTC 或當地時間之差異的作業，都會反映簡單時鐘時間。 不考慮時區差異，而且結果不會反映如何套用時區調整規則。 

* 任何比較或計算兩個未指定時間之差異的作業都可能包含未知間隔，而未知間隔反映兩個不同時區的時間差異。

有許多情況是時區差異不會影響日期和時間計算，或日期和時間資料的內容會定義比較或算術運算的意義。 如需其中部分項目的討論，請參閱[在 DateTime、DateTimeOffset、TimeSpan 與 TimeZoneInfo 之間選擇](choosing-between-datetime.md)。

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>使用 DateTimeOffset 值的比較和算術運算

[System.DateTimeOffset](xref:System.DateTimeOffset) 值不只包含日期和時間，也會包含明確定義該日期和時間相對於 UTC 的位移。 這樣可能會針對 [System.DateTime](xref:System.DateTime) 值定義略有不同的相等性。 而 [DateTime](xref:System.DateTime) 值若具有相同日期和時間值則相等，[DateTimeOffset](xref:System.DateTimeOffset) 值若參照相同時間點則相等。 如果用於判斷兩個日期和時間之間隔的比較和大部分算術運算，則這採用更精確且較不需要解譯的 [DateTimeOffset](xref:System.DateTimeOffset) 值。 下列範例 (即 [DateTimeOffset](xref:System.DateTimeOffset) 等於比較當地和 UTC DateTime 值的前一個範例) 說明這項行為差異。

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

在此範例中，[DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) 方法表示目前當地時間和目前 UTC 時間相等，而且減去 [DateTimeOffset](xref:System.DateTimeOffset) 值表示兩個時間的差異是 [TimeSpan.Zero](xref:System.TimeSpan.Zero)。 

在日期和時間運算中使用 [DateTimeOffset](xref:System.DateTimeOffset) 值的主要限制，在於雖然 [DateTimeOffset](xref:System.DateTimeOffset) 值具有一些時區感知，但並不是完全時區感知的。 雖然 [DateTimeOffset](xref:System.DateTimeOffset) 值的位移會在第一次指派 [DateTimeOffset](xref:System.DateTimeOffset) 變數的值時反映時區與 UTC 的位移，但是之後會與時區解除關聯。 因為它不再與可識別時間直接關聯，所以加上和減去日期和時間間隔不會視為時區的調整規則。 

舉例而言，美國中央標準時間時區轉換成日光節約時間是在 2008 年 3 月 9 日的 凌晨 2:00 發生。 這表示，中央標準時間 2008 年 3 月 9 日上午 1:30 加上兩個半小時的間隔， 就會產生 2008 年 3 月 9 日凌晨 5:00 的 日期和時間。 不過，如下列範例所示，加上兩個半小時後為 2008 年 3 月 9 日 凌晨 4:00。 請注意，雖然這並非我們感興趣的時區時間 (亦即，它沒有預期的時區位移)，但是這項作業的結果確實代表正確時間點。

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a>使用時區時間的算術運算

[System.TimeZoneInfo](xref:System.TimeZoneInfo) 類別未提供任何方法，可在您執行日期和時間運算時自動套用調整規則。 不過，作法是將時區時間轉換為 UTC，並執行算術運算，然後從 UTC 轉換回時區時間。 如需詳細資訊，請參閱[如何：在日期和時間運算中使用時區](use-time-zones-in-arithmetic.md)。

例如，下列程式碼與前面的程式碼類似，也是將 2008 年 3 月 9 日 凌晨 2:00 加上兩個半小時。 不過，因為它會先將美加中部標準時間轉換為 UTC，再執行日期和時間運算，然後將 UTC 的結果轉換回美加中部標準時間，所以產生的時間會反映美加中部標準時區到日光節約時間的轉換。

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[如何：在日期與時間運算中使用時區](use-time-zones-in-arithmetic.md)





<!--HONumber=Nov16_HO1-->


