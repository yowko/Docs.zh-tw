---
title: "自訂數值格式字串"
description: "自訂數值格式字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b1c16ee-956f-4e9c-8502-c3dd6598c51d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e36c0117f6f011589299fa59a8abd139870c2257

---

# <a name="custom-numeric-format-strings"></a>自訂數值格式字串

您可以建立由一個或多個自訂數值規範所組成的自訂數值格式字串，以定義如何格式化數值資料。 自訂數值格式字串為任何非[標準數值格式字串](standard-numeric.md)的格式字串。 

所有數字類型的 `ToString` 方法的一些多載可支援自訂數值格式字串。 例如，您可以提供數值格式字串給 [Int32](xref:System.Int32) 類型的 [ToString(String)](xref:System.Int32.ToString(System.String)) 和 [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) 方法。 .NET Framework 的[複合格式](composite-format.md)功能也支援自訂數值格式字串，此功能是由 [Console](xref:System.Console) 與 [StreamWriter](xref:System.IO.StreamWriter) 類別的一些 `Write` 和 `WriteLine` 方法，以及 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法和 [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 方法所使用。

下表說明自訂數值格式規範，並顯示每個格式範例所產生的範例輸出。 如需使用自訂數值格式字串的其他資訊，請參閱[備註](#notes)一節，如需其用法的完整解說，請參閱[範例](#example)一節。

格式規範 | 名稱 | 描述 | 範例
---------------- | ---- | ----------- | --------
"0" | 零值預留位置 | 以對應的數字 (如果有的話) 取代零，否則結果字串中會出現零。 | `1234.5678 ("00000") -> 01235`; `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"#" | 數字預留位置 | 將 "#" 符號取代為對應的數字 (如果有的話)，否則結果字串中不會出現任何數字。 請注意，如果輸入字串中對應的數字是不重要的 0，結果字串中就不會顯示任何數字。 例如，0003 ("####") -> 3。 | `1234.5678 ("#####") -> 1235`; `0.45678 ("#.##", en-US) -> .46`; `0.45678 ("#.##", fr-FR) -> ,46`
"." | 小數點 | 決定結果字串中小數點的位置。 | `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"," | 群組分隔符號和數值範圍 | 同時做為群組分隔符號和數值縮放規範。 如果做為群組分隔符號，則會在每個群組之間插入當地語系化群組分隔符號字元。 做為數值縮放規範時，每指定一個逗號就會將數字除以 1000。 | 群組分隔符號規範：`2147483647 ("##,#", en-US) -> 2,147,483,647`、`2147483647 ("##,#", es-ES) -> 2.147.483.647`。 調整規範：`2147483647 ("#,#,,", en-US) -> 2,147`；`2147483647 ("#,#,,", es-ES) -> 2.147`
"%" | 百分比預留位置 | 將數字乘以 100，並在結果字串中插入當地語系化的百分比符號。 | `0.3697 ("%#0.00", en-US) -> %36.97`; `0.3697 ("%#0.00", el-GR) -> %36,97`; `0.3697 ("##.0 %", en-US) -> 37.0 %`; `0.3697 ("##.0 %", el-GR) -> 37,0 %`
"‰" | 千分之一符號預留位置 | 將數字乘以 1000，並在結果字串中插入當地語系化的千分比符號。 | `0.03697 ("#0.00‰", en-US) -> 36.97‰`; `0.03697 ("#0.00‰", ru-RU) -> 36,97‰`
"E0"、"E+0"、"E-0"、"e0"、"e+0"、"e-0" | 指數標記法 | 如果後面至少接著一個 0 (零)，則使用指數標記法來格式化結果。 大小寫 "E" 或 "e" 表示結果字串中指數符號的大小寫。 接在 "E" 或 "e" 字元後面的零個數決定指數中的最少位數。 加號 (+) 表示指數前面一律加上正負號字元。 減號 (-) 表示只在負指數前面才加上正負號字元。 | `987654 ("#0.0e0") -> 98.8e4`; `1503.92311 ("0.0##e+00") -> 1.504e+03`; `1.8901385E-16 ("0.0e+00") -> 1.9e-16`
\ | 逸出字元 | 將下一個字元解譯為常值，而不是自訂格式規範。 | `987654 ("\###00\#") -> #987654#`
'string'、"string" | 常值字串分隔符號 | 表示應該將所括住的字元原封不動地複製到結果字串。 | `68 ("# ' degrees'") -> 68 degrees`
; | 區段分隔符號 | 以個別格式字串來定義正數、負數和零值的區段。 | `12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35`; `0 ("#0.0#;(#0.0#);-\0-") -> -0-`; `-12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)`; `12.345 ("#0.0#;(#0.0#)") -> 12.35`; `0 ("#0.0#;(#0.0#)") -> 0.0 ; -12.345 ("#0.0#;(#0.0#)") -> (12.35)`
其他 | 所有其他字元 | 字元會原封不動地複製到結果字串。 | `68 ("# °") -> 68 °`

下列各節提供每個自訂數值格式規範的詳細資訊。

## <a name="the-0-custom-specifier"></a>"0" 自訂規範

"0" 自訂格式規範是當做零預留位置符號。 如果正在格式化的值有數字位於格式字串中出現零的位置上，則該數字會複製到結果字串，否則結果字串中會出現零。 小數點前最左邊的零和小數點後最右邊的零位置，決定要一直在輸出字串中出現的位數範圍。 

"00" 規範會造成數值捨入至最接近的小數點前面數值，而其中永遠使用遠離零的捨入方式。 例如，使用 "00" 格式化 34.5 將會得到值 35。

下列範例顯示使用包含零預留位置的自訂格式字串來格式化的幾個值。

```csharp
double value;

value = 123;
Console.WriteLine(value.ToString("00000"));
Console.WriteLine(String.Format("{0:00000}", value));
// Displays 00123

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

CultureInfo daDK = CultureInfo.CreateSpecificCulture("da-DK");
Console.WriteLine(value.ToString("00.00", daDK)); 
Console.WriteLine(String.Format(daDK, "{0:00.00}", value));
// Displays 01,20

value = .56;
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value));
// Displays 0.6

value = 1234567890;
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value)); 
// Displays 1,234,567,890      

CultureInfo elGR = CultureInfo.CreateSpecificCulture("el-GR");
Console.WriteLine(value.ToString("0,0", elGR)); 
Console.WriteLine(String.Format(elGR, "{0:0,0}", value));   
// Displays 1.234.567.890

value = 1234567890.123456;
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture));   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value));   
// Displays 1,234,567,890.1  

value = 1234.567890;
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture));  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value));  
// Displays 1,234.57
```

```vb
Dim value As Double

value = 123
Console.WriteLine(value.ToString("00000"))
Console.WriteLine(String.Format("{0:00000}", value))
' Displays 00123

value = 1.2
Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                  "{0:0.00}", value))
' Displays 1.20
Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value))
' Displays 01.20
Dim daDK As CultureInfo = CultureInfo.CreateSpecificCulture("da-DK")
Console.WriteLine(value.ToString("00.00", daDK))
Console.WriteLine(String.Format(daDK, "{0:00.00}", value))
' Displays 01,20

value = .56
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value))
' Displays 0.6

value = 1234567890
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture))  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value))  
' Displays 1,234,567,890      
Dim elGR As CultureInfo = CultureInfo.CreateSpecificCulture("el-GR")
Console.WriteLine(value.ToString("0,0", elGR))
Console.WriteLine(String.Format(elGR, "{0:0,0}", value))    
' Displays 1.234.567.890

value = 1234567890.123456
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value))    
' Displays 1,234,567,890.1  

value = 1234.567890
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture))   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value))   
' Displays 1,234.57
```

## <a name="the-custom-specifier"></a>"#" 自訂規範

"#" 自訂格式規範是當做數字預留位置符號。 如果正在格式化的值有數字位於格式字串中出現 "#" 符號的位置上，則該數字會複製到輸出字串。 否則，沒有東西會存放在結果字串中的那個位置。 

請注意，這個規範永遠不會顯示不是有效位數的零，即使字串中只有零這個數字也一樣。 只有當零在所顯示的數字中是有效位數時，才會顯示零。 

"##" 格式字串會造成數值捨入至最接近的小數點前面數值，而其中永遠使用遠離零的捨入方式。 例如，使用 "##" 格式化 34.5 將會得到值 35。

下列範例顯示使用包含數字預留位置的自訂格式字串來格式化的幾個值。

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value));
// Displays 1.2

