---
title: "如何：從特定日期擷取一星期的哪一日"
description: "如何從特定日期擷取一星期的哪一日"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 88a8f8b9-f5c9-4503-b968-84468b52bb8e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 1b9d1d497524e62e5758c9be7be7b586a421a258
ms.lasthandoff: 03/03/2017

---

# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>如何：從特定日期擷取一星期的哪一日

.NET 可方便判斷特定日期是一週的第幾天，並可顯示特定日期當地語系化的工作日名稱。 您可以從 [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) 或 [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek) 屬性取得指出對應於特定日期是星期幾的列舉值。 相對地，擷取工作日名稱是一種格式化作業，可藉由呼叫格式化方法來執行，例如日期和時間值的 `ToString` 方法或 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法。 本主題示範如何執行下列格式化作業：

## <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>從特定日期擷取指出星期幾的數字

1. 如果您使用的是日期的字串表示，請使用靜態 [DateTime.Parse](xref:System.DateTime.Parse(System.String)) 或 [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) 方法，將它轉換成 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值。

2. 使用 [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) 或 [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek) 屬性，以擷取指出星期幾的 [DayOfWeek](xref:System.DayOfWeek) 值。

3. 如有必要，請將 [DayOfWeek](xref:System.DayOfWeek) 值轉換成整數。 

下列範例顯示代表特定日期是星期幾的整數。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      DateTime dateValue = new DateTime(2008, 6, 11);
      Console.WriteLine((int) dateValue.DayOfWeek);      
   }
}
// The example displays the following output:
//       3
```

```vb
Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.DayOfWeek)           
   End Sub
End Module
' The example displays the following output:
'    3
```

## <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>從特定日期擷取縮寫的工作日名稱。

1. 如果您使用的是日期的字串表示，請使用靜態 [DateTime.Parse](xref:System.DateTime.Parse(System.String)) 或 [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) 方法，將它轉換成 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值。

2. 您可以擷取目前文化特性或特定文化特性的工作日名稱縮寫。

    a. 若要擷取目前文化特性的工作日名稱縮寫，請呼叫日期和時間值的 [DateTime.ToString(String)](xref:System.DateTimeSystem.DateTime.ToString(System.String) 或 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 執行個體方法，並傳遞字串 "ddd" 作為 *format* 參數。 下列範例說明如何呼叫 `ToString(String)` 方法。
    
```csharp
using System;

public class Example
{
   public static void Main()
   {
  DateTime dateValue = new DateTime(2008, 6, 11);
  Console.WriteLine(dateValue.ToString("ddd"));   
   }
}
// The example displays the following output:
//       Wed
```

```vb
Module Example
   Public Sub Main()
  Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.ToString("ddd"))    
   End Sub
End Module
' The example displays the following output:
'       Wed
```

    b. To extract the abbreviated weekday name for a specific culture, call the date and time value’s [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) instance method. Pass the string "ddd" as the *format* parameter. Pass either a [CultureInfo](xref:System.Globalization.CultureInfo) or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that represents the culture whose weekday name you want to retrieve as the *provider* parameter. The following code illustrates a call to the [ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) method using a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the fr-FR culture.
    
```csharp
using System;
using System.Globalization;

public class Example
{
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("ddd", 
                            new CultureInfo("fr-FR")));    
    }
}
// The example displays the following output:
//       mer. 
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.ToString("ddd", 
                        New CultureInfo("fr-FR")))
   End Sub
End Module
' The example displays the following output:
'       mer.
```

## <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>從特定日期擷取完整的工作日名稱。

1. 如果您使用的是日期的字串表示，請使用靜態 [DateTime.Parse](xref:System.DateTime.Parse(System.String)) 或 [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) 方法，將它轉換成 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值。

2. 您可以擷取目前文化特性或特定文化特性的工作日名稱縮寫。

    a. 若要擷取目前文化特性的工作日名稱縮寫，請呼叫日期和時間值的 [DateTime.ToString(String)](xref:System.DateTimeSystem.DateTime.ToString(System.String) 或 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 執行個體方法，並傳遞字串 "ddd" 作為 *format* 參數。 下列範例說明如何呼叫 `ToString(String)` 方法。

```csharp
using System;

