---
title: "如何：在日期與時間值中顯示毫秒"
description: "如何在日期與時間值中顯示毫秒"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 78599e33-1c3f-4335-b320-751e35906338
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 7a110cf28ac8de558cd1460c61a650fc8a80e51a
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>如何：在日期與時間值中顯示毫秒

預設的日期和時間格式化方法 (例如 [DateTime.ToString()](xref:System.DateTime.ToString)) 包括時間值的小時、分鐘和秒，但不包括其毫秒部分。 本主題說明如何將日期和時間的毫秒部分加入格式化的日期和時間字串。

## <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>顯示 DateTime 值的毫秒部分

1. 如果您使用的是日期的字串表示，請使用靜態 [DateTime.Parse(String)](xref:System.DateTime.Parse(System.String)) 或 [DateTimeOffset.Parse(String)](xref:System.DateTimeOffset.Parse(System.String)) 方法，將它轉換成 [DateTime](xref:System.DateTime) 或 [DateTimeOffset](xref:System.DateTimeOffset) 值。

2. 若要擷取時間毫秒部分的字串表示，請呼叫日期和時間值的 [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) 或 [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String)) 方法，並且單獨傳遞 `fff` 或 `FFF` 自訂格式模式，或是連同其他自訂格式規範一併傳遞作為 format 參數。

## <a name="example"></a>範例

此範例會對主控台單獨顯示 [DateTime](xref:System.DateTime) 和 [DateTimeOffset](xref:System.DateTimeOffset) 值的毫秒部分，並包含在較長的日期和時間字串中一併顯示。 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class MillisecondDisplay
{
   public static void Main()
   {
      string dateString = "7/16/2008 8:32:45.126 AM";

      try
      {
         DateTime dateValue = DateTime.Parse(dateString);
         DateTimeOffset dateOffsetValue = DateTimeOffset.Parse(dateString);

         // Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", 
                           dateValue.ToString("fff"));
         Console.WriteLine("Millisecond component only: {0}", 
                           dateOffsetValue.ToString("fff"));

         // Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));

         // Append millisecond pattern to current culture's full date time pattern
         string fullPattern = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern;
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff");

         // Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", 
                           dateValue.ToString(fullPattern));
         Console.WriteLine("Modified full date time pattern: {0}",
                           dateOffsetValue.ToString(fullPattern));
      }
      catch (FormatException)
      {
         Console.WriteLine("Unable to convert {0} to a date.", dateString);
      }
   }
}
// The example displays the following output if the current culture is en-US:
//    Millisecond component only: 126
//    Millisecond component only: 126
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

```vb
Imports System.Globalization
Imports System.Text.REgularExpressions

Module MillisecondDisplay
   Public Sub Main()

      Dim dateString As String = "7/16/2008 8:32:45.126 AM"

      Try
         Dim dateValue As Date = Date.Parse(dateString)
         Dim dateOffsetValue As DateTimeOffset = DateTimeOffset.Parse(dateString)

         ' Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", _
                           dateValue.ToString("fff"))
         Console.WriteLine("Millisecond component only: {0}", _
                           dateOffsetValue.ToString("fff"))

         ' Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))

         ' Append millisecond pattern to current culture's full date time pattern
         Dim fullPattern As String = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff")

         ' Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateValue.ToString(fullPattern))                        
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateOffsetValue.ToString(fullPattern))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)      
      End Try
   End Sub
End Module
' The example displays the following output if the current culture is en-US:
'    Millisecond component only: 126
'    Millisecond component only: 126
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

`fff` 格式模式會包含毫秒值尾端的任何零。 `FFF` 格式模式則會加以隱藏。 下列範例會說明其間的差異。

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine(dateValue.ToString("fff"));    
Console.WriteLine(dateValue.ToString("FFF"));
// The example displays the following output to the console:
//    180
//    18 
```

```vb
Dim dateValue As New Date(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLIne(dateValue.ToString("fff"))    
Console.WriteLine(dateValue.ToString("FFF"))
' The example displays the following output to the console:
'    180
'    18
```

定義包含日期和時間毫秒部分之完整自訂格式規範的問題在於，它會定義硬式編碼格式，而該格式可能不會對應至應用程式目前文化特性中時間項目的排列。 建議改為擷取目前文化特性之 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件所定義的其中一個日期和時間顯示模式，然後修改該模式以加入毫秒。 此範例也會說明這個方法。 這個方法會從 [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) 屬性擷取目前文化特性的完整日期和時間模式，然後在其秒模式後面插入自訂模式 `.ffff`。 請注意，此範例使用規則運算式，以單一方法呼叫來執行這項操作。

除了毫秒之外，您也可以使用自訂格式規範顯示秒的其他小數部分。 例如，`f` 或 `F` 自訂格式規範會顯示十分之一秒，`ff` 或 `FF` 自訂格式規範會顯示百分之一秒，而 `ffff` 或 `FFFF` 自訂格式規範會顯示萬分之一秒。 毫秒的小數部分會在傳回的字串中被截斷，而不是四捨五入。 下列範例會使用這些格式規範。

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"));
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"));      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"));
// The example displays the following output to the console:
//    45.1 seconds
//    45.18 seconds
//    45.1800 seconds
```

```vb
Dim dateValue As New DateTime(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"))
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"))      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"))
' The example displays the following output to the console:
'    45.1 seconds
'    45.18 seconds
'    45.1800 seconds
```

> [!NOTE]
> 您可以使用非常小的小數單位來顯示秒，例如萬分之一秒或十萬分之一秒。 不過，這些值可能沒有太大的意義。 日期和時間值的精確度會根據系統時鐘的解析度而定。

## <a name="see-also"></a>另請參閱

[System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)

[自訂日期與時間格式字串](custom-datetime.md)


