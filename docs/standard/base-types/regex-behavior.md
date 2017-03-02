---
title: "規則運算式行為的詳細資訊"
description: "規則運算式行為的詳細資訊"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6f11047f-45a4-4caf-a259-18abe08cc0d2
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 5656cabb708dcfc311ac7a709446003951b97aa6
ms.lasthandoff: 03/02/2017

---

# <a name="details-of-regular-expression-behavior"></a>規則運算式行為的詳細資訊


.NET 規則運算式引擎是回溯規則運算式比對器，它結合了傳統的非決定性有限自動化 (NFA) 引擎，例如 Perl、Python、Emacs 和 Tcl 所使用的引擎。 這使得它與較快速、但限制較多的純規則運算式決定性有限自動化 (DFA) 引擎有所區別，例如 awk、egrep 或 lex 中的引擎。 這也和標準的但較緩慢的 POSIX NFA 有差異。 下節描述三種規則運算式引擎，並且說明在 .NET 中為何使用傳統 NFA 引擎來實作規則運算式。

## <a name="benefits-of-the-nfa-engine"></a>NFA 引擎的優點

當 DFA 引擎執行模式比對時，其處理順序是由輸入字串所驅動。 引擎會從輸入字串的開頭開始執行，並循序地繼續判斷下一個字元是否符合規則運算式模式。 它們可以保證比對可能最長的字串。 因為 DFA 引擎絕不會測試相同的字元兩次，所以不支援回溯。 但因為 DFA 引擎只包含有限狀態，它不能以反向參考比對模式，並且因為它不建構明確的展開，所以不能擷取子運算式。

和 DFA 引擎不同，傳統 NFA 引擎在執行模式比對時，其處理順序是由規則運算式模式所驅動。 在處理某特定 language 元素時，引擎會使用 Greedy (窮盡) 比對，亦即盡可能比對輸入字串的最多內容。 但是，它也會在成功比對子運算式之後儲存其狀態。 如果比對最終失敗，此引擎可以回到儲存的狀態，以便嘗試其他比對。 放棄成功的子運算式比對，以便比對規則運算式中後續的 language 元素，這個程序稱之為回溯。 NFA 引擎會使用回溯依特定順序測試規則運算式的所有可能展開，並接受第一個符合項目。 因為傳統 NFA 引擎會為成功的比對建構規則運算式的特定展開，所以可以擷取子運算式符合項目和比對的反向參考。 但因為傳統 NFA 會回溯，所以可多次造訪相同的狀態，如果此狀態是經由不同的路徑到達。 結果最壞的情況是，它可以指數方式緩慢執行。 因為傳統 NFA 引擎接受找到的第一個符合項目，所以也可能發現不了其他 (可能是更長的) 符合項目。

POSIX NFA 引擎很像傳統 NFA 引擎，只是它們會繼續回溯直到能夠保證已經找到最長的可能符合項目。 結果，POSIX NFA 引擎比傳統 NFA 引擎更緩慢，而且當您使用 POSIX NFA 引擎時，您不能變更回溯搜尋的順序，讓較短的符合項目優先於較長的符合項目。 

程式設計人員偏愛傳統 NFA 引擎，因為它們比 DFA 或 POSIX NFA 引擎更能夠掌控字串比對。 雖然最壞的情況是它們可能執行緩慢，但您可以使用減低模稜兩可並限制回溯的模式，操縱它們以線性或多項式時間尋找符合項目。 換言之，雖然 NFA 引擎是以效能換取功效和彈性，但是在大多數情況下，如果規則運算式撰寫得宜並可避免回溯指數衰減效能的話，它們所提供的效能還不錯。

> [!NOTE]
> 如需大量回溯所造成效能影響的詳細資訊，以及撰寫規則運算式來解決問題的方式，請參閱[規則運算式中的回溯](backtracking.md)。
 
## <a name="net-framework-engine-capabilities"></a>.NET framework 引擎功能

為利用傳統 NFA 引擎的優點，.NET 規則運算式引擎包含了完整的建構集合，讓程式設計人員可以操縱回溯引擎。 這些建構可用於更快速尋找符合項目，或讓特定展開優先於其他展開。

.NET 規則運算式引擎包含下列其他功能： 

### <a name="lazy-quantifiers"></a>Lazy (最少) 數量詞

