---
title: "規則運算式中的字元類別"
description: "規則運算式中的字元類別"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c7a9305f-7144-4fe8-80e8-a727bf7d223f
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ae677af2590636fd144d8978a3500c37f9d33615
ms.lasthandoff: 03/03/2017

---

# <a name="character-classes-in-regular-expressions"></a>規則運算式中的字元類別

字元類別會定義一組字元，其中任何字元都可在輸入字串中出現，以便讓比對成功。 .NET 中的規則運算式語言支援下列字元類別：

* 正字元群組。 輸入字串中的字元必須符合指定字元集的其中一個字元。 如需詳細資訊，請參閱[正字元群組](#positive-character-group--)。

* 負字元群組。 輸入字串中的字元不得符合指定字元集的其中一個字元。 如需詳細資訊，請參閱[負字元群組](#negative-character-group-)。

* 任何字元。 . 在規則運算式中的 . (點或句號) 字元是萬用字元，可符合 **\n** 以外的任何字元。 如需詳細資訊，請參閱[任何字元](#any-character-)。 

* 一般 Unicode 分類或具名區塊。 輸入字串中的字元必須是特定 Unicode 分類的成員，或者必須落在 Unicode 字元的連續範圍內，比對才會成功。 如需詳細資訊，請參閱 [Unicode 分類或 Unicode 區塊](#unicode-category-or-unicode-block-p)。

* 負的一般 Unicode 分類或是具名區塊。 輸入字串中的字元不得是特定 Unicode 分類的成員，或者不得落在 Unicode 字元的連續範圍內，比對才會成功。 如需詳細資訊，請參閱[負 Unicode 分類或 Unicode 區塊](#negative-unicode-category-or-unicode-block-p)。

* 文字字元。 輸入字串中的字元可以隸屬於任何適用於文字字元的 Unicode 分類。 如需詳細資訊，請參閱[文字字元](#word-character-w)。

* 非文字字元。 輸入字串中的字元可以隸屬於任何非文字字元的 Unicode 分類。 如需詳細資訊，請參閱[非文字字元](#non-word-character-w)。

* 空白字元。 輸入字串中的字元可以是任何 Unicode 分隔符號字元，以及任何一種控制字元。 如需詳細資訊，請參閱[空白字元](#white-space-character-s)。

* 非空白字元。 輸入字串中的字元可以是空白字元以外的任何字元。 如需詳細資訊，請參閱[非空白字元](#non-white-space-character-s)。

* 十進位數字。 輸入字串中的字元可以是歸類為 Unicode 十進位數字的任何一個數字字元。 如需詳細資訊，請參閱[十進位數字字元](#decimal-digit-character-d)。

* 非十進位數字。 輸入字串中的字元可以是 Unicode 十進位數字以外的任何字元。 如需詳細資訊，請參閱[非數字字元](#non-digit-character-d)。


.NET 支援字元類別減法運算式，可讓您將一組字元定義為從某個字元類別中排除另一個字元類別的結果。 如需詳細資訊，請參閱[字元類別減法](#character-class-subtraction)。

## <a name="positive-character-group--"></a>正字元群組：[ ]

正字元群組會指定一份字元清單，其中任何字元都可出現在輸入字串中，以便出現相符項目。 這份字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。 

指定個別字元清單的語法如下所示： 

[*character*_*group*]

其中 *character_group* 是為了讓比對成功而可以出現在輸入字串中的個別字元清單。 *character*_*group* 可以由一或多個常值字元、[逸出字元](escapes.md)或字元類別的任何組合所構成。 

指定字元範圍的語法如下所示：

```
[firstCharacter-lastCharacter]
```

其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。 字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。 如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。

下表列出一些包含正字元類別的常見規則運算式模式。

模式 | 描述
------- | ----------- 
`[aeiou]` | 比對所有母音。
`[\p{P}\d]` | 比對所有標點符號和十進位數字字元。
`[\s\p{P}]` | 比對所有空白字元和標點符號。
 
下列範例會定義包含字元 "a" 和 "e" 的正字元群組，因此輸入字串必須包含文字 "grey" 或 "gray" 且後面接著另一個文字，才會出現相符項目。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"gr[ae]y\s\S+?[\s\p{P}]";
      string input = "The gray wolf jumped over the grey wall.";
      MatchCollection matches = Regex.Matches(input, pattern);
      foreach (Match match in matches)
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       gray wolf
//       grey wall.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "gr[ae]y\s\S+?[\s\p{P}]"
      Dim input As String = "The gray wolf jumped over the grey wall."
      Dim matches As MatchCollection = Regex.Matches(input, pattern)
      For Each match As Match In matches
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       gray wolf
'       grey wall.
```

規則運算式 `gr[ae]y\s\S+?[\s|\p{P}]` 定義如下：

模式 | 描述
------- | ----------- 
`gr` | 比對常值字元 "gr"。
`[ae]` | 比對 "a" 或 "e"。
`y\s` | 比對後面接著空白字元的常值字元 "y"。
`\S+?` | 比對一個或多個非空白字元，但越少越好。
`[\s\p{P}]` | 比對空白字元或標點符號。
 
下列範例將比對以任何大寫字母開頭的文字。 範例將使用子運算式 `[A-Z]` 表示從 A 到 Z 的大寫字母範圍。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b[A-Z]\w*\b";
      string input = "A city Albany Zulu maritime Marseilles";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       A
//       Albany
//       Zulu
//       Marseilles
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b[A-Z]\w*\b"
      Dim input As String = "A city Albany Zulu maritime Marseilles"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
```

規則運算式 `\b[A-Z]\w*\b` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`[A-Z]` | 比對從 A 到 Z 的任何大寫字元。
`\w*` | 比對零個或多個文字字元。
`\b` | 比對字邊界。

## <a name="negative-character-group-"></a>負字元群組：[^]

負字元群組會指定一份字元清單，其中任何字元不得出現在輸入字串中，才會出現相符項目。 字元清單可以個別指定，也可以依範圍指定，或同時依兩種方式指定。 

指定個別字元清單的語法如下所示：

[^*character*_*group*]

其中 *character_group* 是為了讓比對成功而不可出現在輸入字串中的個別字元清單。 *character*_*group* 可以由一或多個常值字元、[逸出字元](escapes.md)或字元類別的任何組合所構成。 

指定字元範圍的語法如下所示：

[^*firstCharacter-lastCharacter*]

其中 *firstCharacter* 是範圍開始的字元，而 *lastCharacter* 是範圍結束的字元。 字元範圍是指一系列連續的字元，定義的方式是指定系列中的第一個字元、連字號 (-)，然後是系列中的最後一個字元。 如果兩個字元具有相鄰的 Unicode 字碼指標，這兩個字元就是連續字元。

可以串連兩個或多個字元範圍。 例如，若要指定從 "0" 到 "9" 的十進位數字範圍、從 "a" 到 "f" 的小寫字母範圍，以及從 "A" 到 "F" 的大寫字母範圍，可以使用 `[0-9a-fA-F]`。

負字元群組中的前置 ^ 字元是必要的，它表示字元群組是負字元群組而非正字元群組。

> [!IMPORTANT]
> 較大規則運算式模式中的負字元群組不是零寬度的判斷提示。 也就是說，在評估負字元群組之後，規則運算式引擎會在輸入字串中前進一個字元。

下表列出一些包含負字元群組的常見規則運算式模式。

模式 | 描述
------- | ----------- 
`[^aeiou]` | 比對除了母音之外的所有字元。
`[^\p{P}\d]` | 比對標點符號和十進位數字字元之外的所有字元。
 
下列範例將比對任何開頭字元是 "th" 且後面不是接著 "o" 的文字。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bth[^o]\w+\b";
      string input = "thought thing though them through thus thorough this";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       thing
//       them
//       through
//       thus
//       this
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bth[^o]\w+\b"
      Dim input As String = "thought thing though them through thus " + _
                            "thorough this"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       thing
'       them
'       through
'       thus
'       this
```

規則運算式 `\bth[^o]\w+\b` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`th` | 比對常值字元 "th"。
`[^o]` | 比對不是 "o" 的任何字元。
`\w+` | 比對一個或多個文字字元。
`\b` | 在字邊界結束。

## <a name="any-character-"></a>任何字元：.

句號字元 (.) 會比對 **\n** (新行字元 **\u000A**) 以外任何具有下列兩項資格的字元：

* 若 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項修改了規則運算式，或  **s** 選項修改了模式中包含 . 字元的部分， 就會比對任何字元。 如需詳細資訊，請參閱[規則運算式選項](options.md)。

  下列範例說明 . 字元類別的預設行為與搭配 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項一起使用時的行為差異。 規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。 根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 **\r** 或 **\u000D**，但不會比對 **\n**。 由於 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 **\n**。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Singleline))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r
//       
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
    Public Sub Main()
        Dim pattern As String = "^.+"
        Dim input As String = "This is one line and" + vbCrLf + "this is the second."
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine(Regex.Escape(match.Value))
        Next
        Console.WriteLine()
        For Each match As Match In Regex.Matches(input, pattern, RegexOptions.SingleLine)
           Console.WriteLine(Regex.Escape(match.Value))
        Next
     End Sub
  End Module
  ' The example displays the following output:
  '       This\ is\ one\ line\ and\r
  '       
  '       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

  > [!NOTE]
  > 由於它會比對 **\n** 以外的任何字元，因此 . 字元類別也會比對 **\r** (歸位字元 **\u000D**)。
 
* 在正或負字元群組中，句號會視為常值句號字元而非字元類別。 如需詳細資訊，請參閱本主題前文的[正字元群組](#positive-character-group--)及[負字元群組](#negative-character-group-)。 下列範例將進行示範，定義包含句號字元 (**.**) 作為字元類別以及作為正字元群組成員的規則運算式。 規則運算式 `\b.*[.?!;:](\s|\z)` 會從字邊界開始比對所有字元，直到遇到包括句號的四個標點符號其中之一，然後比對空白字元或字串結尾。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b.*[.?!;:](\s|\z)";
      string input = "this. what: is? go, thing.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       this. what: is? go, thing.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As STring = "\b.*[.?!;:](\s|\z)"
      Dim input As String = "this. what: is? go, thing."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next   
   End Sub
End Module
' The example displays the following output:
'       this. what: is? go, thing.
```

  > [!NOTE]
  > 由於它會比對任何字元， 因此如果規則運算式模式嘗試多次比對任何字元，. 語言項目就會經常與 Lazy 數量詞搭配使用。 如需詳細資訊，請參閱[規則運算式中的數量詞](quantifiers.md)。 
 
## <a name="unicode-category-or-unicode-block-p"></a>Unicode 分類或 Unicode 區塊：\p{}

Unicode 標準會為每個字元指派一種一般分類。 例如，特定字元可以是大寫字母 (以 **Lu** 分類表示)、十進位數字 (**Nd** 分類)、數學符號 (**Sm** 分類) 或段落分隔符號 (**Zl** 分類)。 Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。 例如，從 **\u0000** 到 **\u007F** 可找到基本拉丁字元集，從 **\u0600** 到 **\u06FF** 則可找到阿拉伯字元集。 

規則運算式建構

**\p{**_name_**}**

比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 name 是分類縮寫或具名區塊名稱。 如需分類縮寫的清單，請參閱本主題後文的[支援的 Unicode 一般分類](#supported-unicode-general-categories)一節。 如需具名區塊清單，請參閱本主題後文的[支援的具名區塊](#supported-named-blocks)一節。 

下列範例會使用 **\p{**_name_**}** 建構同時比對 Unicode 一般分類 (在本例中為 **Pd**或 Punctuation,Dash 分類) 以及具名區塊 (**IsGreek** 和 **IsBasicLatin** 具名區塊)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+";
      string input = "?ata ?a??a??? - The Gospel of Matthew";

      Console.WriteLine(Regex.IsMatch(input, pattern));        // Displays True.
   }
}
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+"
      Dim input As String = "Κατα Μαθθαίον - The Gospel of Matthew"

      Console.WriteLine(Regex.IsMatch(input, pattern))         ' Displays True.
   End Sub
End Module
```

規則運算式 `\b(\p{IsGreek}+(\s)?)+\p{Pd}\s(\p{IsBasicLatin}+(\s)?)+` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`\p{IsGreek}+` | 比對一個或多個希臘字元。
`(\s)?` | 比對零個或一個空白字元。
`(\p{IsGreek}+(\s)?)+` | 一次或多次比對一個或多個希臘字元後面接著零或一個空白字元的模式。 
`\p{Pd}` | 比對標點符號、虛線字元。
`\s` | 比對空白字元。
`\p{IsBasicLatin}+` | 比對一個或多個基本拉丁字元。
`(\s)?` | 比對零個或一個空白字元。
`(\p{IsBasicLatin}+(\s)?)+` | 一次或多次比對一個或多個基本拉丁字元後面接著零個或一個空白字元的模式。

## <a name="negative-unicode-category-or-unicode-block-p"></a>負 Unicode 分類或 Unicode 區塊：\P{}

Unicode 標準會為每個字元指派一種一般分類。 例如，特定字元可以是大寫字母 (以 **Lu** 分類表示)、十進位數字 (**Nd** 分類)、數學符號 (**Sm** 分類) 或段落分隔符號 (**Zl** 分類)。 Unicode 標準中的特定字元集也會佔據連續字碼指標的特定範圍或區塊。 例如，從 **\u0000** 到 **\u007F** 可找到基本拉丁字元集，從 **\u0600** 到 **\u06FF** 則可找到阿拉伯字元集。 

規則運算式建構

**\P{**_name_**}**

比對屬於 Unicode 一般分類或具名區塊的任何字元，其中 name 是分類縮寫或具名區塊名稱。 如需分類縮寫的清單，請參閱本主題後文的[支援的 Unicode 一般分類](#supported-unicode-general-categories)一節。 如需具名區塊清單，請參閱本主題後文的[支援的具名區塊](#supported-named-blocks)一節。

下列範例會使用 **\P{**_name_**}** 建構從數值字串中移除任何貨幣符號 (在本例中為 **Sc** 或 Symbol, Currency 分類)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\P{Sc})+";

      string[] values = { "$164,091.78", "£1,073,142.68", "73¢", "€120" };
      foreach (string value in values)
         Console.WriteLine(Regex.Match(value, pattern).Value);
   }
}
// The example displays the following output:
//       164,091.78
//       1,073,142.68
//       73
//       120
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\P{Sc})+"

      Dim values() As String = { "$164,091.78", "£1,073,142.68", "73¢", "€120"}
      For Each value As String In values
         Console.WriteLine(Regex.Match(value, pattern).Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       164,091.78
'       1,073,142.68
'       73
'       120
```

規則運算式模式 `(\P{Sc})+` 會比對一個或多個不是貨幣符號的字元，並且會有效移除結果字串中的所有貨幣符號。

## <a name="word-character-w"></a>文字字元：\w

**\w** 會比對任何文字字元。 文字字元是下表中所列的任何 Unicode 分類的成員。 

分類 | 描述
-------- | ----------- 
Ll | 字母、小寫
Lu | 字母、大寫
Lt | 字母、字首大寫
Lo | 字母、其他
Lm | 字母、修飾詞
Mn | 記號，非間距
Nd | 數字、十進位數字
Pc | 標點符號、連接器。 這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。
 
如果指定了符合 ECMAScript 的行為，**\w** 就等於 `[a-zA-Z_0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。 

> [!NOTE]
> 由於它會比對任何文字字元，因此如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，\w 語言項目就會經常與 lazy 數量詞搭配使用。 如需詳細資訊，請參閱[規則運算式中的數量詞](quantifiers.md)。

下列範例會使用 **\w** 語言項目比對文字中重複的字元。 這個範例會定義規則運算式模式 **(\w)\1**，該模式解譯如下。

項目 | 描述
------- | -----------
(\w) | 比對文字字元。 這是第一個擷取群組。
\1 | 比對第一個擷取的值。 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string[] words = { "trellis", "seer", "latter", "summer", 
                         "hoarse", "lesser", "aardvark", "stunned" };
      foreach (string word in words)
      {
         Match match = Regex.Match(word, pattern);
         if (match.Success)
            Console.WriteLine("'{0}' found in '{1}' at position {2}.", 
                              match.Value, word, match.Index);
         else
            Console.WriteLine("No double characters in '{0}'.", word);
      }                                                  
   }
}
// The example displays the following output:
//       'll' found in 'trellis' at position 3.
//       'ee' found in 'seer' at position 1.
//       'tt' found in 'latter' at position 2.
//       'mm' found in 'summer' at position 2.
//       No double characters in 'hoarse'.
//       'ss' found in 'lesser' at position 2.
//       'aa' found in 'aardvark' at position 0.
//       'nn' found in 'stunned' at position 3.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim words() As String = { "trellis", "seer", "latter", "summer", _
                                "hoarse", "lesser", "aardvark", "stunned" }
      For Each word As String In words
         Dim match As Match = Regex.Match(word, pattern)
         If match.Success Then
            Console.WriteLine("'{0}' found in '{1}' at position {2}.", _
                              match.Value, word, match.Index)
         Else
            Console.WriteLine("No double characters in '{0}'.", word)
         End If
      Next                                                  
   End Sub
End Module
' The example displays the following output:
'       'll' found in 'trellis' at position 3.
'       'ee' found in 'seer' at position 1.
'       'tt' found in 'latter' at position 2.
'       'mm' found in 'summer' at position 2.
'       No double characters in 'hoarse'.
'       'ss' found in 'lesser' at position 2.
'       'aa' found in 'aardvark' at position 0.
'       'nn' found in 'stunned' at position 3.
```

## <a name="non-word-character-w"></a>非文字字元：\W

**\W** 會比對任何非文字字元。 **\W** 語言項目相當於下列字元類別：

```
[^\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]
```

換句話說，它會比對下表所列 Unicode 分類中字元以外的所有字元。

分類 | 描述
-------- | -----------
Ll | 字母、小寫
Lu | 字母、大寫
Lt | 字母、字首大寫
Lo | 字母、其他
Lm | 字母、修飾詞
Mn | 記號，非間距
Nd | 數字、十進位數字
Pc | 標點符號、連接器。 這個分類包含十個字元，其中最常用的是 LOWLINE 字元 (_)，u+005F。
 
如果指定了符合 ECMAScript 的行為，**\W** 就等於 `[^a-zA-Z_0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。 

> [!NOTE]
> 由於它會比對任何文字字元，因此如果規則運算式模式嘗試多次比對任何文字字元且後面接著特定文字字元，\w 語言項目就會經常與 lazy 數量詞搭配使用。 如需詳細資訊，請參閱[規則運算式中的數量詞](quantifiers.md)。 

以下範例將說明 **\W** 字元類別。 它會定義規則運算式模式 `\b(\w+)(\W){1,2}`，該模式會比對後面接一個或多個非文字字元的文字，例如空白字元或標點符號。 規則運算式的解譯方式如下表所示。

項目 | 描述
------- | ----------- 
\b | 開始字緣比對。
(\w+) | 比對一個或多個文字字元。 這是第一個擷取群組。
(\W){1,2} | 比對一次或兩次非文字字元。 這是第二個擷取群組。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)(\W){1,2}";
      string input = "The old, grey mare slowly walked across the narrow, green pasture.";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         Console.Write("   Non-word character(s):");
         CaptureCollection captures = match.Groups[2].Captures;
         for (int ctr = 0; ctr < captures.Count; ctr++)
             Console.Write(@"'{0}' (\u{1}){2}", captures[ctr].Value, 
                           Convert.ToUInt16(captures[ctr].Value[0]).ToString("X4"), 
                           ctr < captures.Count - 1 ? ", " : "");
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The
//          Non-word character(s):' ' (\u0020)
//       old,
//          Non-word character(s):',' (\u002C), ' ' (\u0020)
//       grey
//          Non-word character(s):' ' (\u0020)
//       mare
//          Non-word character(s):' ' (\u0020)
//       slowly
//          Non-word character(s):' ' (\u0020)
//       walked
//          Non-word character(s):' ' (\u0020)
//       across
//          Non-word character(s):' ' (\u0020)
//       the
//          Non-word character(s):' ' (\u0020)
//       narrow,
//          Non-word character(s):',' (\u002C), ' ' (\u0020)
//       green
//          Non-word character(s):' ' (\u0020)
//       pasture.
//          Non-word character(s):'.' (\u002E)
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)(\W){1,2}"
      Dim input As String = "The old, grey mare slowly walked across the narrow, green pasture."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         Console.Write("   Non-word character(s):")
         Dim captures As CaptureCollection = match.Groups(2).Captures
         For ctr As Integer = 0 To captures.Count - 1
             Console.Write("'{0}' (\u{1}){2}", captures(ctr).Value, _
                           Convert.ToUInt16(captures(ctr).Value.Chars(0)).ToString("X4"), _
                           If(ctr < captures.Count - 1, ", ", ""))
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'       The
'          Non-word character(s):' ' (\u0020)
'       old,
'          Non-word character(s):',' (\u002C), ' ' (\u0020)
'       grey
'          Non-word character(s):' ' (\u0020)
'       mare
'          Non-word character(s):' ' (\u0020)
'       slowly
'          Non-word character(s):' ' (\u0020)
'       walked
'          Non-word character(s):' ' (\u0020)
'       across
'          Non-word character(s):' ' (\u0020)
'       the
'          Non-word character(s):' ' (\u0020)
'       narrow,
'          Non-word character(s):',' (\u002C), ' ' (\u0020)
'       green
'          Non-word character(s):' ' (\u0020)
'       pasture.
'          Non-word character(s):'.' (\u002E)
```

由於第二個擷取群組的 `Group` 物件只包含單一擷取的非文字字元，因此這個範例會從 `CaptureCollection` 屬性所傳回之 `Group.Captures` 物件擷取所有擷取的非文字字元。

## <a name="white-space-character-s"></a>空白字元：\s

**\s** 會比對任何空白字元。 它相當於下表列出的逸出序列和 Unicode 分類。 

分類 | 說明
-------- | ----------- 
**\f** | 換頁字元 \u000C。
**\n** | 新行字元 \u000A。
**\r** | 歸位字元 \u000D。
**\t** | 定位字元 \u0009。
**\v** | 垂直定位字元 \u000B。
**\x85** | 省略符號或 NEXT LINE (NEL) 字元 (…) \u0085。
**\p{Z}** | 比對任何分隔符號字元。
 

如果指定了符合 ECMAScript 的行為，**\s** 就等於 `[ \f\n\r\t\v]`。  如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。 

以下範例將說明 \s 字元類別。 它會定義規則運算式模式 `\b\w+(e)?s(\s|$)`，該模式會比對結尾為 "s" 或 "es" 且後面加上空白字元或是輸入字串結尾的文字。 規則運算式的解譯方式如下表所示。

項目 | 描述
------- | -----------
\b | 開始字緣比對。
\w+ | 比對一個或多個文字字元。 
(e)? | 比對 "e" 零次或一次。
s | 比對 "s"。
(\s&#124;$) | 比對空白字元或輸入字串的結尾。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\w+(e)?s(\s|$)";
      string input = "matches stores stops leave leaves";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       matches
//       stores
//       stops
//       leaves
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\w+(e)?s(\s|$)"
      Dim input As String = "matches stores stops leave leaves"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)      
      Next
   End Sub
End Module
' The example displays the following output:
'       matches
'       stores
'       stops
'       leaves
```

## <a name="non-white-space-character-s"></a>非空白字元：\S

**\S** 會比對任何非空白字元。 它相當於 `[^\f\n\r\t\v\x85\p{Z}]` 規則運算式模式，或是規則運算式模式的相反模式，相當於會比對空白字元的 **\s**。 如需詳細資訊，請參閱上一節＜空白字元：\s＞。

如果指定了符合 ECMAScript 的行為，**\S** 就等於 `[^ \f\n\r\t\v]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。

下列範例將說明 **\S** 語言項目。 規則運算式模式 \b(\S+)\s? 會比對以空白字元分隔的字串。 在比對之 GroupCollection 物件中的第二個項目包含相符的字串。 規則運算式的解譯方式如下表所示。

項目 | 描述
------- | ----------- 
`\b` | 開始字緣比對。
`(\S+)` | 比對一個或多個非空白字元。 這是第一個擷取群組。
`\s?` | 比對零個或一個空白字元。 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\S+)\s?";
      string input = "This is the first sentence of the first paragraph. " + 
                            "This is the second sentence.\n" + 
                            "This is the only sentence of the second paragraph.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Groups[1]);
   }
}
// The example displays the following output:
//    This
//    is
//    the
//    first
//    sentence
//    of
//    the
//    first
//    paragraph.
//    This
//    is
//    the
//    second
//    sentence.
//    This
//    is
//    the
//    only
//    sentence
//    of
//    the
//    second
//    paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\S+)\s?"
      Dim input As String = "This is the first sentence of the first paragraph. " + _
                            "This is the second sentence." + vbCrLf + _
                            "This is the only sentence of the second paragraph."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Groups(1))
      Next
   End Sub
End Module
' The example displays the following output:
'    This
'    is
'    the
'    first
'    sentence
'    of
'    the
'    first
'    paragraph.
'    This
'    is
'    the
'    second
'    sentence.
'    This
'    is
'    the
'    only
'    sentence
'    of
'    the
'    second
'    paragraph.
```

## <a name="decimal-digit-character-d"></a>十進位數字字元：\d

**\d** 會比對任何十進位數字。 它相當於 `\\p{Nd}` 規則運算式模式，其中包括標準的十進位數字 0-9，以及若干其他字元集的十進位數字。

如果指定了符合 ECMAScript 的行為，**\d** 就等於 `[0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。

下列範例將說明 **\d** 語言項目。 它會測試輸入字串是否表示美國和加拿大的有效電話號碼。 規則運算式模式 `^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$` 的定義如下表所示。

項目 | 描述
------- | ----------- 
`^` | 在輸入字串的開頭開始比對。
`\(?` | 比對零個或一個常值 "(" 字元。 
`\d{3}` | 比對三個十進位數字。 
`\)?` | 比對零個或一個常值 ")" 字元。
`[\s-]` | 比對連字號或空白字元。
`(\(?\d{3}\)?[\s-])?` | 比對零次或一次選擇性的左括號，後面接著三個十進位數字、選擇性的右括號，以及空白字元或是連字號。 這是第一個擷取群組。
`\d{3}-\d{4}` | 比對三個十進位數字，後面接著連字號和另外四個十進位數字。
`$` | 比對輸入字串的結尾。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$";
      string[] inputs = { "111 111-1111", "222-2222", "222 333-444", 
                          "(212) 111-1111", "111-AB1-1111", 
                          "212-111-1111", "01 999-9999" };

      foreach (string input in inputs)
      {
         if (Regex.IsMatch(input, pattern)) 
            Console.WriteLine(input + ": matched");
         else
            Console.WriteLine(input + ": match failed");
      }
   }
}
// The example displays the following output:
//       111 111-1111: matched
//       222-2222: matched
//       222 333-444: match failed
//       (212) 111-1111: matched
//       111-AB1-1111: match failed
//       212-111-1111: matched
//       01 999-9999: match failed
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^(\(?\d{3}\)?[\s-])?\d{3}-\d{4}$"
      Dim inputs() As String = { "111 111-1111", "222-2222", "222 333-444", _
                                 "(212) 111-1111", "111-AB1-1111", _
                                 "212-111-1111", "01 999-9999" }

      For Each input As String In inputs
         If Regex.IsMatch(input, pattern) Then 
            Console.WriteLine(input + ": matched")
         Else
            Console.WriteLine(input + ": match failed")
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111 111-1111: matched
'       222-2222: matched
'       222 333-444: match failed
'       (212) 111-1111: matched
'       111-AB1-1111: match failed
'       212-111-1111: matched
'       01 999-9999: match failed
```

## <a name="non-digit-character-d"></a>非數字字元：\D

**\D** 會比對任何非數字字元。 它相當於 `\P{Nd}` 規則運算式模式。

如果指定了符合 ECMAScript 的行為，**\D** 就等於 `[^0-9]`。 如需 ECMAScript 規則運算式的資訊，請參閱[規則運算式選項](options.md)中的 [ECMAScript 比對行為](options.md#ecmascript-matching-behavior)一節。

下列範例將說明 **\D** 語言項目。 它會測試像是組件編號這類字串，是否由十進位和非十進位字元的適當組合所構成。 規則運算式模式 `^\D\d{1,5}\D*$` 的定義如下表所示。

項目 | 描述
------- | ----------- 
`^` | 在輸入字串的開頭開始比對。
`\D` | 比對非數字字元。 
`\d{1,5}` | 比對從一個到五個十進位數字。 
`\D*` | 比對零個、一個或更多非十進位字元。 
`$` | 比對輸入字串的結尾。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^\D\d{1,5}\D*$"; 
      string[] inputs = { "A1039C", "AA0001", "C18A", "Y938518" }; 

      foreach (string input in inputs)
      {
         if (Regex.IsMatch(input, pattern))
            Console.WriteLine(input + ": matched");
         else
            Console.WriteLine(input + ": match failed");
      }
   }
}
// The example displays the following output:
//       A1039C: matched
//       AA0001: match failed
//       C18A: matched
//       Y938518: match failed
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^\D\d{1,5}\D*$" 
      Dim inputs() As String = { "A1039C", "AA0001", "C18A", "Y938518" } 

      For Each input As String In inputs
         If Regex.IsMatch(input, pattern) Then
            Console.WriteLine(input + ": matched")
         Else
            Console.WriteLine(input + ": match failed")
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
```

## <a name="supported-unicode-general-categories"></a>支援的 Unicode 一般分類

Unicode 定義了下表中所列的一般類別。 如需詳細資訊，請參閱 [Unicode Character Database](http://www.unicode.org/reports/tr44/) 中的 "UCD File Format" 和 "General Category Values" 副標題。

分類 | 說明
-------- | -----------
**Lu** | 字母、大寫
**Ll** | 字母、小寫
**Lt** | 字母、字首大寫
**Lm** | 字母、修飾詞
**Lo** | 字母、其他
**L** | 所有字母字元。 這包括 **Lu**、**Ll**、**Lt**、**Lm** 和 **Lo** 字元。
**Mn** | 記號，非間距
**Mc** | 記號，間距組合
**Me** | 記號，封入
**M** | 所有變音符號記號。 這包括 **Mn**、**Mc** 和 **Me** 分類。
**Nd** | 數字、十進位數字
**Nl** | 數字，字母
**No** | 數字，其他
**N** | 所有數字。 這包括 **Nd**、**Nl** 和 **No** 分類。
**Pc** | 標點符號，連接器
**Pd** | 標點符號，破折號
**Ps** | 標點符號，左括號
**Pe** | 標點符號，右括號
**Pi** | 標點符號，左引號 (根據使用方式，作用可能像 Ps 或 Pe)
**Pf** | 標點符號，右引號 (根據使用方式，作用可能像 Ps 或 Pe)
**Po** | 標點符號，其他
**P** | 所有標點符號字元。 這包括 **Pc**、**Pd**、**Ps**、**Pe**、**Pi**、**Pf** 和 **Po** 分類。
**Sm** | 符號，數學
**Sc** | 符號，貨幣
**Sk** | 符號，修飾詞
**So** | 符號，其他
**S** | 所有符號。 這包括 **Sm**、**Sc**、**Sk** 和 **So** 分類。
**Zs** | 分隔符號，空格
**Zl** | 分隔符號，行
**Zp** | 分隔符號，段落
**Z** | 所有分隔符號字元。 這包括 **Zs**、**Zl** 和 **Zp** 分類。
**Cc** | 其他，控制
**Cf** | 其他，格式
**Cs** | 其他，Surrogate
**Co** | 其他，專用
**Cn** | 其他，未指派 (沒有字元擁有這個屬性)
**C** | 所有控制字元。 這包括 **Cc**、**Cf**、**Cs**、**Co** 和 **Cn** 分類。
 
##<a name="supported-named-blocks"></a>支援的具名區塊

.NET 提供下表所列的具名區塊。 這一組支援的具名區塊是根據 Unicode 4.0 和 Perl 5.6。

字碼指標範圍 | 區塊名稱
---------------- | ---------- 
0000 - 007F | **IsBasicLatin**
0080 - 00FF | **IsLatin-1Supplement**
0100 - 017F | **IsLatinExtended-A**
0180 - 024F | **IsLatinExtended-B**
0250 - 02AF | **IsIPAExtensions**
02B0 - 02FF | **IsSpacingModifierLetters**
0300 - 036F | **IsCombiningDiacriticalMarks**
0370 - 03FF | **IsGreek** -或- **IsGreekandCoptic**
0400 - 04FF | **IsCyrillic**
0500 - 052F | **IsCyrillicSupplement**
0530 - 058F | **IsArmenian**
0590 - 05FF | **IsHebrew**
0600 - 06FF | **IsArabic**
0700 - 074F | **IsSyriac**
0780 - 07BF | **IsThaana**
0900 - 097F | **IsDevanagari**
0980 - 09FF | **IsBengali**
0A00 - 0A7F | **IsGurmukhi**
0A80 - 0AFF | **IsGujarati**
0B00 - 0B7F | **IsOriya**
0B80 - 0BFF | **IsTamil**
0C00 - 0C7F | **IsTelugu**
0C80 - 0CFF | **IsKannada**
0D00 - 0D7F | **IsMalayalam**
0D80 - 0DFF | **IsSinhala**
0E00 - 0E7F | **IsThai**
0E80 - 0EFF | **IsLao**
0F00 - 0FFF | **IsTibetan**
1000 - 109F | **IsMyanmar**
10A0 - 10FF | **IsGeorgian**
1100 - 11FF | **IsHangulJamo**
1200 - 137F | **IsEthiopic**
13A0 - 13FF | **IsCherokee**
1400 - 167F | **IsUnifiedCanadianAboriginalSyllabics**
1680 - 169F | **IsOgham**
16A0 - 16FF | **IsRunic**
1700 - 171F | **IsTagalog**
1720 - 173F | **IsHanunoo**
1740 - 175F | **IsBuhid**
1760 - 177F | **IsTagbanwa**
1780 - 17FF | **IsKhmer**
1800 - 18AF | **IsMongolian**
1900 - 194F | **IsLimbu**
1950 - 197F | **IsTaiLe**
19E0 - 19FF | **IsKhmerSymbols**
1D00 - 1D7F | **IsPhoneticExtensions**
1E00 - 1EFF | **IsLatinExtendedAdditional**
1F00 - 1FFF | **IsGreekExtended**
2000 - 206F | **IsGeneralPunctuation**
2070 - 209F | **IsSuperscriptsandSubscripts**
20A0 - 20CF | **IsCurrencySymbols**
20D0 - 20FF | **IsCombiningDiacriticalMarksforSymbols** -或- **IsCombiningMarksforSymbols**
2100 - 214F | **IsLetterlikeSymbols**
2150 - 218F | **IsNumberForms**
2190 - 21FF | **IsArrows**
2200 - 22FF | **IsMathematicalOperators**
2300 - 23FF | **IsMiscellaneousTechnical**
2400 - 243F | **IsControlPictures**
2440 - 245F | **IsOpticalCharacterRecognition**
2460 - 24FF | **IsEnclosedAlphanumerics**
2500 - 257F | **IsBoxDrawing**
2580 - 259F | **IsBlockElements**
25A0 - 25FF | **IsGeometricShapes**
2600 - 26FF | **IsMiscellaneousSymbols**
2700 - 27BF | **IsDingbats**
27C0 - 27EF | **IsMiscellaneousMathematicalSymbols-A**
27F0 - 27FF | **IsSupplementalArrows-A**
2800 - 28FF | **IsBraillePatterns**
2900 - 297F | **IsSupplementalArrows-B**
2980 - 29FF | **IsMiscellaneousMathematicalSymbols-B**
2A00 - 2AFF | **IsSupplementalMathematicalOperators**
2B00 - 2BFF | **IsMiscellaneousSymbolsandArrows**
2E80 - 2EFF | **IsCJKRadicalsSupplement**
2F00 - 2FDF | **IsKangxiRadicals**
2FF0 - 2FFF | **IsIdeographicDescriptionCharacters**
3000 - 303F | **IsCJKSymbolsandPunctuation**
3040 - 309F | **IsHiragana**
30A0 - 30FF | **IsKatakana**
3100 - 312F | **IsBopomofo**
3130 - 318F | **IsHangulCompatibilityJamo**
3190 - 319F | **IsKanbun**
31A0 - 31BF | **IsBopomofoExtended**
31F0 - 31FF | **IsKatakanaPhoneticExtensions**
3200 - 32FF | **IsEnclosedCJKLettersandMonths**
3300 - 33FF | **IsCJKCompatibility**
3400 - 4DBF | **IsCJKUnifiedIdeographsExtensionA**
4DC0 - 4DFF | **IsYijingHexagramSymbols**
4E00 - 9FFF | **IsCJKUnifiedIdeographs**
A000 - A48F | **IsYiSyllables**
A490 - A4CF | **IsYiRadicals**
AC00 - D7AF | **IsHangulSyllables**
D800 - DB7F | **IsHighSurrogates**
DB80 - DBFF | **IsHighPrivateUseSurrogates**
DC00 - DFFF | **IsLowSurrogates**
E000 - F8FF | **IsPrivateUse** 或 **IsPrivateUseArea**
F900 - FAFF | **IsCJKCompatibilityIdeographs**
FB00 - FB4F | **IsAlphabeticPresentationForms** 
FB50 - FDFF | **IsArabicPresentationForms-A** 
FE00 - FE0F | **IsVariationSelectors** 
FE20 - FE2F | **IsCombiningHalfMarks** 
FE30 - FE4F | **IsCJKCompatibilityForms** 
FE50 - FE6F | **IsSmallFormVariants**
FE70 - FEFF | **IsArabicPresentationForms-B** 
FF00 - FFEF | **IsHalfwidthandFullwidthForms** 
FFF0 - FFFF | **IsSpecials**
 
<a name="character-class-subtraction"></a>
## <a name="character-class-subtraction-basegroup---excludedgroup"></a>字元類別減法：[base_group - [excluded_group]]

字元類別會定義字元集， 字元類別減法會產生字元集，這個字元集是將某一個字元類別中的字元從另一個字元類別中排除的結果。 

字元類別減法運算式的格式如下：

__[__*base*_*group*-__[__*excluded*_*group*__]]--

方括號 (**[]**) 和連字號 (-) 為必要。 *base_group* 是正字元群組或負字元群組。 *excluded_group* 元件是另一個正字元群組或負字元群組，或者是另一個字元類別減法運算式 (也就是說，您可以將字元類別減法運算式設為巢狀)。 

例如，假設您有一個由 "a" 到 "z" 字元範圍組成的基底群組。 若要定義一組由基底群組所組成的字元，但不包括字元 "m"，則使用 `[a-z-[m]]`。 若要定義一組由基底群組所組成的字元，但不包括 "d"、"j" 和 "p" 這組字元，則使用 `[a-z-[djp]]`。 若要定義一組由基底群組所組成的字元，但不包括 "m" 到 "p" 的字元範圍，則使用 `[a-z-[m-p]]`。 

請考慮使用巢狀字元類別減法運算式 `[a-z-[d-w-[m-o]]]`。 這個運算式會從最內部的字元範圍向外評估。 首先從 "d" 到 "w" 字元範圍減去 "m" 到 "o" 字元範圍，這樣會產生從 "d" 到 "l" 及從 "p" 到 "w" 的字元集。 接著會從字元範圍 "a" 到 "z" 中減去該字元集，此時會產生 `[abcmnoxyz]` 字元集。

您可以使用任何字元類別搭配字元類別減法。 若要定義由 \u0000 到 \uFFFF 的所有 Unicode 字元組成的字元集，但是不包含空白字元 (**\s**)、標點符號一般分類內的字元 (**\p{P}**)、**IsGreek** 具名區塊內的字元 (**\p{IsGreek}**) 以及 Unicode NEXT LINE 控制字元 (\x85)，請使用 `[\u0000-\uFFFF-[\s\p{P}\p{IsGreek}\x85]]`。

為字元類別減法運算式選擇將會產生有用結果的字元類別， 避免選擇會產生空字元集的運算式，該運算式無法比對任何項目，也不要選擇相當於原始基底群組的運算式。 例如，空集合是 `[\p{IsBasicLatin}-[\x00-\x7F]]` 運算式的結果，該運算式會從 **IsBasicLatin** 一般分類中減去 **IsBasicLatin** 字元範圍中的所有字元。 同樣地，原始基底群組是 `[a-z-[0-9]]` 運算式的結果。 這是因為基底群組就是從 "a" 到 "z" 的字母字元範圍，該群組不包含已排除之群組中的任何字元，也就是從 "0" 到 "9" 的十進位數字字元範圍。 

下列範例會定義規則運算式 (`^[0-9-[2468]]+$`)，該運算式會比對輸入字串中的零和奇數數字。 規則運算式的解譯方式如下表所示。

項目 | 描述
------- | ----------- 
`^` | 從輸入字串開頭開始比對。
`[0-9-[2468]]+` | 比對 0 到 9 中不包括 2、4、6 和 8 的任何出現一次或多次的字元。 換句話說，就是比對出現一次或多次的零或奇數。
`$` | 在輸入字串結尾結束比對。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "123", "13579753", "3557798", "335599901" };
      string pattern = @"^[0-9-[2468]]+$";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success) 
            Console.WriteLine(match.Value);
      }      
   }
}
// The example displays the following output:
//       13579753
//       335599901
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "123", "13579753", "3557798", "335599901" }
      Dim pattern As String = "^[0-9-[2468]]+$"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       13579753
'       335599901
```

## <a name="see-also"></a>請參閱

[規則運算式選項](options.md)
