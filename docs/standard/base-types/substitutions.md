---
title: "規則運算式中的替代項目"
description: "規則運算式中的替代項目"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0fded615-1021-4468-a644-b491814305c6
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3e02d18d6566c67c7fff7003671f340f97b0dfce

---

# <a name="substitutions-in-regular-expressions"></a>規則運算式中的替代項目

替代是指只有在取代模式內才能辨識的語言項目。 這些項目使用規則運算式模式定義要取代輸入字串中相符文字的全部或部分文字。 取代模式可以包含一個或多個替代，以及常值字元。 取代模式會將多載提供給具有 *replacement* 參數的 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法，以及提供給 [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) 方法。 這些方法會將符合的模式取代為 *replacement* 參數所定義的模式。

.NET 會定義下表列出的替代項目。

替代 | 描述
------------ | ----------- 
**$**_number_ | 包括在取代字串中與 *number* 所指定之擷取群組相符的最後一個子字串，其中 *number* 是十進位值。 如需詳細資訊，請參閱[替代編號群組](#substituting-a-numbered-group)。
**${**_name_**}** | 包括在取代字串中與 **(?<**_name_**>)** 所指定之具名群組相符的最後一個子字串。 如需詳細資訊，請參閱[替代具名群組](#substituting-a-named-group)。
**$$** | 取代字串中包括單一 "$" 常值。 如需詳細資訊，請參閱[替代 "$" 符號](#substituting-a--character)。
**$&** | 取代字串中包括整個相符項目的複本。 如需詳細資訊，請參閱[替代整個相符項目](#substituting-the-entire-match)。
**$`** | 取代字串中包括輸入字串中相符項目之前的所有文字。 如需詳細資訊，請參閱[替代相符項目前的文字](#substituting-the-text-before-the-match)。
**$'** | 取代字串中包括輸入字串中相符項目之後的所有文字。 如需詳細資訊，請參閱[替代相符項目後的文字](#substituting-the-text-after-the-match)。 
**$+** | 將上一個擷取的群組加入取代字串中。 如需詳細資訊，請參閱[替代上一個擷取的群組](#substituting-the-last-captured-group)。
**$_** | 取代字串中包括整個輸入字串。 如需詳細資訊，請參閱[替代整個輸入字串](#substituting-the-entire-input-string)。
 
## <a name="substitution-elements-and-replacement-patterns"></a>替代項目與取代模式

替代是取代模式中唯一能夠辨認的特殊建構。 不支援其他規則運算式語言項目，包括逸出字元和符合任何字元的句號 (**.**)。 同樣的，替代語言項目只有在取代模式中才能辨識，而且在規則運算式模式中永遠無效。 

唯一能夠在規則運算式模式或替代項目中出現的字元是 **$** 字元，不過它在這兩種內容中的意義不同。 在規則運算式模式中，**$** 是比對字串結尾的錨點。 在取代模式中，**$** 表示替代項目的開頭。 

> [!NOTE]
> 如需規則運算式內類似取代模式的功能，請使用反向參考。 如需反向參考的詳細資訊，請參閱[反向參考建構](backreference.md)。
 
## <a name="substituting-a-numbered-group"></a>替代編號群組

**$**_number_ 語言項目包括取代字串中與 number 擷取群組相符的最後一個子字串，其中 *number* 是擷取群組的索引。 例如，取代模式 `$1` 表示第一個擷取的群組將取代相符的子字串。 如需編號擷取群組的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

**$** 後面接著的所有數字都會解譯為屬於 number 群組。 如果這不是您的目的，可以改為替代具名群組。 例如，您可以使用取代字串 **${1}1** 而非 **$11**，將取代字串定義為第一個擷取之群組的值連同數字 "1"。 如需詳細資訊，請參閱[替代具名群組](#substituting-a-named-group)。 

未使用 **(?<**_name-**>)** 語法明確指派名稱的擷取群組，會從 1 開始由左至右編號。 具名群組是從最後一個未命名群組的索引加一開始，由左至右編號。 例如，在規則運算式 `(\w)(?<digit>\d)` 中，`digit` 具名群組的索引為 2。

如果 *number* 沒有指定在規則運算式模式中定義的有效擷取群組，就會將 **$**_number_ 解譯為用以取代每個相符項目的常值字元序列。

下列範例使用 **$**_number_ 替代項目，從十進位值中去除貨幣符號。 它會移除在貨幣數值的開頭或結尾找到的貨幣符號，並且辨識兩種最常見的十進位分隔符號 ("." 和 ",")。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "$1";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "$1"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

規則運算式模式 `\p{Sc}*(\s?\d+[.,]?\d*)\p{Sc}*` 的定義如下表所示。

模式 | 描述
------- | -----------
`\p{Sc}*` | 比對零個或多個貨幣符號字元。
`\s?` | 比對零個或一個空白字元。
`\d+` | 比對一個或多個十進位數字。
`[.,]?` | 比對零個或一個句號或逗號。
`\d*` | 比對零個或多個十進位數字。
`(\s?\d+[.,]?\d*)` | 比對空白字元後面接著一個或多個十進位數字，再接零個或一個句號或逗號，最後再接零個或多個十進位數字。 這是第一個擷取群組。 由於取代模式為 `$1`，因此呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法會將整個相符的子字串取代為這個擷取的群組。 
 
## <a name="substituting-a-named-group"></a>替代具名群組

**${**_name_**}** 語言項目會替代與 *name* 擷取群組相符的最後一個子字串，其中 *name*是由 **(?<**_name_**>)** 語言項目定義之擷取群組的名稱。 如需具名擷取群組的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

如果 *name* 未指定規則運算式模式中定義的有效具名擷取群組，卻包含數字，則會將 **${**_name_**}** 解譯為編號的群組。 

如果 *name* 未指定規則運算式模式中定義的有效具名擷取群組，也未定義有效的編號擷取群組，則會將 **${**_name_**}** 解譯為用以取代每個相符項目的常值字元序列。

下列範例使用 **${**_name_**}** 替代項目，從十進位值中去除貨幣符號。 它會移除在貨幣數值的開頭或結尾找到的貨幣符號，並且辨識兩種最常見的十進位分隔符號 ("." 和 ",")。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*";
      string replacement = "${amount}";
      string input = "$16.32 12.19 £16.29 €18.29  €18,29";
      string result = Regex.Replace(input, pattern, replacement);
      Console.WriteLine(result);
   }
}
// The example displays the following output:
//       16.32 12.19 16.29 18.29  18,29
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\p{Sc}*(?<amount>\s?\d+[.,]?\d*)\p{Sc}*"
      Dim replacement As String = "${amount}"
      Dim input As String = "$16.32 12.19 £16.29 €18.29  €18,29"
      Dim result As String = Regex.Replace(input, pattern, replacement)
      Console.WriteLine(result)
   End Sub
End Module
' The example displays the following output:
'       16.32 12.19 16.29 18.29  18,29
```

規則運算式模式 `\p{Sc}*(?<amount>\s?\d[.,]?\d*)\p{Sc}*` 的定義如下表所示。 

模式 | 描述
------- | -----------
`\p{Sc}*` | 比對零個或多個貨幣符號字元。
`\s?` | 比對零個或一個空白字元。
`\d+` | 比對一個或多個十進位數字。
`[.,]?` | 比對零個或一個句號或逗號。
`\d*` | 比對零個或多個十進位數字。
`(?<amount>\s?\d[.,]?\d*)` | 比對空白字元，後面接著一個或多個十進位數字，再接零個或一個句號或逗號，最後再接零個或多個十進位數字。 這是名為 amount 的擷取群組。 由於取代模式為 `${amount}`，因此呼叫 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法會將整個相符的子字串取代為這個擷取的群組。 
 
## <a name="substituting-a-character"></a>替代 $ 字元

**$$** 替代項目會在取代的字串中插入常值 "$" 字元。 

下列範例會使用 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件決定目前文化特性的貨幣符號，以及它在貨幣字串中的位置。 然後，它會動態建置規則運算式模式和取代模式。 如果這個範例是在目前文化特性為 zh-TW 的電腦上執行，則會產生規則運算式模式 `\b(\d+)(\.(\d+))?` 以及取代模式 `$$ $1$2`。 取代模式會將相符的文字取代為貨幣符號和空格，後面接著第一個和第二個擷取群組。

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Define array of decimal values.
      string[] values= { "16.35", "19.72", "1234", "0.99"};
      // Determine whether currency precedes (True) or follows (False) number.
      bool precedes = NumberFormatInfo.CurrentInfo.CurrencyPositivePattern % 2 == 0;
      // Get decimal separator.
      string cSeparator = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator;
      // Get currency symbol.
      string symbol = NumberFormatInfo.CurrentInfo.CurrencySymbol;
      // If symbol is a "$", add an extra "$".
      if (symbol == "$") symbol = "$$";

      // Define regular expression pattern and replacement string.
      string pattern = @"\b(\d+)(" + cSeparator + @"(\d+))?"; 
      string replacement = "$1$2";
      replacement = precedes ? symbol + " " + replacement : replacement + " " + symbol;
      foreach (string value in values)
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement));
   }
}
// The example displays the following output:
//       16.35 --> $ 16.35
//       19.72 --> $ 19.72
//       1234 --> $ 1234
//       0.99 --> $ 0.99
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Define array of decimal values.
      Dim values() As String = { "16.35", "19.72", "1234", "0.99"}
      ' Determine whether currency precedes (True) or follows (False) number.
      Dim precedes As Boolean = (NumberFormatInfo.CurrentInfo.CurrencyPositivePattern Mod 2 = 0)
      ' Get decimal separator.
      Dim cSeparator As String = NumberFormatInfo.CurrentInfo.CurrencyDecimalSeparator
      ' Get currency symbol.
      Dim symbol As String = NumberFormatInfo.CurrentInfo.CurrencySymbol
      ' If symbol is a "$", add an extra "$".
      If symbol = "$" Then symbol = "$$"

      ' Define regular expression pattern and replacement string.
      Dim pattern As String = "\b(\d+)(" + cSeparator + "(\d+))?" 
      Dim replacement As String = "$1$2"
      replacement = If(precedes, symbol + " " + replacement, replacement + " " + symbol)
      For Each value In values
         Console.WriteLine("{0} --> {1}", value, Regex.Replace(value, pattern, replacement))
      Next
   End Sub
