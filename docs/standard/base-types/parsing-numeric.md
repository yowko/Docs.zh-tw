---
title: "在 .NET 中剖析數值字串"
description: "在 .NET 中剖析數值字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 209d24d32eb3b235ff2fde2ef11ffd0ee4e930cf

---

# <a name="parsing-numeric-strings-in-net"></a>在 .NET 中剖析數值字串

所有數值類型皆有兩個靜態剖析方法：`Parse` 和 `TryParse`，可將數字的字串表示轉換成數值類型。 這些方法可讓您剖析使用[標準數值格式字串](standard-numeric.md)和[自訂數值格式字串](custom-numeric.md)中記錄的格式字串所產生的字串。 根據預設，`Parse` 和 `TryParse` 方法只能將包含十進位數字的字串成功轉換為整數值。 它們可以將包含整數和小數的十進位數字、群組分隔符號，以及小數分隔符號的字串，成功轉換為浮點值。 如果作業失敗，即 `TryParse` 方法傳回 `false`，則 `Parse` 方法會擲回例外狀況。

## <a name="parsing-and-format-providers"></a>剖析及格式提供者

數值的字串表示通常會隨文化特性而不同。 數值字串的元素都會因文化特性而有所不同，包括貨幣符號、群組 (或千分位) 分隔符號以及小數分隔符號。 剖析方法會隱含或明確使用能夠辨識這些特定文化特性變化的格式提供者。 如果在 `Parse` 或 `TryParse` 方法的叫中不指定格式提供者，則會使用與目前執行緒文化特性相關聯的格式提供者 ([NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 屬性所傳回的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件)。 

格式提供者是由 [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 實作代表。 此介面有單一成員 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法，其單一參數是表示要格式化類型的 [Type](xref:System.Type) 物件。 此方法會傳回提供格式設定資訊的物件。 .NET 支援下列兩個剖析數值字串的 [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 實作︰

* [CultureInfo](xref:System.Globalization.CultureInfo) 物件，其 [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) 方法會傳回提供特定文化特性格式資訊的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，其 [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) 方法會傳回自己本身。

下例嘗試將陣列中的每個字串轉換成 [Double](xref:System.Double) 值。 它會先嘗試使用反映英文 (美國) 文化特性慣例的格式提供者剖析字串。 如果此作業擲回 [FormatException](xref:System.FormatException)，它會嘗試使用來映法文 (法國) 文化特性慣例的格式提供者剖析字串。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a>剖析及 NumberStyles 值

剖析作業可以處理的樣式項目 (例如空白字元、群組分隔符號和小數分隔符號)，是由 [NumberStyles](xref:System.Globalization.NumberStyles) 列舉值所定義。 根據預設，代表整數值的字串是使用 [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) 值剖析，這僅允許數字、前置和後置空白字元和前置正負號。 表示浮點值的字串是使用 [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) 和 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 的組合值剖析，此複合樣式允許十進位數字及前置和後置空白字元、前置正負號、小數分隔符號、群組分隔符號和指數。 藉由呼叫包含 [NumberStyles](xref:System.Globalization.NumberStyles) 類型參數的 `Parse` 或 `TryParse` 方法的多載，及設定一或多個 [NumberStyles](xref:System.Globalization.NumberStyles) 旗標，您可以控制字串得以顯示的樣式項目，成功進行利剖析作業。 

例如，使用 [Int32.Parse(String)](xref:System.Int32.Parse(System.String)) 方法無法將包含群組分隔符號的字串轉換為 [Int32](xref:System.Int32) 值。 但若使用 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 旗標，則轉換會成功，如下列範例所示。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> **警告**
>
> 剖析作業一律使用特定文化特性的格式化慣例。 如果不藉由傳遞 [CultureInfo](xref:System.Globalization.CultureInfo) 或 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來指定文化特性，就會使用與目前執行緒相關聯的文化特性。
 
下表列出 [NumberStyles](xref:System.Globalization.NumberStyles) 列舉的成員，並說明它們對剖析作業的影響。

NumberStyles 值 | 對要剖析字串的影響
------------------ | --------------------------------- 
[NumberStyles.None](xref:System.Globalization.NumberStyles.None) | 只允許數字。
[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | 允許小數分隔符號和小數位。 若為整數值，小數位只允許零。 有效的十進位分隔符號由 [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) 或 [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) 屬性決定。
[NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) | 可以使用 "e" 或 "E" 字元表示指數標記法。
[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | 可以使用前置空白字元。
[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | 可以使用後置空白字元。
[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) | 數字前面可以使用正負號。
[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign) | 數字後面可以使用正負號。
[NumberStyles.AllowParentheses](xref:System.Globalization.NumberStyles.AllowParentheses) | 可以使用括號表示負數值。
[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) | 允許群組分隔符號。 群組分隔符號字元由 [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) 或 [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) 屬性決定。
[NumberStyles.AllowCurrencySymbol](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | 允許使用貨幣符號。 根據貨幣符號是由 [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) 屬性定義。
[NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | 要剖析的字串會解譯為十六進位數字。 它可以包含十六進位數字 0-9、A-F 和 a-f。 這個旗標只能用於剖析整數值。
 
此外，[NumberStyles](xref:System.Globalization.NumberStyles) 列舉提供下列複合樣式，包括多個 [NumberStyles](xref:System.Globalization.NumberStyles) 旗標。 

複合的 NumberStyles 值 | 包含成員
---------------------------- | ---------------- 
[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) | 包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) 和 [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) 樣式。 這是用來剖析整數值的預設樣式。
[NumberStyles.Number](xref:System.Globalization.NumberStyles.Number) | 包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) 和 [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 樣式。
[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) | 包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) 和 [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) 樣式。
[NumberStyles.Currency](xref:System.Globalization.NumberStyles.Currency) | 包含所有樣式，但 [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) 和 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 除外。
[NumberStyles.Any](xref:System.Globalization.NumberStyles.Any) | 包含所有樣式，但 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 除外。
[NumberStyles.HexNumber](xref:System.Globalization.NumberStyles.HexNumber) | 包含 [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) 和 [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) 樣式。
 
## <a name="parsing-and-unicode-digits"></a>剖析及 Unicode 數字

Unicode 標準會定義各種書寫系統中數字的字碼指標。 例如，U+0030 到 U+0039 的字碼指標表示基本拉丁文數字 0 到 9，U+09E6 到 U+09EF 字碼指標表示孟加拉文數字 0 到 9，而 U+FF10 到 U+FF19 字碼指數表示全形數字 0 到 9。 不過，剖析方法唯一認識的數字是基本拉丁文數字 0-9 與 U+0030 到 U+0039 字碼指標。 如果數值剖析方法傳遞的字串包含任何其他數字，則方法會擲回 [FormatException](xref:System.FormatException)。

下例使用 [Int32.Parse](xref:System.Int32.Parse(System.String)) 方法剖析以不同書寫系統數字組成的字串。 如範例的輸出所示，嘗試剖析基本拉丁文數字會成功，而嘗試剖析全型、阿拉伯-印度文和孟加拉文數字則會失敗。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a>請參閱

[System.Globalization.NumberStyles](xref:System.Globalization.NumberStyles)

[在 .NET 中剖析字串](parsing-strings.md)

[在 .NET 中格式化類型](formatting-types.md)




<!--HONumber=Nov16_HO3-->