Lazy (最少) 數量詞：**??**、__*?__、**+?**、**{**_n_**,**_m_**}?**。 這些建構告訴回溯引擎要先搜尋最小數目的重複。 相反地，一般 Greedy (窮盡) 數量詞會先嘗試比對最多的重複 項目。 下例會說明兩者間的差異。 規則運算式會比對以數字結尾的句子，以及用來擷取該數字的擷取群組。 規則運算式 `.+(\d+)\.` 包含 Greedy (窮盡) 數量詞 `.+`，這導致規則運算式引擎只會擷取數字的最後一個位數。 相反地，規則運算式 `.+?(\d+)\.` 包含 Lazy (最少) 數量詞 `.+?`，這導致規則運算式引擎會擷取整個數字。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string lazyPattern = @".+?(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
       // Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", lazyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (greedy): 5
//       Number at end of sentence (lazy): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim lazyPattern As String = ".+?(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (greedy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match using lazy quantifier .+?.
      match = Regex.Match(input, lazyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (lazy): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", lazyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (greedy): 5
'       Number at end of sentence (lazy): 107325
```

此規則運算式的 Greedy (窮盡) 與 Lazy (最少) 版本定義如下表所示。

模式 | 描述
------- | -----------
`.+` (Greedy (窮盡) 數量詞) | 比對至少出現一次的任何字元。 這會導致規則運算式引擎比對整個字串，然後視需要進行回溯，以比對模式的其餘部分。
`.+?` (Lazy (最少) 數量詞) | 出現的任何字元至少比對一次，但比對愈少愈好。
`(\d+)` | 比對至少一個數值字元，並將它指派給第一個擷取群組。
`\.` | 比對句點。
 
如需 Lazy (最少) 數量詞的詳細資訊，請參閱[規則運算式中的數量詞](quantifiers.md)。

### <a name="positive-lookahead"></a>右合樣 (Positive Lookahead)

右合樣︰**(?**=_subexpression_**)**。 此功能允許回溯引擎在比對子運算式之後返回到文字的相同地方。 這對自相同位置開始驗證多個模式，以全面搜尋文字，很有用處。 它也可以讓引擎驗證子字串是否存在於符合項目的結尾，而不需在相符的文字中包含該子字串。 下例使用右合樣在句子中擷取後面未接標點符號的文字。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b[A-Z]+\b(?=\P{P})";
      string input = "If so, what comes next?";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       If
//       what
//       comes
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b[A-Z]+\b(?=\P{P})"
      Dim input As String = "If so, what comes next?"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next   
   End Sub
End Module
' The example displays the following output:
'       If
'       what
'       comes
```

規則運算式 `\b[A-Z]+\b(?=\P{P})` 的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`[A-Z]+` | 比對任何字母字元一或多次。 因為 [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法是用 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 選項呼叫，所以比較不區分大小寫。 
`\b` | 結束字緣比對。
`(?=\P{P})` | 向右合樣以判斷下一個字元是否為標點符號。 如果不是，則比對成功。

如需右合樣判斷提示的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

### <a name="negative-lookahead"></a>右不合樣 (Negative Lookahead)

右不合樣︰**(?!**_subexpression_**)**。 此功能加入了只有子運算式無法比對時才會比對運算式的功能。 這在刪除搜尋時特別有功用，因為提供應該排除情況的運算式通常會比指供必須包含情況的運算式簡單。 例如，針對開頭不是 "non" 的單字撰寫運算式很困難。 下例使用右不合樣進行排除。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?!non)\w+\b";
      string input = "Nonsense is not always non-functional.";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       is
//       not
//       always
//       functional
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?!non)\w+\b"
      Dim input As String = "Nonsense is not always non-functional."
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       is
'       not
'       always
'       functional
```

規則運算式模式 `\b(?!non)\w+\b` 的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`(?!non)` | 向右合樣以確定目前的字串不是以 "non" 開頭。 如果是，則比對失敗。
`(\w+)` | 比對一個或多個文字字元。
`\b` | 結束字緣比對。
 
如需右不合樣判斷提示的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

### <a name="conditional-evaluation"></a>條件式評估

條件式評估︰**(?(**_expression_**)**_yes_&#124;_no_**)** 和 **(?(**_name_**)**_yes_&#124;_no_**)**，其中 *expression* 是要比對的子運算式，*name* 是擷取群組的名稱，*yes* 是要比對的字串，如果 *expression* 相符或 *name* 是有效的非空白擷取群組；而 *no* 是要比對的子運算式，如果 *expression* 不相符或 *name* 不是有效的非空白擷取群組。 此功能可讓引擎根據前一個子運算式比對的結果或零寬度判斷提示的結果，使用一個以上的替代模式進行搜尋。 這允許更強大的反向參考形式，例如允許根據前一個子運算式是否相符來比對子運算式。 下例中的規則運算式會比對同時可供公用和內部使用的段落。 僅供內部使用的段落會以 `<PRIVATE>` 標記開頭。 規則運算式模式 `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` 會使用條件式評估，將可供公用和內部使用的段落內容指派給個別的擷取群組。 再以不同的方式來處理這些段落。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "<PRIVATE> This is not for public consumption." + Environment.NewLine + 
                     "But this is for public consumption." + Environment.NewLine + 
                     "<PRIVATE> Again, this is confidential.\n";  
      string pattern = @"^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$";
      string publicDocument = null, privateDocument = null;

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
      {
         if (match.Groups[1].Success) {
            privateDocument += match.Groups[1].Value + "\n";
         }
         else {
            publicDocument += match.Groups[3].Value + "\n";   
            privateDocument += match.Groups[3].Value + "\n";
         }  
      }

      Console.WriteLine("Private Document:");
      Console.WriteLine(privateDocument);
      Console.WriteLine("Public Document:");
      Console.WriteLine(publicDocument);
   }
}
// The example displays the following output:
//    Private Document:
//    This is not for public consumption.
//    But this is for public consumption.
//    Again, this is confidential.
//    
//    Public Document:
//    But this is for public consumption.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "<PRIVATE> This is not for public consumption." + vbCrLf + _
                            "But this is for public consumption." + vbCrLf + _
                            "<PRIVATE> Again, this is confidential." + vbCrLf
      Dim pattern As String = "^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$"
      Dim publicDocument As String = Nothing
      Dim privateDocument As String = Nothing

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         If match.Groups(1).Success Then
            privateDocument += match.Groups(1).Value + vbCrLf
         Else
            publicDocument += match.Groups(3).Value + vbCrLf   
            privateDocument += match.Groups(3).Value + vbCrLf
         End If  
      Next

      Console.WriteLine("Private Document:")
      Console.WriteLine(privateDocument)
      Console.WriteLine("Public Document:")
      Console.WriteLine(publicDocument)
   End Sub
End Module
' The example displays the following output:
'    Private Document:
'    This is not for public consumption.
'    But this is for public consumption.
'    Again, this is confidential.
'    
'    Public Document:
'    But this is for public consumption.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | -----------
`^` | 在一行的開頭開始比對。
`(?<Pvt>\<PRIVATE\>\s)?` | 比對出現零次或一次且後面接著空白字元的字串 `<PRIVATE>`。 將相符項目指派給名為 Pvt 的擷取群組。
`(?(Pvt)((\w+\p{P}?\s)+)` | 如果 `Pvt` 擷取群組存在，則比對出現一或多次的一或多個單字字元，且該字元後面接著零或一個標點分隔符號和一個空白字元。 將子字串指派給第一個擷取群組。
`&#124;((\w+\p{P}?\s)+))` | 如果 `Pvt` 擷取群組不存在，則比對出現一或多次的一或多個單字字元，且該字元後面接著零或一個標點分隔符號和一個空白字元。 將子字串指派給第三個擷取群組。
`\r?$` | 比對行尾或字串結尾。
 
如需條件式評估的詳細資訊，請參閱[規則運算式中的替代建構](alternation.md)。

### <a name="balancing-group-definitions"></a>平衡群組定義

平衡群組定義︰**(?<**_name1-name2_**>** _subexpression_**)**。 此功能可讓規則運算式引擎追蹤巢狀建構，例如括號或左右中括弧。 如需範例，請參閱[規則運算式中的群組建構](grouping.md)。

### <a name="nonbacktracking-subexpressions"></a>非回溯子運算式

非回溯子運算式 (也稱為 Greedy (窮盡) 子運算式)：**(?>**_subexpression_**)**。 此功能可讓回溯引擎保證子運算式只比對為該子運算式找到的第一個相符項目，就好像運算式的執行不受其包含運算式的影響。 如果不使用此建構，較大型運算式中的回溯搜尋可以變更子運算式的行為。 例如，規則運算式 `(a+)\w` 會比對一或多個 "a" 字元，以及緊接在 "a" 字元序列後面的單字字元，並將 "a" 字元序列指派給第一個擷取群組。但是，如果輸入字串的最後一個字元也是 "a"，則以 `\w` language 元素比對，且不包含在擷取的群組中。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string backtrackingPattern = @"(a+)\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, backtrackingPattern);
         Console.WriteLine("   Pattern: {0}", backtrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: (a+)\w
//             Match: aaaaa
//             Group 1: aaaa
//       Input: aaaaab
//          Pattern: (a+)\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim backtrackingPattern As String = "(a+)\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, backtrackingPattern)
         Console.WriteLine("   Pattern: {0}", backtrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: (a+)\w
'             Match: aaaaa
'             Group 1: aaaa
'       Input: aaaaab
'          Pattern: (a+)\w
'             Match: aaaaab
'             Group 1: aaaaa
```

規則運算式 `((?>a+))\w` 可防止此行為發生。 因為不需要回溯，所有連續的 "a" 字元便已相符，所以第一個擷取群組會包含所有連續的 "a" 字元。 如果 "a" 字元後面未再接著至少一個 "a" 以外的字元，則比對失敗。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "aaaaa", "aaaaab" };
      string nonbacktrackingPattern = @"((?>a+))\w";
      Match match;

      foreach (string input in inputs) {
         Console.WriteLine("Input: {0}", input);
         match = Regex.Match(input, nonbacktrackingPattern);
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern);
         if (match.Success) { 
            Console.WriteLine("      Match: {0}", match.Value);
            Console.WriteLine("      Group 1: {0}", match.Groups[1].Value);
         }
         else {
            Console.WriteLine("      Match failed.");
         }   
      }
      Console.WriteLine();            
   }
}
// The example displays the following output:
//       Input: aaaaa
//          Pattern: ((?>a+))\w
//             Match failed.
//       Input: aaaaab
//          Pattern: ((?>a+))\w
//             Match: aaaaab
//             Group 1: aaaaa
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "aaaaa", "aaaaab" }
      Dim nonbacktrackingPattern As String = "((?>a+))\w"
      Dim match As Match

      For Each input As String In inputs
         Console.WriteLine("Input: {0}", input)
         match = Regex.Match(input, nonbacktrackingPattern)
         Console.WriteLine("   Pattern: {0}", nonbacktrackingPattern)
         If match.Success Then 
            Console.WriteLine("      Match: {0}", match.Value)
            Console.WriteLine("      Group 1: {0}", match.Groups(1).Value)
         Else 
            Console.WriteLine("      Match failed.")
         End If   
      Next
      Console.WriteLine()            
   End Sub
End Module
' The example displays the following output:
'       Input: aaaaa
'          Pattern: ((?>a+))\w
'             Match failed.
'       Input: aaaaab
'          Pattern: ((?>a+))\w
'             Match: aaaaab
'             Group 1: aaaaa
```

如需非回溯子運算式的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

### <a name="right-to-left-matching"></a>從右至左比對

從右至左比對，將 [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) 選項提供給 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態執行個體比對方法，即可指定此種比對。 當從右至左搜尋取代從左至右搜尋時，或在從右邊部分 (而非自左邊) 開始比對模式較有效率的情況中，這項功能很有用處。 如下例所示，使用由右至左比對會變更 Greedy (窮盡) 數量詞的行為。 此範例會搜尋兩次以數字結尾的句子。 使用 Greedy (窮盡) 數量詞 `+` 的由左至右搜尋，會比對句子中的六個數字其中一個，而由右至左搜尋會比對全部六個數字。 如需規則運算式模式的說明，請參閱本節前文說明 Lazy (最少) 數量詞的範例。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string greedyPattern = @".+(\d+)\.";
      string input = "This sentence ends with the number 107325.";
      Match match;

      // Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);

      // Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft);
      if (match.Success)
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups[1].Value);
      else
         Console.WriteLine("{0} finds no match.", greedyPattern);
   }
}
// The example displays the following output:
//       Number at end of sentence (left-to-right): 5
//       Number at end of sentence (right-to-left): 107325
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim greedyPattern As String = ".+(\d+)\."
      Dim input As String = "This sentence ends with the number 107325."
      Dim match As Match

      ' Match from left-to-right using lazy quantifier .+?.
      match = Regex.Match(input, greedyPattern)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (left-to-right): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If

      ' Match from right-to-left using greedy quantifier .+.
      match = Regex.Match(input, greedyPattern, RegexOptions.RightToLeft)
      If match.Success Then
         Console.WriteLine("Number at end of sentence (right-to-left): {0}", 
                           match.Groups(1).Value)
      Else
         Console.WriteLine("{0} finds no match.", greedyPattern)
      End If
   End Sub