value = 123;
Console.WriteLine(value.ToString("#####"));
Console.WriteLine(String.Format("{0:#####}", value));
// Displays 123

value = 123456;
Console.WriteLine(value.ToString("[##-##-##]"));      
Console.WriteLine(String.Format("{0:[##-##-##]}", value));      
// Displays [12-34-56]

value = 1234567890;
Console.WriteLine(value.ToString("#"));
Console.WriteLine(String.Format("{0:#}", value));
// Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"));
Console.WriteLine(String.Format("{0:(###) ###-####}", value));
// Displays (123) 456-7890
```

```vb
Dim value As Double

value = 1.2
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value))
' Displays 1.2

value = 123
Console.WriteLine(value.ToString("#####"))
Console.WriteLine(String.Format("{0:#####}", value))
' Displays 123

value = 123456
Console.WriteLine(value.ToString("[##-##-##]"))      
Console.WriteLine(String.Format("{0:[##-##-##]}", value))      
' Displays [12-34-56]

value = 1234567890
Console.WriteLine(value.ToString("#"))
Console.WriteLine(String.Format("{0:#}", value))
' Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"))
Console.WriteLine(String.Format("{0:(###) ###-####}", value))
' Displays (123) 456-7890
```

若要傳回結果字串，以空格取代不存在的數字或前置零，請使用[複合格式](composite-format.md)功能並指定欄位寬度，如下列範例所示。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double value = .324;
      Console.WriteLine("The value is: '{0,5:#.###}'", value);
   }
}
// The example displays the following output if the current culture
// is en-US:
//      The value is: ' .324'
```

