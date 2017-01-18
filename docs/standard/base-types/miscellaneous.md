---
title: "規則運算式中的其他建構"
description: "規則運算式中的其他建構"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 478901dc-db6c-4d90-9d3b-f5cfdca2cbf5
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4205d2a318849a7b24ac0f1fd65f7e8a23ec7f55

---

# <a name="miscellaneous-constructs-in-regular-expressions"></a>規則運算式中的其他建構


.NET 中的規則運算式包含三個其他語言建構。 其中一個可讓您在規則運算式模式的中間，啟用或停用特定比對選項。 其餘兩個可讓您在規則運算式中包含註解。

## <a name="inline-options"></a>內嵌選項

您可以使用下列語法，設定或停用部分規則運算式的特定模式比對選項

```
(?imnsx-imnsx)
```

您在問號之後列出要啟用的選項，並在減號之後列出要停用的選項。 下表會說明每個選項。 如需每個選項的詳細資訊，請參閱[規則運算式選項](options.md)。

選項 | 說明
------ | ----------- 
**i** | 不區分大小寫的比對。
**m** | 多行模式。
**n** | 僅明確擷取 (括號不可作為擷取群組)。
**s** | 單行模式。
**x** | 忽略未逸出的空白字元，並允許 x 模式註解。 
 
**(?imnsx-imnsx)** 建構所定義規則運算式選項中的任何變更，其效果會一直維持到封入群組的結尾。

> [!NOTE]
> **(?imnsx-imnsx**:_subexpression_**)** 群組建構會為子運算式提供相同的功能。 如需詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。
 