End Module
' The example displays the following output:
'       16.35 --> $ 16.35
'       19.72 --> $ 19.72
'       1234 --> $ 1234
'       0.99 --> $ 0.99
```

規則運算式模式 `\b(\d+)(\.(\d+))?` 的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 在字邊界的開頭開始比對。
`(\d+)` | 比對一個或多個十進位數字。 這是第一個擷取群組。
`\.` | 比對句號 (十進位分隔符號)。
`(\d+)` | 比對一個或多個十進位數字。 這是第三個擷取群組。
`(\.(\d+))?` | 比對零個或一個句號，後面接著一個或多個十進位數字。 這是第二個擷取群組。
 
## <a name="substituting-the-entire-match"></a>替代整個相符項目

**$&** 替代項目會在取代字串中包含整個相符項目。 通常，它會用來將子字串加入至相符字串的開頭或結尾。 例如，`($&)` 取代模式會在每個相符項目的開頭和結尾加上括號。 如果沒有相符項目，**$&** 替代項目就不會有任何作用。

下列範例會使用 **$&** 替代項目，在字串陣列中所儲存的書名開頭和結尾加上引號。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\w+\s?)+$";
      string[] titles = { "A Tale of Two Cities", 
                          "The Hound of the Baskervilles", 
                          "The Protestant Ethic and the Spirit of Capitalism", 
                          "The Origin of Species" };
      string replacement = "\"$&\"";
      foreach (string title in titles)
         Console.WriteLine(Regex.Replace(title, pattern, replacement));
   }
}
// The example displays the following output:
//       "A Tale of Two Cities"
//       "The Hound of the Baskervilles"
//       "The Protestant Ethic and the Spirit of Capitalism"
//       "The Origin of Species"
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\w+\s?)+$"
      Dim titles() As String = { "A Tale of Two Cities", _
                                 "The Hound of the Baskervilles", _
                                 "The Protestant Ethic and the Spirit of Capitalism", _
                                 "The Origin of Species" }
      Dim replacement As String = """$&"""
      For Each title As String In titles
         Console.WriteLine(Regex.Replace(title, pattern, replacement))
      Next  
   End Sub
End Module
' The example displays the following output:
'       "A Tale of Two Cities"
'       "The Hound of the Baskervilles"
'       "The Protestant Ethic and the Spirit of Capitalism"
'       "The Origin of Species"
```

