---
title: ".NET 中的規則運算式"
description: ".NET 中的規則運算式"
keywords: ".NET、.NET Core"
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d1a640cf-09ca-48f7-800c-a627a6d549c9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: e9ae9cb47955fb926507be32afb875efd3260ce3

---

# <a name="regular-expressions-in-net"></a>.NET 中的規則運算式

規則運算式提供功能強大、彈性且有效率的方法來處理文字。 規則運算式的廣泛模式比對標記法可讓您快速剖析大量文字，以尋找特定的字元模式；驗證文字，以確保其符合預先定義的模式 (例如電子郵件地址)；擷取、編輯、取代或刪除文字子字串；以及將擷取的字串加入集合中，以產生報告。 對許多處理字串或剖析大型文字區塊的應用程式而言，規則運算式是不可或缺的工具。

## <a name="how-regular-expressions-work"></a>規則運算式的運作方式

使用規則運算式來處理文字的核心是規則運算式引擎，以 .NET 中的 [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 物件來表示。 使用規則運算式來處理文字時，至少需要提供規則運算式引擎以及下列兩個資訊項目：

* 要在文字中識別的規則運算式模式。 
  
  在 .NET 中，規則運算式模式是以特殊的語法或語言來定義，其相容於 Perl 5 規則運算式，並新增一些其他功能，例如由右至左比對。 如需詳細資訊，請參閱[規則運算式語言 - 快速參考](quick-ref.md)。
  
* 要為規則運算式模式剖析的文字。

[Regex](xref:System.Text.RegularExpressions.Regex) 類別的方法可讓您執行下列作業：

* 呼叫 [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法，以判定規則運算式模式是否出現在輸入文字中。 如需使用 [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法來驗證文字的範例，請參閱[如何：確認字串是否為有效的電子郵件格式](verify-format.md)。

* 呼叫 [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 或 [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法，以擷取符合規則運算式模式的所有文字。 前一個方法會傳回 [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) 物件，提供相符文字的相關資訊。 後者傳回 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件，其包含在每個已剖析文字中找到之相符項目的一個 [System.Text.RegularExpressions.Match](xref:System.Text.RegularExpressions.Match) 物件。 

* 呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法，以取代符合規則運算式模式的文字。 如需使用 [Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法來變更日期格式，以及移除字串中無效字元的範例，請參閱[如何：從字串中刪除無效的字元](strip-characters.md)和[規則運算式範例：變更日期格式](changing-formats.md)。

如需規則運算式物件模型概觀，請參閱[規則運算式物件模型](object-model.md)。

如需規則運算式語言的詳細資訊，請參閱[規則運算式語言 - 快速參考](quick-ref.md)。

## <a name="regular-expression-examples"></a>規則運算式範例

[String](xref:System.String) 類別包含數種字串搜尋和取代方法，可供您在大型字串中尋找常值字串時使用。 當您想要在大型字串中尋找數個子字串時，或是當您想要識別字串中的模式時，規則運算式最為好用，如下列範例所示。 

### <a name="example-1-replacing-substrings"></a>範例 1：取代子字串

假設郵寄清單包含的名稱有時候會包括稱謂 (Mr.、Mrs.、Miss 或 Ms.) 以及姓名。 當您從清單產生信封標籤時，如果不想包括稱謂，就可以使用規則運算式來移除稱謂，如下列範例所示。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(Mr\\.? |Mrs\\.? |Miss |Ms\\.? )";
      string[] names = { "Mr. Henry Hunt", "Ms. Sara Samuels", 
                         "Abraham Adams", "Ms. Nicole Norris" };
      foreach (string name in names)
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty));
   }
}
// The example displays the following output:
//    Henry Hunt
//    Sara Samuels
//    Abraham Adams
//    Nicole Norris
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(Mr\.? |Mrs\.? |Miss |Ms\.? )"
      Dim names() As String = { "Mr. Henry Hunt", "Ms. Sara Samuels", _
                                "Abraham Adams", "Ms. Nicole Norris" }
      For Each name As String In names
         Console.WriteLine(Regex.Replace(name, pattern, String.Empty))
      Next                                
   End Sub
End Module
' The example displays the following output:
'    Henry Hunt
'    Sara Samuels
'    Abraham Adams
'    Nicole Norris
```

規則運算式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 會比對所出現的任何 "Mr "、"Mr. "、"Mrs "、"Mrs. "、"Miss "、"Ms 或 "Ms. "。 呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法會以 [String.Empty](xref:System.String.Empty) 取代相符的字串；換句話說，就是從原始字串中移除它。

### <a name="example-2-identifying-duplicated-words"></a>範例 2：識別重複的文字

不小心重複文字是作者常犯的錯誤。 規則運算式可用來識別重複的文字，如下列範例所示。

```csharp
using System;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string pattern = @"\b(\w+?)\s\1\b";
      string input = "This this is a nice day. What about this? This tastes good. I saw a a dog.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", 
                           match.Value, match.Groups[1].Value, match.Index);
   }
}
// The example displays the following output:
//       This this (duplicates 'This)' at position 0
//       a a (duplicates 'a)' at position 66
```

```vb
Imports System.Text.RegularExpressions

