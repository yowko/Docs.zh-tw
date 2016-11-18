---
title: "如何：在非西曆中顯示日期"
description: "如何在非西曆中顯示日期"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 93f06e1d-544b-4ccc-a0b2-95cd674852cb
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 85c9d450be48c553ea3a1f1a0f16c298941fa325

---

# <a name="how-to-display-dates-in-nongregorian-calendars"></a>如何：在非西曆中顯示日期

[DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 類型使用西曆作為其預設月曆。 這表示即使該日期和時間是使用其他月曆所建立，呼叫日期和時間值的 `ToString` 方法仍會使用西曆顯示該日期和時間的字串表示。 以下範例將說明這種情況，其中會使用兩種不同的方式建立波斯曆的日期和時間值，但是在呼叫 [ToString](xref:System.DateTime.ToString) 方法時，仍會以西曆顯示這些日期和時間值。 此範例反映兩種常用來顯示特殊月曆之日期，但不正確的技術。

```csharp
PersianCalendar persianCal = new PersianCalendar();

DateTime persianDate = persianCal.ToDateTime(1387, 3, 18, 12, 0, 0, 0);
Console.WriteLine(persianDate.ToString());

persianDate = new DateTime(1387, 3, 18, persianCal);
Console.WriteLine(persianDate.ToString());
// The example displays the following output to the console:
//       6/7/2008 12:00:00 PM
//       6/7/2008 12:00:00 AM
```

```vb
Dim persianCal As New PersianCalendar()

Dim persianDate As Date = persianCal.ToDateTime(1387, 3, 18, _
                                                12, 0, 0, 0)
Console.WriteLine(persianDate.ToString())

persianDate = New DateTime(1387, 3, 18, persianCal)
Console.WriteLine(persianDate.ToString())
' The example displays the following output to the console:
'       6/7/2008 12:00:00 PM
'       6/7/2008 12:00:00 AM
```

這兩種不同的技術可用來顯示特殊月曆的日期。 第一種技術要求該月曆必須是某個文化特性的預設月曆。 第二種技術可搭配任何月曆使用。

## <a name="to-display-the-date-for-a-cultures-default-calendar"></a>顯示文化特性預設月曆的日期

1. 具現化衍生自 [Calendar](xref:System.Globalization.Calendar) 類別的月曆物件，該物件代表要使用的月曆。

2. 具現化 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，該物件代表將使用其格式來顯示日期的文化特性。

3. 呼叫 [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) 方法，判斷月曆物件是否為 [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) 屬性所傳回陣列的成員。 這表示該月曆可作為 [CultureInfo](xref:System.Globalization.CultureInfo) 物件的預設月曆。 如果不是陣列成員，請依照＜顯示任何月曆中的日期＞一節中的指示進行。

4. 將月曆物件指派給 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性所傳回之 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的 [Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) 屬性。

  > [!NOTE]
  > [CultureInfo](xref:System.Globalization.CultureInfo) 類別也有 [Calendar](xref:System.Globalization.CultureInfo.Calendar) 屬性。 不過該屬性是唯讀且固定的，不會變更以反映指派給 [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) 屬性的新預設月曆。
  
5. 呼叫 [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)) 或 [DateTime.ToString(String,IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 方法，並將上一個步驟中修改其預設月曆的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件傳遞給該方法。

## <a name="to-display-the-date-in-any-calendar"></a>顯示任何月曆中的日期

1. 具現化衍生自 [Calendar](xref:System.Globalization.Calendar) 類別的月曆物件，該物件代表要使用的月曆。

2. 決定應出現在日期和時間值的字串表示中的日期和時間項目。

3. 針對您要顯示的每一個日期和時間項目，呼叫月曆物件的 `Get…` 方法。 下列為可用的方法：

    * [GetYear](xref:System.Globalization.Calendar.GetYear(System.DateTime))，用來顯示適當月曆中的年份。
    
    * [GetMonth](xref:System.Globalization.Calendar.GetMonth(System.DateTime))，用來顯示適當月曆中的月份。 
    
    * [GetDayOfMonth](xref:System.Globalization.Calendar.GetDayOfMonth(System.DateTime))，用來顯示適當月曆中某個月份的日期數字。
    
    * [GetHour](xref:System.Globalization.Calendar.GetHour(System.DateTime))，用來顯示適當月曆中某天的小時。
    
    * [GetMinute](xref:System.Globalization.Calendar.GetMinute(System.DateTime))，用來顯示適當月曆中某小時的分鐘。
    
    * [GetSecond](xref:System.Globalization.Calendar.GetSecond(System.DateTime))，用來顯示適當月曆中某分鐘的秒鐘。 
    
    * [GetMilliseconds](xref:System.Globalization.Calendar.GetMilliseconds(System.DateTime))，用來顯示適當月曆中某一秒的毫秒。
    
## <a name="example"></a>範例
    
這個範例顯示使用兩種不同月曆的日期。 日期會在定義回曆作為 ar-JO 文化特性的預設月曆之後顯示，並且會使用波斯曆顯示日期，而波斯曆並不是 fa-IR 文化特性支援的選用月曆。

```csharp
using System;
using System.Globalization;

public class CalendarDates
{
   public static void Main()
   {
      HijriCalendar hijriCal = new HijriCalendar();
      CalendarUtility hijriUtil = new CalendarUtility(hijriCal);
      DateTime dateValue1 = new DateTime(1429, 6, 29, hijriCal);
      DateTimeOffset dateValue2 = new DateTimeOffset(dateValue1, 
                                  TimeZoneInfo.Local.GetUtcOffset(dateValue1));
      CultureInfo jc = CultureInfo.CreateSpecificCulture("ar-JO");

      // Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", 
                        dateValue1.ToString("d"));
      // Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", 
                        dateValue1.ToString("d", jc));
      // Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:");
      // Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc));
      // Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc));

      Console.WriteLine();

      PersianCalendar persianCal = new PersianCalendar();
      CalendarUtility persianUtil = new CalendarUtility(persianCal);
      CultureInfo ic = CultureInfo.CreateSpecificCulture("fa-IR");

      // Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}",       
                        dateValue1.ToString("d", ic));
      // Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic));
      // Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic));
   }
}

public class CalendarUtility
{
   private Calendar thisCalendar;
   private CultureInfo targetCulture;

   public CalendarUtility(Calendar cal)
   {
      this.thisCalendar = cal;
   }

   private bool CalendarExists(CultureInfo culture)
   {
      this.targetCulture = culture;
      return Array.Exists(this.targetCulture.OptionalCalendars, 
                          this.HasSameName);
   }

   private bool HasSameName(Calendar cal)
   {
      if (cal.ToString() == thisCalendar.ToString())
         return true;
      else
         return false;
   }

   public string DisplayDate(DateTime dateToDisplay, CultureInfo culture)
   {
      DateTimeOffset displayOffsetDate = dateToDisplay;
      return DisplayDate(displayOffsetDate, culture);
   }

   public string DisplayDate(DateTimeOffset dateToDisplay, 
                             CultureInfo culture)
   {
      string specifier = "yyyy/MM/dd";

      if (this.CalendarExists(culture))
      {
         Console.WriteLine("Displaying date in supported {0} calendar...", 
                           this.thisCalendar.GetType().Name);
         culture.DateTimeFormat.Calendar = this.thisCalendar;
         return dateToDisplay.ToString(specifier, culture);
      }
      else
      {
         Console.WriteLine("Displaying date in unsupported {0} calendar...", 
                           thisCalendar.GetType().Name);

         string separator = targetCulture.DateTimeFormat.DateSeparator;

         return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") +
                separator +
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") + 
                separator +
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00"); 
      }
   } 
}
// The example displays the following output to the console:
//       Using the system default culture: 7/3/2008
//       Using the ar-JO culture's original default calendar: 03/07/2008
//       Using the ar-JO culture with Hijri as the default calendar:
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       Displaying date in supported HijriCalendar calendar...
//       1429/06/29
//       
//       Using the ir-FA culture's default calendar: 7/3/2008
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
//       Displaying date in unsupported PersianCalendar calendar...
//       1387/04/13
```

```vb
Imports System.Globalization

Public Class CalendarDates
   Public Shared Sub Main()
      Dim hijriCal As New HijriCalendar()
      Dim hijriUtil As New CalendarUtility(hijriCal)
      Dim dateValue1 As Date = New Date(1429, 6, 29, hijriCal)
      Dim dateValue2 As DateTimeOffset = New DateTimeOffset(dateValue1, _
                                         TimeZoneInfo.Local.GetUtcOffset(dateValue1))
      Dim jc As CultureInfo = CultureInfo.CreateSpecificCulture("ar-JO")

      ' Display the date using the Gregorian calendar.
      Console.WriteLine("Using the system default culture: {0}", _
                        dateValue1.ToString("d"))
      ' Display the date using the ar-JO culture's original default calendar.
      Console.WriteLine("Using the ar-JO culture's original default calendar: {0}", _
                        dateValue1.ToString("d", jc))
      ' Display the date using the Hijri calendar.
      Console.WriteLine("Using the ar-JO culture with Hijri as the default calendar:")
      ' Display a Date value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue1, jc))
      ' Display a DateTimeOffset value.
      Console.WriteLine(hijriUtil.DisplayDate(dateValue2, jc))

      Console.WriteLine()

      Dim persianCal As New PersianCalendar()
      Dim persianUtil As New CalendarUtility(persianCal)
      Dim ic As CultureInfo = CultureInfo.CreateSpecificCulture("fa-IR")

      ' Display the date using the ir-FA culture's default calendar.
      Console.WriteLine("Using the ir-FA culture's default calendar: {0}", _      
                        dateValue1.ToString("d", ic))
      ' Display a Date value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue1, ic))
      ' Display a DateTimeOffset value.
      Console.WriteLine(persianUtil.DisplayDate(dateValue2, ic))
   End Sub
End Class

Public Class CalendarUtility
   Private thisCalendar As Calendar
   Private targetCulture As CultureInfo

   Public Sub New(cal As Calendar)
      Me.thisCalendar = cal
   End Sub

   Private Function CalendarExists(culture As CultureInfo) As Boolean
      Me.targetCulture = culture
      Return Array.Exists(Me.targetCulture.OptionalCalendars, _
                          AddressOf Me.HasSameName)
   End Function 

   Private Function HasSameName(cal As Calendar) As Boolean
      If cal.ToString() = thisCalendar.ToString() Then
         Return True
      Else
         Return False
      End If
   End Function

   Public Function DisplayDate(dateToDisplay As Date, _
                               culture As CultureInfo) As String
      Dim displayOffsetDate As DateTimeOffset = dateToDisplay
      Return DisplayDate(displayOffsetDate, culture)
   End Function

   Public Function DisplayDate(dateToDisplay As DateTimeOffset, _
                               culture As CultureInfo) As String
      Dim specifier As String = "yyyy/MM/dd"

      If Me.CalendarExists(culture) Then
         Console.WriteLine("Displaying date in supported {0} calendar...", _
                           thisCalendar.GetType().Name)
         culture.DateTimeFormat.Calendar = Me.thisCalendar
         Return dateToDisplay.ToString(specifier, culture)
      Else
         Console.WriteLine("Displaying date in unsupported {0} calendar...", _
                           thisCalendar.GetType().Name)

         Dim separator As String = targetCulture.DateTimeFormat.DateSeparator

         Return thisCalendar.GetYear(dateToDisplay.DateTime).ToString("0000") & separator & _
                thisCalendar.GetMonth(dateToDisplay.DateTime).ToString("00") & separator & _
                thisCalendar.GetDayOfMonth(dateToDisplay.DateTime).ToString("00") 
      End If             
   End Function
End Class
' The example displays the following output to the console:
'       Using the system default culture: 7/3/2008
'       Using the ar-JO culture's original default calendar: 03/07/2008
'       Using the ar-JO culture with Hijri as the default calendar:
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       Displaying date in supported HijriCalendar calendar...
'       1429/06/29
'       
'       Using the ir-FA culture's default calendar: 7/3/2008
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
'       Displaying date in unsupported PersianCalendar calendar...
'       1387/04/13
```

每個 [CultureInfo](xref:System.Globalization.CultureInfo) 物件可支援一或多個月曆，並以 [OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) 屬性表示。 其中一個月曆會指定為文化特性的預設月曆，並且由唯讀 [CultureInfo.Calendar](xref:System.Globalization.CultureInfo.Calendar) 屬性傳回。 另一個選用月曆可以藉由指派代表該月曆的 [Calendar](xref:System.Globalization.Calendar) 物件給 [DateTimeFormatInfo.Calendar](xref:System.Globalization.DateTimeFormatInfo.Calendar) 屬性 (由 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性傳回) 指定為預設值。 不過，有些月曆 (例如 [PersianCalendar](xref:System.Globalization.PersianCalendar) 類別所代表的波斯曆) 無法作為任何文化特性的選用月曆。   

這個範例會定義可重複使用的月曆公用程式類別 `CalendarUtility`，用來處理使用特殊月曆產生日期的字串表示時的許多細節。 `CalendarUtility` 類別具有下列成員： 

* 參數化的建構函式，其單一參數為用來表示日期的 [Calendar](xref:System.Globalization.Calendar) 物件。 這個參數會指派給類別的私用欄位。

* `CalendarExists` 是私用方法，會傳回布林值指出以參數形式傳遞給方法的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，是否支援 `CalendarUtility` 物件所代表的日曆。 這個方法會包裝 [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) 方法的呼叫，並且傳遞 [CultureInfo.OptionalCalendars](xref:System.Globalization.CultureInfo.OptionalCalendars) 陣列給該方法。

* `HasSameName` 是指派給 [Predicate&lt;T&gt;](xref:System.Predicate%601) 委派的私用方法，會以參數形態傳遞給 [Array.Exists&lt;T&gt;](xref:System.Array.Exists``1(``0[],System.Predicate{``0})) 方法。 每一個陣列成員都會傳遞至方法，直到方法傳回 `true` 為止。 這個方法會判斷選用月曆的名稱是否與 `CalendarUtility` 物件代表的月曆相同。

* `DisplayDate` 是多載的公用方法，[DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值會以參數形態傳遞給此方法在 `CalendarUtility` 物件所代表的日曆中表示，以及要使用之格式化規則所屬的文化特性。 在傳回日期的字串表示時，其行為會根據文化特性是否支援要使用其格式化規則的目標月曆而定。

不論在本範例中用來建立 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值的月曆為何，該值通常會以西曆日期來表示。 這是因為 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 類型不會保留任何月曆資訊。 這兩個值會在內部表示為自 0001 年 1 月 1 日午夜開始經過的刻度數。 該數字的轉譯會根據月曆而定。 大部分文化特性的預設月曆是西曆。 

## <a name="see-also"></a>另請參閱

[執行格式化作業](performing-formatting-operations.md)



<!--HONumber=Nov16_HO3-->


