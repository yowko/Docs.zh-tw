---
title: "複合格式化"
description: "複合格式化"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a01efc8f-c242-4535-bd32-acd0032d9590
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 9bcf2ff74237f7e7faf2890849c2d68a0a602353

---

# <a name="composite-formatting"></a>複合格式化

.NET 複合格式功能會採用物件清單和複合格式字串作為輸入。 複合格式字串是由混合索引替代符號 (Placeholder) 的固定文字所組成 (這些符號稱為對應至清單內物件的格式項目)。 格式作業產生的結果字串是由原始固定文字所組成，這些固定文字混合了清單中代表物件的字串。 

下列方法支援複合格式功能： 

* [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))，傳回格式化的結果字串。 

* [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider, System.String, System.Object)，將格式化的結果字串附加至 [StringBuilder](xref:System.Text.StringBuilder) 物件。

* [Console](xref:System.Console) `WriteLine` 方法的部分多載，對主控台顯示格式化的結果字串。  

* [TextWriter](xref:System.IO.TextWriter) `WriteLine` 方法的部分多載，將格式化的結果字串寫入至資料流或檔案。 衍生自 [TextWriter](xref:System.IO.TextWriter) 的類別 (例如 [StreamWriter](xref:System.IO.StreamWriter)) 也會共用這項功能。

* [Debug.WriteLine(String, Object[])](xref:System.Diagnostics.Debug.WriteLine(System.String,System.Object[]))，將格式化的訊息輸出至追蹤接聽項。 

* [Trace.TraceError(String, Object[])](xref:System.Diagnostics.Trace.TraceError(System.String,System.Object[]))、[Trace.TraceInformation(String, Object[])](xref:System.Diagnostics.Trace.TraceInformation(System.String,System.Object[])) 和 [Trace.TraceWarning(String, Object[])](xref:System.Diagnostics.Trace.TraceWarning(System.String,System.Object[])) 方法，將格式化的訊息輸出至追蹤接聽項。 

* [TraceSource.TraceInformation(String, Object[])](xref:System.Diagnostics.TraceSource.TraceInformation(System.String,System.Object[])) 方法，將告知性方法寫入至追蹤接聽項。 

## <a name="composite-format-string"></a>複合格式字串

複合格式字串和物件清單會當做支援複合格式功能之方法的引數來使用。 複合格式字串是由零個或更多段與一個或多個格式項目混合的固定文字所組成， 固定文字是您選擇的任何文字，而每個格式項目都會對應到清單內的一個物件或 boxed 結構。 複合格式功能將會傳回新的結果字串，其中每一個格式項目都會由清單內對應物件的字串表示來取代。

