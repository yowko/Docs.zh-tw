---
title: "規則運算式物件模型"
description: "規則運算式物件模型"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a1e611ec-c6a2-48c6-9c52-0ed845787621
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: becfe2624ad1ee1d03707ef48c780f518eb8eb28

---

# <a name="the-regular-expression-object-model"></a>規則運算式物件模型

本主題說明用來處理 .NET 規則運算式的物件模型。 它包含以下各節：

* [規則運算式引擎](#the-regular-expression-engine)

* [MatchCollection 與 Match 物件](#the-matchcollection-and-match-objects)

* [群組集合](#the-group-collection)

* [擷取的群組](#the-captured-group)

* [擷取的集合](#the-capture-collection)

* [個別擷取](#the-individual-capture)

## <a name="the-regular-expression-engine"></a>規則運算式引擎

.NET 的規則運算式引擎是以 [Regex](xref:System.Text.RegularExpressions.Regex) 類別表示。 規則運算式引擎負責剖析和編譯規則運算式，以及執行規則運算式模式與輸入字串的比對作業。 引擎是 .NET 規則運算式物件模型的中心元件。

規則運算式引擎有兩種使用方式：

* 呼叫 [Regex](xref:System.Text.RegularExpressions.Regex) 類別的靜態方法。 方法參數包括輸入字串和規則運算式模式。 規則運算式引擎會快取靜態方法呼叫中所使用的規則運算式，因此重複呼叫使用相同規則運算式的靜態規則運算式方法，可提供相對較佳的效能。

* 傳遞規則運算式到類別建構函式，以具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。 在此案例中，[Regex](xref:System.Text.RegularExpressions.Regex) 物件不可變 (唯讀)，並代表與單一規則運算式緊密結合的規則運算式引擎。 由於未快取 Regex 執行個體所使用的規則運算式，因此您不應該以相同的規則運算式將 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化多次。

您可以呼叫 [Regex](xref:System.Text.RegularExpressions.Regex) 類別的方法來執行下列作業： 

* 判定字串是否符合規則運算式模式。

* 擷取單一相符項目或第一個相符項目。

* 擷取所有相符項目。

* 取代相符的子字串。

* 將單一字串分割成字串陣列。

下面各節將會說明這些作業。

### <a name="matching-a-regular-expression-pattern"></a>比對規則運算式模式

如果字串符合模式，[Regex.IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法會傳回 `true`，如果不符合，則傳回 `false`。 [IsMatch](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String)) 方法常用來驗證字串輸入。 例如，下列程式碼可確保字串符合美國境內有效的社會安全號碼。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] values = { "111-22-3333", "111-2-3333"};
      string pattern = @"^\d{3}-\d{2}-\d{4}$";
      foreach (string value in values) {
         if (Regex.IsMatch(value, pattern))
            Console.WriteLine("{0} is a valid SSN.", value);
         else   
            Console.WriteLine("{0}: Invalid", value);
      }
   }
}
// The example displays the following output:
//       111-22-3333 is a valid SSN.
//       111-2-3333: Invalid
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim values() As String = { "111-22-3333", "111-2-3333"}
      Dim pattern As String = "^\d{3}-\d{2}-\d{4}$"
      For Each value As String In values
         If Regex.IsMatch(value, pattern) Then
            Console.WriteLine("{0} is a valid SSN.", value)
         Else   
            Console.WriteLine("{0}: Invalid", value)
         End If   
      Next
   End Sub
End Module
' The example displays the following output:
'       111-22-3333 is a valid SSN.
'       111-2-3333: Invalid
```

規則運算式模式 `^\d{3}-\d{2}-\d{4}$` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`^` | 比對輸入字串的開頭。
`\d{3}` | 比對三個十進位數字。
`-` | 比對連字號。
`\d{2}` | 比對兩個十進位數字。
`-` | 比對連字號。
`\d{4}` | 比對四個十進位數字。
`$` | 比對輸入字串的結尾。
 
### <a name="extracting-a-single-match-or-the-first-match"></a>擷取一個相符項目或第一個相符項目

[Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 方法會傳回 [Match](xref:System.Text.RegularExpressions.Match) 物件，其中包含符合規則運算式模式之第一個子字串的相關資訊。 如果 `Match.Success` 屬性傳回 `true`，指出已找到相符項目，您就可以呼叫 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法來擷取後續相符項目的相關資訊。 這些方法呼叫可以一直持續到 `Match.Success` 屬性傳回 `false`。 例如，下列程式碼會使用 [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) 方法來尋找字串中第一次出現的重複文字。 然後會呼叫 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法來尋找所出現的任何其他重複文字。 此範例會在每次方法呼叫之後檢查 `Match.Success` 屬性，以判定目前比對是否成功，以及後面是否應該接著呼叫 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      Match match = Regex.Match(input, pattern);
      while (match.Success)
      {
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
         match = match.NextMatch();
      }                       
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
         match = match.NextMatch()
      Loop                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

規則運算式模式 `\b(\w+)\W+(\1)\b` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 開始字邊界比對。
`(\w+)` | 比對一個或多個文字字元。 這是第一個擷取群組。
`\W+` | 比對一或多個非文字字元。
`(\1)` | 比對第一個擷取的字串。 這是第二個擷取群組。 
`\b` | 結束字邊界比對。
 
### <a name="extracting-all-matches"></a>擷取所有相符項目

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法會傳回 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件，其中包含規則運算式引擎在輸入字串中找到之所有相符項目的相關資訊。 例如，您可以將上一個範例重寫為呼叫 [Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法，而不是 [Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 和 [NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is a a farm that that raises dairy cattle."; 
      string pattern = @"\b(\w+)\W+(\1)\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("Duplicate '{0}' found at position {1}.",  
                           match.Groups[1].Value, match.Groups[2].Index);
   }
}
// The example displays the following output:
//       Duplicate 'a' found at position 10.
//       Duplicate 'that' found at position 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is a a farm that that raises dairy cattle." 
      Dim pattern As String = "\b(\w+)\W+(\1)\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Duplicate '{0}' found at position {1}.", _ 
                           match.Groups(1).Value, match.Groups(2).Index)
      Next                       
   End Sub
End Module
' The example displays the following output:
'       Duplicate 'a' found at position 10.
'       Duplicate 'that' found at position 22.
```

### <a name="replacing-a-matched-substring"></a>取代相符的子字串

[Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法會將符合規則運算式模式的每個子字串，取代為指定的字串或規則運算式模式，並傳回含有取代項目的整個輸入字串。 例如，下列程式碼會在字串中的十進位數字前面加上美國貨幣符號。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+\.\d{2}\b";
      string replacement = "$$$&"; 
      string input = "Total Cost: 103.64";
      Console.WriteLine(Regex.Replace(input, pattern, replacement));     
   }
}
// The example displays the following output:
//       Total Cost: $103.64
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+\.\d{2}\b"
      Dim replacement As String = "$$$&" 
      Dim input As String = "Total Cost: 103.64"
      Console.WriteLine(Regex.Replace(input, pattern, replacement))     
   End Sub
End Module
' The example displays the following output:
'       Total Cost: $103.64
```

規則運算式模式 `\b\d+\.\d{2}\b` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 開始字緣比對。
`\d+` | 比對一個或多個十進位數字。
`\.` | 比對句點。
`\d{2}` | 比對兩個十進位數字。
`\b` | 結束字緣比對。
 
取代模式 `$$$&` 的解譯方式如下表所示。

模式 | 取代字串
------- | ------------------ 
`$$` | 貨幣符號 (**$**) 字元。
`$&` | 整個相符子字串。
 
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>將單一字串分割成字串陣列

[Regex.Split](xref:System.Text.RegularExpressions.Regex.Split(System.String)) 方法會在規則運算式比對所定義的位置分割輸入字串。 例如，下列程式碼會將編號清單中的項目放在字串陣列中。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea";
      string pattern = @"\b\d{1,2}\.\s";
      foreach (string item in Regex.Split(input, pattern))
      {
         if (! String.IsNullOrEmpty(item))
            Console.WriteLine(item);
      }      
   }
}
// The example displays the following output:
//       Eggs
//       Bread
//       Milk
//       Coffee
//       Tea
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "1. Eggs 2. Bread 3. Milk 4. Coffee 5. Tea"
      Dim pattern As String = "\b\d{1,2}\.\s"
      For Each item As String In Regex.Split(input, pattern)
         If Not String.IsNullOrEmpty(item) Then
            Console.WriteLine(item)
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       Eggs
'       Bread
'       Milk
'       Coffee
'       Tea
```

規則運算式模式 `\b\d{1,2}\.\s` 的解譯方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`\d{1,2}` | 比對一個或兩個十進位數字。
`\.` | 比對句點。
`\s` | 比對空白字元。
 
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection 與 Match 物件

[Regex](xref:System.Text.RegularExpressions.Regex) 方法會傳回兩個屬於規則運算式物件模型的物件：[MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件和 [Match](xref:System.Text.RegularExpressions.Match) 物件。 

### <a name="the-match-collection"></a>比對集合

[Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法會傳回 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件，其中包含 [Match](xref:System.Text.RegularExpressions.Match) 物件，這些物件代表規則運算式引擎找到的所有相符項目，並按照其於輸入字串中出現的順序排列。 如果沒有符合的成員，則此方法會傳回包含 [Match](xref:System.Text.RegularExpressions.Match) 物件但沒有成員的 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件。 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` 屬性可讓您依索引存取集合的個別成員，從零到 [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) 屬性的值減一。 'Item` 是集合的索引子 (在 C# 中) 和預設屬性 (在 Visual Basic 中)。

依預設，呼叫 [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法時會使用延遲評估來填入 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件。 若要存取需要完整填入集合的屬性，例如 [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) 和 `Item` 屬性，可能會導致效能傷害。 因此，建議您使用 [MatchCollection.GetEnumerator](xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator) 方法傳回的 [IEnumerator](xref:System.Collections.IEnumerator) 物件來存取集合。 個別語言提供的建構，例如 C# 的 `foreach` 和 Visual Basic 的 `For Each'，會包裝集合的 IEnumerator](xref:System.Collections.IEnumerator) 介面。

下列範例使用 [Regex.Matches(String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 方法，以在輸入字串中找到的所有相符項目來填入 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件。 此範例會列舉集合、將相符項目複製到字串陣列，並記錄整數陣列中的字元位置。

```csharp
using System;
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
       MatchCollection matches;
       List<string> results = new List<string>();
       List<int> matchposition = new List<int>();

       // Create a new Regex object and define the regular expression.
       Regex r = new Regex("abc");
       // Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd");
       // Enumerate the collection to retrieve all matches and positions.
       foreach (Match match in matches)
       {
          // Add the match string to the string array.
           results.Add(match.Value);
           // Record the character position where the match was found.
           matchposition.Add(match.Index);
       }
       // List the results.
       for (int ctr = 0; ctr < results.Count; ctr++)
         Console.WriteLine("'{0}' found at position {1}.", 
                           results[ctr], matchposition[ctr]);  
   }
}
// The example displays the following output:
//       'abc' found at position 3.
//       'abc' found at position 7.
```

```vb
Imports System.Collections.Generic
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
       Dim matches As MatchCollection
       Dim results As New List(Of String)
       Dim matchposition As New List(Of Integer)

       ' Create a new Regex object and define the regular expression.
       Dim r As New Regex("abc")
       ' Use the Matches method to find all matches in the input string.
       matches = r.Matches("123abc4abcd")
       ' Enumerate the collection to retrieve all matches and positions.
       For Each match As Match In matches
          ' Add the match string to the string array.
           results.Add(match.Value)
           ' Record the character position where the match was found.
           matchposition.Add(match.Index)
       Next
       ' List the results.
       For ctr As Integer = 0 To results.Count - 1
         Console.WriteLine("'{0}' found at position {1}.", _
                           results(ctr), matchposition(ctr))  
       Next
   End Sub
End Module
' The example displays the following output:
'       'abc' found at position 3.
'       'abc' found at position 7.
```

### <a name="the-match"></a>比對

[Match](xref:System.Text.RegularExpressions.Match) 類別代表單一規則運算式比對的結果。 您可以用兩個方式來存取 [Match](xref:System.Text.RegularExpressions.Match) 物件：

* 從 Regex.Matches 方法傳回的 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件中擷取。 若要擷取個別的 [Match](xref:System.Text.RegularExpressions.Match) 物件，請使用 `foreach` (在 C# 中) 或 `For Each...Next` (在 Visual Basic 中) 建構逐一查看集合，或使用 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) `Item` 屬性依據索引或名稱擷取特定的 [Match](xref:System.Text.RegularExpressions.Match) 物件。 您也可以依索引 (從零到集合中的物件數減一) 從集合擷取個別 [Match](xref:System.Text.RegularExpressions.Match) 物件。 不過，此方法不會利用延遲評估，因為它會存取 [MatchCollection.Count](xref:System.Text.RegularExpressions.MatchCollection.Count) 屬性。 

  下例會使用 `foreach` 建構逐一查看集合，以從 [MatchCollection](xref:System.Text.RegularExpressions.MatchCollection) 物件擷取個別 [Match](xref:System.Text.RegularExpressions.Match) 物件。 規則運算式會單純比對輸入字串中的字串 "abc"。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        foreach (Match match in Regex.Matches(input, pattern))
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        For Each match As Match In Regex.Matches(input, pattern)
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
        Next                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

* 呼叫 [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 方法，它會傳回代表字串中第一個相符項目或字串一部分的 [Match](xref:System.Text.RegularExpressions.Match) 物件。 您可以擷取 `Match.Success` 屬性的值，以判斷是否找到相符項目。 若要擷取代表後續相符項目的 [Match](xref:System.Text.RegularExpressions.Match) 物件，請重複呼叫 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法，直到傳回之 [Match](xref:System.Text.RegularExpressions.Match) 物件的 `Success` 屬性為 `false`。 

  下例會使用 [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)) 和 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法來比對輸入字串中的字串 "abc"。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "abc";
        string input = "abc123abc456abc789";
        Match match = Regex.Match(input, pattern);
        while (match.Success)
        {
           Console.WriteLine("{0} found at position {1}.", 
                             match.Value, match.Index);
           match = match.NextMatch();                  
        }                     
     }
  }
  // The example displays the following output:
  //       abc found at position 0.
  //       abc found at position 6.
  //       abc found at position 12.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "abc"
        Dim input As String = "abc123abc456abc789"
        Dim match As Match = Regex.Match(input, pattern)
        Do While match.Success
           Console.WriteLine("{0} found at position {1}.", _
                             match.Value, match.Index)
           match = match.NextMatch()                  
        Loop                     
     End Sub
  End Module
  ' The example displays the following output:
  '       abc found at position 0.
  '       abc found at position 6.
  '       abc found at position 12.
  ```

[Match](xref:System.Text.RegularExpressions.Match) 類別的兩個屬性會傳回集合物件：

* [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性會傳回 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件，其中包含符合規則運算式模式中之擷取群組的子字串相關資訊。 

* `Match.Captures` 屬性會傳回用法受限的 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件。 針對 `Success` 屬性為 `false` 的 [Match](xref:System.Text.RegularExpressions.Match) 物件，不會填入集合。 否則，就會包含具有與 [Match](xref:System.Text.RegularExpressions.Match) 物件相同資訊的單一 [Capture](xref:System.Text.RegularExpressions.Capture) 物件。 

如需這些物件的詳細資訊，請參閱本主題後文的[群組集合](#the-group-collection)及[擷取集合](#the-capture-collection)兩節。

[Match](xref:System.Text.RegularExpressions.Match) 類別的兩個其他屬性會提供比對的相關資訊。 `Match.Value` 屬性會傳回輸入字串中，符合規則運算式模式的子字串。 `Match.Index` 屬性會傳回輸入字串中相符字串以零起始的開始位置。

[Match](xref:System.Text.RegularExpressions.Match) 類別也有兩個模式比對方法：

* [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法會尋找目前 [Match](xref:System.Text.RegularExpressions.Match) 物件代表之相符項目後面的相符項目，並傳回代表該相符項目的 [Match](xref:System.Text.RegularExpressions.Match) 物件。

* [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) 方法會在相符字串上執行指定的取代作業，並傳回結果。 


下列範例會使用 [Match.Result](xref:System.Text.RegularExpressions.Match.NextMatch) 方法，在包含兩個小數位數的每個數字前面，加上 **$** 符號和空格。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b\d+(,\d{3})*\.\d{2}\b";
      string input = "16.32\n194.03\n1,903,672.08"; 

      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Result("$$ $&"));
   }
}
// The example displays the following output:
//       $ 16.32
//       $ 194.03
//       $ 1,903,672.08
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b\d+(,\d{3})*\.\d{2}\b"
      Dim input As String = "16.32" + vbCrLf + "194.03" + vbCrLf + "1,903,672.08" 

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Result("$$ $&"))
      Next
   End Sub
End Module
' The example displays the following output:
'       $ 16.32
'       $ 194.03
'       $ 1,903,672.08
```

規則運算式模式 `\b\d+(,\d{3})*\.\d{2}\b` 的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`\d+` | 比對一個或多個十進位數字。
`(,\d{3})*` | 比對後面接三個十進位數字的零或多個逗號。
`\.` | 比對小數點字元。
`\d{2} | 比對兩個十進位數字。
`\b` | 結束字緣比對。
 
取代模式 **$$ $&** 指出相符的子字串應取代為貨幣 (**$**) 符號 (`$$` 模式)、空格和相符項的值 (`$&` 模式)。

## <a name="the-group-collection"></a>群組集合

[Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性會傳回 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件，其中包含單一比對中代表擷取群組的 [Group](xref:System.Text.RegularExpressions.Group) 物件。 集合中的第一個 [Group](xref:System.Text.RegularExpressions.Group) 物件 (索引位置為 0) 代表整個比對。 後面接續的每個物件各代表單一擷取群組的結果。 

您可以使用 [GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) 屬性，擷取集合中的個別 [Group](xref:System.Text.RegularExpressions.Group) 物件。 您可以依集合中的序數位置來擷取未具名群組，以及依名稱或依序數位置來擷取具名群組。 未具名擷取會先出現在集合中，並依其出現在規則運算式模式中的順序，由左至右編排索引。 具名擷取的索引會依其出現在規則運算式模式中的順序，由左至右編排在未具名擷取之後。 若要判定特定規則運算式比對方法傳回的集合中，有哪些編號群組可用，您可以呼叫執行個體 [Regex.GetGroupNumbers](xref:System.Text.RegularExpressions.Regex.GetGroupNumbers) 方法。 若要判定集合中有哪些具名群組可用，您可以呼叫執行個體 [Regex.GetGroupNames](xref:System.Text.RegularExpressions.Regex.GetGroupNames) 方法。 在用來分析任何規則運算式找到之相符項目的一般用途常式中，這兩種方法都特別好用。 

[GroupCollection.Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) 屬性在 C# 是集合的索引子，在 Visual Basic 中是集合物件的預設屬性。 這表示，可以依索引 (若為具名群組，可依名稱) 來存取個別 [Group](xref:System.Text.RegularExpressions.Group) 物件，如下所示： 

```csharp
Group group = match.Groups[ctr];
```

```vb
Dim group As Group = match.Groups(ctr)
```

下列範例定義的規則運算式會使用群組建構來擷取日期的月、日和年。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+)\s(\d{1,2}),\s(\d{4})\b";
      string input = "Born: July 28, 1989";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
         for (int ctr = 0; ctr <  match.Groups.Count; ctr++)
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups[ctr].Value);
    }
}
// The example displays the following output:
//       Group 0: July 28, 1989
//       Group 1: July
//       Group 2: 28
//       Group 3: 1989
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+)\s(\d{1,2}),\s(\d{4})\b"
      Dim input As String = "Born: July 28, 1989"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         For ctr As Integer = 0 To match.Groups.Count - 1
            Console.WriteLine("Group {0}: {1}", ctr, match.Groups(ctr).Value)
         Next      
      End If   
   End Sub
End Module
' The example displays the following output:
'       Group 0: July 28, 1989
'       Group 1: July
'       Group 2: 28
'       Group 3: 1989
```

規則運算式模式 `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` 的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`(\w+)` | 比對一個或多個文字字元。 這是第一個擷取群組。
`\s` | 比對空白字元。
`(\d{1,2})` | 比對一個或兩個十進位數字。 這是第二個擷取群組。
`,` | 比對逗號。
`\s` | 比對空白字元。
`(\d{4})` | 比對四個十進位數字。 這是第三個擷取群組。
`\b` | 結束字邊界比對。
 
## <a name="the-captured-group"></a>擷取的群組

[Group](xref:System.Text.RegularExpressions.Group) 類別代表單一擷取群組的結果。 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性傳回之 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件的 [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) 屬性，會傳回代表規則運算式中定義之擷取群組的 [Group](xref:System.Text.RegularExpressions.Group) 物件。 [Item](xref:System.Text.RegularExpressions.GroupCollection.Item(System.Int32)) 屬性是 [Group](xref:System.Text.RegularExpressions.Group) 類別的索引子 (在 C# 中) 及預設屬性 (在 Visual Basic 中)。 您也可以使用 `foreach` 建構，逐一查看集合來擷取個別成員。 如需範例，請參閱上一節。

下列範例會使用巢狀群組建構，將子字串擷取至群組中。 規則運算式模式 `(a(b))c` 會相符字串 "abc"。 它會將子字串 "ab" 指派給第一個擷取群組，並將子字串 "b" 指派給第二個擷取群組。

```csharp
List<int> matchposition = new List<int>();
List<string> results = new List<string>();
// Define substrings abc, ab, b.
Regex r = new Regex("(a(b))c"); 
Match m = r.Match("abdabc");
for (int i = 0; m.Groups[i].Value != ""; i++) 
{
   // Add groups to string array.
   results.Add(m.Groups[i].Value); 
   // Record character position.
   matchposition.Add(m.Groups[i].Index); 
}

// Display the capture groups.
for (int ctr = 0; ctr < results.Count; ctr++)
   Console.WriteLine("{0} at position {1}", 
                     results[ctr], matchposition[ctr]);
// The example displays the following output:
//       abc at position 3
//       ab at position 3
//       b at position 4
```

```vb
Dim matchposition As New List(Of Integer)
 Dim results As New List(Of String)
 ' Define substrings abc, ab, b.
 Dim r As New Regex("(a(b))c") 
 Dim m As Match = r.Match("abdabc")
 Dim i As Integer = 0
 While Not (m.Groups(i).Value = "")    
    ' Add groups to string array.
    results.Add(m.Groups(i).Value)     
    ' Record character position. 
    matchposition.Add(m.Groups(i).Index) 
     i += 1
 End While

 ' Display the capture groups.
 For ctr As Integer = 0 to results.Count - 1
    Console.WriteLine("{0} at position {1}", _ 
                      results(ctr), matchposition(ctr))
 Next                     
' The example displays the following output:
'       abc at position 3
'       ab at position 3
'       b at position 4
```

下列範例會使用具名群組建構，從包含 "DATANAME:VALUE" 格式 (規則運算式會在冒號 (:) 處分割) 資料的字串擷取子字串。

```csharp
Regex r = new Regex("^(?<name>\\w+):(?<value>\\w+)");
Match m = r.Match("Section1:119900");
Console.WriteLine(m.Groups["name"].Value);
Console.WriteLine(m.Groups["value"].Value);
// The example displays the following output:
//       Section1
//       119900
```

```vb
Dim r As New Regex("^(?<name>\w+):(?<value>\w+)")
Dim m As Match = r.Match("Section1:119900")
Console.WriteLine(m.Groups("name").Value)
Console.WriteLine(m.Groups("value").Value)
' The example displays the following output:
'       Section1
'       119900
```

規則運算式模式 `^(?<name>\w+):(?<value>\w+)` 的定義如下表所示。

模式 | 描述
------- | -----------
`^` | 在輸入字串的開頭開始比對。
`(?<name>\w+)` | 比對一個或多個文字字元。 此擷取群組的名稱為「名稱」。
`:` | 比對冒號。
`(?<value>\w+)` | 比對一個或多個文字字元。 此擷取群組的名稱為「值」。
 
[Group](xref:System.Text.RegularExpressions.Group) 類別的屬性會提供擷取群組的相關資訊：`Group.Value` 屬性包含擷取的子字串，`Group.Index` 屬性會指出擷取群組在輸入文字中的開始位置，`Group.Length` 屬性包含擷取文字的長度，而 `Group.Success` 屬性會指出子字串是否符合擷取群組所定義的模式。

將數量詞套用至群組 (如需詳細資訊，請參閱[規則運算式中的數量詞](quantifiers.md)) 會以下列兩種方式，各修改每一個擷取群組之一個擷取的關聯性：

* 如果 __*__ 或 __*?__ 數量詞 (可指定零或多個相符項目) 套用至群組，擷取群組在輸入字串中可會沒有相符項目。 沒有擷取文字時，[Group](xref:System.Text.RegularExpressions.Group) 物件的屬性會設定如下表所示。

  群組屬性 | 值
  -------------- | ----- 
  `Success` | `false`
  `Value` | [String.Empty](xref:System.String.Empty) 
  `Length` | 0
 
  下列範例提供一個實例。 在規則運算式模式 `aaa(bbb)*ccc` 中，第一個擷取群組 (子字串 "bbb") 可比對零或多次。 因為輸入字串 "aaaccc" 符合模式，所以擷取群組沒有相符項目。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = "aaa(bbb)*ccc";
        string input = "aaaccc";
        Match match = Regex.Match(input, pattern);
        Console.WriteLine("Match value: {0}", match.Value);
        if (match.Groups[1].Success)
           Console.WriteLine("Group 1 value: {0}", match.Groups[1].Value);
        else
           Console.WriteLine("The first capturing group has no match.");
     }
  }
  // The example displays the following output:
  //       Match value: aaaccc
  //       The first capturing group has no match.
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "aaa(bbb)*ccc"
        Dim input As String = "aaaccc"
        Dim match As Match = Regex.Match(input, pattern)
        Console.WriteLine("Match value: {0}", match.Value)
        If match.Groups(1).Success Then
           Console.WriteLine("Group 1 value: {0}", match.Groups(1).Value)
        Else
           Console.WriteLine("The first capturing group has no match.")
       End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match value: aaaccc
  '       The first capturing group has no match.
  ```

* 數量詞可以比對多次出現的擷取群組定義的模式。 在此情況下，[Group](xref:System.Text.RegularExpressions.Group) 物件的 `Value` 和 `Length` 屬性只包含最後擷取之子字串的相關資訊。 例如，下列規則運算式會比對以句點結尾的單一句子。 其使用兩個群組建構：第一個群組建構會擷取個別文字和空格字元，第二個群組建構會擷取個別文字。 如範例輸出所示，雖然規則運算式成功擷取了整個句子，但是第二個擷取群組只擷取了最後一個字。

  ```csharp
  using System;
  using System.Text.RegularExpressions;

  public class Example
  {
     public static void Main()
     {
        string pattern = @"\b((\w+)\s?)+\.";
        string input = "This is a sentence. This is another sentence.";
        Match match = Regex.Match(input, pattern);
        if (match.Success)
        {
           Console.WriteLine("Match: " + match.Value);
           Console.WriteLine("Group 2: " + match.Groups[2].Value);
        }   
     }
  }
  // The example displays the following output:
  //       Match: This is a sentence.
  //       Group 2: sentence
  ```

  ```vb
  Imports System.Text.RegularExpressions

  Module Example
     Public Sub Main()
        Dim pattern As String = "\b((\w+)\s?)+\."
        Dim input As String = "This is a sentence. This is another sentence."
        Dim match As Match = Regex.Match(input, pattern)
        If match.Success Then
           Console.WriteLine("Match: " + match.Value)
           Console.WriteLine("Group 2: " + match.Groups(2).Value)
        End If   
     End Sub
  End Module
  ' The example displays the following output:
  '       Match: This is a sentence.
  '       Group 2: sentence
  ```

## <a name="the-capture-collection"></a>擷取集合

[Group](xref:System.Text.RegularExpressions.Group) 物件只包含最後一個擷取的相關資訊。 不過，您仍可從 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 屬性傳回的 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件，取得擷取群組所建立的一整組擷取。 集合的每個成員都是 [Capture](xref:System.Text.RegularExpressions.Capture) 物件，代表擷取群組所建立的擷取，並依照擷取的順序排列 (因此，順序為在輸入字串中比對擷取群組的順序，由左至右排列)。 您可以從集合擷取個別 [Capture](xref:System.Text.RegularExpressions.Capture) 物件，有兩種方式： 

* 使用 `foreach` (在 C# 中) 或 `For Each` (在 Visual Basic 中) 之類的建構逐一查看集合。

* 使用 [CaptureCollection.Item](xref:System.Text.RegularExpressions.CaptureCollection.Item(System.Int32)) 屬性，依索引擷取特定物件。 Item 屬性是 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件的預設屬性 (在 Visual Basic 中) 或索引子 (在 C# 中)。


如果沒有將數量詞套用至擷取群組，則 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件會包含單一較無用處的 [Capture](xref:System.Text.RegularExpressions.Capture) 物件，因為其提供與其 [Group](xref:System.Text.RegularExpressions.Group) 物件相同之相符項目的相關資訊。 如果將數量詞套用至擷取群組，則 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件包含擷取群組建立的所有擷取，而集合的最後一個成員代表與 [Group](xref:System.Text.RegularExpressions.Group) 物件相同的擷取。 

例如，如果您使用規則運算式模式 `((a(b))c)+` (其中 `+` 數量詞指定一或多個比對)，以從字串 "abcabcabc" 擷取相符項目，則每個 [Group](xref:System.Text.RegularExpressions.Group) 物件的 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件各包含三個成員。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "((a(b))c)+";
      string input = "abcabcabc";

      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Match: '{0}' at position {1}",  
                           match.Value, match.Index);
         GroupCollection groups = match.Groups;
         for (int ctr = 0; ctr < groups.Count; ctr++) {
            Console.WriteLine("   Group {0}: '{1}' at position {2}", 
                              ctr, groups[ctr].Value, groups[ctr].Index);
            CaptureCollection captures = groups[ctr].Captures;
            for (int ctr2 = 0; ctr2 < captures.Count; ctr2++) {
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", 
                                 ctr2, captures[ctr2].Value, captures[ctr2].Index);
            }                     
         }
      }
   }
}
// The example displays the following output:
//       Match: 'abcabcabc' at position 0
//          Group 0: 'abcabcabc' at position 0
//             Capture 0: 'abcabcabc' at position 0
//          Group 1: 'abc' at position 6
//             Capture 0: 'abc' at position 0
//             Capture 1: 'abc' at position 3
//             Capture 2: 'abc' at position 6
//          Group 2: 'ab' at position 6
//             Capture 0: 'ab' at position 0
//             Capture 1: 'ab' at position 3
//             Capture 2: 'ab' at position 6
//          Group 3: 'b' at position 7
//             Capture 0: 'b' at position 1
//             Capture 1: 'b' at position 4
//             Capture 2: 'b' at position 7
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example dosplays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

下列範例使用規則運算式 `(Abc)+`，在字串 "XYZAbcAbcAbcXYZAbcAb" 中尋找一或多次連續執行的字串 "Abc"。 此範例說明如何使用 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 屬性來傳回多個擷取子字串群組。

```csharp
{
   int counter;
   Match m;
   CaptureCollection cc;
   GroupCollection gc;

   // Look for groupings of "Abc".
   Regex r = new Regex("(Abc)+"); 
   // Define the string to search.
   m = r.Match("XYZAbcAbcAbcXYZAbcAb"); 
   gc = m.Groups;

   // Display the number of groups.
   Console.WriteLine("Captured groups = " + gc.Count.ToString());

   // Loop through each group.
   for (int i=0; i < gc.Count; i++) 
   {
      cc = gc[i].Captures;
      counter = cc.Count;

      // Display the number of captures in this group.
      Console.WriteLine("Captures count = " + counter.ToString());

      // Loop through each capture in the group.
      for (int ii = 0; ii < counter; ii++) 
      {
         // Display the capture and its position.
         Console.WriteLine(cc[ii] + "   Starts at character " + 
              cc[ii].Index);
      }
   }
}
// The example displays the following output:
//       Captured groups = 2
//       Captures count = 1
//       AbcAbcAbc   Starts at character 3
//       Captures count = 3
//       Abc   Starts at character 3
//       Abc   Starts at character 6
//       Abc   Starts at character 9  
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "((a(b))c)+"
      Dim input As STring = "abcabcabc"

      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Match: '{0}' at position {1}", _ 
                           match.Value, match.Index)
         Dim groups As GroupCollection = match.Groups
         For ctr As Integer = 0 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at position {2}", _
                              ctr, groups(ctr).Value, groups(ctr).Index)
            Dim captures As CaptureCollection = groups(ctr).Captures
            For ctr2 As Integer = 0 To captures.Count - 1
               Console.WriteLine("      Capture {0}: '{1}' at position {2}", _
                                 ctr2, captures(ctr2).Value, captures(ctr2).Index)
            Next
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Match: 'abcabcabc' at position 0
'          Group 0: 'abcabcabc' at position 0
'             Capture 0: 'abcabcabc' at position 0
'          Group 1: 'abc' at position 6
'             Capture 0: 'abc' at position 0
'             Capture 1: 'abc' at position 3
'             Capture 2: 'abc' at position 6
'          Group 2: 'ab' at position 6
'             Capture 0: 'ab' at position 0
'             Capture 1: 'ab' at position 3
'             Capture 2: 'ab' at position 6
'          Group 3: 'b' at position 7
'             Capture 0: 'b' at position 1
'             Capture 1: 'b' at position 4
'             Capture 2: 'b' at position 7
```

## <a name="the-individual-capture"></a>個別擷取

[Capture](xref:System.Text.RegularExpressions.Capture) 類別包含單一子運算式擷取的結果。 [Capture.Value](xref:System.Text.RegularExpressions.Capture.Value) 屬性包含相符的文字，而 [Capture.Index](xref:System.Text.RegularExpressions.Capture.Index) 屬性指出輸入字串中以零起始的位置，也就是相符的子字串開始的位置。 

下列範例會針對所選城市的氣溫剖析輸入字串。 逗號 (",") 用來分隔城市及其氣溫，而分號 (";") 用來分隔每個城市的資料。 整個輸入字串代表單一比對。 在規則運算式模式 `((\w+(\s\w+)*),(\d+);)+` (用來剖析字串) 中，城市名稱指派給第二個擷取群組，而氣溫指派給第四個擷取群組。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;"; 
      string pattern = @"((\w+(\s\w+)*),(\d+);)+";
      Match match = Regex.Match(input, pattern);
      if (match.Success)
      {
         Console.WriteLine("Current temperatures:");
         for (int ctr = 0; ctr < match.Groups[2].Captures.Count; ctr++)
            Console.WriteLine("{0,-20} {1,3}", match.Groups[2].Captures[ctr].Value, 
                              match.Groups[4].Captures[ctr].Value);
      }
   }
}
// The example displays the following output:
//       Current temperatures:
//       Miami                 78
//       Chicago               62
//       New York              67
//       San Francisco         59
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "Miami,78;Chicago,62;New York,67;San Francisco,59;Seattle,58;" 
      Dim pattern As String = "((\w+(\s\w+)*),(\d+);)+"
      Dim match As Match = Regex.Match(input, pattern)
      If match.Success Then
         Console.WriteLine("Current temperatures:")
         For ctr As Integer = 0 To match.Groups(2).Captures.Count - 1
            Console.WriteLine("{0,-20} {1,3}", match.Groups(2).Captures(ctr).Value, _
                              match.Groups(4).Captures(ctr).Value)
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Current temperatures:
'       Miami                 78
'       Chicago               62
'       New York              67
'       San Francisco         59
```

規則運算式的定義如下表所示。

模式 | 描述
------- | -----------
`\w+` | 比對一個或多個文字字元。
`(\s\w+)*` | 比對出現零或多次、後接一或多個文字字元的空格字元。 此模式會比對多字的城市名稱。 這是第三個擷取群組。
`(\w+(\s\w+)*)` | 比對一或多個文字字元，其後面接出現零或多次的空格字元，以及一或多個文字字元。 這是第二個擷取群組。
`,` | 比對逗號。
`(\d+)` | 比對一或多個數字。 這是第四個擷取群組。
`;` | 比對分號。
`((\w+(\s\w+)*),(\d+);)+` | 一或多次比對文字的模式，該文字後面接任何其他文字，後面再接逗號、一或多個數字和分號。 這是第一個擷取群組。 
 
## <a name="see-also"></a>請參閱

[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[.NET 規則運算式](regular-expressions.md)

[規則運算式語言 - 快速參考](quick-ref.md)




<!--HONumber=Nov16_HO3-->