```vb
Module Example
   Public Sub Main()
      Dim value As Double = .324
      Console.WriteLine("The value is: '{0,5:#.###}'", value)
   End Sub
End Module
' The example displays the following output if the current culture
' is en-US:
'      The value is: ' .324'
```

## <a name="the-custom-specifier"></a>"." 自訂規範

"." 自訂格式規範會將當地語系化的十進位分隔符號插入結果字串中。 格式字串中第一個點決定所格式化值中的小數分隔符號位置；任何其他點將被忽略。 

結果字串中當做小數分隔符號的字元不一定是點，而是由控制格式設定的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的 [NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) 屬性來決定。

下列範例使用 "." 格式規範來定義幾個結果字串中小數點的位置。

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

Console.WriteLine(value.ToString("00.00", 
                CultureInfo.CreateSpecificCulture("da-DK")));
Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                "{0:00.00}", value));
// Displays 01,20

value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value)); 
// Displays 8.6%

value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.###E+0}", value));
// Displays 8.6E+4
```

```vb
Dim value As Double

  value = 1.2
  Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
  Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:0.00}", value))
  ' Displays 1.20

  Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:00.00}", value))
  ' Displays 01.20

  Console.WriteLine(value.ToString("00.00", _
                    CultureInfo.CreateSpecificCulture("da-DK")))
  Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                    "{0:00.00}", value))
  ' Displays 01,20

  value = .086
  Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)) 
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#0.##%}", value)) 
  ' Displays 8.6%

  value = 86000
  Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                    "{0:0.###E+0}", value))
' Displays 8.6E+4
```

## <a name="the-custom-specifier"></a>"," 自訂規範

"," 字元同時當做群組分隔符號和數值縮放規範。 

* 群組分隔符號：如果在用於格式化數字整數位數的兩個數字預留位置 (0 或 #) 之間指定一個或多個逗號，則會在輸出的整數部分中在每個數字群組之間插入群組分隔符號字元。 

  目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的 [NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) 和 [NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) 屬性會判斷當做數字群組分隔符號使用的字元，以及每個數字群組的大小。 例如，如果使用字串 "#,#" 和不變的文化特性來格式化數字 1000，則輸出為 "1,000"。
  
* 數值縮放規範：如果在明確或隱含小數點的左側緊接著指定一個或多個逗號，則每指定一個逗號就會將要格式化的數字除以 1000。 例如，如果使用字串 "0,," 來格式化數字 1 億，則其輸出為 "100"。 

您可以在相同的格式字串內使用群組分隔符號和數值縮放規範。 例如，如果使用字串 "#,0,," 和不變的文化特性來格式化數字 10 億，則輸出為 "1,000"。 

下列範例示範使用逗號做為群組分隔符號。

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value));
// Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));
// Displays 1,235
```

```vb
Dim value As Double = 1234567890
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value))
' Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value))
' Displays 1,235
```

下列範例示範使用逗點做為數值縮放的規範。

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,}", value)); 
// Displays 1235   

Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,,}", value));
// Displays 1  

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));       
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));       
// Displays 1,235
```  

```vb
Dim value As Double = 1234567890
  Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture))    
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, "{0:#,,}", value))  
  ' Displays 1235   

  Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,,,}", value))