下列範例使用 **i**、**n** 和 **x** 選項，啟用不區分大小寫和明確擷取，並忽略規則運算式中間之規則運算式模式中的空白字元。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern; 
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      pattern = @"\b(D\w+)\s(d\w+)\b";
      // Match pattern using default options.
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
      }
      Console.WriteLine();

      // Change regular expression pattern to include options.
      pattern = @"\b(D\w+)(?ixn) \s (d\w+) \b";
      // Match new pattern with options. 
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
            for (int ctr = 1; ctr < match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Drooling dog
//          Group 1: Drooling
//          Group 2: dog
//       
//       Drooling dog
//          Group 1: 'Drooling'
//       Dreaded Deep
//          Group 1: 'Dreaded'
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String 
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      pattern = "\b(D\w+)\s(d\w+)\b"
      ' Match pattern using default options.
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
      Console.WriteLine()

      ' Change regular expression pattern to include options.
      pattern = "\b(D\w+)(?ixn) \s (d\w+) \b"
      ' Match new pattern with options. 
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: '{1}'", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       Drooling dog
'          Group 1: Drooling
'          Group 2: dog
'       
'       Drooling dog
'          Group 1: 'Drooling'
'       Dreaded Deep
'          Group 1: 'Dreaded'
```

此範例會定義兩個規則運算式。 第一個規則運算式 `\b(D\w+)\s(d\w+)\b` 會比對開頭為大寫 "D" 和小寫 "d" 的兩個連續字組。 第二個規則運算式 `\b(D\w+)(?ixn) \s (d\w+) \b` 會使用內嵌選項來修改此模式，如下表所述。 然後比較結果，以確認 `(?ixn)` 建構的效果。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`(D\w+)` | 比對後面接著一個或多個文字字元的大寫 "D"。 這是第一個擷取群組。
`(?ixn)` | 從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。
`\s` | 比對空白字元。
`(d\w+)` | 比對後面接著一個或多個文字字元的大寫或小寫 "d"。 因為已啟用 n (明確擷取) 選項，所以不會擷取此群組。
`\b` | 比對字邊界。
 
## <a name="inline-comment"></a>內嵌註解

**(?#** _comment_**)** 建構可讓您在規則運算式中包含內嵌註解。 規則運算式引擎未在模式比對中使用註解的任何一部分，不過會將註解包含在 [Regex.ToString](xref:System.Text.RegularExpressions.Regex.Unescape(System.String)) 方法所傳回的字串中。 註解會在第一個右括號結束。

下列範例會重複上一節範例中的第一個規則運算式模式。 它會將兩個內嵌註解加入規則運算式，以指出比較是否區分大小寫。 規則運算式模式 `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b` 定義如下。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`(?# case-sensitive comparison)` | 註解。 它不會影響模式比對行為。
`(D\w+)` | 比對後面接著一個或多個文字字元的大寫 "D"。 這是第一個擷取群組。
`\s` | 比對空白字元。
`(?ixn)` |從這裡開始，進行不區分大小寫的比較、只進行明確擷取，並忽略規則運算式模式中的空白字元。
`(?#case-insensitive comparison)` | 註解。 它不會影響模式比對行為。 
`(d\w+)` | 比對後面接著一個或多個文字字元的大寫或小寫 "d"。 這是第二個擷取群組。
`\b` | 比對字邊界。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b";
      Regex rgx = new Regex(pattern);
      string input = "double dare double Double a Drooling dog The Dreaded Deep";

      Console.WriteLine("Pattern: " + pattern.ToString());
      // Match pattern using default options.
      foreach (Match match in rgx.Matches(input))
      {
         Console.WriteLine(match.Value);
         if (match.Groups.Count > 1)
         {
            for (int ctr = 1; ctr <match.Groups.Count; ctr++) 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups[ctr].Value);
         }
      }
   }
}
// The example displays the following output:
//    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
//    arison)d\w+)\b
//    Drooling dog
//       Group 1: Drooling
//    Dreaded Deep
//       Group 1: Dreaded
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comparison)d\w+)\b"
      Dim rgx As New Regex(pattern)
      Dim input As String = "double dare double Double a Drooling dog The Dreaded Deep"

      Console.WriteLine("Pattern: " + pattern.ToString())
      ' Match pattern using default options.
      For Each match As Match In rgx.Matches(input)
         Console.WriteLine(match.Value)
         If match.Groups.Count > 1 Then
            For ctr As Integer = 1 To match.Groups.Count - 1 
               Console.WriteLine("   Group {0}: {1}", ctr, match.Groups(ctr).Value)
            Next
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'    Pattern: \b((?# case sensitive comparison)D\w+)\s(?ixn)((?#case insensitive comp
'    arison)d\w+)\b
'    Drooling dog
'       Group 1: Drooling
'    Dreaded Deep
'       Group 1: Dreaded
```

## <a name="end-of-line-comment"></a>行結尾註解

數字符號 (**#**) 會標記 x 模式註解，從規則運算式模式結尾未逸出的 # 字元開始，並持續到行結尾。 若要使用此建構，您必須在具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件或呼叫靜態 [Regex](xref:System.Text.RegularExpressions.Regex) 方法時，啟用 **x** 選項 (透過內嵌選項)，或提供 [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 值給 *option* 參數。 

下列範例說明行結尾註解建構。 它會判斷字串是否為至少包含一個格式項目的複合格式字串。 下表說明規則運算式模式中的建構： 

`\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item`. 

模式 | 描述
------- | ----------- 
`\{` | 比對左括號。
`\d+` | 比對一個或多個十進位數字。
`(,-*\d+)*` | 比對零個或一個出現的逗號，後面接著一個選擇性減號，再接著一個或多個十進位數字。
`(\:\w{1,4}?)*` | 比對零個或一個出現的冒號，後面接著一到四個 (但越少越好) 空白字元。
`(?#case insensitive comparison)` | 內嵌註解。 它不會影響模式比對行為。
`\}` | 比對右括號。
`(?x)` | 啟用忽略模式空白字元選項，以辨識行結尾註解。
`# Looks for a composite format item.` | 行結尾註解。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.";
      string input = "{0,-3:F}";
      Console.WriteLine("'{0}':", input);
      if (Regex.IsMatch(input, pattern))
         Console.WriteLine("   contains a composite format item.");
      else
         Console.WriteLine("   does not contain a composite format item.");
   }
}
// The example displays the following output:
//       '{0,-3:F}':
//          contains a composite format item.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item."
      Dim input As String = "{0,-3:F}"
      Console.WriteLine("'{0}':", input)
      If Regex.IsMatch(input, pattern) Then
         Console.WriteLine("   contains a composite format item.")
      Else
         Console.WriteLine("   does not contain a composite format item.")
      End If
   End Sub
End Module
' The example displays the following output:
'       '{0,-3:F}':
'          contains a composite format item.
```

請注意，除了在規則運算式中提供 `(?x)` 建構，也可以藉由呼叫 [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法，並將 [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 列舉值傳遞給此方法，來辨識註解。

## <a name="see-also"></a>另請參閱

[規則運算式語言 - 快速參考](quick-ref.md)




<!--HONumber=Nov16_HO3-->