規則運算式模式 `^(\w+\s?)+$` 的定義如下表所示。

模式 | 描述
------- | -----------
`^` | 在輸入字串的開頭開始比對。
`(\w+\s?)+` | 一次或多次比對一個或多個文字字元後面接著零或一個空白字元的模式。 
`$` | 比對輸入字串的結尾。

`"$&"` 取代模式會在每個相符項目的開頭和結尾加上常值引號。

## <a name="substituting-the-text-before-the-match"></a>替代相符項目前的文字

**$`** substitution replaces the matched string with the entire input string before the match. That is, it duplicates the input string up to the match while removing the matched text. Any text that follows the matched text is unchanged in the result string. If there are multiple matches in an input string, the replacement text is derived from the original input string, rather than from the string in which text has been replaced by earlier matches. (The example provides an illustration.) If there is no match, the **$`** 替代項目就沒有任何作用。

下列範例會使用規則運算式模式 `\d+`，比對輸入字串中的一或多個十進位數字序列。 取代字串 **$`** 會以相符文字前的文字取代這些數字。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$`";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);

      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$`"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

在這個範例中，輸入字串 `"aa1bb2cc3dd4ee5"` 包含五個相符項目。 下表將說明 $` 替代項目如何讓規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在「結果字串」一欄中。

