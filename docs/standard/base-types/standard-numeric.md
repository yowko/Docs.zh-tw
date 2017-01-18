---
title: "標準數值格式字串"
description: "標準數值格式字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 285faf73-466a-4af0-8eba-7e509958f240
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4887a55690e47f7867cee28ab9b9fe258b208e54

---

# <a name="standard-numeric-format-strings"></a>標準數值格式字串

標準數值格式字串會用來格式化一般數字類型。 標準數值格式字串會採用 **A**_xx_ 格式，其中： 

* **A** 是稱為「格式規範」的單一字母字元。 任何包含一個以上字母字元 (包含泛空白字元 (White Space)) 的數值格式字串都會解譯為自訂數值格式字串。 如需詳細資訊，請參閱[自訂數值格式字串](custom-numeric.md)。 

* *xx* 是稱為「有效位數規範」的選用性整數。 精確度規範的範圍從 0 到 99，而且會影響結果內的位數。 請注意，精確度規範可控制數字字串表示法中的位數。 它不會捨入數字本身。 若要執行四捨五入運算，請使用 [Math.Ceiling](xref:System.Math)、[Math.Floor](xref:System.Math) 或 [Math.Round](xref:System.Math) 方法。 

當「有效位數規範」控制結果字串中小數點後數字的位數時，結果字串會反映遠離零四捨五入的數字 (亦即，使用 [MidpointRounding.AwayFromZero](xref:System.MidpointRounding.AwayFromZero))。 

> [!NOTE]
> 有效位數規範可判斷結果字串中的位數。 若要使用前置或尾端空格填補結果字串，請使用[複合格式設定](composite-format.md)功能，並在格式項目中定義「對齊元件」。 