public class Example
{
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("dddd"));    
    }
}
// The example displays the following output:
//       Wednesday
```

```vb
Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.ToString("dddd"))
   End Sub
End Module
' The example displays the following output:
'       Wednesday
```

    b. To extract the weekday name for a specific culture, call the date and time value’s [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) instance method. Pass the string "dddd" as the *format* parameter. Pass either a [CultureInfo](xref:System.Globalization.CultureInfo) or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that represents the culture whose weekday name you want to retrieve as the *provider* parameter. The following code illustrates a call to the [ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) method using a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the es-ES  culture.

```csharp
using System;
using System.Globalization;

public class Example
{
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("dddd", 
                            new CultureInfo("es-ES")));    
    }
}
// The example displays the following output:
//       miércoles.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.ToString("dddd", _
                        New CultureInfo("es-ES"))) 
   End Sub
End Module
' The example displays the following output:
'       miércoles.
```

## <a name="example"></a>範例

此範例說明如何呼叫 [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) 和 [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek) 屬性以及 [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String) 或 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 方法，以針對特定日期擷取代表星期幾的數字、縮寫的工作日名稱，以及完整的工作日名稱。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string dateString = "6/11/2007";
      DateTime dateValue;
      DateTimeOffset dateOffsetValue;

      try
      {
         DateTimeFormatInfo dateTimeFormats;
         // Convert date representation to a date value
         dateValue = DateTime.Parse(dateString, CultureInfo.InvariantCulture);
         dateOffsetValue = new DateTimeOffset(dateValue, 
                                      TimeZoneInfo.Local.GetUtcOffset(dateValue));         

         // Convert date representation to a number indicating the day of week
         Console.WriteLine((int) dateValue.DayOfWeek);
         Console.WriteLine((int) dateOffsetValue.DayOfWeek);

         // Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"));
         Console.WriteLine(dateOffsetValue.ToString("ddd"));

         // Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"));
         Console.WriteLine(dateOffsetValue.ToString("dddd"));

         // Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", new CultureInfo("de-DE")));
         Console.WriteLine(dateOffsetValue.ToString("ddd", 
                                                     new CultureInfo("de-DE")));

         // Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = new CultureInfo("de-DE").DateTimeFormat;
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats));
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats));

         // Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", new CultureInfo("fr-FR")));
         Console.WriteLine(dateOffsetValue.ToString("ddd", 
                                                    new CultureInfo("fr-FR")));

         // Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = new CultureInfo("fr-FR").DateTimeFormat;
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats));
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats));
      }
      catch (FormatException)
      {
         Console.WriteLine("Unable to convert {0} to a date.", dateString);
      }
   }
}
// The example displays the following output:
//       1
//       1
//       Mon
//       Mon
//       Monday
//       Monday
//       Mo
//       Mo
//       Mo
//       Mo
//       lun.
//       lun.
//       lundi
//       lundi
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateString As String = "6/11/2007"
      Dim dateValue As Date
      Dim dateOffsetValue As DateTimeOffset

      Try
         Dim dateTimeFormats As DateTimeFormatInfo
         ' Convert date representation to a date value
         dateValue = Date.Parse(dateString, CultureInfo.InvariantCulture)
         dateOffsetValue = New DateTimeOffset(dateValue, _
                                     TimeZoneInfo.Local.GetUtcOffset(dateValue))            
         ' Convert date representation to a number indicating the day of week
         Console.WriteLine(dateValue.DayOfWeek)
         Console.WriteLine(dateOffsetValue.DayOfWeek)

         ' Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"))
         Console.WriteLine(dateOffsetValue.ToString("ddd"))

         ' Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"))
         Console.WriteLine(dateOffsetValue.ToString("dddd"))

         ' Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("de-DE")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("de-DE")))

         ' Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("de-DE").DateTimeFormat
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats))

         ' Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("fr-FR")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("fr-FR")))

         ' Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("fr-FR").DateTimeFormat
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'       1
'       1
'       Mon
'       Mon
'       Monday
'       Monday
'       Mo
'       Mo
'       Mo
'       Mo
'       lun.
'       lun.
'       lundi
'       lundi
```

