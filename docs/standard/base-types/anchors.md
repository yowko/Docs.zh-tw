---
title: "規則運算式中的錨點"
description: "規則運算式中的錨點"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 96dff1be-3005-4ba5-af1b-323182a26085
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: ef2a63115f1efbe2418c348a3379fe7dd2face86

---

# <a name="anchors-in-regular-expressions"></a>規則運算式中的錨點

錨點或不可部分完成的無寬度判斷提示會指定字串中必須比對的位置。 當您在搜尋運算式中使用錨點時，規則運算式引擎不會在字串中前進或使用字元；它只會尋找指定位置中的相符項目。 例如，**^** 指定必須從行首或字串的開頭開始比對。 因此，僅當行首出現 "http:" 時，規則運算式 `^http:` 才會與其相符。 下表列出 .NET 中此規則運算式所支援的錨點。 

錨點 | 描述
------ | ----------- 
**^** | 比對必須發生在字串的開頭或行首。
**$** | 比對必須發生在字串結尾或行尾，或是發生在字串結尾或行尾的 \n 之前。
**\A** | 比對只能發生在字串的開頭 (不支援多行)
**\Z** | 比對必須發生在字串結尾，或發生在字串結尾的 \n 之前。
**\z** | 比對只能發生在字串結尾。 
**\G** | 比對必須從上一個比對結束的位置開始。
**\b** | 比對必須發生在字邊界上。
**\B** | 比對不可發生在字邊界上。
 
## <a name="start-of-string-or-line-"></a>字串開頭或行首：^

**^** 錨點可讓您指定下列模式必須從字串的第一個字元位置開始。 若並用 **^** 與 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項 (請參閱[規則運算式選項](options.md))，比對必須從每一行的行首開始。

下列範例會在規則運算式中使用 **^** 錨點，該規則運算式會擷取與某些職業棒球隊存在期間年份相關的資訊。 此範例會呼叫 `Regex.Matches` 方法的兩個多載： 

* 在符合規則運算式模式的輸入字串中，對 [Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) 多載的呼叫只會尋找其中的第一個子字串。 

* 對 [Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 多載的呼叫 (options 參數設為 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline)) 會尋找所有五個子字串。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      startPos = 0
      endPos = 70
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


'       For Each match As Match in Regex.Matches(input, pattern, RegexOptions.Multiline)
'          Console.Write("The {0} played in the {1} in", _
'                            match.Groups(1).Value, match.Groups(4).Value)
'          For Each capture As Capture In match.Groups(5).Captures
'             Console.Write(capture.Value)
'          Next
'          Console.WriteLine(".")
'       Next
   End Sub
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