End Module
' The example displays the following output:
'       Number at end of sentence (left-to-right): 5
'       Number at end of sentence (right-to-left): 107325
```

如需由右至左比對的詳細資訊，請參閱[規則運算式選項](options.md)。

### <a name="positive-and-negative-lookbehind"></a>左合樣和左不合樣

左合樣和左不合樣：**(?<**=_subexpression_**)** 適用於左合樣，而 **(?<!**_subexpression_**)** 適用於左不合樣。 此功能類似於本主題前文中所討論的向右合樣。 因為規則運算式引擎允許完整的由右至左比對，規則運算式允許無限制的向左合樣。 當巢狀子運算式為外部運算式的超集時，左合樣和左不合樣也可以用來避免產生巢狀數量詞。 具有此種巢狀數量詞的規則運算式通常效能不佳。 例如，下例會驗證字串是否以英數字元開頭和結尾，以及字串中的任何其他字元是否為較大子集之一。 它會構成用來驗證電子郵件地址的規則運算式的一部分；如需詳細資訊，請參閱[如何：確認字串是否為有效的電子郵件格式](verify-format.md)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                          "me.myself!" };
      string pattern = @"^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$";
      foreach (string input in inputs) {
         if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
            Console.WriteLine("{0}: Valid", input);
         else
            Console.WriteLine("{0}: Invalid", input);
      }
   }
}
// The example displays the following output:
//       jack.sprat: Valid
//       dog#: Invalid
//       dog#1: Valid
//       me.myself: Valid
//       me.myself!: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "jack.sprat", "dog#", "dog#1", "me.myself", 
                                 "me.myself!" }
      Dim pattern As String = "^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$"
      For Each input As String In inputs
         If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
            Console.WriteLine("{0}: Valid", input)
         Else
            Console.WriteLine("{0}: Invalid", input)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       jack.sprat: Valid
'       dog#: Invalid
'       dog#1: Valid
'       me.myself: Valid
'       me.myself!: Invalid
```