所有數字類型的 `ToString` 方法的一些多載可支援標準數值格式字串。 例如，您可以提供數值格式字串給 [Int32](xref:System.Int32) 類型的 [ToString(String)](xref:System.Int32.ToString(System.String)) 和 [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) 方法。 .NET 的[複合格式設定](composite-format.md)功能也支援標準數值格式字串，此功能是由 [Console](xref:System.Console) 與 [StreamWriter](xref:System.IO.StreamWriter) 類別的一些 `Write` 和 `WriteLine` 方法、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法和 [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 方法所使用。 複合格式功能可讓您將多個資料項目的字串表示法包含在單一字串中，以指定欄位寬度，以及對齊欄位中的數字。 如需詳細資訊，請參閱[複合格式設定](composite-format.md)。 

下表描述標準數值格式規範，並顯示每個格式範例所產生的範例輸出。 如需使用標準數值格式字串的詳細資訊，請參閱[備註](#notes)一節，如需其用法的完整解說，請參閱[範例](#example)一節。

|格式規範|名稱|描述|範例|  
|----------------------|----------|-----------------|--------------|  
|"C" 或 "c"|貨幣|結果：貨幣值。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 有效位數規範：小數位數的數目。<br /><br /> 預設有效位數規範：由 [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) 定義。<br /><br /> |123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|"D" 或 "d"|Decimal|結果：帶選擇性負號的整數位數。<br /><br /> 支援的類型：只有整數類型。<br /><br /> 精確度規範：最少位數。<br /><br /> 預設精確度規範：必要的最少位數。<br /><br /> |1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|"E" 或 "e"|指數 (科學記號)|結果：指數標記法。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 有效位數規範：小數位數的數目。<br /><br /> 預設精確度規範：6。<br /><br /> |1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1,05E+003|  
|"F" 或 "f"|固定點|結果：帶選擇性負號的整數和小數位數。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 有效位數規範：小數位數的數目。<br /><br /> 預設有效位數規範：由 [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) 定義。<br /><br /> |1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|  
|"G" 或 "g"|一般|結果：固定點和科學標記法兩者中更精簡的一個。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 精確度規範：有效位數。<br /><br /> 預設精確度規範：因數字類型而異。<br /><br /> |-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|"N" 或 "n"|數字|結果：帶選擇性負號的整數和小數位數、群組分隔符號，以及小數分隔符號。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 精確度規範：想要的小數位數。<br /><br /> 預設有效位數規範：由 [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) 定義。<br /><br /> |1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|  
|"P" 或 "p"|百分比|結果：乘以 100 並加上百分比符號來顯示的數字。<br /><br /> 支援的類型：所有數字類型。<br /><br /> 精確度規範：想要的小數位數。<br /><br /> 預設有效位數規範：由 [NumberFormatInfo.PercentDecimalDigits](assetId:///P:System.Globalization.NumberFormatInfo.PercentDecimalDigits?qualifyHint=True&autoUpgrade=True) 定義。<br /><br /> |1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|  
|"R" 或 "r"|來回|結果：可以來回轉換為相同數字的字串。<br /><br /> 支援的類型：[Single](xref:System.Single)、[Double](xref:System.Double) 和 [BigInteger](xref:System.Numerics.BigInteger)。<br /><br /> 精確度規範：忽略。<br /><br /> |123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|"X" 或 "x"|十六進位|結果：十六進位字串。<br /><br /> 支援的類型：只有整數類型。<br /><br /> 精確度規範：結果字串中的位數。<br /><br /> |255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|任何其他單一字元|未知的規範|結果：在執行階段擲回 [FormatException](xref:System.FormatException)。|| 

## <a name="using-standard-numeric-format-strings"></a>使用標準數值格式字串

使用標準數值格式字串來定義數值的格式有兩種方式：

* 您可以將它傳遞至具有 *format* 參數之 `ToString` 方法的多載。 下列範例會以目前 (在此範例中是 en-US) 文化特性將數值格式化為貨幣字串。 

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine(value.ToString("C2"));
  // Displays $123.46
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine(value.ToString("C2"))         
  ' Displays $123.46
  ```
  
* 您可以在搭配 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))、[Console.WriteLine](xref:System.Console.WriteLine) 和 [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 等方法一起使用的格式項目中，將它做為 *formatString* 引數提供。 如需詳細資訊，請參閱[複合格式設定](composite-format.md)。 下列範例會使用格式項目，在字串中插入貨幣值。

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine("Your account balance is {0:C2}.", value);
  // Displays "Your account balance is $123.46."
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine("Your account balance is {0:C2}.", value)
  ' Displays "Your account balance is $123.46."
  ```
  
  您可以選擇性地提供對齊引數，來指定數值欄位的寬度，以及其值為靠右或靠左對齊。 下列範例在 28 個字元的欄位中將貨幣值靠左對齊，並在 14 個字元的欄位中將貨幣值靠右對齊。
  
  ```csharp
  decimal[] amounts = { 16305.32m, 18794.16m };
  Console.WriteLine("   Beginning Balance           Ending Balance");
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts[0], amounts[1]);
  // Displays:
  //        Beginning Balance           Ending Balance
  //        $16,305.32                      $18,794.16
  ```

  ```vb
  Dim amounts() As Decimal = { 16305.32d, 18794.16d }
  Console.WriteLine("   Beginning Balance           Ending Balance")
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts(0), amounts(1))
  ' Displays:
  '        Beginning Balance           Ending Balance
  '        $16,305.32                      $18,794.16
  ```
  
下列各節提供每個標準數值格式字串的詳細資訊。

## <a name="the-currency-c-format-specifier"></a>貨幣 ("C") 格式規範

"C" (表示貨幣) 格式規範會將數字轉換為表示貨幣金額的字串。 精確度規範表示在結果字串中所需要的小數位數。 如果省略有效位數規範，則預設有效位數會由 [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) 屬性定義。

如果要格式化的值擁有的小數位數超過指定或預設的小數位數，則分數值會在結果字串中四捨五入。 如果指定的小數位數右邊的值為 5 或更大值，則結果字串中的最後一位數會遠離零四捨五入。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) | 定義正值的貨幣符號位置。
[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) | 定義負值的貨幣符號位置，並指定負號是以括號還是 [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) 屬性來表示。
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義在 [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) 表示不使用括號時所使用的負號。 
[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) | 定義貨幣符號。
[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) | 定義貨幣值中的預設小數位數。 您可以使用有效位數規範來覆寫這個值。
[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) | 定義分隔整數與小數位數的字串。
[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) | 定義分隔整數群組的字串。 
[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) | 定義整數部分的每個群組中出現的整數位數。

下列範例會使用貨幣格式規範格式化 [Double](xref:System.Double) 值。 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", 
                  CultureInfo.CreateSpecificCulture("da-DK")));