' Displays 1  

  Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))       
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,##0,,}", value))       
' Displays 1,235
```

## <a name="the-custom-specifier"></a>"%" 自訂規範

格式字串中的百分比符號 (%) 會使得數字在格式化之前先乘以 100。 數字中會根據格式字串中出現 % 的位置，插入當地語系化百分比符號。 使用的百分比字元由目前 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件的 [PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) 屬性所定義。

下列範例會定義幾個包含 "%" 自訂規範的自訂格式字串。

```csharp
double value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value));
// Displays 8.6%     
```

```vb
Dim value As Double = .086
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value))
' Displays 8.6% 
```

## <a name="the-custom-specifier"></a>"‰" 自訂規範

格式字串中的千分比字元 (‰ 或 \u2030) 會使得數字在格式化之前先乘以 1000。 傳回的字串中會根據格式字串中出現 ‰ 符號的位置，插入適當的千分比符號。 使用的千分之一符號字元是由提供文化特性專屬格式資訊之物件的 [NumberFormatInfo.PerMilleSymbol](xref:System.Globalization.NumberFormatInfo.PerMilleSymbol) 屬性定義的。

下列範例會定義包含 "‰" 自訂規範的自訂格式字串。

```csharp
double value = .00354;
string perMilleFmt = "#0.## " + '\u2030';
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value));
// Displays 3.54‰   
```

```vb
Dim value As Double = .00354
Dim perMilleFmt As String = "#0.## " & ChrW(&h2030)
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value))
' Displays 3.54 ‰
```

## <a name="the-e-and-e-custom-specifiers"></a>"E" 和 "e" 自訂規範

如果 "E"、"E+"、"E-"、"e"、"e+" 或 "e-" 中的任何一個字串出現在格式字串中，且後面至少緊接著一個零，則會使用科學標記法來格式化數字，並在數字和指數之間插入 "E" 或 "e"。 接在科學標記法指標之後的零個數決定要在指數部分輸出的最少位數。 "E+" 和 "e+" 格式表示指數前面應該一律加上加號或減號。 "E"、"E-"、"e" 或 "e-" 格式表示只應該在負數指數前面加上正負號字元。

下列範例使用科學記號規範來格式化幾個數值。

```csharp
double value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value));
// Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value));
// Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value));
// Displays 8.6E004
```

```vb
Dim value As Double = 86000
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value))
' Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value))
' Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value))
' Displays 8.6E004
```

## <a name="the-escape-character"></a>"\" 逸出字元

格式字串中的 "#"、"0"、"."、","、"%" 和 "‰" 符號會解譯為格式規範，而不是常值字元。 大寫和小寫 "E" 以及 + 和 - 符號視其在自訂格式字串中的位置而定，也有可能會解譯為格式規範。 

若要避免將字元解譯為格式規範，您可以在前面加上反斜線，這是逸出字元。 逸出字元表示接下來的字元是字元常值，應該原封不動地放入結果字串中。

若要在結果字串中加上反斜線，您必須再加上一個反斜線 (變成 \\)，才能將反斜線解譯為常值。 

> [!NOTE]
> 某些編譯器 (例如 C# 編譯器) 也可能會將單一反斜線字元解譯為逸出字元。 為確保格式化時能正確地解譯字串，在使用 C# 時，可以在串前加上逐字字串常值字元 (@ 字元)，或在每個反斜線前再加上一個反斜線字元。 下列 C# 範例示範這兩種做法。

下列範例會使用逸出字元，以避免格式化作業將 "#"、"0" 和 "\" 字元解譯為逸出字元或格式規範。 此範例會多使用一個反斜線，以確保反斜線會解譯為常值字元。

```csharp
int value = 123;
Console.WriteLine(value.ToString("\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#"));
Console.WriteLine(String.Format("{0:\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString(xref:"\#\#\# ##0 dollars and \0\0 cents \#\#\#"));
Console.WriteLine(String.Format(xref:"{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\"));
Console.WriteLine(String.Format("{0:\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\

Console.WriteLine(value.ToString(xref:"\\\\\\ ##0 dollars and \0\0 cents \\\\\\"));
Console.WriteLine(String.Format(xref:"{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\
```

```vb
Dim value As Integer = 123
Console.WriteLine(value.ToString("\#\#\# ##0 dollars and \0\0 cents \#\#\#"))
Console.WriteLine(String.Format("{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}", 
                                value))
' Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\ ##0 dollars and \0\0 cents \\\\\\"))
Console.WriteLine(String.Format("{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}", 
                                value))
' Displays \\\ 123 dollars and 00 cents \\\
```

## <a name="the-section-separator"></a>; 區段分隔符號

冒號 (;) 是條件式格式規範，這個規範會根據數字的值是正數、負數還是零，將不同的格式套用至數字。 若要產生這個行為，自訂格式字串可以包含多達三個以分號分隔的區段， 下表將說明這些區段。 

區段數 | 描述
------------------ | -----------
一個區段 | 此格式字串適用於所有的值。
兩個區段 | 第一個區段適用於正數值及零值，第二個區段適用於負數值。 如果要格式化的數字為負數，但依照第二個區段的格式四捨五入之後成為零，則產生的零會依照第一個區段來格式化。
三個區段 | 第一個區段適用於正數值，第二個區段適用於負數值，而第三個區段則適用於零值。 第二個區段可留白 (分號之間沒有任何內容)，此時第一個區段將套用到所有非零值。 如果要格式化的數字不是零，但依照第一個或第二個區段的格式四捨五入之後成為零，則產生的零會依照第三個區段來格式化。

區段分隔符號會在最終值已格式化時，忽略任何事先存在而與數值相關的格式。 例如，負數值在使用區段分隔符號時永遠不以負號來顯示。 如果您想要最終的格式化值具有負號，您應該明確包含負號做為自訂格式規範的一部分。 

下列範例會使用 ";" 格式規範，以不同方式格式化正數、負數和零。

```csharp
double posValue = 1234;
double negValue = -1234;
double zeroValue = 0;

string fmt2 = "##;(##)";
string fmt3 = "##;(##);**Zero**";

Console.WriteLine(posValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue));    
// Displays 1234

Console.WriteLine(negValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue));    
// Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3)); 
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue));
// Displays **Zero**
```

```vb
Dim posValue As Double = 1234
Dim negValue As Double = -1234
Dim zeroValue As Double = 0

Dim fmt2 As String = "##;(##)"
Dim fmt3 As String = "##;(##);**Zero**"

Console.WriteLine(posValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue))    
' Displays 1234

Console.WriteLine(negValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue))    
' Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3))  
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue))
' Displays **Zero**
```

## <a name="notes"></a>備註

### <a name="floatingpoint-infinities-and-nan"></a>無限浮點數和 NaN

不論格式字串為何，如果 [Single](xref:System.Single) 或 [Double](xref:System.Double) 浮點類型的值為正無限大、負無限大或不是數字 (NaN)，則格式化後的字串會分別是 [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol)、[NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) 或 [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) 屬性的值 (這些屬性由目前適用的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件所指定)。 

### <a name="rounding-and-fixedpoint-format-strings"></a>四捨五入和定點格式字串

如果是定點格式字串 (即不含科學標記法格式字元的格式字串)，則數字會四捨五入成與小數點右邊之數字預留位置一樣多的小數位數。 如果格式字串不包含小數點，數值四捨五入至最接近的整數。 如果數值有比小數點左邊的數字預留位置還要多的位數，額外位數會緊接第一個數字預留位置之前複製到輸出字串。

## <a name="example"></a>範例

下列範例示範兩個自訂數值格式字串。 在這兩個範例中，數字預留位置 (#) 會顯示數值資料，而所有其他字元則會複製到結果字串中。

```csharp
double number1 = 1234567890;
string value1 = number1.ToString("(###) ###-####");
Console.WriteLine(value1);

int number2 = 42;
string value2 = number2.ToString("My Number = #");
Console.WriteLine(value2);
// The example displays the following output:
//       (123) 456-7890
//       My Number = 42
```

```vb
Dim number1 As Double = 1234567890
Dim value1 As String = number1.ToString("(###) ###-####")
Console.WriteLine(value1)

Dim number2 As Integer = 42
Dim value2 As String = number2.ToString("My Number = #")
Console.WriteLine(value2)
' The example displays the following output:
'       (123) 456-7890
'       My Number = 42
```

## <a name="see-also"></a>另請參閱

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[格式化類型](formatting-types.md)

[標準數值格式字串](standard-numeric.md)

[如何：使用前置零填補數字](pad-number.md)

[複合格式](composite-format.md)




<!--HONumber=Nov16_HO1-->