規則運算式 `^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`^` | 從字串的開頭開始比對。
`[A-Z0-9]` | 比對任何數值或英數字元。 (此比較不區分大小寫。)
`([-!#$%&'.*+/=?^`{}&#124;~\w])*` | 比對出現零次或多次的任何文字字元，或下列任一字元：-、!、#、$、%、&、'、.、*、+、/、=、?、^、`、{、}、&#124; 或 ~。
`(?<=[A-Z0-9])` | 向左合樣前一個字元，而該字元必須是數值或英數字元。 (此比較不區分大小寫。)
`$` | 在字串的結尾結束比對。
 
如需左合樣及左不合樣的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。


## <a name="related-topics"></a>相關主題

標題 | 說明
----- | ----------- 
[回溯](backtracking.md) | 提供規則運算式回溯如何擴展以尋找替代符合項目的相關資訊。
[編譯及重複使用](compilation.md) | 提供編譯和重複使用規則運算式以提升效能的相關資訊。
[執行緒安全](thread-safety.md) | 提供規則運算式執行緒安全的相關資訊，並說明何時應該同步處理規則運算式物件的存取。
[.NET 規則運算式](regular-expressions.md) | 提供規則運算式的程式設計語言方面的概觀。
[規則運算式物件模型](object-model.md) | 提供說明規則運算式類別使用方式的資訊和程式碼範例。
[規則運算式範例](regex-examples.md) | 包含程式碼範例，說明規則運算式在常見應用程式中的使用方式。
[規則運算式語言 - 快速參考](quick-ref.md) | 提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。
 
## <a name="reference"></a>參考資料

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)