Module modMain
   Public Sub Main()
      Dim pattern As String = "\b(\w+?)\s\1\b"
      Dim input As String = "This this is a nice day. What about this? This tastes good. I saw a a dog."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine("{0} (duplicates '{1}') at position {2}", _
                           match.Value, match.Groups(1).Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       This this (duplicates 'This)' at position 0
'       a a (duplicates 'a)' at position 66
```

規則運算式模式 `\b(\w+?)\s\1\b` 可解譯如下：

語法 | 意義
------ | -------
`\b` | 從字緣開始。
`(\w+?)` | 比對一或多個字元，但字元數愈少愈好。 這些一起構成可稱之為 `\1` 的群組。
`\s` | 比對空白字元。
`\1` | 比對等同於名為 `\1` 之群組的子字串。
`\b` | 比對字邊界。

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法是以設為 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 的規則運算式選項呼叫。 因此，比對作業不區分大小寫，而且此範例會將子字串 "This this" 視為重複。

請注意，輸入字串包括子字串 "this? This"。 不過，因為中間有標點符號，所以不會將其視為重複。

### <a name="example-3-dynamically-building-a-culturesensitive-regular-expression"></a>範例 3：動態建立區分文化特性的規則運算式

下列範例說明規則運算式結合 .NET 全球化功能所提供的彈性，功能有多麼強大。 它會使用 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件來判定系統目前文化特性中的幣值格式， 然後利用該資訊動態建構可從文字擷取幣值的規則運算式。 針對每個比對，它會擷取僅包含數值字串的子群組，將其轉換成[十進位](xref:System.Decimal)值，並計算執行總計。 

```csharp
using System;
using System.Collections.Generic;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define text to be parsed.
      string input = "Office expenses on 2/13/2008:\n" + 
                     "Paper (500 sheets)                      $3.95\n" + 
                     "Pencils (box of 10)                     $1.00\n" + 
                     "Pens (box of 10)                        $4.49\n" + 
                     "Erasers                                 $2.19\n" + 
                     "Ink jet printer                        $69.95\n\n" + 
                     "Total Expenses                        $ 81.58\n"; 

      // Get current culture's NumberFormatInfo object.
      NumberFormatInfo nfi = CultureInfo.CurrentCulture.NumberFormat;
      // Assign needed property values to variables.
      string currencySymbol = nfi.CurrencySymbol;
      bool symbolPrecedesIfPositive = nfi.CurrencyPositivePattern % 2 == 0;
      string groupSeparator = nfi.CurrencyGroupSeparator;
      string decimalSeparator = nfi.CurrencyDecimalSeparator;

      // Form regular expression pattern.
      string pattern = Regex.Escape( symbolPrecedesIfPositive ? currencySymbol : "") + 
                       @"\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + 
                       Regex.Escape(decimalSeparator) + "[0-9]+)?)" + 
                       (! symbolPrecedesIfPositive ? currencySymbol : ""); 
      Console.WriteLine( "The regular expression pattern is:");
      Console.WriteLine("   " + pattern);      

      // Get text that matches regular expression pattern.
      MatchCollection matches = Regex.Matches(input, pattern, 
                                              RegexOptions.IgnorePatternWhitespace);               
      Console.WriteLine("Found {0} matches.", matches.Count); 

      // Get numeric string, convert it to a value, and add it to List object.
      List<decimal> expenses = new List<Decimal>();

      foreach (Match match in matches)
         expenses.Add(Decimal.Parse(match.Groups[1].Value));      

      // Determine whether total is present and if present, whether it is correct.
      decimal total = 0;
      foreach (decimal value in expenses)
         total += value;

      if (total / 2 == expenses[expenses.Count - 1]) 
         Console.WriteLine("The expenses total {0:C2}.", expenses[expenses.Count - 1]);
      else
         Console.WriteLine("The expenses total {0:C2}.", total);
   }  
}
// The example displays the following output:
//       The regular expression pattern is:
//          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
//       Found 6 matches.
//       The expenses total $81.58.
```

```vb
Imports System.Collections.Generic
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Module Example
   Public Sub Main()
      ' Define text to be parsed.
      Dim input As String = "Office expenses on 2/13/2008:" + vbCrLf + _
                            "Paper (500 sheets)                      $3.95" + vbCrLf + _
                            "Pencils (box of 10)                     $1.00" + vbCrLf + _
                            "Pens (box of 10)                        $4.49" + vbCrLf + _
                            "Erasers                                 $2.19" + vbCrLf + _
                            "Ink jet printer                        $69.95" + vbCrLf + vbCrLf + _
                            "Total Expenses                        $ 81.58" + vbCrLf
      ' Get current culture's NumberFormatInfo object.
      Dim nfi As NumberFormatInfo = CultureInfo.CurrentCulture.NumberFormat
      ' Assign needed property values to variables.
      Dim currencySymbol As String = nfi.CurrencySymbol
      Dim symbolPrecedesIfPositive As Boolean = CBool(nfi.CurrencyPositivePattern Mod 2 = 0)
      Dim groupSeparator As String = nfi.CurrencyGroupSeparator
      Dim decimalSeparator As String = nfi.CurrencyDecimalSeparator

      ' Form regular expression pattern.
      Dim pattern As String = Regex.Escape(CStr(IIf(symbolPrecedesIfPositive, currencySymbol, ""))) + _
                              "\s*[-+]?" + "([0-9]{0,3}(" + groupSeparator + "[0-9]{3})*(" + _
                              Regex.Escape(decimalSeparator) + "[0-9]+)?)" + _
                              CStr(IIf(Not symbolPrecedesIfPositive, currencySymbol, "")) 
      Console.WriteLine("The regular expression pattern is: ")
      Console.WriteLine("   " + pattern)      

      ' Get text that matches regular expression pattern.
      Dim matches As MatchCollection = Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)               
      Console.WriteLine("Found {0} matches. ", matches.Count)

      ' Get numeric string, convert it to a value, and add it to List object.
      Dim expenses As New List(Of Decimal)

      For Each match As Match In matches
         expenses.Add(Decimal.Parse(match.Groups.Item(1).Value))      
      Next

      ' Determine whether total is present and if present, whether it is correct.
      Dim total As Decimal
      For Each value As Decimal In expenses
         total += value
      Next

      If total / 2 = expenses(expenses.Count - 1) Then
         Console.WriteLine("The expenses total {0:C2}.", expenses(expenses.Count - 1))
      Else
         Console.WriteLine("The expenses total {0:C2}.", total)
      End If   
   End Sub