個別語言可能會提供功能來複製或補充 .NET 提供的功能。 例如，Visual Basic 就有包含兩個這類函式：

* `Weekday` 會傳回指出特定日期是星期幾的數字。 它會將一週第一天的序數值視為一，而 [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) 屬性會將其視為零。

* `WeekdayName` 會傳回目前文化特性中對應特定工作日編號的週間日名稱。

下列範例說明如何使用 Visual Basic `Weekday` 和 `WeekdayName` 函式。

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#

      ' Get weekday number using Visual Basic Weekday function
      Console.WriteLine(Weekday(dateValue))                 ' Displays 4
      ' Compare with .NET DateTime.DayOfWeek property
      Console.WriteLine(dateValue.DayOfWeek)                ' Displays 3

      ' Get weekday name using Weekday and WeekdayName functions
      Console.WriteLine(WeekdayName(Weekday(dateValue)))    ' Displays Wednesday

      ' Change culture to de-DE
      Dim originalCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
      Thread.CurrentThread.CurrentCulture = New CultureInfo("de-DE")
      ' Get weekday name using Weekday and WeekdayName functions
      Console.WriteLine(WeekdayName(Weekday(dateValue)))   ' Displays Donnerstag

      ' Restore original culture
      Thread.CurrentThread.CurrentCulture = originalCulture   
   End Sub
End Module
``` 

您也可以使用 [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) 屬性傳回的值來擷取特定日期的工作日名稱。 這只需要在該屬性傳回的 [DayOfWeek](xref:System.DayOfWeek) 值上呼叫 [Enum.ToString](xref:System.Enum.ToString(System.String)) 方法。 不過，此技巧並不會產生目前文化特性的當地語系化工作日名稱，如下列範例所說明。 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      // Change current culture to fr-FR
      CultureInfo originalCulture = Thread.CurrentThread.CurrentCulture;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("fr-FR");

      DateTime dateValue = new DateTime(2008, 6, 11);
      // Display the DayOfWeek string representation
      Console.WriteLine(dateValue.DayOfWeek.ToString());   
      // Restore original current culture
      Thread.CurrentThread.CurrentCulture = originalCulture;
   }
}
// The example displays the following output:
//       Wednesday
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateString As String = "6/11/2007"
      Dim dateValue As Date
      Dim dateOffsetValue As DateTimeOffset

      Try
         Dim dateTimeFormats As DateTimeFormatInfo
         ' Convert date representation to a date value
         dateValue = Date.Parse(dateString, CultureInfo.InvariantCulture)
         dateOffsetValue = New DateTimeOffset(dateValue, _
                                     TimeZoneInfo.Local.GetUtcOffset(dateValue))            
         ' Convert date representation to a number indicating the day of week
         Console.WriteLine(dateValue.DayOfWeek)
         Console.WriteLine(dateOffsetValue.DayOfWeek)

         ' Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"))
         Console.WriteLine(dateOffsetValue.ToString("ddd"))

         ' Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"))
         Console.WriteLine(dateOffsetValue.ToString("dddd"))

         ' Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("de-DE")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("de-DE")))

         ' Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("de-DE").DateTimeFormat
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats))

         ' Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("fr-FR")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("fr-FR")))

         ' Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("fr-FR").DateTimeFormat
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'       1
'       1
'       Mon
'       Mon
'       Monday
'       Monday
'       Mo
'       Mo
'       Mo
'       Mo
'       lun.
'       lun.
'       lundi
'       lundi
```

## <a name="see-also"></a>請參閱

[執行格式化作業](performing-formatting-operations.md)

[標準日期與時間格式字串](standard-datetime.md)

[自訂日期與時間格式字串](custom-datetime.md)
    

