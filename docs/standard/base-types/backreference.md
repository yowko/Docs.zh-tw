---
title: "規則運算式中的反向參考建構"
description: "規則運算式中的反向參考建構"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c453ed78-650f-4c3c-9ab4-9d89d250bf88
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 757c8c4e71bbafb12c8add925723daf1a24e06d1

---

# <a name="backreference-constructs-in-regular-expressions"></a>規則運算式中的反向參考建構

反向參考提供便利的方式來識別字串內的重複字元或子字串。 例如，如果輸入字串包含多次出現的任意子字串，您可以比對第一個出現的子字串與擷取的群組，接著使用反向參考來比對隨後出現的子字串。 

> [!NOTE]
> 對於取代字串中的具名和編號擷取群組，會使用不同的語法來參考。 如需詳細資訊，請參閱[規則運算式中的替代項目](substitutions.md)。
 
.NET 會定義個別的語言項目，以參考編號和具名擷取群組。 如需擷取群組的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

## <a name="numbered-backreferences"></a>編號反向參考

編號反向參考會使用下列語法：

**\**_number_

其中 *number* 是規則運算式中的擷取群組序數位置。 例如，`\4` 會比對第四個擷取群組的內容。 如果在規則運算式模式中未定義 *number*，便會發生剖析錯誤，而且規則運算式引擎會擲回 [ArgumentException](xref:System.ArgumentException)。 例如，規則運算式 `\b(\w+)\s\1` 有效，因為 `(\w+)` 是運算式中第一個和唯一的擷取群組。 另一方面，`\b(\w+)\s\2` 無效並擲回引數例外狀況，因為沒有編號為 `\2` 的擷取群組。

請注意八進位逸出字碼 (例如 `\16`) 與使用相同標記法之 **\**_number_反向參考間的不明確。 這個模棱兩可的情況已解決，如下所示：

* 運算式 `\1` 到 `\9` 一律會解譯為反向參考，而不是八進位字碼。

* 如果多位數運算式的第一個數字是 8 或 9 (例如 `\80` 或 `\91`)，該運算式會解譯為常值。

* 從 `\10` 到更大值的運算式會視為反向參考 (如果有對應至該數字的反向參考)，否則會解譯為八進位字碼。

* 如果規則運算式包含未定義之群組號碼的反向參考，便會發生剖析錯誤，而且規則運算式引擎會擲回 [ArgumentException](xref:System.ArgumentException)。

如果有不明確的問題，您可以使用 **\k<**_name_**>** 標記法，這樣就不會不明確，而且不會與八進位字元碼混淆。 同樣地，十六進位字碼 (例如 `\xdd`) 不會不明確，而且不會與反向參考混淆。

下列範例會在字串中尋找雙字組字元。 它會定義由下列項目組成的規則運算式 `(\w)\1,`。

項目 | 描述
------- | -----------
`(\w)` | 比對文字字元，並將其指派給第一個擷取群組。
`\1` | 比對與第一個擷取群組之值相同的下一個字元。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(\w)\1";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(\w)\1"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="named-backreferences"></a>具名反向參考

具名反向參考是使用下列語法來定義：

**\k<**_name_**>**

或：

**\k'**_name_**'**

其中 *name* 是規則運算式模式中所定義之擷取群組的名稱。 如果在規則運算式模式中未定義 *name*，便會發生剖析錯誤，而且規則運算式引擎會擲回 [ArgumentException](xref:System.ArgumentException)。

下列範例會在字串中尋找雙字組字元。 它會定義由下列項目組成的規則運算式 `(?<char>\w)\k<char>`。

項目 | 描述
------- | -----------
`(?<char>\w)` | 比對文字字元，並將其指派給名為 char 的擷取群組。
`\k<char>` | 比對與 char 擷取群組之值相同的下一個字元。
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<char>\w)\k<char>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<char>\w)\k<char>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

請注意，*name* 也可以是數字的字串表示。 例如，下列範例會使用規則運算式 `(?<2>\w)\k<2>` 來尋找字串中的雙字組字元。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<2>\w)\k<2>";
      string input = "trellis llama webbing dresser swagger";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found '{0}' at position {1}.", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found 'll' at position 3.
//       Found 'll' at position 8.
//       Found 'bb' at position 16.
//       Found 'ss' at position 25.
//       Found 'gg' at position 33.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<2>\w)\k<2>"
      Dim input As String = "trellis llama webbing dresser swagger"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found '{0}' at position {1}.", _
                           match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Found 'll' at position 3.