比對 | 位置 | 相符項目前的字串 | 結果字串
----- | -------- | ------------------- | -------------
1 | 2 | aa | aa**aa**bb2cc3dd4ee5
2 | 5 | aa1bb | aaaabb**aa1bb**cc3dd4ee5
3 | 8 | aa1bb2cc | aaaabbaa1bbcc**aa1bb2cc**dd4ee5
4 | 11 | aa1bb2cc3dd | aaaabbaa1bbccaa1bb2ccdd**aa1bb2cc3dd**ee5
5 | 14 | aa1bb2cc3dd4ee | aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddee **aa1bb2cc3dd4ee**
 
## <a name="substituting-the-text-after-the-match"></a>替代相符項目後的文字

**$'** 替代項目會以相符項目後的整個輸入字串取代相符的字串。 也就是說，它在移除相符文字的同時，也會在相符項目後複製輸入字串。 在結果字串中，相符文字之前的任何文字都會保持不變。 如果沒有相符項目，**$'** 替代項目就不會有任何作用。

下列範例會使用規則運算式模式 `\d+`，比對輸入字串中的一或多個十進位數字序列。 取代字串 **$'** 會以相符項目後的文字取代這些數字。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "aa1bb2cc3dd4ee5";
      string pattern = @"\d+";
      string substitution = "$'";
      Console.WriteLine("Matches:");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
      Console.WriteLine("Input string:  {0}", input);
      Console.WriteLine("Output string: " + 
                        Regex.Replace(input, pattern, substitution));
   }
}
// The example displays the following output:
//    Matches:
//       1 at position 2
//       2 at position 5
//       3 at position 8
//       4 at position 11
//       5 at position 14
//    Input string:  aa1bb2cc3dd4ee5
//    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "aa1bb2cc3dd4ee5"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$'"
      Console.WriteLine("Matches:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
      Console.WriteLine("Input string:  {0}", input)
      Console.WriteLine("Output string: " + _
                        Regex.Replace(input, pattern, substitution))
   End Sub
End Module
' The example displays the following output:
'    Matches:
'       1 at position 2
'       2 at position 5
'       3 at position 8
'       4 at position 11
'       5 at position 14
'    Input string:  aa1bb2cc3dd4ee5
'    Output string: aaaabbaa1bbccaa1bb2ccddaa1bb2cc3ddeeaa1bb2cc3dd4ee
```

在這個範例中，輸入字串 `"aa1bb2cc3dd4ee5"` 包含五個相符項目。 下表將說明 **$'** 替代項目如何讓規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在「結果字串」一欄中。

比對 | 位置 | 相符項目前的字串 | 結果字串
----- | -------- | ------------------- | -------------
1 | 2 | bb2cc3dd4ee5 | aa**bb2cc3dd4ee5**bb2cc3dd4ee5
2 | 5 | cc3dd4ee5 | aabb2cc3dd4ee5bb**cc3dd4ee5**cc3dd4ee5
3 | 8 | dd4ee5 | aabb2cc3dd4ee5bbcc3dd4ee5cc**dd4ee5**dd4ee5
4 | 11 | ee5 | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5dd**ee5**ee5
5 | 14 | [String.Empty](xref:System.String.Empty) | aabb2cc3dd4ee5bbcc3dd4ee5ccdd4ee5ddee5ee
 
## <a name="substituting-the-last-captured-group"></a>替代上一個擷取的群組

**$+** 替代項目會以上一個擷取的群組取代相符的字串。 若未擷取任何群組，或上一個擷取的群組值是 [String.Empty](xref:System.String.Empty)，**$+** 替代項目就沒有任何作用。

下列範例會識別字串中的重複文字，並使用 **$+** 替代項目將這些文字取代為單次出現的文字。 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 選項是用來確保只有大小寫不同的相同單字，都會視為重複項目。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s\1\b";
      string substitution = "$+";
      string input = "The the dog jumped over the fence fence.";
      Console.WriteLine(Regex.Replace(input, pattern, substitution, 
                        RegexOptions.IgnoreCase));
   }
}
// The example displays the following output:
//      The dog jumped over the fence.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s\1\b"
      Dim substitution As String = "$+"
      Dim input As String = "The the dog jumped over the fence fence."
      Console.WriteLine(Regex.Replace(input, pattern, substitution, _
                                      RegexOptions.IgnoreCase))
   End Sub
End Module
' The example displays the following output:
'      The dog jumped over the fence.
```

規則運算式模式 `\b(\w+)\s\1\b` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 開始字緣比對。
`(\w+)` | 比對一個或多個文字字元。 這是第一個擷取群組。
`\s` | 比對空白字元。
`\1` | 比對第一個擷取的群組。
`\b` | 結束字緣比對。
 
## <a name="substituting-the-entire-input-string"></a>替代整個輸入字串

**$_** 替代項目會將相符的字串取代為整個輸入字串。 也就是說，它會移除相符的文字，並會以整個字串來取代，包括相符的文字。

下列範例會比對輸入字串中的一個或多個十進位數字。 它會使用 **$_** 替代項目，以整個輸入字串來取代它們。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "ABC123DEF456";
      string pattern = @"\d+";
      string substitution = "$_";
      Console.WriteLine("Original string:          {0}", input);
      Console.WriteLine("String with substitution: {0}", 
                        Regex.Replace(input, pattern, substitution));      
   }
}
// The example displays the following output:
//       Original string:          ABC123DEF456
//       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "ABC123DEF456"
      Dim pattern As String = "\d+"
      Dim substitution As String = "$_"
      Console.WriteLine("Original string:          {0}", input)
      Console.WriteLine("String with substitution: {0}", _
                        Regex.Replace(input, pattern, substitution))      
   End Sub
End Module
' The example displays the following output:
'       Original string:          ABC123DEF456
'       String with substitution: ABCABC123DEF456DEFABC123DEF456
```

在這個範例中，輸入字串 `"ABC123DEF456"` 包含兩個相符項目。 下表將說明 **$_** 替代項目如何讓規則運算式引擎取代輸入字串中的每個相符項目。 插入的文字會以粗體顯示在「結果字串」一欄中。

比對 | 位置 | 相符項目前的字串 | 結果字串
----- | -------- | ------------------- | -------------
1 | 3 | 123 | ABC**ABC123DEF456**DEF456
2 | 5 | 456 | ABCABC123DEF456DEF**ABC123DEF456**
 
## <a name="see-also"></a>請參閱

[規則運算式語言 - 快速參考](quick-ref.md)




<!--HONumber=Nov16_HO1-->


