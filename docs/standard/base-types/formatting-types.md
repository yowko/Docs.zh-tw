---
title: "格式化類型"
description: "格式化類型"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: dc0693c2e2c034c4c71b4270ef2812be4af72e72
ms.lasthandoff: 03/02/2017

---

# <a name="formatting-types"></a>格式化類型

格式化是將類別、結構或列舉值的執行個體轉換成字串表示的過程，通常是為了將結果字串展示予使用者，或是為了將字串藉還原序列化方式還原成原始的資料類型。 這種轉換可能面臨幾項挑戰：

* 值的內部儲存方式不見得反映出使用者想要的檢視方式。 例如，電話號碼可能以 **8009999999** 的格式儲存，但這並不太符合使用者的閱讀習慣。 應該改以顯示成 **800-999-9999**。 如需以此方式格式化數字的範例，請參閱[自訂格式字串](#custom-format-strings)一節。 

* 物件轉換後的字串表示有時候並不符合直覺。 例如，**Temperature** 物件或 **Person** 物件的字串表示應該為何種格式，就不是那麼清楚。 如需以各種方式格式化 **Temperature** 物件的範例，請參閱[標準格式字串](#standard-format-strings)一節。

* 值的格式通常需要符合文化特性。 例如，如果應用程式需要使用數字來表達貨幣值，則數值字串應該包含目前文化特性的貨幣符號、群組分隔符號 (即大部分文化特性中的千位分隔符號) 和小數點符號。 如需範例，請參閱[使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)一節。 

* 應用程式可能需要以不同的方式來顯示相同的值。 例如，應用程式在表示列舉成員時，在做法上可能是顯示其名稱的字串表示，或顯示其基礎值。 如需以不同方式格式化 [DayOfWeek](xref:System.DayOfWeek) 列舉成員的範例，請參閱[標準格式字串](#standard-format-strings)一節。

.NET 提供豐富的格式化支援，可滿足開發人員的這些需求。 

> [!NOTE]
> 格式化會將某種類型的值轉換為字串表示。 剖析是格式化的反向操作。 剖析作業會從資料類型的字串表示來建立資料類型的執行個體。 如需將字串轉換為其他資料類型的資訊，請參閱[剖析字串](parsing-strings.md)。

本概觀包含下列各節：

* [.NET 中的格式化​​](#formatting-in-net)

* [使用 ToString 方法的預設格式](#default-formatting-using-the-tostring-method)

* [覆寫 ToString 方法](#overriding-the-tostring-method)

* [ToString 方法及格式字串](#the-tostring-method-and-format-strings)

    * [標準格式字串](#standard-format-strings)
    
    * [自訂格式字串](#custom-format-strings)
    
    * [格式字串與 .NET 類型](#format-strings-and-net-types)
    
* [使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [區分文化特性格式的數值](#culture-sensitive-formatting-of-numeric-values)
    
    * [區分文化特性格式的日期與時間值](#culture-sensitive-formatting-of-date-and-time-values)
    
* [IFormattable 介面](#the-iformattable-interface)

* [複合格式](#composite-formatting)

* [使用 ICustomFormatter 的自訂格式](#custom-formatting-with-icustomformatter)

* [相關主題](#related-topics)

* [參考](#reference)

## <a name="formatting-in-net"></a>.NET 中的格式化​​

[Object.ToString](xref:System.Object.ToString)預設會實作格式化的基本機制。本主題後文的[使用 ToString 方法的預設格式](#default-formatting-using-the-tostring-method)一節將有所討論。 不過，.NET 提供幾種方式來修改和擴充其預設格式化支援。 這些需求包括下列各項：

* 覆寫 [Object.ToString](xref:System.Object.ToString) 方法來定義物件值的自訂字串表示。 如需詳細資訊，請參閱本主題後文的[覆寫 ToString 方法](#overriding-the-tostring-method)一節。

* 定義格式規範，格式規範讓物件值的字串表示可以採用多種形式。 例如，下列陳述式中的 "X" 格式規範會將整數轉換為十六進位值的字串表示。

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  如需格式規範的詳細資訊，請參閱 [ToString 方法與格式字串](#the-tostring-method-and-format-strings)一節。
  
* 透過格式提供者來採用特定文化特性的格式化慣例。 例如，下列陳述式會使用 en-US 文化特性的格式化慣例來顯示貨幣值。 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  如需如何使用格式提供者及 IFormatProvider 介面的詳細資訊，請參閱[使用格式提供者及 IFormatProvider 介面執行區分文化特性的格式化](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)一節。  
  
* 實作 [IFormattable](xref:System.IFormattable) 介面，以同時支援使用 [Convert](xref:System.Convert) 類別和複合格式來轉換字串。 如需詳細資訊，請參閱 [IFormattable 介面](#the-iformattable-interface)一節。

* 使用複合格式將值的字串表示嵌入更大的字串中。 如需詳細資訊，請參閱[複合格式](#composite-formatting)一節。

* 實作 [ICustomFormatter](xref:System.ICustomFormatter) 和 [IFormatProvider](xref:System.IFormatProvider) 來提供完整的自訂格式解決方案。 如需詳細資訊，請參閱[使用 ICustomFormatter 的自訂格式](#custom-formatting-with-icustomformatter)一節。

下列各節會討論這些將物件轉換為其字串表示的方法。

## <a name="default-formatting-using-the-tostring-method"></a>使用 ToString 方法的預設格式

每個衍生自 [System.Object](xref:System.Object) 的類型都會自動繼承無參數的 [ToString](xref:System.Object.ToString) 方法，這個方法預設會傳回型別的名稱。 下列範例示範預設的 [ToString](xref:System.Object.ToString) 方法。 範例中會定義一個不具任何實作的 `Automobile` 類別。 當具現化這個類別並呼叫其 [ToString](xref:System.Object.ToString) 方法時，會顯示這個類別的類型名稱。 請注意，在範例中不會明確呼叫 [ToString](xref:System.Object.ToString) 方法。 [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) 方法會隱含呼叫本身所收到作為引數傳遞之物件的 [ToString](xref:System.Object.ToString) 方法。 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

因為除介面以外的所有其他類型都會衍生自 [Object](xref:System.Object)，所以您的自訂類別或結構會自動被賦予此功能。 不過，預設的 [ToString](xref:System.Object.ToString) 方法提供的功能有限：它雖然可以識別類型，但無法提供類型執行個體的任何資訊。 若要提供物件的字串表示來表達該物件的相關資訊，您必須覆寫 [ToString](xref:System.Object.ToString) 方法。

> [!NOTE]
> 結構會繼承自 [ValueType](xref:System.ValueType)，而後者又會衍生自 [Object](xref:System.Object)。 雖然 [ValueType](xref:System.ValueType) 會覆寫 [Object.ToString](xref:System.Object.ToString)，但實作方法是相同的。

## <a name="overriding-the-tostring-method"></a>覆寫 ToString 方法

顯示類型的名稱通常用途不大，亦無法讓您類型的使用者藉以區分不同的執行個體。 不過，您可以覆寫 [ToString](xref:System.Object.ToString) 方法，以更實用的方式表示物件的值。 下列範例定義 `Temperature` 物件，並覆寫其 [ToString](xref:System.Object.ToString) 方法來顯示攝氏溫度。

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

在 .NET 中，每個基本實值型別的 [ToString](xref:System.Object.ToString) 方法都已經過覆寫來顯示物件的值，而非物件的名稱。 下表顯示各基本類型如何覆寫 ToString 方法。 請注意，大部分經過覆寫的方法都會呼叫 [ToString](xref:System.Object.ToString) 方法的另一個多載，並且將 "G" 格式規範 (此規範定義此類型的一般格式) 和 [IFormatProvider](xref:System.IFormatProvider) 物件 (此物件表示目前文化特性) 傳遞至這個多載。

類型 | ToString 覆寫
---- | -----------------
[布林值](xref:System.Boolean) | 傳回 [Boolean.TrueString](xref:System.Boolean.TrueString) 或 [Boolean.FalseString](xref:System.Boolean.FalseString)。
[Byte](xref:System.Byte) | 呼叫 `Byte.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Byte](xref:System.Byte) 值。
[Char](xref:System.Char) | 以字串形式傳回字元。
[DateTime](xref:System.DateTime) | 呼叫 `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)`，以根據對目前的文化特性來格式化日期和時間值。 
[Decimal](xref:System.Decimal) | 呼叫 `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Decimal](xref:System.Decimal) 值。
[Double](xref:System.Double) | 呼叫 `Double.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Double](xref:System.Double) 值。
[Int16](xref:System.Int16) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int16](xref:System.Int16) 值。
[Int32](xref:System.Int32) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int32](xref:System.Int32) 值。
[Int64](xref:System.Int64) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Int64](xref:System.Int64) 值。
[SByte](xref:System.SByte) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [SByte](xref:System.SByte) | 值。
[Single](xref:System.Single) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [Single](xref:System.Single) 值。
[UInt32](xref:System.UInt32) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt32](xref:System.UInt32) 值。
[UInt32](xref:System.UInt32) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt32](xref:System.UInt32) 值。
[UInt64](xref:System.UInt64) | 呼叫 `Int16.ToString("G", NumberFormatInfo.CurrentInfo)`，以根據目前的文化特性來格式化 [UInt64](xref:System.UInt64) 值。

## <a name="the-tostring-method-and-format-strings"></a>ToString 方法及格式字串

當物件只有單一字串表示時，使用預設 [ToString](xref:System.Object.ToString) 方法或覆寫 [ToString](xref:System.Object.ToString) 都沒有問題。 不過，物件的值通常有多種表示。 例如，溫度可以用華氏、攝氏或開氏溫度表示。 同樣地，整數值 10 可以用許多方式表示，包括 10、10.0、1.0e01 或 $10.00。

為了讓單一值可以具有多種字串表示，.NET 使用格式字串。 格式字串是包含一個或多個預先定義之格式規範的字串，這個字串是單一字元或字元群組，用於定義 [ToString](xref:System.Object.ToString) 方法應採用的輸出格式。 然後，格式字串會當做參數傳遞至物件的 [ToString](xref:System.Object.ToString) 方法，以決定如何呈現該物件值的字串表示。

.NET 中所有的數值類型、日期和時間類型，以及列舉類型，都支援一組預先定義的格式規範。 您也可以利用格式字串定義多種字串表示給您應用程式中定義的資料類型。

### <a name="standard-format-strings"></a>標準格式字串

標準格式字串包含單一格式規範 (一個字母字元，定義套用此規範之物件的字串表示) 和選擇性的精確度規範 (這個規範影響結果字串中顯示的位數)。 如果省略或不支援精確度規範，則標準格式規範與標準格式字串無異。 

.NET 定義一組適用於所有數值類型、所有日期和時間類型，以及所有列舉類型的標準格式規範。 例如，這些分類每個都支援 "G" 標準格式規範 (這個規範定義該類型之值的一般字串表示)。

列舉類型的標準格式字串直接控制了值的字串表示。 傳遞給列舉值之 [ToString](xref:System.Object.ToString) 方法的格式字串決定了該值是以其字串名稱 ("G" 和 "F" 格式規範)、基礎整數值 ("D" 格式規範)，還是十六進位值 ("X" 格式規範) 來顯示。 下列範例示範如何使用標準格式字串來格式化 [DayOfWeek](xref:System.DayOfWeek) 列舉值。 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

如需列舉格式字串的資訊，請參閱[列舉格式字串](enumeration-format.md)。

數值類型的標準格式字串定義出的結果字串之確切外觀通常是由一個或多個屬性值所控制。 例如，"C" 格式規範會將數字格式化為貨幣值。 當您將 "C" 格式規範作為唯一參數來呼叫 [ToString](xref:System.Object.ToString) 方法時，會使用目前文化特性之 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件中的下列屬性值來定義數值的字串表示：

* [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) 屬性，指定目前文化特性的貨幣符號。

* [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) 或 [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) 屬性，這個屬性傳回的整數會決定： 

    * 貨幣符號的位置。
    
    * 負值是以開頭負號、結尾負號還是括號來表示。
    
    * 數值和貨幣符號之間是否顯示一個空格。
    
* [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) 屬性，定義結果字串中的小數位數。

* [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) 屬性，定義結果字串中的十進位分隔符號。

* [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) 屬性，定義群組分隔符號。

* [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) 屬性，定義小數點左邊每個群組的位數。

* [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) 屬性，決定當不使用括號來表示負值時，要在結果字串中使用的負號。

此外，數值格式字串也可以包含精確度規範。 這個規範的意義視搭配使用的格式字串而定，但通常是表示結果字串中應該顯示的總位數或小數位數。 例如，下列範例會使用 "X4" 標準數值字串和精確度規範，建立具有四個十六進位數字的字串值。

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

如需標準數值格式字串的詳細資訊，請參閱[標準數值格式字串](standard-numeric.md)。 

日期和時間值的標準格式字串是特定 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 類別所儲存之自訂格式字串的別名。 例如，以 "D" 格式規範來呼叫日期和時間值的 [ToString](xref:System.Object.ToString) 方法，將會使用目前文化特性之 [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) 屬性中所儲存的自訂格式字串來顯示日期和時間 (如需自訂格式字串的詳細資訊，請參閱[自訂格式字串](#custom-format-strings)一節)。下列範例示範這種關聯性。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

如需標準日期與時間格式字串的詳細資訊，請參閱[標準日期與時間格式字串](standard-datetime.md)。

對於應用程式定義的物件，您也可以使用標準格式字串來定義由該物件的 `ToString(String)` 方法所產生的字串表示。 您可以定義您的物件所支援的特定標準格式規範，並且決定這項規範是否區分大小寫。 您對 `ToString(String)` 方法的實作應該要能支援：

* "G" 格式規範，表示物件的慣用或通用格式。 您物件的 `ToString` 方法的無參數多載應該要呼叫這個方法的 `ToString(String)` 多載，並且將 "G" 標準格式字串傳遞給這個方法。

* 支援等於 null 參考的格式規範。 等於 null 參考的格式規範應該要視為相當於 "G" 格式規範。

例如，`Temperature` 類別可以在內部以攝氏儲存溫度，並透過格式規範以攝氏、華氏和開氏溫度來表示 `Temperature` 物件的值。 下列範例提供一個實例。

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a>自訂格式字串

除了標準格式字串，.NET 也為數值以及日期和時間值定義了自訂格式字串。 自訂格式字串由一個或多個自訂格式規範組成，這些規範定義了值的字串表示。 例如，自訂日期和時間格式字串 "yyyy/mm/dd hh:mm:ss.ffff t zzz" 會將日期轉換為其字串表示，以 en-US 文化特性而言為 "2008/11/15 07:45:00.0000 P -08:00" 形式。 同樣地，自訂格式字串 "0000" 會將整數值 12 轉換為 "0012"。 如需完整的自訂格式字串清單，請參閱[自訂日期與時間格式字串](custom-datetime.md)及[自訂數值格式字串](custom-numeric.md)。

如果格式字串由單一自訂格式規範組成，則應該在格式規範前面加上百分比 (%) 符號，以避免與標準格式規範產生混淆。 下列範例會使用 "M" 自訂格式規範來顯示特定日期的一位數或兩位數月份。

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

日期和時間值的許多標準格式字串都是自訂格式字串 (這些自訂格式字串由 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件的屬性所定義) 的別名。 自訂格式字串也提供極大的彈性，來提供應用程式定義的數值或日期和時間值格式。 您可以將多個自訂格式規範結合成單一自訂格式字串，以自訂您的數值及日期和時間值結果字串。 下列範例定義的自訂格式字串，會在月份名稱、日期和年後面顯示加上括號的星期。

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

下列範例會定義自訂格式字串，該字串會將 [Int64](xref:System.Int64) 值顯示為標準的七位數美國電話號碼且包含其區碼。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

雖然標準格式字串通常能夠為應用程式定義的類型解決大部分的格式需求，但您也可以定義自訂格式規範來格式化您的類型。 

### <a name="format-strings-and-net-types"></a>格式字串與 .NET 類型

所有數值類型 (也就是 [Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64) 和 [BigInteger](xref:System.Numerics.BigInteger) 類型)，以及 [DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)、[TimeSpan](xref:System.TimeSpan)、[Guid](xref:System.Guid) 和所有列舉類型，都支援以格式字串進行格式化。 如需每個類型所支援特定格式字串的資訊，請參閱下列主題： 

標題 | 定義
----- | ----------
[標準數值格式字串](standard-numeric.md) | 說明建立數值常用之字串表示的標準格式字串。 
[自訂數值格式字串](custom-numeric.md) | 說明建立應用程式專屬數值格式的自訂格式字串。
[標準日期與時間格式字串](standard-datetime.md) | 說明建立 [DateTime](xref:System.DateTime) 值之常用字串表示的標準格式字串。
[自訂日期與時間格式字串](custom-datetime.md) | 說明為 [DateTime](xref:System.DateTime)值建立應用程式專屬格式的自訂格式字串。
[標準 TimeSpan 格式字串](standard-timespan.md) | 說明建立時間間隔之常用字串表示的標準格式字串。
[自訂 TimeSpan 格式字串](custom-timespan.md) | 說明建立應用程式專屬數值格式的自訂格式字串。
[列舉格式字串](enumeration-format.md) | 說明用來建立列舉值之字串表示的標準格式字串。
[Guid.ToString(String)](xref:System.Guid.ToString(System.String)) | 描述 [Guid](xref:System.Guid) 值的標準格式字串。

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>以格式提供者和 IFormatProvider 介面進行符合文化特性的格式化

雖然格式規範可讓您自訂物件的格式，但如果要為物件產生有意義的字串表示，您通常還需要其他格式設定資訊。 例如，如果要使用 "C" 標準格式字串或自訂格式字串 (例如 "$ #,#.00") 將數字格式化為貨幣值，您至少還需要有正確的貨幣符號、群組分隔符號和小數分隔符號的相關資訊。 在 .NET 中，這項額外的格式資訊是透過 [IFormatProvider](xref:System.IFormatProvider) 介面取得，而這個介面會當做傳遞至數值類型以及日期和時間類型的 `ToString` 方法之一個或多個多載的參數來提供。 [IFormatProvider](xref:System.IFormatProvider) 實作會在 .NET 中用來支援文化特性專屬格式。 下列範例示範以代表不同文化特性的三個 [IFormatProvider](xref:System.IFormatProvider) 物件進行格式化時，物件的字串表示會有什麼樣的變化。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

[IFormatProvider](xref:System.IFormatProvider) 介面包含一個 [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)) 方法，這個方法具有單一參數來指定可提供格式設定資訊之物件的類型。 如果這個方法可以提供該類型的物件，則會傳回該物件。 否則會傳回 null 參考。

[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 是一種回呼方法。 當您呼叫包含 [IFormatProvider](xref:System.IFormatProvider) 參數的 `ToString` 方法多載時，這個多載會呼叫該 [IFormatProvider](xref:System.IFormatProvider) 物件的 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法負責將提供必要格式資訊的物件 (由其 *formatType* 參數指定)，傳回給 `ToString` 方法。 

有幾個格式化或字串轉換方法都包含 [IFormatProvider](xref:System.IFormatProvider) 類型的參數，但通常呼叫方法時，會忽略這個參數的值。 下表列出一些使用這個參數的格式化方法，以及這些方法傳遞至 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法之 [Type](xref:System.Type) 物件的類型。 

方法 | *formatType* 參數的類型
------ | ------------------------------
數字類型的 `ToString` 方法 | [System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)
日期和時間類型的 `ToString` 方法 | [System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)
[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)

.NET 提供三個實作 [IFormatProvider](xref:System.IFormatProvider) 的類別： 

* [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)，這個類別提供特定文化特性之日期和時間值的格式資訊。 它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作會傳回本身的執行個體。

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)，這個類別提供特定文化特性的數值格式資訊。 它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作會傳回本身的執行個體。

* [CultureInfo](xref:System.Globalization.CultureInfo)。 它的 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作可以傳回 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來提供數值格式資訊，或傳回 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件來提供日期和時間值的格式資訊。 

您也可以實作自己的格式提供者來取代上述任何一個類別。 不過，您實作的 `GetFormat` 方法如果必須提供格式設定資訊給 `ToString` 方法，則必須傳回上表所列之類型的物件。

### <a name="culture-sensitive-formatting-of-numeric-values"></a>區分文化特性的數值格式

根據預設，數值格式會區分文化特性。 如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。 下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) 方法。 在各案例中，結果字串都會反映目前文化特性的格式設定慣例。 這是因為 `ToString` 和 `ToString(String)` 方法會包裝對每個數值類型之 `ToString(String, IFormatProvider)` 方法的呼叫。 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

您也可以呼叫具有 *provider* 參數的 `ToString` 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的數值： 

* [CultureInfo](xref:System.Globalization.CultureInfo) 物件，表示要使用其格式化慣例的文化特性。 它的 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回 [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) 屬性的值，也就是為數值提供文化特性專屬格式資訊的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件會定義要使用的文化特性專屬格式化慣例。 它的 [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) 方法會傳回本身的執行個體。

下列範例將使用 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件表示用於格式化浮點數的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>區分文化特性的日期與時間值格式

根據預設，日期和時間值的格式區分文化特性。 如果當您呼叫格式化方法時未指定文化特性，則會使用目前執行緒文化特性的格式設定慣例。 下列範例將說明這種情形，其中目前執行緒文化特性會變更四次，然後呼叫 [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) 方法。 在各案例中，結果字串都會反映目前文化特性的格式設定慣例。 這是因為 [DateTime.ToString()](xref:System.DateTime.ToString)、[DateTime.ToString(String)](xref:System.DateTime.ToString(System.String))、[DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) 和 [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) 方法會包裝 [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 和 [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) 方法的呼叫。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

您也可以呼叫具有 provider 參數的 [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 或 [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) 多載並且將下列任一項傳遞給它，藉此格式化特定文化特性的日期和時間值： 

* [CultureInfo](xref:System.Globalization.CultureInfo) 物件，表示要使用其格式化慣例的文化特性。 它的 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回 [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) 屬性的值，也就是為數值提供文化特性專屬格式資訊的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。

* [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，該物件會定義要使用的文化特性專屬格式化慣例。 它的 [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) 方法會傳回本身的執行個體。

下列範例將使用 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件，該物件表示用於格式化日期的英文 (美國) 和英文 (英國) 文化特性，以及法文和俄文中性文化特性。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a>IFormattable 介面

以格式字串和 [IFormatProvider](xref:System.IFormatProvider) 參數來多載 `ToString` 方法的類型，通常也會實作 [IFormattable](xref:System.IFormattable) 介面。 這個介面具有單一成員 [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider))，這個成員同時包含格式字串和格式提供者作為參數。

針對您的應用程式定義類別來實作 [IFormattable](xref:System.IFormattable) 介面有兩項好處： 

* 支援透過 [Convert](xref:System.Convert) 類別來轉換字串。 呼叫 [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) 和 [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) 方法時，會自動呼叫您的 [IFormattable](xref:System.IFormattable) 實作。

* 支援複合格式。 如果使用包含格式字串的格式項目來格式化您的自訂類型，則 Common Language Runtime 會自動呼叫您的 [IFormattable](xref:System.IFormattable) 實作並將格式字串傳遞給這個實作。 如需各種方法之複合格式 (例如 `String.Format` 或 `Console.WriteLine`) 的詳細資訊，請參閱[複合格式](#composite-formatting)一節。

下列範例定義一個實作 [IFormattable](xref:System.IFormattable) 介面的 `Temperature` 類別。 這個類別支援 "C" 或 "G" 格式規範來顯示攝氏溫度、支援 "F" 格式規範來顯示華氏溫度，也支援 "K" 格式規範來顯示絕對溫度。

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

下列範例會執行個體化 `Temperature` 物件。 然後呼叫 [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) 方法，並使用數個複合格式字串來取得 `Temperature` 物件的不同字串表示。 其中每個方法又呼叫 `Temperature` 類別的 [IFormattable](xref:System.IFormattable) 實作。

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a>複合格式

某些方法 (例如 `String.Format` 和 `StringBuilder.AppendFormat`) 支援複合格式。 複合格式字串是一種範本，可傳回由零個、一個或更多物件的字串表示所組成的單一字串。 複合格式字串中的每個物件都以有索引的格式項目來表示。 格式項目的索引對應至其所表示的物件在方法的參數清單中的位置。 索引以零為起始。 例如，在下列對 `String.Format` 方法的呼叫中，第一個格式項目 `{0:D}` 由 `thatDate` 的字串表示所取代、第二個格式項目 `{1}` 由 `item1` 的字串表示所取代，而第三個格式項目 `{2:C2}` 由 `item1.Value` 的字串表示所取代。

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

除了取代具有對應物件字串表示格式的項目，格式項目也可讓您控制下列幾項： 

* 當物件實作 [IFormattable](xref:System.IFormattable) 介面，並支援格式字串時，物件表示為字串的特定方式。 您可將格式項目索引後面接上 : (冒號) ，後面再接有效的格式字串，以執行此作業。 前一個範例採用的方法是用 "d" (簡短日期模式) 格式字串來格式化日期值 (例如 `{0:d}`) 以及用 "C2" 格式字串 (例如 `{2:C2}`) 來格式化數值，以表示具有兩個小數位數的十進位數字之貨幣值。 

* 包含物件字串表示法及在該欄位中對齊方式的字串表示法之欄位寬度。 您可將格式項目索引後面接上 , (逗號) ，後面再接欄位寬度，以執行此作業。 如果欄位寬度是正值，則此欄位中的字串為靠右對齊；如果欄位寬度是負值，則為靠左對齊。 下列範例在長 20 個字元的欄位中將日期值靠左對齊，並在長 11 個字元的欄位中將具有一位小數位數的十進位值靠右對齊。 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

請注意如果對齊字串元件和格式字串元件都存在，則前者優先於後者 (例如，`{0,-20:g}`)。 

如需複合格式的詳細資訊，請參閱[複合格式](composite-format.md)。

## <a name="custom-formatting-with-icustomformatter"></a>使用 ICustomFormatter 的自訂格式

[String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) 和 [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 這兩個複合格式化方法包含支援自訂格式的格式提供者參數。 呼叫這兩種格式化方法的任一種時，會將表示 [ICustomFormatter](xref:System.ICustomFormatter) 介面的 [Type](xref:System.Type) 物件傳遞至格式提供者的 `GetFormat` 方法。 然後，`GetFormat` 方法負責傳回 [ICustomFormatter](xref:System.ICustomFormatter) 實作，這個實作提供自訂格式。

[ICustomFormatter](xref:System.ICustomFormatter) 介面具有單一方法 [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider))，複合格式化方法會自動針對複合格式字串中的每個格式項目，各呼叫一次這個方法。 [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法具有三個參數：格式字串 (表示格式項目中的 *formatString* 引數)、要格式化的物件，以及提供格式化服務的 [IFormatProvider](xref:System.IFormatProvider) 物件。 實作 [ICustomFormatter](xref:System.ICustomFormatter) 的類別通常也會實作 [IFormatProvider](xref:System.IFormatProvider)，所以這最後一個參數是對自訂格式類別的參考。 方法會傳回要格式化之物件的自訂格式化字串表示。 如果方法無法格式化物件，則應該傳回 null 參考。

下列範例提供一個名為 `ByteByByteFormatter` 的 [ICustomFormatter](xref:System.ICustomFormatter) 實作，這個實作會將整數值顯示為一連串由兩位數十六進位值再加上一個空格所組成的數列。

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

下列範例會使用 `ByteByByteFormatter` 類別來格式化整數值。 請注意，[ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法在第二個 [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法呼叫中被呼叫不只一次，且第三個方法呼叫中使用預設 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 提供者，因為 `.ByteByByteFormatter.Format` 方法無法辨認 "N0" 格式字串而傳回 null 參考。

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a>相關主題

標題 | 定義
----- | ----------
[標準數值格式字串](standard-numeric.md) | 說明建立數值常用之字串表示的標準格式字串。 
[自訂數值格式字串](custom-numeric.md) | 說明建立應用程式專屬數值格式的自訂格式字串。
[標準日期與時間格式字串](standard-datetime.md) |  說明建立 [DateTime](xref:System.DateTime) 值之常用字串表示的標準格式字串。
[自訂日期與時間格式字串](custom-datetime.md) | 說明為 [DateTime](xref:System.DateTime)值建立應用程式專屬格式的自訂格式字串。
[標準 TimeSpan 格式字串](standard-timespan.md) | 說明建立時間間隔之常用字串表示的標準格式字串。
[自訂 TimeSpan 格式字串](custom-timespan.md) | 說明建立應用程式專屬數值格式的自訂格式字串。
[列舉格式字串](enumeration-format.md) | 說明用來建立列舉值之字串表示的標準格式字串。
[複合格式](composite-format.md) | 描述如何將一個或更多的格式化值嵌入字串。 字串可以隨後顯示在主控台 (Console) 或寫入資料流。
[執行格式化作業](performing-formatting-operations.md) | 列出各主題，提供執行特定格式設定作業的逐步指示。
[剖析字串](parsing-strings.md) | 說明如何將物件初始化為這些物件的字串表示所描述的值。 剖析是格式化的反向作業。

## <a name="reference"></a>參考資料

[System.IFormattable](xref:System.IFormattable)

[System.IFormatProvider](xref:System.IFormatProvider)

[System.ICustomFormatter](xref:System.ICustomFormatter)