'       Found 'll' at position 8.
'       Found 'bb' at position 16.
'       Found 'ss' at position 25.
'       Found 'gg' at position 33.
```

## <a name="what-backreferences-match"></a>反向參考比對的項目

反向參考會參考群組最近使用的定義 (由左至右比對時，最接近左邊的定義)。 當群組進行多個擷取時，反向參考會參考最近發生的擷取。 

下列範例包含規則運算式模式 `(?<1>a)(?<1>\1b)*`，此模式可重新定義 \1 具名群組。 下表說明規則運算式中的每個模式。 

模式 | 描述
------- | -----------
`(?<1>a)` | 比對字元 "a"，並將結果指派給名為 1 的擷取群組。
`(?<1>\1b)*` |比對出現 0 或 1 次的群組 1b，並將結果指派給名為 1 的擷取群組。 
 
```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"(?<1>a)(?<1>\1b)*";
      string input = "aababb";
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("Match: " + match.Value);
         foreach (Group group in match.Groups)
            Console.WriteLine("   Group: " + group.Value);
      }
   }
}
// The example displays the following output:
//          Group: aababb
//          Group: abb
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?<1>a)(?<1>\1b)*"
      Dim input As String = "aababb"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: " + match.Value)
         For Each group As Group In match.Groups
            Console.WriteLIne("   Group: " + group.Value)
         Next
      Next
   End Sub
End Module
' The example display the following output:
'          Group: aababb
'          Group: abb
```

在比較規則運算式與輸入字串 ("aababb") 時，規則運算式引擎會執行下列作業：

1. 它會從該字串的開頭開始，並且成功地比對 "a" 與運算式 `(?<1>a)`。 1 群組的值現在是 "a"。

2. 它會前進到第二個字元，並且成功地比對字串 "ab" 與運算式 `\1b`，或是 "ab"。 然後它會將結果 "ab" 指派給 `\1`。

3. 它會前進到第四個字元。 運算式 `(?<1>\1b)` 要比對零次以上，才算成功地比對字串 "abb" 與運算式 `\1b`。 然後它會將結果 "abb" 指派回到 `\1`。

在此範例中，\* 是迴圈數量詞，它會重複評估直到規則運算式引擎無法符合其所定義的模式為止。 迴圈數量詞並不會清除群組定義。

如果群組沒有擷取任何子字串，該群組的反向參考會是未定義的，而且永遠不會進行比對。 這由定義如下的規則運算式模式 `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b,` 說明：

模式 | 描述
------- | -----------
`\b` | 開始字邊界比對。
`(\p{Lu}{2})` | 比對兩個大寫字母。 這是第一個擷取群組。
`(\d{2})?` | 比對出現零次或一次的兩個十進位數字。 這是第二個擷取群組。
`(\p{Lu}{2})` | 比對兩個大寫字母。 這是第三個擷取群組。
`\b` | 結束字邊界比對。

輸入字串可以符合這個規則運算式，即使不存在第二個擷取群組所定義的兩個十進位數字亦然。 下列範例顯示即使比對成功，仍會在兩個成功的擷取群組之間找到空的擷取群組。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b";
      string[] inputs = { "AA22ZZ", "AABB" };
      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
         {
            Console.WriteLine("Match in {0}: {1}", input, match.Value);
            if (match.Groups.Count > 1)
            {
               for (int ctr = 1; ctr <= match.Groups.Count - 1; ctr++)
               {
                  if (match.Groups[ctr].Success)
                     Console.WriteLine("Group {0}: {1}", 
                                       ctr, match.Groups[ctr].Value);
                  else
                     Console.WriteLine("Group {0}: <no match>", ctr);
               }
            }
         }
         Console.WriteLine();
      }      
   }
}
// The example displays the following output:
//       Match in AA22ZZ: AA22ZZ
//       Group 1: AA
//       Group 2: 22
//       Group 3: ZZ
//       
//       Match in AABB: AABB
//       Group 1: AA
//       Group 2: <no match>
//       Group 3: BB
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b"
      Dim inputs() As String = { "AA22ZZ", "AABB" }
      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("Match in {0}: {1}", input, match.Value)
            If match.Groups.Count > 1 Then
               For ctr As Integer = 1 To match.Groups.Count - 1
                  If match.Groups(ctr).Success Then
                     Console.WriteLine("Group {0}: {1}", _
                                       ctr, match.Groups(ctr).Value)
                  Else
                     Console.WriteLine("Group {0}: <no match>", ctr)
                  End If      
               Next
            End If
         End If
         Console.WriteLine()
      Next      
   End Sub
End Module
' The example displays the following output:
'       Match in AA22ZZ: AA22ZZ
'       Group 1: AA
'       Group 2: 22
'       Group 3: ZZ
'       
'       Match in AABB: AABB
'       Group 1: AA
'       Group 2: <no match>
'       Group 3: BB
```

## <a name="see-also"></a>另請參閱

[規則運算式語言 - 快速參考](quick-ref.md)




<!--HONumber=Nov16_HO3-->


