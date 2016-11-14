---
title: "在 .NET 中剖析日期和時間字串"
description: "在 .NET 中剖析日期和時間字串"
keywords: ".NET、.NET Core"
author: stevehoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e61514cd-5329-4eb8-b122-482fffb54ab7
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: ad1976f44d8c4ec3a22c6156b4f6ad58f867908b

---

# <a name="parsing-date-and-time-strings-in-net"></a>在 .NET 中剖析日期和時間字串

剖析方法會將表示日期和時間的字串，轉換為同等的 [DateTime](xref:System.DateTime) 物件。 [Parse](xref:System.DateTime.Parse(System.String)) 和 [TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) 方法會轉換數種常見的日期和時間表示。 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 和 [TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@)) 方法會將符合的字串表示轉換成日期和時間格式字串指定的模式。 (請參閱[標準日期和時間格式字串](standard-datetime.md)以及[自訂日期和時間格式字串](custom-datetime.md)主題。) 

剖析受到格式提供者的屬性影響，格式提供者提供的資訊為日期和時間分隔符號使用的字串，以及月份、日和紀元名稱等等。 格式提供者是目前的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，由目前執行緒文化特性隱含提供或由剖析方法的 [IFormatProvider](xref:System.IFormatProvider) 參數明確提供。 在 [IFormatProvider](xref:System.IFormatProvider) 參數中指定表示文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或指定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 

要剖析的日期表示字串，必須包含月份以及至少天或年。 時間的字串表示必須包含小時，以及至少分鐘或 AM/PM 指示項。 但若有可能，剖析會為省略的元件提供預設值。 遺漏日期預設為目前的日期，遺漏的年份預設為目前的年份，遺漏的某月某日預設為該月第一天，而遺漏的時間預設為午夜。 

如果字串表示只指定時間，剖析會傳回 [DateTime](xref:System.DateTime) 物件及設定為 [Today](xref:System.DateTime.Today) 屬性對應值的其 [Year](xref:System.DateTime.Year)、[Month](xref:System.DateTime.Month) 及 [Day](xref:System.DateTime.Day) 屬性。 不過，如果剖析方法中指定了 [DateTimeStyles.NoCurrentDateDefault](xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault) 常數，則產生的 year、month 及 day 屬性都會設成值 1。

除了日期和時間元件外，日期和時間的字串表示可以包含表示時間與國際標準時間 (UTC) 差的位移。 例如，字串 "2/14/2007 5:32:00 -7:00" 定義的時間比 UTC 早 7 個小時。 如果時間的字串表示中省略了位移，剖析會傳回 [DateTime](xref:System.DateTime) 物件及其設為 [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 的 [Kind](xref:System.DateTime.Kind) 屬性。 如果指定了位移，剖析會傳回 [DateTime](xref:System.DateTime) 物件及其設為 [Local](xref:System.DateTimeKind.Local) 的 [Kind](xref:System.DateTime.Kind) 屬性，且其值會調整成您電腦的當地時區。 您可以使用 [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 常數及剖析方法修改此行為。

格式提供者也可以用來解譯不明確的數值日期。 例如，在字串 "02/03/04" 中，不清楚那個日期元件表示月、日和年。 這種情況下，就會根據格式提供者中的相似日期格式順序來解譯元件。 

## <a name="parse"></a>剖析

下面的程式碼範例會示範如何使用 `Parse` 方法將字串轉換成 `DateTime`。 本例會使用與目前執行緒相關聯的文化特性執行剖析。 如果與目前文化特性相關聯的 [CultureInfo](xref:System.Globalization.CultureInfo) 無法剖析輸入的字串，則會擲回 [FormatException](xref:System.FormatException)。

```csharp
string MyString = "Jan 1, 2009";
DateTime MyDateTime = DateTime.Parse(MyString);
Console.WriteLine(MyDateTime);
// Displays the following output on a system whose culture is en-US:
//       1/1/2009 12:00:00 AM
```

```vb
Dim MyString As String = "Jan 1, 2009"
Dim MyDateTime As DateTime = DateTime.Parse(MyString)
Console.WriteLine(MyDateTime)
' Displays the following output on a system whose culture is en-US:
'       1/1/2009 12:00:00 AM
```

您也可以指定一個設為該物件定義的文化特性之一的 `CultureInfo`，或者指定 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性傳回的標準 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件之一。 下列程式碼範例使用格式提供者將德文字串剖析成 `DateTime`。 代表 de-DE 文化特性的 `CultureInfo` 是由剖析中的字串定義及傳遞，以確保成功剖析這個特定的字串。 這可排除 `CurrentThread` 的 `CurrentCulture` 有任何設定。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output:
//       6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

不過，雖然您可以使用 [Parse](xref:System.DateTime.Parse(System.String)) 方法的多載指定自訂的格式提供者，此方法卻不支援使用非標準的格式提供者。 若要剖析以非標準格式表示的日期和時間，請改用 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法。

下列程式碼範例使用 [DateTimeStyles](xref:System.Globalization.DateTimeStyles) 列舉，指定目前的日期和時間資訊不應加入字串不定義的欄位 `DateTime` 中。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("de-DE");
      string MyString = "12 Juni 2008";
      DateTime MyDateTime = DateTime.Parse(MyString, MyCultureInfo, 
                                           DateTimeStyles.NoCurrentDateDefault);
      Console.WriteLine(MyDateTime);
   }
}
// The example displays the following output if the current culture is en-US:
//      6/12/2008 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("de-DE")
      Dim MyString As String = "12 Juni 2008"
      Dim MyDateTime As DateTime = DateTime.Parse(MyString, MyCultureInfo)
      Console.WriteLine(MyDateTime)
   End Sub