// The example displays the following output on a system whose
// current culture is English (United States):
//       $12,345.68
//       $12,345.679
//       kr 12.345,679
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", _
                  CultureInfo.CreateSpecificCulture("da-DK")))
' The example displays the following output on a system whose
' current culture is English (United States):
'       $12,345.68
'       $12,345.679
'       kr 12.345,679
```

## <a name="the-decimal-d-format-specifier"></a>十進位 ("D") 格式規範

"D" (表示十進位) 格式規範會將數字轉換為十進位數 (0-9) 的字串，如果數字為負數，則在前面加上負號。 只有整數類資料類型 (Integral Type) 才支援這個格式。

精確度規範指示產生的字串中所需要的最少位數。 如果有必要，數值以零填補其左邊，產生精確度規範所指定的位數。 如果未指定精確度規範，則預設值為在不填補前置零的情況下，表示整數所需的最小值。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 如下表所示，只有一個屬性會影響結果字串的格式設定。 

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。 

下列範例會使用十進位格式規範來格式化 [Int32](xref:System.Int32) 值。

```csharp
int value; 

value = 12345;
Console.WriteLine(value.ToString("D"));
// Displays 12345
Console.WriteLine(value.ToString("D8"));
// Displays 00012345

value = -12345;
Console.WriteLine(value.ToString("D"));
// Displays -12345
Console.WriteLine(value.ToString("D8"));
// Displays -00012345
```

```vb
Dim value As Integer 

value = 12345
Console.WriteLine(value.ToString("D"))
' Displays 12345   
Console.WriteLine(value.ToString("D8"))
' Displays 00012345

value = -12345
Console.WriteLine(value.ToString("D"))
' Displays -12345
Console.WriteLine(value.ToString("D8"))
' Displays -00012345
```

## <a name="the-exponential-e-format-specifier"></a>指數 ("E") 格式規範

指數 ("E") 格式規範會將數字轉換為 "-d.ddd…E+ddd" 或 "-d.ddd…e+ddd" 形式的字串，其中 "d" 表示數字 (0-9)。 字串以負號開始，如果數值為負數的話。 在小數點前面永遠會有確切一個位數。 

精確度規範指示小數點之後需要的位數。 如果省略精確度規範，則使用小數點之後有六位數的預設值。 

格式規範的大小寫表示要在指數之前加上 "E" 還是 "e"。 指數永遠由正號或負號和最少三位數所組成。 必要時，指數將以零填補來符合指定的最少位數。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制傳回字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字在係數和指數部分都是負數的字串。 
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 定義將係數中的整數位數與小數位數分隔的字串。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 定義表示指數為正數的字串。

下列範例會使用指數格式規範來格式化 [Double](xref:System.Double) 值。 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture));
// Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture));
// Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture));
// Displays 1.2346e+004

Console.WriteLine(value.ToString("E", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 1,234568E+004
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture))
' Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture))
' Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture))
' Displays 1.2346e+004

Console.WriteLine(value.ToString("E", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 1,234568E+004
```

## <a name="the-fixedpoint-f-format-specifier"></a>固定點 ("F") 格式規範

固定點 ("F") 格式規範會將數字轉換為 "-ddd.ddd…" 形式的字串， 其中 "d" 表示數字 (0-9)。 字串以負號開始，如果數值為負數的話。 

