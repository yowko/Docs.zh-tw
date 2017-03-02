---
title: "規則運算式選項"
description: "規則運算式選項"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2db2c3e6-953e-4913-8168-d707c437f2df
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: af32095fa5f11ec7eba5924c969fbd6ab179cbd4
ms.lasthandoff: 03/02/2017

---

# <a name="regular-expression-options"></a>規則運算式選項

依預設，輸入字串與規則運算式模式中任何常值字元的比較會區分大小寫，規則運算式模式中的空白字元會解譯成常值空白字元，而規則運算式中的擷取群組會隱含也會明確命名。 您可以藉由指定規則運算式選項來修改這些預設規則運算式行為和幾個其他方面。 這些選項 (列示於下表) 可以內嵌為規則運算式模式的部分，或是提供給 [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態模式比對方法，以作為 [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 列舉值。 

RegexOptions 成員 | 內嵌字元 | 作用
------------------- | ---------------- | ------ 
[無](xref:System.Text.RegularExpressions.RegexOptions.None) | 無法使用 | 使用預設行為。 如需詳細資訊，請參閱[預設選項](#default-options)。
[IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) | **i** | 使用不區分大小寫的比對方式。 如需詳細資訊，請參閱[不區分大小寫的比對方式](#case-insensitive-matching)。
[多行](xref:System.Text.RegularExpressions.RegexOptions.Multiline) | **m** | 使用多行模式，其中 **^** 和 **$** 會比對每一行的開頭與結尾 (而不是輸入字串的開頭和結尾)。 如需詳細資訊，請參閱[多行模式](#multiline-mode)。
[Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) | **s** | 使用單行模式，其中句點 (**.**) 會比對每個字元 (而不是 **\n** 以外的每個字元)。 如需詳細資訊，請參閱[單行模式](#single-line-mode)。
[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) | **n** | 不擷取未命名的群組。 唯一有效的擷取是明確命名或編號的群組，格式如下：**(?<**_name_**>** _subexpression_**)**。 如需詳細資訊，請參閱[僅明確擷取](#explicit-captures-only)。
[已編譯](xref:System.Text.RegularExpressions.RegexOptions.Compiled) | 無法使用 | 將規則運算式編譯為組件。 如需詳細資訊，請參閱[編譯的規則運算式](#compiled-regular-expressions)。
[IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) | **x** | 在模式中排除未逸出的空白字元，並且在數字符號 (**#**) 後面啟用註解。 如需詳細資訊，請參閱[忽略空白字元](#ignore-white-space)。
[RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) | 無法使用 | 變更搜尋方向。 搜尋方向為由右至左，而不是由左至右。 如需詳細資訊，請參閱[由右至左模式](#right-to-left-mode)。
[ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) | 無法使用 | 為運算式啟用符合 ECMAScript 的行為。 如需詳細資訊，請參閱 [ECMAScript 比對行為](#ecmascript-matching-behavior)。
[CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) | 無法使用 | 忽略語言中的文化特性差異。 如需詳細資訊，請參閱[使用不因國別而異的文化特性比較](#comparison-using-the-invariant-culture)。
 
## <a name="specifying-the-options"></a>指定選項

指定規則運算式選項的方式有三種：

* 在如 [Regex.Regex(String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions)) 等 [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式的 *options* 參數中，或靜態 (Visual Basic 中為 Shared) 模式比對方法中，例如 [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions))。 *options* 參數是 [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 列舉值的位元 OR 組合。 

  當使用類別建構函式的 *options* 參數向給 [Regex](xref:System.Text.RegularExpressions.Regex) 執行個體提供選項時，選項會指派給 [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 屬性。 不過，[System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 屬性不會在規則運算式模式中反映內嵌選項。 

  下列範例提供一個實例。 其使用 [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法的 *options* 參數來啟用不區分大小寫比對，並且在識別以字母 "d" 開頭的文字時，忽略模式空白字元。

  ```csharp
  string pattern = @"d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  RegexOptions options = RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace;
  
  foreach (Match match in Regex.Matches(input, pattern, options))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."
  Dim options As RegexOptions = RegexOptions.IgnoreCase Or RegexOptions.IgnorePatternWhitespace

  For Each match As Match In Regex.Matches(input, pattern, options)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* 使用語法 **(?imnsx-imnsx)**，在規則運算式模式中套用內嵌選項。 此選項會從定義選項的位置開始套用至模式，直到模式結尾，或是有其他內嵌選項取消定義選項為止。 請注意，[Regex](xref:System.Text.RegularExpressions.Regex) 執行個體的 [System.Text.RegularExpressions.RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 屬性 不會反映這些內嵌選項。 如需詳細資訊，請參閱[規則運算式中的其他建構](miscellaneous.md)主題。

  下列範例提供一個實例。 其使用內嵌選項來啟用不區分大小寫比對，並且在識別以字母 "d" 開頭的文字時，忽略模式空白字元。

  ```csharp
  string pattern = @"(?ix) d \w+ \s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix) d \w+ \s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9.  
  ```

* 使用語法 **(?imnsx-imnsx:**_subexpression_**)**，在規則運算式模式的特定群組建構中套用內嵌選項。 如果選項集前面沒有符號，會開啟選項集；如果選項集前面有減號，則會關閉選項集。 (**?** 是語言建構語法的固定部分，無論啟用或停用選項，都需要此部分。)此選項僅適用於該群組。 如需詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

  下列範例提供一個實例。 其使用群組建構中的內嵌選項來啟用不區分大小寫比對，並且在識別以字母 "d" 開頭的文字時，忽略模式空白字元。

  ```csharp
  string pattern = @"\b(?ix: d \w+)\s";
  string input = "Dogs are decidedly good pets.";
  
  foreach (Match match in Regex.Matches(input, pattern))
     Console.WriteLine("'{0}// found at index {1}.", match.Value, match.Index);
  // The example displays the following output:
  //    'Dogs // found at index 0.
  //    'decidedly // found at index 9.      
  ```

  ```vb
  Dim pattern As String = "\b(?ix: d \w+)\s"
  Dim input As String = "Dogs are decidedly good pets."

  For Each match As Match In Regex.Matches(input, pattern)
     Console.WriteLine("'{0}' found at index {1}.", match.Value, match.Index)
  Next
  ' The example displays the following output:
  '    'Dogs ' found at index 0.
  '    'decidedly ' found at index 9. 
  ```


如果將選項指定為內嵌，選項或選項集前面的減號 (-) 會關閉那些選項。 例如，內嵌建構 **(?ix-ms)** 會開啟 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 和 [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 選項，並關閉 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 和 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項。 依預設，會關閉所有規則運算式選項。

> [!NOTE]
> 如果建構函式或方法呼叫的 options 參數指定的規則運算式選項，與規則運算式模式中指定內嵌的選項相衝突，則會使用內嵌選項。
 

*options* 參數和內嵌都可以用來設定下列五個規則運算式選項：

* [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase)

* [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)

* [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline)

* [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture)

* [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace)

下列五個規則運算式選項可以用 *options* 參數來設定，但不能設定內嵌：

* [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)

* [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled)

* [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft)

* [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant)

* [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript)

## <a name="determining-the-options"></a>決定選項

您可以判定，在擷取唯讀 [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) 屬性的值來將物件具現化時，提供了哪些選項給 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。

若要測試任何選項 ([RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) 除外) 是否存在，請使用 [Regex.Options](xref:System.Text.RegularExpressions.Regex.Options) 屬性的值和您感興趣的 [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 值來執行 AND 作業。 然後測試結果是否等於 [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 值。 下列範例會測試是否已設定 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 選項。 

```csharp
if ((rgx.Options & RegexOptions.IgnoreCase) == RegexOptions.IgnoreCase)
   Console.WriteLine("Case-insensitive pattern comparison.");
else
   Console.WriteLine("Case-sensitive pattern comparison.");
```

```vb
If (rgx.Options And RegexOptions.IgnoreCase) = RegexOptions.IgnoreCase Then
   Console.WriteLine("Case-insensitive pattern comparison.")
Else
   Console.WriteLine("Case-sensitive pattern comparison.")
End If 
```

請如下例所示，測試 [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)，判斷 [RegexOptions](xref:System.Text.RegularExpressions.RegexOptions) 屬性的值是否等於 [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None)。 

```csharp
if (rgx.Options == RegexOptions.None)
   Console.WriteLine("No options have been set.");
```

```vb
If rgx.Options = RegexOptions.None Then
   Console.WriteLine("No options have been set.")
End If
```

以下各節會列出 .NET 中規則運算式所支援的選項。 

## <a name="default-options"></a>預設選項

[RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) 選項指出未指定任何選項，而規則運算式引擎使用其預設行為。 其中包括下列項目：

* 模式被解譯為標準規則運算式，而不是 ECMAScript 規則運算式。

* 在輸入字串中，由左至右比對規則運算式模式。

* 比較會區分大小寫。

* **^** 和 **$** 語言項目會比對輸入字串的開頭和結尾。

* **.** 語言項目會比對 **\n** 以外的每個字元。

* 規則運算式模式中的任何空白字元會被解譯成常值空白字元。

* 將模式與輸入字串比較時，會使用目前文化特性的慣例。 

* 規則運算式模式中的擷取群組是隱含的，也是明確的。 

> [!NOTE]
> [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) 選項沒有內嵌對等項目。 將規則運算式選項套用為內嵌時，會關閉特定選項，依據各選項逐一還原預設行為。 例如，`(?i)` 會開啟不區分大小寫比較，而 `(?-i)` 會還原預設區分大小寫比較。
 
因為 [RegexOptions.None](xref:System.Text.RegularExpressions.RegexOptions.None) 選項代表規則運算式引擎的預設行為，所以很少明確地指定在方法呼叫中， 而是會呼叫不含 options 參數的建構函式或靜態模式比對方法。

## <a name="case-insensitive-matching"></a>不區分大小寫的比對方式

[RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 選項 (或 **i** 內嵌選項) 提供不區分大小寫比對。 依預設，會使用目前文化特性的大小寫慣例。

下列範例定義規則運算式模式 `\bthe\w*\b`，它會比對以 "the" 開頭的所有文字。 因為第一次呼叫 Match 方法是使用預設的區分大小寫比較，所以輸出指出未比對句子開頭的 "The" 字串。 選項設為 [IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 來呼叫 [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法時，才會加以比對。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bthe\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bthe\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern, _
                                               RegexOptions.IgnoreCase)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

下列範例會修改上一個範例中的規則運算式模式，改為使用內嵌選項，而不是使用 *options* 參數，以提供不區分大小寫比較。 第一個模式在群組建構中定義不區分大小寫選項，只套用於字串 "the" 中的字母 "t"。 因為選項建構出現在模式開頭，所以第二個模式會將不區分大小寫選項套用於整個規則運算式。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?i:t)he\w*\b";
      string input = "The man then told them about that event.";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);

      Console.WriteLine();
      pattern = @"(?i)\bthe\w*\b";
      foreach (Match match in Regex.Matches(input, pattern, 
                                            RegexOptions.IgnoreCase))
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
//       
//       Found The at index 0.
//       Found then at index 8.
//       Found them at index 18.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?i:t)he\w*\b"
      Dim input As String = "The man then told them about that event."
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
      Console.WriteLine()
      pattern = "(?i)\bthe\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Found {0} at index {1}.", match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
'       
'       Found The at index 0.
'       Found then at index 8.
'       Found them at index 18.
```

## <a name="multiline-mode"></a>多行模式

[RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項 (或 **m** 內嵌選項) 可讓規則運算式引擎處理構成多行的輸入字串。 它會變更 **^** 和 **$** 語言項目的解譯，以便比對字行的開頭和結尾，而不是輸入字串的開頭和結尾。 

依預設，**$** 只會比對輸入字串的結尾。 如果您指定 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項，則會比對新行字元 (**(\n)**) 或輸入字串的結尾。 不過，並不會比對歸位字元/換行字元組合。 若要順利比對，請使用子運算式 **\r?$**，而不只是使用 **$**。 

下列範例會擷取保齡球員的名字和分數，並將其加入 [SortedList&lt;TKey, TValue&gt;](xref:System.Collections.Generic.SortedList%602) 集合，以遞減順序排序。 呼叫 [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法兩次。 在第一次呼叫方法時，規則運算式為 `^(\w+)\s(\d+)$`，且沒有設定選項。 如輸出所示，因為規則運算式引擎無法隨著輸入字串的開頭和結尾來比對輸入模式，所以沒有找到相符項目。 在第二次呼叫方法時，規則運算式變更為 `^(\w+)\s(\d+)\r?$`，且選項設為 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)。 如輸出所示，已成功比對名字和分數，且分數以遞減順序顯示。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" + 
                     "Sam 208\n" + 
                     "Allison 211\n" + 
                     "Gwen 171\n"; 
      string pattern = @"^(\w+)\s(\d+)$";
      bool matched = false;

      Console.WriteLine("Without Multiline option:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);
         matched = true;
      }
      if (! matched)
         Console.WriteLine("   No matches.");
      Console.WriteLine();

      // Redefine pattern to handle multiple lines.
      pattern = @"^(\w+)\s(\d+)\r*$";
      Console.WriteLine("With multiline option:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Int32.Parse(match.Groups[2].Value), (string) match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y)
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//   Without Multiline option:
//      No matches.
//   
//   With multiline option:
//   Allison: 211
//   Sam: 208
//   Gwen: 171
//   Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "^(\w+)\s(\d+)$"
      Dim matched As Boolean = False

      Console.WriteLine("Without Multiline option:")
      For Each match As Match In Regex.Matches(input, pattern)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
         matched = True
      Next
      If Not matched Then Console.WriteLine("   No matches.")
      Console.WriteLine()

      ' Redefine pattern to handle multiple lines.
      pattern = "^(\w+)\s(\d+)\r*$"
      Console.WriteLine("With multiline option:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Without Multiline option:
'       No matches.
'    
'    With multiline option:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

規則運算式模式 `^(\w+)\s(\d+)\r*$` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`^` | 從字行開頭開始。
`(\w+)` | 比對一個或多個文字字元。 這是第一個擷取群組。
`\s` | 比對空白字元。
`(\d+)` | 比對一個或多個十進位數字。 這是第二個擷取群組。
`\r?` | 比對零或一個歸位字元。
`$` | 在字行結尾結束。
 
下列範例與上一個範例相同，只是下列範例是使用內嵌選項 **(?m)** 來設定多行選項。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      SortedList<int, string> scores = new SortedList<int, string>(new DescendingComparer<int>());

      string input = "Joe 164\n" +  
                     "Sam 208\n" +  
                     "Allison 211\n" +  
                     "Gwen 171\n"; 
      string pattern = @"(?m)^(\w+)\s(\d+)\r*$";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.Multiline))
         scores.Add(Convert.ToInt32(match.Groups[2].Value), match.Groups[1].Value);

      // List scores in descending order. 
      foreach (KeyValuePair<int, string> score in scores)
         Console.WriteLine("{0}: {1}", score.Value, score.Key);
   }
}

public class DescendingComparer<T> : IComparer<T>
{
   public int Compare(T x, T y) 
   {
      return Comparer<T>.Default.Compare(x, y) * -1;       
   }
}
// The example displays the following output:
//    Allison: 211
//    Sam: 208
//    Gwen: 171
//    Joe: 164
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim scores As New SortedList(Of Integer, String)(New DescendingComparer(Of Integer)())

      Dim input As String = "Joe 164" + vbCrLf + _
                            "Sam 208" + vbCrLf + _
                            "Allison 211" + vbCrLf + _
                            "Gwen 171" + vbCrLf
      Dim pattern As String = "(?m)^(\w+)\s(\d+)\r*$"

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.Multiline)
         scores.Add(CInt(match.Groups(2).Value), match.Groups(1).Value)
      Next
      ' List scores in descending order. 
      For Each score As KeyValuePair(Of Integer, String) In scores
         Console.WriteLine("{0}: {1}", score.Value, score.Key)
      Next
   End Sub
End Module

Public Class DescendingComparer(Of T) : Implements IComparer(Of T)
   Public Function Compare(x As T, y As T) As Integer _
          Implements IComparer(Of T).Compare
      Return Comparer(Of T).Default.Compare(x, y) * -1       
   End Function
End Class
' The example displays the following output:
'    Allison: 211
'    Sam: 208
'    Gwen: 171
'    Joe: 164
```

## <a name="single-line-mode"></a>單行模式

[RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項 (或 s 內嵌選項) 會使規則運算式引擎將輸入字串當作其包含單行。 其作法是變更句點 (**.**) 語言項目的行為，使其比對每個字元，而不是比對新行字元 **\n** 或 \u000A 以外的每個字元。

下例說明 . 的 語言項目行為，在您使用 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項時如何變更。 規則運算式 `^.+` 會從字串開頭開始，比對每一個字元。 根據預設，比對會在第一行結尾結束。規則運算式模式會比對歸位字元 **\r** 或 \u000D，但不會比對 **\n**。 由於 [RegexOptions.Singleline](xref:System.Text.RegularExpressions.RegexOptions.Singleline) 選項會將整個輸入字串解譯為單行，因此它會比對輸入字串中的每個字元，包括 **\n**。

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

下列範例與上一個範例相同，只是下列範例是使用內嵌選項 **(?s)** 來啟用單行模式。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {      
      string pattern = "(?s)^.+";
      string input = "This is one line and" + Environment.NewLine + "this is the second.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(Regex.Escape(match.Value));
   }
}
// The example displays the following output:
//       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(?s)^.+"
      Dim input As String = "This is one line and" + vbCrLf + "this is the second."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(Regex.Escape(match.Value))
      Next
   End Sub
End Module
' The example displays the following output:
'       This\ is\ one\ line\ and\r\nthis\ is\ the\ second\.
```

## <a name="explicit-captures-only"></a>僅明確擷取

依預設，擷取群組的定義方式是在規則運算式模式中使用括號。 具名群組是以 **(?<**_name_**>** _subexpression_**)** 語言選項來指派名稱或號碼，而未具名群組可透過索引來存取。 在 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中，未具名群組的前面是具名群組。 

群組建構通常只用來將數量詞套用至多個語言項目，我們對所擷取的子字串並不感興趣。 例如，如果下列運算式：

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

目的只是要從文件中擷取以句點、驚嘆號或問號結尾的句子，則我們只對所產生的句子 (由 [Match](xref:System.Text.RegularExpressions.Match) 物件代表) 感興趣。 我們對集合中的個別文字並不感興趣。 

非後續使用的擷取群組可能會耗用很多資源，因為規則運算式引擎必須同時填入 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 集合物件。 或者，您也可以使用 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 選項或 **n** 內嵌選項，指定唯一有效的擷取是 **(?<**_name_**>** _subexpression_**)** 建構所指定的明確命名或編號群組。 

下列範例顯示，當呼叫 [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32)) 方法時，如果沒有使用 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 選項，`\b\(?((\w+),?\s?)+[\.!?]\)?` 規則運算式模式所傳回的比對相關資訊。 當第一個方法呼叫的輸出顯示時，規則運算式引擎會以擷取子字串的相關資訊完整填入 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 集合物件。 因為呼叫第二個方法時，選項設為 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture)，所以沒有擷取群組的資訊。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";
      Console.WriteLine("With implicit captures:");
      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
      Console.WriteLine();
      Console.WriteLine("With explicit captures only:");
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.ExplicitCapture))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//    With implicit captures:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//       Group 1: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//       Group 2: sentence
//          Capture 0: This
//          Capture 1: is
//          Capture 2: the
//          Capture 3: first
//          Capture 4: sentence
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//       Group 1: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//       Group 2: masterpiece
//          Capture 0: Is
//          Capture 1: it
//          Capture 2: the
//          Capture 3: beginning
//          Capture 4: of
//          Capture 5: a
//          Capture 6: literary
//          Capture 7: masterpiece
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//       Group 1: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//       Group 2: not
//          Capture 0: I
//          Capture 1: think
//          Capture 2: not
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
//       Group 1: paragraph
//          Capture 0: Instead,
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//       Group 2: paragraph
//          Capture 0: Instead
//          Capture 1: it
//          Capture 2: is
//          Capture 3: a
//          Capture 4: nonsensical
//          Capture 5: paragraph
//    
//    With explicit captures only:
//    The match: This is the first sentence.
//       Group 0: This is the first sentence.
//          Capture 0: This is the first sentence.
//    The match: Is it the beginning of a literary masterpiece?
//       Group 0: Is it the beginning of a literary masterpiece?
//          Capture 0: Is it the beginning of a literary masterpiece?
//    The match: I think not.
//       Group 0: I think not.
//          Capture 0: I think not.
//    The match: Instead, it is a nonsensical paragraph.
//       Group 0: Instead, it is a nonsensical paragraph.
//          Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?((?>\w+),?\s?)+[\.!?]\)?"
      Console.WriteLine("With implicit captures:")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
      Console.WriteLine()
      Console.WriteLine("With explicit captures only:")
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.ExplicitCapture)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'    With implicit captures:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'       Group 1: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'       Group 2: sentence
'          Capture 0: This
'          Capture 1: is
'          Capture 2: the
'          Capture 3: first
'          Capture 4: sentence
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'       Group 1: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'       Group 2: masterpiece
'          Capture 0: Is
'          Capture 1: it
'          Capture 2: the
'          Capture 3: beginning
'          Capture 4: of
'          Capture 5: a
'          Capture 6: literary
'          Capture 7: masterpiece
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'       Group 1: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'       Group 2: not
'          Capture 0: I
'          Capture 1: think
'          Capture 2: not
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
'       Group 1: paragraph
'          Capture 0: Instead,
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'       Group 2: paragraph
'          Capture 0: Instead
'          Capture 1: it
'          Capture 2: is
'          Capture 3: a
'          Capture 4: nonsensical
'          Capture 5: paragraph
'    
'    With explicit captures only:
'    The match: This is the first sentence.
'       Group 0: This is the first sentence.
'          Capture 0: This is the first sentence.
'    The match: Is it the beginning of a literary masterpiece?
'       Group 0: Is it the beginning of a literary masterpiece?
'          Capture 0: Is it the beginning of a literary masterpiece?
'    The match: I think not.
'       Group 0: I think not.
'          Capture 0: I think not.
'    The match: Instead, it is a nonsensical paragraph.
'       Group 0: Instead, it is a nonsensical paragraph.
'          Capture 0: Instead, it is a nonsensical paragraph.
```

規則運算式模式 `\b\(?((?>\w+),?\s?)+[\.!?]\)?` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字邊界開始。
`\(?` | 比對出現零或一次的左括號 ("(")。
`(?>\w+),?` | 比對後面接著零或一個逗號的一或多個文字字元。 比對文字字元時，請勿回溯。
`\s?` | 比對零個或一個空白字元。
`((\w+),?\s?)+` | 一或多次比對一或多個文字字元、零或一個逗號及零或一個空白字元的組合。
`[\.!?]\)?` | 比對這三種標點符號中的任一種，後面接零或一個右括號 (")")。
 
您也可以使用 **(?n)** 內嵌元素來隱藏自動擷取。 下列範例會修改上一個規則運算式模式，以使用 **(?n)** 內嵌項目，而不是使用 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 選項。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?n)\b\(?((?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

最後，您可以使用內嵌群組項目 **(?n:)**，針對每個群組逐一隱藏自動擷取。 下列範例會修改上一個模式，以隱藏外部群組 `((?>\w+),?\s?)` 中的未具名擷取。 請注意，這也會隱藏內部群組中的未具名擷取。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern))
      {
         Console.WriteLine("The match: {0}", match.Value);
         int groupCtr = 0;
         foreach (Group group in match.Groups)
         {
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value);
            groupCtr++;
            int captureCtr = 0;
            foreach (Capture capture in group.Captures)
            {
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value);
               captureCtr++;
            }
         }
      }
   }
}
// The example displays the following output:
//       The match: This is the first sentence.
//          Group 0: This is the first sentence.
//             Capture 0: This is the first sentence.
//       The match: Is it the beginning of a literary masterpiece?
//          Group 0: Is it the beginning of a literary masterpiece?
//             Capture 0: Is it the beginning of a literary masterpiece?
//       The match: I think not.
//          Group 0: I think not.
//             Capture 0: I think not.
//       The match: Instead, it is a nonsensical paragraph.
//          Group 0: Instead, it is a nonsensical paragraph.
//             Capture 0: Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b\(?(?n:(?>\w+),?\s?)+[\.!?]\)?"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("The match: {0}", match.Value)
         Dim groupCtr As Integer = 0
         For Each group As Group In match.Groups
            Console.WriteLine("   Group {0}: {1}", groupCtr, group.Value)
            groupCtr += 1
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               Console.WriteLine("      Capture {0}: {1}", captureCtr, capture.Value)
               captureCtr += 1
            Next
         Next
      Next
   End Sub
End Module
' The example displays the following output:
'       The match: This is the first sentence.
'          Group 0: This is the first sentence.
'             Capture 0: This is the first sentence.
'       The match: Is it the beginning of a literary masterpiece?
'          Group 0: Is it the beginning of a literary masterpiece?
'             Capture 0: Is it the beginning of a literary masterpiece?
'       The match: I think not.
'          Group 0: I think not.
'             Capture 0: I think not.
'       The match: Instead, it is a nonsensical paragraph.
'          Group 0: Instead, it is a nonsensical paragraph.
'             Capture 0: Instead, it is a nonsensical paragraph.
```

## <a name="compiled-regular-expressions"></a>編譯的規則運算式

預設會解譯 .NET 中的規則運算式。 將 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化，或是呼叫靜態 [Regex](xref:System.Text.RegularExpressions.Regex) 方法時，會將規則運算式模式剖析成一組自訂作業碼，而解譯器會使用這些作業碼來執行規則運算式。 這需要有所取捨：要將初始化規則運算式引擎的成本降到最低，就會犧牲執行時期效能。

您可以使用 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項，以編譯的規則運算式來取代解譯的規則運算式。 在這個情況下，將模式傳遞至規則運算式時，會將該模式剖析成一組自訂作業碼，然後再轉換成 Microsoft 中繼語言 (MSIL)，可直接傳遞至通用語言執行平台。 編譯的規則運算式可充分提升執行時期效能，但會犧牲初始化時間。

> [!NOTE]
> 若要編譯規則運算式，唯一的方法就是提供 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 值給 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態模式比對方法的 options 參數。 無法以內嵌選項來提供此值。 
 

在呼叫靜態和執行個體規則運算式時，都可以使用編譯的規則運算式。 在靜態規則運算式中，會將 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項傳遞至規則運算式模式比對方法的 options 參數。 在執行個體規則運算式中，則會傳遞至 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式的 options 參數。 在這兩個情況中，都會增強效能。 

不過，只有在下列條件下，效能才會提升：

* 在對規則運算式模式比對方法的多個呼叫中，都會使用代表特定規則運算式的 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。

* [Regex](xref:System.Text.RegularExpressions.Regex) 物件不能超出範圍，因此可以重複使用。

* 在對規則運算式模式比對方法的多個呼叫中，會使用靜態規則運算式。 (效能提升是有可能的，因為規則運算式引擎會快取靜態方法呼叫中所使用的規則運算式。) 

## <a name="ignore-white-space"></a>忽略空白字元

依預設，規則運算式模式中的空白字元很重要；它會強制規則運算式引擎比對輸入字串中的空白字元。 因此，規則運算式 `"\b\w+\s"` 和 `"\b\w+ "` 是大致相等的規則運算式。 此外，在規則運算式模式中遇到數字符號 (**#**) 時，會將其解譯成常值字元，以供比對。

[RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 選項 (或 **x** 內嵌選項) 會變更此預設行為，如下所示︰

* 規則運算式模式中未逸出的空白字元會被忽略。 若要在規則運算式模式中使用空白字元，就必須將它逸出 (例如，**\s** 或 "**\** ")。

* 數字符號 (**#**) 會解譯成註解的開頭，而不是常值字元。 規則運算式模式中，從 **#** 字元到字串結尾的所有文字會被解譯成註解。

不過，在下列案例中，即使您使用 [RegexOptions.IgnorePatternWhitespace](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 選項，也不會忽略規則運算式中的空白字元： 

* 字元類別中的空白字元一律解譯為常值。 例如，規則運算式模式 `[ .,;:]` 會比對任何單一空白字元、句點、逗號、分號或冒號。 

* 方括號數量詞中不允許空白字元，例如 **{**_n_**}**、**{**_n_**,}** 和 **{**_n_**,**_m_**}**。 例如，規則運算式模式 **\d{1. 3}** 無法比對從一到三位數的任何數字序列，因為其中包含空白字元。 

* 引進語言項目的字元序列中，不允許空白字元。 例如:  

    * 語言項目 **(?:**_subexpression_**)** 代表非擷取群組，而該項目的 **(?:** 部分不能有內嵌空格。 模式 **(? :**_subexpression_**)** 會在執行時期擲回 [ArgumentException](xref:System.ArgumentException)，因為規則運算式引擎無法剖析該模式，而模式 **(? :**_subexpression_**)** 無法比對 *subexpression*。

    * 語言項目 **\p{**_name_**}** 代表 Unicode 類別或具名資料區塊，不能在此項目的 **\p{** 部分中包含內嵌空格。 如果包含空白字元，則此項目會在執行時期擲回 [ArgumentException](xref:System.ArgumentException)。 

啟用此選項有助於簡化通常很難剖析及了解的規則運算式。 其增進了可讀性，並且讓規則運算式可以被記載下來。 

下列範例定義下列規則運算式模式：

`\b \(? ( (?>\w+) ,?\s? )+ [\.!?] \)? # Matches an entire sentence`.

此模式類似[僅明確擷取](#explicit-captures-only)一節中定義的模式，但會使用 [RegexOptions.IgnorePatternWhitespace ](xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace) 選項忽略模式的空白字元。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"\b\(?((?>\w+),?\s?)+[\.!?]\)?";

      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnorePatternWhitespace)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

下列範例使用內嵌選項 **(?x)** 來忽略模式空白字元。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is the first sentence. Is it the beginning " + 
                     "of a literary masterpiece? I think not. Instead, " + 
                     "it is a nonsensical paragraph.";
      string pattern = @"(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.";

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This is the first sentence.
//       Is it the beginning of a literary masterpiece?
//       I think not.
//       Instead, it is a nonsensical paragraph.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is the first sentence. Is it the beginning " + _
                            "of a literary masterpiece? I think not. Instead, " + _
                            "it is a nonsensical paragraph."
      Dim pattern As String = "(?x)\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence."

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This is the first sentence.
'       Is it the beginning of a literary masterpiece?
'       I think not.
'       Instead, it is a nonsensical paragraph.
```

## <a name="right-to-left-mode"></a>由右至左模式

依預設，規則運算式引擎會由左至右搜尋。 您可以使用 [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) 選項來反轉搜尋方向。 此搜尋會自動從字串最後一個字元的位置開始。 針對包含開始位置參數的模式比對方法，例如 [Regex.Match(String, Int32)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.Int32))，開始位置是要開始搜尋之最右邊字元位置的索引。 

> [!NOTE]
> 若要使用由右至左模式，唯一的方法就是提供 [RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) 值給 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態模式比對方法的 options 參數。 無法以內嵌選項來提供此值。 
 

[RegexOptions.RightToLeft](xref:System.Text.RegularExpressions.RegexOptions.RightToLeft) 選項只會變更搜尋方向，並不會由右至左解譯規則運算式模式。 例如，規則運算式 `\bb\w+\s` 會比對字母 "b" 開頭、後接空白字元的文字。 在下列範例中，輸入字串是由包含一或數個 "b" 字元的三個單字所組成。 第一個單字以 "b" 開頭，第二個單字以 "b" 結尾，而第三個單字中間包含兩個 "b" 字元。 如範例輸出所示，只有第一個單字符合規則運算式模式。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\bb\w+\s";
      string input = "builder rob rabble";
      foreach (Match match in Regex.Matches(input, pattern, RegexOptions.RightToLeft))
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);     
   }
}
// The example displays the following output:
//       'builder ' found at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\bb\w+\s"
      Dim input As String = "builder rob rabble"
      For Each match As Match In Regex.Matches(input, pattern, RegexOptions.RightToLeft)
         Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)     
      Next
   End Sub
End Module
' The example displays the following output:
'       'builder ' found at position 0.
```

另請注意，右合樣判斷提示 (**(?**=_subexpression_**)** 語言項目) 和左合樣判斷提示 (**(?<**=_subexpression_**)** 語言項目) 沒有變更方向。 右合樣判斷提示朝右看，而左合樣判斷提示朝左看。 例如，規則運算式 `(?<=\d{1,2}\s)\w+,?\s\d{4}` 使用左合樣判斷提示來測試月份名稱前面的日期。 然後規則運算式會比對月和年。 如需右合樣判斷提示和左合樣判斷提示的詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "1 May 1917", "June 16, 2003" };
      string pattern = @"(?<=\d{1,2}\s)\w+,?\s\d{4}";

      foreach (string input in inputs)
      {
         Match match = Regex.Match(input, pattern, RegexOptions.RightToLeft);
         if (match.Success)
            Console.WriteLine("The date occurs in {0}.", match.Value);
         else
            Console.WriteLine("{0} does not match.", input);
      }
   }
}
// The example displays the following output:
//       The date occurs in May 1917.
//       June 16, 2003 does not match.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "1 May 1917", "June 16, 2003" }
      Dim pattern As String = "(?<=\d{1,2}\s)\w+,?\s\d{4}"

      For Each input As String In inputs
         Dim match As Match = Regex.Match(input, pattern, RegexOptions.RightToLeft)
         If match.Success Then
            Console.WriteLine("The date occurs in {0}.", match.Value)
         Else
            Console.WriteLine("{0} does not match.", input)
         End If
      Next
   End Sub
End Module
' The example displays the following output:
'       The date occurs in May 1917.
'       June 16, 2003 does not match.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`(?<=\d{1,2}\s)` | 相符項目的開頭前面必須要有一個或兩個十進位數字後接空格。
`\w+` | 比對一個或多個文字字元。
`,?` | 比對零或一個逗號字元。
`\s` | 比對空白字元。
`\d{4}` | 比對四個十進位數字。
 
## <a name="ecmascript-matching-behavior"></a>ECMAScript 比對行為

依預設，在比對規則運算式模式與輸入文字時，規則運算式引擎會使用標準行為。 不過，您可以指定 [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) 選項，以指示規則運算式引擎使用 ECMAScript 相符行為。 

> [!NOTE]
> 若要使用由右至左模式，唯一的方法就是提供 [RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) 值給 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態模式比對方法的 options 參數。 無法以內嵌選項來提供此值。 
 
[RegexOptions.ECMAScript](xref:System.Text.RegularExpressions.RegexOptions.ECMAScript) 選項只能結合 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 和 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項。 在規則運算式中使用任何其他選項將會導致 [ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException)。

ECMAScript 的行為與標準規則運算式有三個不同層面：字元類別語法、自我參考擷取群組，以及八進位與反向參考解譯。 

* 字元類別語法。 因為標準規則運算式支援 Unicode，而 ECMAScript 不支援，所以 ECMAScript 中的字元類別有較多的語法限制，而且有些字元類別語言項目有不同的意義。 例如，ECMAScript 不支援語言項目 (例如 Unicode 類別) 或資料區塊項目 *\p* 和 **\P**。 同樣地，比對文字字元的 **\w** 元素，在使用 ECMAScript 時相當於 **[a-zA-Z_0-9]** 字元類別，使用標準行為時相當於 **[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]**。 如需詳細資訊，請參閱[規則運算式中的字元類別](classes.md)。

  下列範例說明標準與 ECMAScript 模式比對之間的差異。 其定義規則運算式 `\b(\w+\s*)+`，可比對後接空白字元的文字。 該輸入包含兩個字串，一個使用 Latin 字元集，另一個使用 Cyrillic 字元集。 如輸出所示，呼叫使用 ECMAScript 比對的 [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法時，無法比對 Cyrillic 文字，而使用標準比對的方法呼叫則可比對這些文字。 

  ```csharp
  using System;
  using System.Text.RegularExpressions;
  
  public class Example
  {
     public static void Main()
     {
        string[] values = { "целый мир", "the whole world" };
        string pattern = @"\b(\w+\s*)+";
        foreach (var value in values)
        {
           Console.Write("Canonical matching: ");
           if (Regex.IsMatch(value, pattern))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
  
           Console.Write("ECMAScript matching: ");
           if (Regex.IsMatch(value, pattern, RegexOptions.ECMAScript))
              Console.WriteLine("'{0}' matches the pattern.", value);
           else
              Console.WriteLine("{0} does not match the pattern.", value);
           Console.WriteLine();
        }
     }
  }
  // The example displays the following output:
  //       Canonical matching: 'целый мир' matches the pattern.
  //       ECMAScript matching: целый мир does not match the pattern.
  //       
  //       Canonical matching: 'the whole world' matches the pattern.
  //       ECMAScript matching: 'the whole world' matches the pattern.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim values() As String = { "целый мир", "the whole world" }
        Dim pattern As String = "\b(\w+\s*)+"
        For Each value In values
           Console.Write("Canonical matching: ")
           If Regex.IsMatch(value, pattern)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If

           Console.Write("ECMAScript matching: ")
           If Regex.IsMatch(value, pattern, RegexOptions.ECMAScript)
              Console.WriteLine("'{0}' matches the pattern.", value)
           Else
              Console.WriteLine("{0} does not match the pattern.", value)
           End If
           Console.WriteLine()
        Next
     End Sub
  End Module
  ' The example displays the following output:
  '       Canonical matching: 'целый мир' matches the pattern.
  '       ECMAScript matching: целый мир does not match the pattern.
  '       
  '       Canonical matching: 'the whole world' matches the pattern.
  '       ECMAScript matching: 'the whole world' matches the pattern.
  ```

* 自我參考擷取群組。 具有自我反向參考的規則運算式擷取類別必須以每個擷取反覆項目來更新。 如下列範例所示，使用 ECMAScript 時，此功能可讓規則運算式 `((a+)(\1) ?)+` 比對輸入字串 " aa aaaa aaaaaa "，使用標準比對時則不能。 

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     static string pattern;
  
     public static void Main()
     {
        string input = "aa aaaa aaaaaa "; 
        pattern = @"((a+)(\1) ?)+";
  
        // Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern));

        // Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript));
     }   

     private static void AnalyzeMatch(Match m)
     {
        if (m.Success)
        {
           Console.WriteLine("'{0}' matches {1} at position {2}.",  
                             pattern, m.Value, m.Index);
           int grpCtr = 0;
           foreach (Group grp in m.Groups)
           {
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value);
              grpCtr++;
              int capCtr = 0;
              foreach (Capture cap in grp.Captures)
              {
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value);
                 capCtr++;
              }
           }
        }
        else
        {
           Console.WriteLine("No match found.");
        }   
        Console.WriteLine();
     }
  }
  // The example displays the following output:
  //    No match found.
  //    
  //    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  //       0: 'aa aaaa aaaaaa '
  //          0: 'aa aaaa aaaaaa '
  //       1: 'aaaaaa '
  //          0: 'aa '
  //          1: 'aaaa '
  //          2: 'aaaaaa '
  //       2: 'aa'
  //          0: 'aa'
  //          1: 'aa'
  //          2: 'aa'
  //       3: 'aaaa '
  //          0: ''
  //          1: 'aa '
  //          2: 'aaaa '
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Dim pattern As String

     Public Sub Main()
        Dim input As String = "aa aaaa aaaaaa " 
        pattern = "((a+)(\1) ?)+"
  
        ' Match input using canonical matching.
        AnalyzeMatch(Regex.Match(input, pattern))

        ' Match input using ECMAScript.
        AnalyzeMatch(Regex.Match(input, pattern, RegexOptions.ECMAScript))
     End Sub   

     Private Sub AnalyzeMatch(m As Match)
        If m.Success
           Console.WriteLine("'{0}' matches {1} at position {2}.", _ 
                             pattern, m.Value, m.Index)
           Dim grpCtr As Integer = 0
           For Each grp As Group In m.Groups
              Console.WriteLine("   {0}: '{1}'", grpCtr, grp.Value)
              grpCtr += 1
              Dim capCtr As Integer = 0
              For Each cap As Capture In grp.Captures
                 Console.WriteLine("      {0}: '{1}'", capCtr, cap.Value)
                 capCtr += 1
              Next
           Next
        Else
           Console.WriteLine("No match found.")
        End If   
        Console.WriteLine()
     End Sub
  End Module
  ' The example displays the following output:
  '    No match found.
  '    
  '    '((a+)(\1) ?)+' matches aa aaaa aaaaaa  at position 0.
  '       0: 'aa aaaa aaaaaa '
  '          0: 'aa aaaa aaaaaa '
  '       1: 'aaaaaa '
  '          0: 'aa '
  '          1: 'aaaa '  
  '          2: 'aaaaaa '
  '       2: 'aa'
  '          0: 'aa'
  '          1: 'aa'
  '          2: 'aa'
  '       3: 'aaaa '
  '          0: ''
  '          1: 'aa '
  '          2: 'aaaa '
  ``

  The regular expression is defined as shown in the following table.

Pattern | Description
------- | ----------- 
`(a+)` | Match the letter "a" one or more times. This is the second capturing group.
`(\1)` | Match the substring captured by the first capturing group. This is the third capturing group.
`?` | Match zero or one space characters.
`((a+)(\1) ?)+` | Match the pattern of one or more "a" characters followed by a string that matches the first capturing group followed by zero or one space characters one or more times. This is the first capturing group.
  
* Resolution of ambiguities between octal escapes and backreferences. The following table summarizes the differences in octal versus backreference interpretation by canonical and ECMAScript regular expressions.

Regular expression | Canonical behavior | ECMAScript behavior
------------------ | ------------------ | ------------------- 
`\0` followed by 0 to 2 octal digits | Interpret as an octal. For example, `\044` is always interpreted as an octal value and means "**$**". | Same behavior.
**\** followed by a digit from 1 to 9, followed by no additional decimal digits | Interpret as a backreference. For example, \9 always means backreference 9, even if a ninth capturing group does not exist. If the capturing group does not exist, the regular expression parser throws an [ArgumentException](xref:System.ArgumentException). | If a single decimal digit capturing group exists, backreference to that digit. Otherwise, interpret the value as a literal.
**\** followed by a digit from 1 to 9, followed by additional decimal digits | Interpret the digits as a decimal value. If that capturing group exists, interpret the expression as a backreference. Otherwise, interpret the leading octal digits up to octal 377; that is, consider only the low 8 bits of the value. Interpret the remaining digits as literals. For example, in the expression `\3000`, if capturing group 300 exists, interpret as backreference 300; if capturing group 300 does not exist, interpret as octal 300 followed by 0. | Interpret as a backreference by converting as many digits as possible to a decimal value that can refer to a capture. If no digits can be converted, interpret as an octal by using the leading octal digits up to octal 377; interpret the remaining digits as literals.
 
## Comparison using the invariant culture

By default, when the regular expression engine performs case-insensitive comparisons, it uses the casing conventions of the current culture to determine equivalent uppercase and lowercase characters. 

However, this behavior is undesirable for some types of comparisons, particularly when comparing user input to the names of system resources, such as passwords, files, or URLs. The following example illustrates such as scenario. The code is intended to block access to any resource whose URL is prefaced with **FILE://**. The regular expression attempts a case-insensitive match with the string by using the regular expression `$FILE://`. However, when the current system culture is tr-TR (Turkish-Turkey), "I" is not the uppercase equivalent of "i". As a result, the call to the [Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) method returns `false`, and access to the file is allowed. 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-sensitive matching ({0} culture)...", 
                  Thread.CurrentThread.CurrentCulture.Name);
if (Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("URLs that access files are not allowed.");      
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-sensitive matching (tr-TR culture)...
//       Access to file://c:/Documents.MyReport.doc is allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-sensitive matching ({0} culture)...", _
                  Thread.CurrentThread.CurrentCulture.Name)
If Regex.IsMatch(input, pattern, RegexOptions.IgnoreCase) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If

Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'       Culture-sensitive matching (tr-TR culture)...
'       Access to file://c:/Documents.MyReport.doc is allowed.
```

> [!NOTE]
>   如需區分大小寫和使用不因國別而異的文化特性之字串比較的詳細資訊，請參閱[在 .NET Framework 中使用字串的最佳作法](best-practices.md)。
 
您可以不要使用不因國別而異的文化特性的不區分大小寫比較，而是指定 [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) 選項來忽略語言中的文化特性差異，並使用不因國別而異的文化特性的慣例。

> [!NOTE]
> 若要使用不因國別而異的文化特性的比較，唯一的方法就是提供 [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) 值給 [Regex](xref:System.Text.RegularExpressions.Regex) 類別建構函式或靜態模式比對方法的 options 參數。 無法以內嵌選項來提供此值。 
 
下列範例與上一個範例相同，差別在於呼叫靜態 [Regex.IsMatch(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法時，是使用包含 [RegexOptions.CultureInvariant](xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant) 的選項。 即使目前的文化特性設為 Turkish (Turkey)，規則運算式引擎還是可以成功比對 "FILE" 和 "file"，並封鎖存取檔案資源。 

```csharp
CultureInfo defaultCulture = Thread.CurrentThread.CurrentCulture;
Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");

string input = "file://c:/Documents.MyReport.doc";
string pattern = "FILE://";

Console.WriteLine("Culture-insensitive matching...");
if (Regex.IsMatch(input, pattern, 
                  RegexOptions.IgnoreCase | RegexOptions.CultureInvariant)) 
   Console.WriteLine("URLs that access files are not allowed.");
else
   Console.WriteLine("Access to {0} is allowed.", input);

Thread.CurrentThread.CurrentCulture = defaultCulture;
// The example displays the following output:
//       Culture-insensitive matching...
//       URLs that access files are not allowed.
```

```vb
Dim defaultCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")

Dim input As String = "file://c:/Documents.MyReport.doc"
Dim pattern As String = "$FILE://"

Console.WriteLine("Culture-insensitive matching...")
If Regex.IsMatch(input, pattern, _
               RegexOptions.IgnoreCase Or RegexOptions.CultureInvariant) Then
   Console.WriteLine("URLs that access files are not allowed.")      
Else
   Console.WriteLine("Access to {0} is allowed.", input)
End If
Thread.CurrentThread.CurrentCulture = defaultCulture
' The example displays the following output:
'        Culture-insensitive matching...
'        URLs that access files are not allowed.
```

## <a name="see-also"></a>請參閱

[規則運算式語言 - 快速參考](quick-ref.md)