End Module
' The example displays the following output:
'       6/12/2008 12:00:00 AM
```

## <a name="parseexact"></a>ParseExact

[DateTime.ParseExact]((xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法會將符合指定字串模式的字串轉換成 `DateTime` 物件。 當不是指定格式的字串傳遞至這個方法時，就會擲回 [FormatException](xref:System.FormatException)。 您可以指定標準日期和時間格式指定名稱的其中之一，或自訂日期和時間格式指定名稱的有限組合。 使用自訂格式指定名稱，您有機會建構自訂的辨識字串。 如需指定名稱的說明，請參閱[標準日期和時間格式字串](standard-datetime.md)以及[自訂日期和時間格式字串](custom-datetime.md)主題。 

每個 [ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)) 方法的多載也都有 [IFormatProvider](xref:System.IFormatProvider) 參數，通常提供有關格式字串的特定文化特性資訊。 此 [IFormatProvider](xref:System.IFormatProvider) 物件通常是代表標準文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件，或 [CultureInfo.DateTimeFormat](xref:System.Globalization.CultureInfo.DateTimeFormat) 屬性所傳回的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 不過，不同於其他日期和時間剖析函式，此方法也支援定義非標準日期和時間格式的 [IFormatProvider](xref:System.IFormatProvider)。 

在下列程式碼範例中，`ParseExact` 方法接到了要剖析的字串物件，後面跟著格式指定名稱和 `CultureInfo` 物件。 此 `ParseExact` 方法只能剖析以 en-US 文化特性展現完整日期模式的字串。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      CultureInfo MyCultureInfo = new CultureInfo("en-US");
      string[] MyString = {" Friday, April 10, 2009", "Friday, April 10, 2009"};
      foreach (string dateString in MyString)
      {
         try {
            DateTime MyDateTime = DateTime.ParseExact(dateString, "D", MyCultureInfo);
            Console.WriteLine(MyDateTime);
         }
         catch (FormatException) {
            Console.WriteLine("Unable to parse '{0}'", dateString);
         }
      }
   }
}
// The example displays the following output:
//       Unable to parse ' Friday, April 10, 2009'
//       4/10/2009 12:00:00 AM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim MyCultureInfo As CultureInfo = new CultureInfo("en-US")
      Dim MyString() As String = {" Friday, April 10, 2009", "Friday, April 10, 2009"}
      For Each dateString As String In MyString
         Try
            Dim MyDateTime As DateTime = DateTime.ParseExact(dateString, "D", _
                                                             MyCultureInfo)
            Console.WriteLine(MyDateTime)
         Catch e As FormatException
            Console.WriteLine("Unable to parse '{0}'", dateString)
         End Try
      Next
   End Sub
End Module
' The example displays the following output:
'       Unable to parse ' Friday, April 10, 2009'
'       4/10/2009 12:00:00 AM
```

## <a name="see-also"></a>另請參閱

[在 .NET 中剖析字串](parsing-strings.md)

[在 .NET 中格式化類型](formatting-types.md)

[在 .NET 中轉換類型](type-conversion.md)




<!--HONumber=Nov16_HO1-->