精確度規範指示所需要的小數位數。 如果省略有效位數規範，則會由目前 [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) 屬性提供數值有效位數。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的屬性，這些屬性控制結果字串的格式設定。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 定義分隔整數位數與小數位數的字串。
[NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | 定義小數位數的預設數目。 您可以使用有效位數規範來覆寫這個值。

下列範例會使用固定點格式規範格式化 [Double](xref:System.Double) 和 [Int32](xref:System.Int32) 值。

```csharp
int integerNumber;
integerNumber = 17843;
Console.WriteLine(integerNumber.ToString("F", 
                  CultureInfo.InvariantCulture));
// Displays 17843.00

integerNumber = -29541;
Console.WriteLine(integerNumber.ToString("F3", 
                  CultureInfo.InvariantCulture));
// Displays -29541.000

double doubleNumber;
doubleNumber = 18934.1879;
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture));
// Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture));
// Displays 18934

doubleNumber = -1898300.1987;
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture));  
// Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays -1898300,199 
```

```vb
Dim integerNumber As Integer
integerNumber = 17843
Console.WriteLine(integerNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 17843.00

integerNumber = -29541
Console.WriteLine(integerNumber.ToString("F3", CultureInfo.InvariantCulture))
' Displays -29541.000

Dim doubleNumber As Double
doubleNumber = 18934.1879
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture))
' Displays 18934

doubleNumber = -1898300.1987
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture))  
' Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", _ 
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays -1898300,199                        
```

## <a name="the-general-g-format-specifier"></a>一般 ("G") 格式規範

一般 ("G") 格式規範會將數字轉換為固定點和科學標記法兩者中較精簡的一個，視數字的類型以及精確度規範是否存在而定。 精確度規範定義結果字串中最多可顯示的有效位數。 如果精確度規範已省略或為零，則由數字的類型決定預設有效位數，如下表所示。 

數字類型 | 預設有效位數
------------ | -----------------
[Byte](xref:System.Byte) 或 [SByte](xref:System.SByte) | 3 位數
[Int16](xref:System.Int16) 或 [UInt16](xref:System.UInt16) | 5 位數
[Int32](xref:System.Int32) 或 [UInt32](xref:System.UInt32) | 10 位數
[Int64](xref:System.Int64) | 19 位數
[UInt64](xref:System.UInt64) | 20 位數
[BigInteger](xref:System.Numerics.BigInteger) | 無限制 (如同 "R")
[Single](xref:System.Single) | 7 位數
[Double](xref:System.Double) | 15 位數
[Decimal](xref:System.Decimal) | 29 位數

如果以科學標記法來表示數字所產生的指數大於 -5 而且小於精確度規範，則會使用固定點標記法，否則使用科學標記法。 必要時，結果會包含小數點並省略小數點後最後幾個零。 如果精確度規範存在，且結果中的有效位數超過指定的有效位數，則會四捨五入來移除超出的尾端位數。 

不過，如果數字是 [Decimal](xref:System.Decimal)，而且省略有效位數規範，則一律會使用固定點標記法，並且保留尾端的零。

使用科學標記法時，結果中的指數前面會加上 "E" (如果格式規範為 "G") 或 "e" (如果格式規範為 "g")。 指數至少包含兩位數。 這不同於指數格式規範所產生的科學標記法格式，此格式會在指數中包含至少三位數。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 定義分隔整數位數與小數位數的字串。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 定義表示指數為正數的字串。 

下列範例會使用一般格式規範來格式化各種浮點數值。

```csharp
double number;

number = 12345.6789;      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays  12345.6789
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture));
// Displays 12345.68 

number = .0000023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 2.3E-06       
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 2,3E-06

number = .0023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 0.0023

number = 1234;
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture));
// Displays 1.2E+03

number = Math.PI;
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture));
// Displays 3.1416    
```

```vb
Dim number As Double

number = 12345.6789      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays  12345.6789
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture))
' Displays 12345.68 

number = .0000023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 2.3E-06       
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 2,3E-06

number = .0023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 0.0023

number = 1234
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture))
' Displays 1.2E+03

number = Math.Pi
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture))
' Displays 3.1416
```

## <a name="the-numeric-n-format-specifier"></a>數值 ("N") 格式規範

數字 ("N") 格式規範會將數字轉換為 "-d,ddd,ddd.ddd…" 形式的字串，其中 "-" 表示負數符號 (如有需要)、"d" 表示數字 (0-9)、"," 表示群組分隔符號，而 "." 表示小數點符號。 精確度規範指示小數點之後需要的位數。 如果省略有效位數規範，則小數位數會由目前的 [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) 屬性定義。

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。
[NumberNegativePattern](xref:System.Globalization.NumberFormatInfo.NumberNegativePattern) | 定義負值的格式，並指定負號是以括號還是 [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) 屬性來表示。
[NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) | 定義在群組分隔符號之間出現的整數位數。
[NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) | 定義分隔整數群組的字串。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 定義分隔整數位數與小數位數的字串。
[NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | 定義小數位數的預設數目。 您可以使用精確度規範來覆寫這個值。

下列範例會使用數字格式規範來格式化各種浮點數值。

```csharp
double dblValue = -12445.6789;
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture));
// Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", 
                  CultureInfo.CreateSpecificCulture("sv-SE")));
// Displays -12 445,7

int intValue = 123456789;
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture));
// Displays 123,456,789.0 
```

```vb
Dim dblValue As Double = -12445.6789
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture))
' Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", _
                  CultureInfo.CreateSpecificCulture("sv-SE")))
' Displays -12 445,7

Dim intValue As Integer = 123456789
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture))
' Displays 123,456,789.0 
```

## <a name="the-percent-p-format-specifier"></a>百分比 ("P") 格式規範

百分比 ("P") 格式規範會將數字乘以 100，然後轉換為表示百分比的字串。 精確度規範指示所需要的小數位數。 如果省略有效位數規範，則會使用目前 [PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) 屬性所提供的預設數值有效位數。

下表列出可控制傳回字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

umberFormatInfo 屬性 | 說明
------------------------- | -----------
[PercentPositivePattern](xref:System.Globalization.NumberFormatInfo.PercentPositivePattern) | 定義正值的百分比符號位置。
[PercentNegativePattern](xref:System.Globalization.NumberFormatInfo.PercentNegativePattern) | 
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。
[PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) | 定義百分比符號。
[PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) | 定義百分比值中的預設小數位數。 您可以使用有效位數規範來覆寫這個值。
[PercentDecimalSeparator](xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator) | 定義分隔整數與小數位數的字串。
[PercentGroupSeparator](xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator) | 定義分隔整數群組的字串。 
[PercentGroupSizes](xref:System.Globalization.NumberFormatInfo.PercentGroupSizes) | 定義整數部分的每個群組中出現的整數位數。

下列範例會使用百分比格式規範來格式化浮點數值。

```csharp
double number = .2468013;
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture));
// Displays 24.68 %
Console.WriteLine(number.ToString("P", 
                  CultureInfo.CreateSpecificCulture("hr-HR")));
// Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture));
// Displays 24.7 %
```

```vb
Dim number As Double = .2468013
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture))
' Displays 24.68 %
Console.WriteLine(number.ToString("P", _
                  CultureInfo.CreateSpecificCulture("hr-HR")))
' Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture))
' Displays 24.7 %
```

## <a name="the-roundtrip-r-format-specifier"></a>來回行程 ("R") 格式規範

來回行程 ("R) 格式規範用來確保轉換為字串的數值可以剖析回到相同數值。 只有 [Single](xref:System.Single)、[Double](xref:System.Double) 和 [BigInteger](xref:System.Numerics.BigInteger) 類型才支援這個格式。 

使用這個規範來格式化 [BigInteger](xref:System.Numerics.BigInteger) 值時，這個值的字串表示會包含 [BigInteger](xref:System.Numerics.BigInteger) 值中的所有有效位數。 使用這個規範來格式化 [Single](xref:System.Single) 或 [Double](xref:System.Double) 值時，則會先使用一般格式來測試該值 (對 [Double](xref:System.Double) 會使用 15 位數，而對 [Single](xref:System.Single) 會使用 7 位數)。 如果該值成功地剖析回到相同數值，即會使用一般格式規範來格式化。 如果該值無法成功地剖析回到相同數值，即會使用 17 位數 (如果是 [Double](xref:System.Double)) 或 9 位數 (如果是 [Single](xref:System.Single)) 來格式化該值。 

雖然您可以包含精確度規範，但該規範會被忽略。 使用來回規範時，這個規範優先於精確度規範。 

結果字串會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 下表列出可控制結果字串之格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 屬性。

NumberFormatInfo 屬性 | 說明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 定義表示數字為負數的字串。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 定義分隔整數位數與小數位數的字串。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 定義表示指數為正數的字串。

 下列範例會使用來回行程格式規範格式化 [Double](xref:System.Double) 值。

```csharp
double value;

value = Math.PI;
Console.WriteLine(value.ToString("r"));
// Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 3,1415926535897931
value = 1.623e-21;
Console.WriteLine(value.ToString("r"));
// Displays 1.623E-21
```

```vb
Dim value As Double

value = Math.Pi
Console.WriteLine(value.ToString("r"))
' Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 3,1415926535897931
value = 1.623e-21
Console.WriteLine(value.ToString("r"))
' Displays 1.623E-21
```

## <a name="the-hexadecimal-x-format-specifier"></a>十六進位 ("X") 格式規範

十六進位 ("X") 格式規範會將數字轉換為十六進位數字的字串。 格式規範的大小寫表示對於大於 9 的十六進位數字，要使用大寫還是小寫字元。 例如，使用 "X" 會產生 "ABCDEF"，使用 "x" 則會產生 "abcdef"。 只有整數類資料類型 (Integral Type) 才支援這個格式。

精確度規範指示產生的字串中所需要的最少位數。 如果有必要，數值以零填補其左邊，產生精確度規範所指定的位數。

結果字串不會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的格式設定資訊所影響。 

下列範例會使用十六進位格式規範格式化 [Int32](xref:System.Int32) 值。

```csharp
int value; 

value = 0x2045e;
Console.WriteLine(value.ToString("x"));
// Displays 2045e
Console.WriteLine(value.ToString("X"));
// Displays 2045E
Console.WriteLine(value.ToString("X8"));
// Displays 0002045E

value = 123456789;
Console.WriteLine(value.ToString("X"));
// Displays 75BCD15
Console.WriteLine(value.ToString("X2"));
// Displays 75BCD15
```

```vb
Dim value As Integer 

value = &h2045e
Console.WriteLine(value.ToString("x"))
' Displays 2045e
Console.WriteLine(value.ToString("X"))
' Displays 2045E
Console.WriteLine(value.ToString("X8"))
' Displays 0002045E

value = 123456789
Console.WriteLine(value.ToString("X"))
' Displays 75BCD15
Console.WriteLine(value.ToString("X2"))
' Displays 75BCD15
```

## <a name="notes"></a>附註

### <a name="numberformatinfo-properties"></a>NumberFormatInfo 屬性

格式設定會受到目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件屬性的影響，而此屬性是由目前執行緒文化特性隱含提供或由叫用格式設定之方法的 [IFormatProvider](xref:System.IFormatProvider) 參數明確提供。 為該參數指定 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 或 [CultureInfo](xref:System.Globalization.CultureInfo) 物件。 

### <a name="integral-and-floatingpoint-numeric-types"></a>整數類資料類型與浮點數值類型

標準數值格式規範的某些描述會參考整數類資料類型或浮點數值類型。 整數數字類型為 [Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64) 和 [BigInteger](xref:System.Numerics.BigInteger)。 浮點數字類型有 [Decimal](xref:System.Decimal)、[Single](xref:System.Single) 和 [Double](xref:System.Double)。 

### <a name="floatingpoint-infinities-and-nan"></a>無限浮點數與 NaN

不論格式字串為何，如果 [Single](xref:System.Single) 或 [Double](xref:System.Double) 浮點類型的值為正無限大、負無限大或不是數字 (NaN)，則格式化後的字串會分別是 [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol)、[NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) 或 [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) 屬性的值 (這些屬性由目前適用的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件所指定)。

## <a name="example"></a>範例

下列範例會使用 en-US 文化特性和所有標準數值格式規範來格式化整數和浮點數值。 這個範例使用兩個特定的數字類型 ([Double](xref:System.Double) 和 [Int32](xref:System.Int32))，但用於其他任何數值基底類型 ([Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[Int64](xref:System.Int64)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)、[BigInteger](xref:System.Numerics.BigInteger), [Decimal](xref:System.Decimal) 和 [Single](xref:System.Single)) 也會產生類似的結果。 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class NumericFormats
{
   public static void Main()
   {
      // Display string representations of numbers for en-us culture
      CultureInfo ci = new CultureInfo("en-us");

      // Output floating point values
      double floating = 10761.937554;
      Console.WriteLine("C: {0}", 
              floating.ToString("C", ci));           // Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", 
              floating.ToString("E03", ci));         // Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", 
              floating.ToString("F04", ci));         // Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}",  
              floating.ToString("G", ci));           // Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", 
              floating.ToString("N03", ci));         // Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", 
              (floating/10000).ToString("P02", ci)); // Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", 
              floating.ToString("R", ci));           // Displays "R: 10761.937554"            
      Console.WriteLine();

      // Output integral values
      int integral = 8395;
      Console.WriteLine("C: {0}", 
              integral.ToString("C", ci));           // Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", 
              integral.ToString("D6", ci));          // Displays "D: 008395" 
      Console.WriteLine("E: {0}", 
              integral.ToString("E03", ci));         // Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", 
              integral.ToString("F01", ci));         // Displays "F: 8395.0"    
      Console.WriteLine("G: {0}",  
              integral.ToString("G", ci));           // Displays "G: 8395"
      Console.WriteLine("N: {0}", 
              integral.ToString("N01", ci));         // Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", 
              (integral/10000.0).ToString("P02", ci)); // Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", 
              integral.ToString("X", ci));           // Displays "X: 0x20CB"
      Console.WriteLine();
   }
}
```

```vb
Option Strict On