請考慮下列 [Format](xref:System.String.Format(System.String.Format(System.IFormatProvider,System.String,System.Object)) 程式碼片段。

```csharp
string name = "Fred";
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now);
```

```vb
Dim name As String = "Fred"
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now)
```

固定的文字為 `"Name = "` 和 `", hours = "`。 格式項目為 `"{0}"` (其索引為 0，且對應至物件 `name`) 及 `"{1:hh}"` (其索引為 1，且對應至物件 `DateTime.Now`)。

## <a name="format-item-syntax"></a>格式項目語法

每個格式項目都會使用下列格式，並由下列元件所組成：

__{__*index*[,*alignment*][:*formatString*]__}__

成對的大括號 ("{" 和 "}") 是必要的。 
 
### <a name="index-component"></a>索引元件

強制的 *index* 元件 (也稱為參數規範) 是用以識別物件清單中對應項目的數字 (從 0 開始)。 也就是說，參數規範為 0 的格式項目會格式化清單中的第一個物件，而參數規範為 1 的格式項目會格式化清單中的第二個物件，依此類推。 下列範例包含四個參數規範 (編號為 0 到 3)，以表示小於 10 的質數： 

```csharp
string primes;
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 );
Console.WriteLine(primes);
// The example displays the following output:
//      Prime numbers less than 10: 2, 3, 5, 7
```

```vb
Dim primes As String
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 )
Console.WriteLine(primes)
' The example displays the following output:
'      Prime numbers less than 10: 2, 3, 5, 7
```

多個格式項目可以藉由指定相同參數規範來參考物件清單中的相同項目。 例如，您可以指定複合格式字串 (例如："0x{0:X} {0:E} {0:N}") 來格式化十六進位、科學格式和數字格式的相同數值，如下列範例所示。 

```csharp
string multiple = String.Format("0x{0:X} {0:E} {0:N}",
                                Int64.MaxValue);
Console.WriteLine(multiple);
// The example displays the following output:
//      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

```vb
Dim multiple As String = String.Format("0x{0:X} {0:E} {0:N}",
                                       Int64.MaxValue)
Console.WriteLine(multiple)
' The example displays the following output:
'      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

每個格式項目皆可參考清單內的任何物件。 例如，如果有三個物件，您可以指定複合格式字串 (如："{1} {0} {2}") 來格式化第二個、第一個和第三個物件。 不是格式項目所參考的物件會被忽略。 如果參數規範指定超出物件清單範圍的項目，則會在執行階段擲回 [FormatException](xref:System.FormatException)。

### <a name="alignment-component"></a>對齊元件

選擇性 *alignment* 元件為帶正負號的整數，表示慣用的格式化欄位寬度。 如果 *alignment* 的值小於格式化字串的長度，則會忽略 *alignment* 並使用格式化字串的長度當做欄位寬度。 如果 *alignment* 為正數，欄位中的格式化資料會靠右對齊；如果 *alignment* 為負數，則會靠左對齊。 如果填補有必要，則會使用泛空白字元 (White Space)。 如果指定了 *alignment*，則需要逗號。

下列範例會定義兩個陣列，一個包含員工的名稱，另一個包含他們在兩週內的工作時數。 複合格式字串會在 20 個字元的欄位中，將名稱靠左對齊，並且在 5 個字元的欄位中，將其工作時數靠右對齊。 請注意，"N1" 標準格式字串也會用來格式化具有一個小數位數的時數。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string[] names = { "Adam", "Bridgette", "Carla", "Daniel",
                         "Ebenezer", "Francine", "George" };
      decimal[] hours = { 40, 6.667m, 40.39m, 82, 40.333m, 80,
                                 16.75m };

      Console.WriteLine("{0,-20} {1,5}\n", "Name", "Hours");
      for (int ctr = 0; ctr < names.Length; ctr++)
         Console.WriteLine("{0,-20} {1,5:N1}", names[ctr], hours[ctr]);

   }
}
// The example displays the following output:
//       Name                 Hours
//
//       Adam                  40.0
//       Bridgette              6.7
//       Carla                 40.4
//       Daniel                82.0
//       Ebenezer              40.3
//       Francine              80.0
//       George                16.8
```

```vb
Module Example
   Public Sub Main()
      Dim names() As String = { "Adam", "Bridgette", "Carla", "Daniel",
                                "Ebenezer", "Francine", "George" }
      Dim hours() As Decimal = { 40, 6.667d, 40.39d, 82, 40.333d, 80,
                                 16.75d }

      Console.WriteLine("{0,-20} {1,5}", "Name", "Hours")
      Console.WriteLine()
      For ctr As Integer = 0 To names.Length - 1
         Console.WriteLine("{0,-20} {1,5:N1}", names(ctr), hours(ctr))
      Next
   End Sub