End Module
' The example displays the following output:
'       The regular expression pattern is:
'          \$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)
'       Found 6 matches.
'       The expenses total $81.58.
```

在目前文化特性為 English - United States (en-US) 的電腦上，此範例會動態建立規則運算式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。 此規則運算式模式可解譯如下：

語法 | 意義
------ | -------
`\$` | 在輸入字串中尋找單獨出現的貨幣符號 ($)。 規則運算式模式字串包含反斜線，表示貨幣符號要解譯為字面意義，而不是規則運算式錨點。 ($ 符號單獨出現表示規則運算式引擎應該嘗試在字串結尾處開始其比對。)為了確保目前文化特性的貨幣符號不會誤譯為規則運算式符號，此範例呼叫 [Escape](xref:System.Text.RegularExpressions.Regex.Escape(System.String)) 方法以逸出字元。
`\s*` | 尋找出現零或多次的空格字元。
`[-+]?` | 尋找出現一或多次的正號或負號。
`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)` | 此運算式外面括號將其定義成擷取群組或子運算式。 如果找到相符項目，從 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性傳回之 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中的第二個 [Group](xref:System.Text.RegularExpressions.Group) 物件，擷取此部分比對字串的相關資訊。 (集合中的第一個項目代表整個比對。)
`[0-9]{0,3}` | 尋找出現零到三次的十進位數字 0 到 9。
`(,[0-9]{3})*` | 尋找出現零或多次、後面接三個十進位數字的群組分隔符號。
`\.` | 尋找單次出現的十進位分隔符號。
`[0-9]+` | 尋找一或多個十進位數字。
`(\.[0-9]+)?` | 尋找出現零或一次、後接至少一個十進位數字的十進位分隔符號。

## <a name="related-topics"></a>相關主題

標題 | 說明
----- | -----------
[規則運算式語言 - 快速參考](quick-ref.md) | 提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。
[規則運算式物件模型](object-model.md) | 提供資訊和程式碼範例，說明如何使用規則運算式類別。
[規則運算式行為的詳細資料](regex-behavior.md) | 提供 .NET 規則運算式之功能和行為的相關資訊。
[規則運算式範例](regex-examples.md) | 提供程式碼範例，以說明規則運算式的一般用法。


## <a name="reference"></a>參考資料

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex)




<!--HONumber=Nov16_HO1-->