Imports System.Globalization
Imports System.Threading

Module NumericFormats
   Public Sub Main()
      ' Display string representations of numbers for en-us culture
      Dim ci As New CultureInfo("en-us")

      ' Output floating point values
      Dim floating As Double = 10761.937554
      Console.WriteLine("C: {0}", _
              floating.ToString("C", ci))           ' Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", _
              floating.ToString("E03", ci))         ' Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", _
              floating.ToString("F04", ci))         ' Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}", _ 
              floating.ToString("G", ci))           ' Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", _
              floating.ToString("N03", ci))         ' Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", _
              (floating/10000).ToString("P02", ci)) ' Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", _
              floating.ToString("R", ci))           ' Displays "R: 10761.937554"            
      Console.WriteLine()

      ' Output integral values
      Dim integral As Integer = 8395
      Console.WriteLine("C: {0}", _
              integral.ToString("C", ci))           ' Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", _
              integral.ToString("D6"))              ' Displays "D: 008395" 
      Console.WriteLine("E: {0}", _
              integral.ToString("E03", ci))         ' Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", _
              integral.ToString("F01", ci))         ' Displays "F: 8395.0"    
      Console.WriteLine("G: {0}", _ 
              integral.ToString("G", ci))           ' Displays "G: 8395"
      Console.WriteLine("N: {0}", _
              integral.ToString("N01", ci))         ' Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", _
              (integral/10000).ToString("P02", ci)) ' Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", _
              integral.ToString("X", ci))           ' Displays "X: 0x20CB"
      Console.WriteLine()
   End Sub
End Module
```

## <a name="see-also"></a>請參閱

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[自訂數值格式字串](custom-numeric.md)

[格式化類型](formatting-types.md)

[如何：使用前置零填補數字](pad-number.md)

[複合格式](composite-format.md)



<!--HONumber=Nov16_HO3-->