End Module
' The example displays the following output:
'       Name                 Hours
'
'       Adam                  40.0
'       Bridgette              6.7
'       Carla                 40.4
'       Daniel                82.0
'       Ebenezer              40.3
'       Francine              80.0
'       George                16.8
```

### <a name="format-string-component"></a>格式字串元件

選擇性 *formatString* 元件是一個格式字串，適用於將格式化的物件類型。 如果對應的物件為數值，請指定標準或自訂數值格式字串；如果對應的物件為 [DateTime](xref:System.DateTime) 物件，請指定標準或自訂日期和時間格式字串；或者，如果對應的物件為列舉值，請指定[列舉格式字串](enumeration-format.md)。 如果未指定 *formatString*，則會使用數值、日期和時間或列舉類型的一般 ("G") 格式規範。 如果指定 *formatString*，則需要冒號。

下表列出 .NET Framework 類別庫中支援預先定義之格式字串的類型或類型分類，並提供列出支援之格式字串的主題連結。 請注意，字串格式是一種可延伸機制，可讓為所有現有類型定義新的格式字串，以及定義一組應用程式定義類型所支援的格式字串。 如需詳細資訊，請參閱 [IFormattable](xref:System.IFormattable) 和 [ICustomFormatter](xref:System.ICustomFormatter) 介面主題。 

類型或類型分類 | 請參閱
--------------------- | ---
日期和時間類型 ([DateTime](xref:System.DateTime)、[DateTimeOffset](xref:System.DateTimeOffset)) | [標準日期與時間格式字串](standard-datetime.md)、[自訂日期與時間格式字串](custom-datetime.md)
列舉類型 (衍生自 [System.Enum](xref:System.Enum) 的所有類型) | [列舉格式字串](enumeration-format.md)
數值類型 ([BigInteger](xref:System.Numerics.BigInteger)、[Byte](xref:System.Byte)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)) | [標準數值格式字串](standard-numeric.md)、[自訂數值格式字串](custom-numeric.md)
[Guid](xref:System.Guid) | [Guid.ToString(String)](xref:System.Guid.ToString(System.String))
[TimeSpan](xref:System.TimeSpan) | [標準 TimeSpan 格式字串](standard-timespan.md)、[自訂 TimeSpan 格式字串](custom-timespan.md)

### <a name="escaping-braces"></a>逸出大括號

左右大括號會被解譯成格式項目的開頭與結尾。 因此，您必須使用逸出序列 (Escape Sequence)，才能顯示字面上的左右大括號。 請在固定文字中指定兩個左邊的大括號 ("{{")，以顯示一個左邊的大括號 ("{")，或者指定兩個右邊的大括號 ("}}") 來顯示一個右邊的大括號 ("}")。 格式項目中的括號會以它們出現的順序依序解譯， 但是不支援解譯巢狀大括號。 

解譯逸出括號的方式，可能會造成無法預期的結果。 例如，格式項目 "{{{0:D}}}" 原本是要顯示一個左邊大括號、一個格式化為十進位的數值和一個右邊大括號。 然而，格式項目實際會以下列方式來解譯： 

1. 前面兩個左邊大括號 ("{{") 逸出，產生一個左邊大括號。 

2. 接下來的三個字元 ("{0:") 會解譯成格式項目的開頭。

3. 再下一個字元 ("D") 可能解譯成十進位 (Decimal) 標準數值格式規範，但後面兩個逸出的右邊大括號 ("}}") 會產生一個大括號。 由於結果字串 ("D}") 並非標準的數值格式規範，因此，結果字串會被解譯成自訂格式字串，表示會顯示成常值字串 "D}"。 

4. 最後的大括號 ("}") 會被解譯成格式項目的結尾。 

5. 最後顯示的結果會是常值字串 "{D}"， 而要進行格式化的數值則不會顯示出來。

撰寫程式碼時，能夠避免錯誤解譯逸出大括號和格式項目的方法，就是個別地格式化大括號和格式項目。 也就是說，在第一個格式化作業中顯示常值的左邊大括號，在下一個作業中顯示格式項目的結果，接著在最終作業中顯示常值的右邊大括號。 下列範例將示範這個方法。

```csharp
int value = 6324;
string output = string.Format("{0}{1:D}{2}", 
                             "{", value, "}");