規則運算式模式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+` 的定義如下表所示。

模式 | 描述
------- | ----------- 
`^` | 開始在輸入字串的開頭比對 (如果是使用 `RegexOptions.Multiline` 選項來呼叫此方法，則從行首開始比對)。
`((\w+(\s?)){2,}` | 比對一個或多個文字字元，後面接零，或接一個空格剛好兩次。 這是第一個擷取群組。 此運算式也定義了第二個和第三個擷取群組：第二個包含所擷取的文字，第三個則包含擷取到的空格。 
`,\s` | 比對後面接著空白字元的逗號。
`(\w+\s\w+)` | 比對一或多個文字字元，後面接空格，再接一或多個文字字元。 這是第四個擷取群組。
`,` | 比對逗號。
`\s\d{4}` | 比對後面接著四個十進位數字的空格。
`(-(\d{4}`&#124;`present))?` |  比對出現零次或一次的連字號，後面接著四個十進位數字或字串 "present"。 這是第六個擷取群組。 它也包括第七個擷取群組。 
`,?` | 比對出現零次或一次的逗號。
`(\s\d{4}(-(\d{4}`&#124;`present))?,?)+` | 比對出現一或多次的下列項目：空格、四個十進位數字、出現零或一次的連字號 (該連字號後面接著四個十進位數字或字串 "present")，以及零或一個逗號。 這是第五個擷取群組。
 
## <a name="end-of-string-or-line-"></a>字串結尾或行尾：$

**$** 錨點指定前述的模式必須發生在輸入字串的結尾，或輸入字串結尾的 \n 之前。 

如果您將 **$** 與 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項搭配使用，則該比對也會在行尾發生。 請注意，**$** 會比對 **\n**，但不會比對 **\r\n** (歸位字元與新行字元的組合，亦即 CR/LF)。 若要比對 CR/LF 字元組合，請在規則運算式模式中包含 **\r?$**。

下列範例會將 **$** 錨點加入上一節＜字串開頭或行首＞中範例所使用的規則運算式模式。 當與原始的輸入字串 (包括五行文字) 搭配使用時，[Regex.Matches(String, String)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String)) 方法會找不到相符項目，因為第一行的結尾不符合 **$** 模式。 當原始的輸入字串分割成字串陣列時，`Regex.Matches(String, String)` 方法會成功地比對這五行。 當呼叫 [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法且 *options* 參數設定為 `RegexOptions.Multiline` 時，會找不到相符項目，因為規則運算式模式並不考慮歸位字元項目 (\u+000D)。 不過，在將 **$** 取代為 **\r?$** 來修改規則運算式模式時，將 *options* 參數再次設定為 `RegexOptions.Multiline` 來呼叫 `Regex.Matches(String, String, RegexOptions)` 方法，則會找出五個相符項目。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string cr = Environment.NewLine;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + cr +
                     "Chicago Cubs, National League, 1903-present" + cr + 
                     "Detroit Tigers, American League, 1901-present" + cr + 
                     "New York Giants, National League, 1885-1957" + cr +  
                     "Washington Senators, American League, 1901-1960" + cr;   
      Match match;

      string basePattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      string pattern = basePattern + "$";
      Console.WriteLine("Attempting to match the entire input string:");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      string[] teams = input.Split(new String[] { cr }, StringSplitOptions.RemoveEmptyEntries);
      Console.WriteLine("Attempting to match each element in a string array:");
      foreach (string team in teams)
      {
         if (team.Length > 70) continue;

         match = Regex.Match(team, pattern);
         if (match.Success)
         {
            Console.Write("The {0} played in the {1} in", 
                          match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);
            Console.WriteLine(".");
         }
      }
      Console.WriteLine();

      startPos = 0;
      endPos = 70;
      Console.WriteLine("Attempting to match each line of an input string with '$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }

      startPos = 0;
      endPos = 70;
      pattern = basePattern + "\r?$"; 
      Console.WriteLine(@"Attempting to match each line of an input string with '\r?$':");
      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Attempting to match the entire input string:
//    
//    Attempting to match each element in a string array:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
//    
//    Attempting to match each line of an input string with '$':
//    
//    Attempting to match each line of an input string with '\r+$':
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
//    The Chicago Cubs played in the National League in 1903-present.
//    The Detroit Tigers played in the American League in 1901-present.
//    The New York Giants played in the National League in 1885-1957.
//    The Washington Senators played in the American League in 1901-1960.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim basePattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      Dim pattern As String = basePattern + "$"
      Console.WriteLine("Attempting to match the entire input string:")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      

      Dim teams() As String = input.Split(New String() { vbCrLf }, StringSplitOptions.RemoveEmptyEntries)
      Console.WriteLine("Attempting to match each element in a string array:")
      For Each team As String In teams
         If team.Length > 70 Then Continue For
         match = Regex.Match(team, pattern)
         If match.Success Then
            Console.Write("The {0} played in the {1} in", _
                           match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
         End If
      Next
      Console.WriteLine()

      startPos = 0
      endPos = 70
      Console.WriteLine("Attempting to match each line of an input string with '$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      


      startPos = 0
      endPos = 70
      pattern = basePattern + "\r?$" 
      Console.WriteLine("Attempting to match each line of an input string with '\r?$':")
      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub
End Module
' The example displays the following output:
'    Attempting to match the entire input string:
'    
'    Attempting to match each element in a string array:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
'    
'    Attempting to match each line of an input string with '$':
'    
'    Attempting to match each line of an input string with '\r+$':
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
'    The Chicago Cubs played in the National League in 1903-present.
'    The Detroit Tigers played in the American League in 1901-present.
'    The New York Giants played in the National League in 1885-1957.
'    The Washington Senators played in the American League in 1901-1960.
```

## <a name="start-of-string-only-a"></a>僅字串開頭：\A

**\A** 錨點指定比對必須發生在輸入字串的開頭。 它與 **^** 錨點相同，不同之處在於 **\A** 會忽略 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項。 因此，它可以只比對多行輸入字串中第一行的行首。

下列範例是類似於 **^** 和 **$** 錨點的範例。 它會在規則運算式中使用 **\A** 錨點，該規則運算式會擷取與某些職業棒球隊存在期間年份相關的資訊。 輸入字串包含五行。 在符合規則運算式模式的輸入字串中，對 [Regex.Matches(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Matches(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法的呼叫只會尋找其中的第一個子字串。 如範例所示，`Multiline` 選項不會有任何作用。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      int startPos = 0, endPos = 70;
      string input = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957\n" +
                     "Chicago Cubs, National League, 1903-present\n" + 
                     "Detroit Tigers, American League, 1901-present\n" + 
                     "New York Giants, National League, 1885-1957\n" +  
                     "Washington Senators, American League, 1901-1960\n";   

      string pattern = @"\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+";
      Match match;

      if (input.Substring(startPos, endPos).Contains(",")) {
         match = Regex.Match(input, pattern, RegexOptions.Multiline);
         while (match.Success) {
            Console.Write("The {0} played in the {1} in", 
                              match.Groups[1].Value, match.Groups[4].Value);
            foreach (Capture capture in match.Groups[5].Captures)
               Console.Write(capture.Value);

            Console.WriteLine(".");
            startPos = match.Index + match.Length;
            endPos = startPos + 70 <= input.Length ? 70 : input.Length - startPos;
            if (! input.Substring(startPos, endPos).Contains(",")) break;
            match = match.NextMatch();
         }
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim startPos As Integer = 0
      Dim endPos As Integer = 70
      Dim input As String = "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957" + vbCrLf + _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf + _
                            "Detroit Tigers, American League, 1901-present" + vbCrLf + _
                            "New York Giants, National League, 1885-1957" + vbCrLf + _
                            "Washington Senators, American League, 1901-1960" + vbCrLf  

      Dim pattern As String = "\A((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+"
      Dim match As Match

      ' Provide minimal validation in the event the input is invalid.
      If input.Substring(startPos, endPos).Contains(",") Then
         match = Regex.Match(input, pattern, RegexOptions.Multiline)
         Do While match.Success
            Console.Write("The {0} played in the {1} in", _
                              match.Groups(1).Value, match.Groups(4).Value)
            For Each capture As Capture In match.Groups(5).Captures
               Console.Write(capture.Value)
            Next
            Console.WriteLine(".")
            startPos = match.Index + match.Length 
            endPos = CInt(IIf(startPos + 70 <= input.Length, 70, input.Length - startPos))
            If Not input.Substring(startPos, endPos).Contains(",") Then Exit Do
            match = match.NextMatch()            
         Loop
         Console.WriteLine()                               
      End If      
   End Sub   
End Module
' The example displays the following output:
'    The Brooklyn Dodgers played in the National League in 1911, 1912, 1932-1957.
```

## <a name="end-of-string-or-before-ending-newline-z"></a>字串結尾或結束新行之前：\Z

**\Z** 錨點指定比對必須發生在輸入字串的結尾，或在輸入字串結尾的 **\n** 之前。 它與 **$** 錨點相同，不同之處在於 **\Z** 會忽略 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項。 因此在多行字串中，它只會比對最後一行的結尾，或 **\n** 前的上一行。

請注意，**\Z** 會比對 **\n**，但不會比對 **\r\n** (CR/LF 字元組合)。 若要比對 CR/LF，請將 **\r?\Z** 包含在規則運算式模式中。

下列範例會在規則運算式中使用 **\Z** 錨點，該規則運算式與上一節＜字串開頭或行首＞中的範例類似，會擷取與某些職業棒球隊存在期間年份相關的資訊。 規則運算式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z` 中的子運算式 `\r?\Z` 會比對字串的結尾，也會比對以 **\n** 或 **\r\n** 結尾的字串。 如此一來，陣列中的每個項目都會符合規則運算式模式。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine, 
                          "Detroit Tigers, American League, 1901-present" + Regex.Unescape(@"\n"), 
                          "New York Giants, National League, 1885-1957", 
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine}; 
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match succeeded.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match succeeded.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match succeeded.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match succeeded.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match succeeded.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match succeeded.
```

## <a name="end-of-string-only-z"></a>僅字串結尾：\z

**\z** 錨點指定比對必須發生在輸入字串的結尾。 與 **$** 語言項目相同，**\z** 會忽略 [RegexOptions.Multiline](xref:System.Text.RegularExpressions.RegexOptions.Multiline) 選項。 不像 **\Z** 語言項目，**\z** 不會比對字串結尾處的 **\n** 字元。 因此，它可以只比對輸入字串的最後一行。

下列範例會在規則運算式中使用 **\z** 錨點，該規則運算式與上一節中的範例相同，它會擷取與某些職業棒球隊存在期間年份相關的資訊。 這個範例會將字串陣列中的五個項目與規則運算模式 `^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z` 進行比對。 有兩個字串以歸位字元與換行字元結尾，一個字串以換行字元結尾，以及兩個字串不以歸位字元也不以換行字元結尾。 如輸出所示，只有不含歸位字元或換行字元的字串會符合模式。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string[] inputs = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957", 
                          "Chicago Cubs, National League, 1903-present" + Environment.NewLine,
                          "Detroit Tigers, American League, 1901-present\\r",
                          "New York Giants, National League, 1885-1957",
                          "Washington Senators, American League, 1901-1960" + Environment.NewLine };  
      string pattern = @"^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z";

      foreach (string input in inputs)
      {
         if (input.Length > 70 || ! input.Contains(",")) continue;

         Console.WriteLine(Regex.Escape(input));
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine("   Match succeeded.");
         else
            Console.WriteLine("   Match failed.");
      }   
   }
}
// The example displays the following output:
//    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
//       Match succeeded.
//    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
//       Match failed.
//    Detroit\ Tigers,\ American\ League,\ 1901-present\n
//       Match failed.
//    New\ York\ Giants,\ National\ League,\ 1885-1957
//       Match succeeded.
//    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
//       Match failed.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim inputs() As String = { "Brooklyn Dodgers, National League, 1911, 1912, 1932-1957",  _
                            "Chicago Cubs, National League, 1903-present" + vbCrLf, _
                            "Detroit Tigers, American League, 1901-present" + vbLf, _
                            "New York Giants, National League, 1885-1957", _
                            "Washington Senators, American League, 1901-1960" + vbCrLf }  
      Dim pattern As String = "^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z"

      For Each input As String In inputs
         If input.Length > 70 Or Not input.Contains(",") Then Continue For

         Console.WriteLine(Regex.Escape(input))
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine("   Match succeeded.")
         Else
            Console.WriteLine("   Match failed.")
         End If
      Next   
   End Sub
End Module
' The example displays the following output:
'    Brooklyn\ Dodgers,\ National\ League,\ 1911,\ 1912,\ 1932-1957
'       Match succeeded.
'    Chicago\ Cubs,\ National\ League,\ 1903-present\r\n
'       Match failed.
'    Detroit\ Tigers,\ American\ League,\ 1901-present\n
'       Match failed.
'    New\ York\ Giants,\ National\ League,\ 1885-1957
'       Match succeeded.
'    Washington\ Senators,\ American\ League,\ 1901-1960\r\n
'       Match failed.
```

## <a name="contiguous-matches-g"></a>連續比對：\G

**\G** 錨點指定比對必須發生在上一個比對結束的點。 當您將此錨點搭配 [Regex.Matches](xref:System.Text.RegularExpressions.Regex.Matches(System.String)) 或 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法使用時，它可確保所有相符項目是連續的。 

下列範例會使用規則運算式從逗點分隔的字串中擷取齧齒動物物種的名稱。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "capybara,squirrel,chipmunk,porcupine,gopher," + 
                     "beaver,groundhog,hamster,guinea pig,gerbil," + 
                     "chinchilla,prairie dog,mouse,rat";
      string pattern = @"\G(\w+\s?\w*),?";
      Match match = Regex.Match(input, pattern);
      while (match.Success) 
      {
         Console.WriteLine(match.Groups[1].Value);
         match = match.NextMatch();
      } 
   }
}
// The example displays the following output:
//       capybara
//       squirrel
//       chipmunk
//       porcupine
//       gopher
//       beaver
//       groundhog
//       hamster
//       guinea pig
//       gerbil
//       chinchilla
//       prairie dog
//       mouse
//       rat
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "capybara,squirrel,chipmunk,porcupine,gopher," + _
                            "beaver,groundhog,hamster,guinea pig,gerbil," + _
                            "chinchilla,prairie dog,mouse,rat"
      Dim pattern As String = "\G(\w+\s?\w*),?"
      Dim match As Match = Regex.Match(input, pattern)
      Do While match.Success
         Console.WriteLine(match.Groups(1).Value)
         match = match.NextMatch()
      Loop 
   End Sub
End Module
' The example displays the following output:
'       capybara
'       squirrel
'       chipmunk
'       porcupine
'       gopher
'       beaver
'       groundhog
'       hamster
'       guinea pig
'       gerbil
'       chinchilla
'       prairie dog
'       mouse
'       rat
```

規則運算式 `\G(\w+\s?\w*),?` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\G` | 從上一次比對結束的地方開始。
`\w+` | 比對一個或多個文字字元。
`\s?` | 比對零或一個空格。
`\w*` | 比對零個或多個文字字元。
`(\w+\s?\w*)` | 比對一或多個文字字元，後面接零或一個空格，再接零或多個文字字元。 這是第一個擷取群組。
`,?` | 比對出現零次或一次的常值逗號字元。
 
## <a name="word-boundary-b"></a>字邊界：\b

**\b** 錨點指定比對必須發生在文字字元 (**\w** 語言項目) 和非文字字元 (**\W** 語言項目) 之間的邊界上。 文字字元由英數字元及底線所組成；非文字字元是非英數字元或底線的任何字元  (如需詳細資訊，請參閱[規則運算式中的字元類別](classes.md))。比對也可能會在字串開頭或結尾的字邊界上發生。

**\b** 錨點經常用來確保子運算式會比對整個字組，而非只比對字組的開頭或結尾。 在下列範例中的規則運算式 `\bare\w*\b` 說明這個的使用方式。 它會比對任何以子字串 "are" 為開頭的字組。 範例的輸出也說明了 **\b** 會比對輸入字串的開頭和結尾。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "area bare arena mare";
      string pattern = @"\bare\w*\b";
      Console.WriteLine("Words that begin with 'are':");
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}",
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       Words that begin with 'are':
//       'area' found at position 0
//       'arena' found at position 10
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "area bare arena mare"
      Dim pattern As String = "\bare\w*\b"
      Console.WriteLine("Words that begin with 'are':")
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       Words that begin with 'are':
'       'area' found at position 0
'       'arena' found at position 10
```

規則運算式模式的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 開始字緣比對。
`are` | 比對子字串 "are"。
`\w*` | 比對零個或多個文字字元。
`\b` | 結束字緣比對。
 
## <a name="non-word-boundary-b"></a>非字邊界：\B

**\B** 錨點指定比對不得發生在字邊界上。 這和 **\b** 錨點相反。

下列範例使用 **\B** 錨點來尋找在字組中出現的子字串 "qu"。 規則運算式模式 `\Bqu\w+` 會比對以 "qu" 開頭的子字串，其中字組開頭並非 "qu"，並且會繼續比對到字組的結尾。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "equity queen equip acquaint quiet";
      string pattern = @"\Bqu\w+";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'quity' found at position 1
//       'quip' found at position 14
//       'quaint' found at position 21
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "equity queen equip acquaint quiet"
      Dim pattern As String = "\Bqu\w+"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next
   End Sub
End Module
' The example displays the following output:
'       'quity' found at position 1
'       'quip' found at position 14
'       'quaint' found at position 21
```

規則運算式模式的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\B` | 不要在字邊界開始比對。
`qu` | 比對子字串 "qu"。
`\w+` | 比對一個或多個文字字元。
 
## <a name="see-also"></a>另請參閱

[規則運算式語言 - 快速參考](quick-ref.md)

[規則運算式選項](options.md)
 



<!--HONumber=Nov16_HO3-->