Console.WriteLine(output);
// The example displays the following output:
//       {6324} 
```

```vb
Dim value As Integer = 6324
Dim output As String = String.Format("{0}{1:D}{2}", _
                                     "{", value, "}")
Console.WriteLine(output)   
' The example displays the following output:
'       {6324}
```

### <a name="processing-order"></a>處理順序

如果對複合格式化方法的呼叫包含的 [IFormatProvider](xref:System.IFormatProvider) 引數其值不是 null，則執行階段會呼叫其 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法要求 [ICustomFormatter](xref:System.ICustomFormatter) 實作。 如果方法能夠傳回 [ICustomFormatter](xref:System.ICustomFormatter) 實作，則會將它快取以供日後使用。 

參數清單中每個對應至格式項目的值都會藉由執行下列步驟轉換為字串。 如果在前三個步驟中有任何條件成立，則會在該步驟傳回值的字串表示，而不會再執行後續步驟。

1. 如果要格式化的值是 `null`，則會傳回空字串 ("")。 

2. 如果可以使用 [ICustomFormatter](xref:System.ICustomFormatter) 實作，則執行階段會呼叫其 [Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法。 它會將格式項目的 *formatString* 值 (如果有的話) 傳遞給方法；如果沒有的話，則將 `null` 連同 [IFormatProvider](xref:System.IFormatProvider) 實作一起傳遞。 

3. 如果值實作 [IFormattable](xref:System.IFormattable) 介面，則會呼叫介面的 [ToString(String,IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) 方法。 如果格式項目中有 *formatString* 值的話，就會將該值傳遞給方法；如果沒有的話，則會傳遞 `null`。 [IFormatProvider](xref:System.IFormatProvider) 引數的判斷如下：

    *   對於數值，如果呼叫具有非 null [IFormatProvider](xref:System.IFormatProvider) 引數的複合格式化方法，則執行階段會從其 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法要求 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。 如果無法提供、如果引數的值為 `null`，或者如果複合格式化方法沒有 [IFormatProvider](xref:System.IFormatProvider) 參數，則會使用目前執行緒文化特性的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo 物件。 
    
    * 對於日期和時間值，如果呼叫具有非 null [IFormatProvider](xref:System.IFormatProvider) 引數的複合格式化方法，則執行階段會從其 [IFormatProvider.GetFormat](xref:System.IFormatProvider._GetFormat(System.Type) 方法要求 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 如果無法提供、如果引數的值為 `null`，或者如果複合格式化方法沒有 [IFormatProvider](xref:System.IFormatProvider) 參數，則會使用目前執行緒文化特性的 [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) 物件。 
    
    * 對於其他類型的物件，如果使用 [IFormatProvider](xref:System.IFormatProvider) 引數呼叫複合格式，其值 (包括未提供 [IFormatProvider](xref:System.IFormatProvider) 物件時的 `null`) 會直接傳遞至 [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) 實作。 否則，表示目前執行緒文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件會傳遞至 [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) 實作。 
    
4. 呼叫類型的無參數 `ToString` 方法，該方法會覆寫 [Object.ToString()](xref:System.Object.ToString) 或繼承其基底類別的行為。 在這種情況下，會忽略 *formatString* 元件在格式項目中指定的格式字串 (如果有的話)。

對齊會在已經執行前面的步驟之後套用。 

## <a name="code-examples"></a>程式碼範例

下列範例顯示一個使用複合格式建立的字串，以及另一個使用物件的 `ToString` 方法建立的字串。 這兩個類型的格式化產生相等結果。 

```csharp
string FormatString1 = String.Format("{0:dddd MMMM}", DateTime.Now);
string FormatString2 = DateTime.Now.ToString("dddd MMMM");
```

```vb
Dim FormatString1 As String = String.Format("{0:dddd MMMM}", DateTime.Now)
Dim FormatString2 As String = DateTime.Now.ToString("dddd MMMM")
```

假設目前日期是五月的星期四，前面範例中兩個字串的值在美國英文文化特性中都是 `Thursday May`。

[Console.WriteLine](xref:System.Console.WriteLine) 會公開與 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 相同的功能。 這兩種方法唯一的差別在於，[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 會以字串形式傳回結果，而 [Console.WriteLine](xref:System.Console.WriteLine) 則會將結果寫入至與 [Console](xref:System.Console) 物件關聯的輸出資料流。 下列範例使用 [Console.WriteLine](xref:System.Console.WriteLine) 方法，將 `MyInt` 的值格式化為貨幣值。

```csharp
int MyInt = 100;
Console.WriteLine("{0:C}", MyInt);
// The example displays the following output 
// if en-US is the current culture:
//        $100.00
```

```vb
Dim MyInt As Integer = 100
Console.WriteLine("{0:C}", MyInt)
' The example displays the following output
' if en-US is the current culture:
'        $100.00
```

下列範例示範多個物件的格式化，其中包括使用兩種不同方式來格式化一個物件。

```csharp
string myName = "Fred";
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}",
      myName, DateTime.Now));
// Depending on the current time, the example displays output like the following:
//    Name = Fred, hours = 11, minutes = 30                 
```

```vb
Dim myName As String = "Fred"
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}", _
                  myName, DateTime.Now))
' Depending on the current time, the example displays output like the following:
'    Name = Fred, hours = 11, minutes = 30
```

下列範例示範格式設定中的對齊用法。 格式化的引數會放在兩個垂直線 (|) 字元之間以強調所產生的對齊。

```csharp
string myFName = "Fred";
string myLName = "Opals";
int myInt = 100;
string FormatFName = String.Format("First Name = |{0,10}|", myFName);
string FormatLName = String.Format("Last Name = |{0,10}|", myLName);
string FormatPrice = String.Format("Price = |{0,10:C}|", myInt); 
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
Console.WriteLine();

FormatFName = String.Format("First Name = |{0,-10}|", myFName);
FormatLName = String.Format("Last Name = |{0,-10}|", myLName);
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt);
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
// The example displays the following output on a system whose current
// culture is en-US:
//          First Name = |      Fred|
//          Last Name = |     Opals|
//          Price = |   $100.00|
//
//          First Name = |Fred      |
//          Last Name = |Opals     |
//          Price = |$100.00   |
```

```vb
Dim myFName As String = "Fred"
Dim myLName As String = "Opals"

Dim myInt As Integer = 100
Dim FormatFName As String = String.Format("First Name = |{0,10}|", myFName)
Dim FormatLName As String = String.Format("Last Name = |{0,10}|", myLName)
Dim FormatPrice As String = String.Format("Price = |{0,10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
Console.WriteLine()

FormatFName = String.Format("First Name = |{0,-10}|", myFName)
FormatLName = String.Format("Last Name = |{0,-10}|", myLName)
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
' The example displays the following output on a system whose current
' culture is en-US:
'          First Name = |      Fred|
'          Last Name = |     Opals|
'          Price = |   $100.00|
'
'          First Name = |Fred      |
'          Last Name = |Opals     |
'          Price = |$100.00   |
```

## <a name="see-also"></a>另請參閱

[Console.WriteLine](xref:System.Console.WriteLine)

[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))

[格式化類型](formatting-types.md)

[標準日期與時間格式字串](standard-datetime.md)

[自訂日期與時間格式字串](custom-datetime.md)

[列舉格式字串](enumeration-format.md)

[標準數值格式字串](standard-numeric.md)

[自訂數值格式字串](custom-numeric.md)

[標準 TimeSpan 格式字串](standard-timespan.md)

[自訂 TimeSpan 格式字串](custom-timespan.md)



<!--HONumber=Nov16_HO1-->


