---
title: "規則運算式範例：掃描 HREF"
description: "規則運算式範例：掃描 HREF"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6484880-bdac-47cd-b5e5-9419c9ed14cd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 494ceeb2cc3bbf77098d2b6145690e7229ed3b9f

---

# <a name="regular-expression-example-scanning-for-hrefs"></a>規則運算式範例：掃描 HREF

下列範例將搜尋輸入字串，並顯示所有 href="..." 值和它們在字串中的位置。 

## <a name="the-regex-object"></a>Regex 物件

由於您可以從使用者程式碼多次呼叫 `DumpHRefs` 方法，因此它會使用 `static` [Regex.Match(String, String, RegexOptions)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions)) 方法。 這可讓規則運算式引擎快取規則運算式，並避免在每次呼叫方法時，因具現化新 [Regex](xref:System.Text.RegularExpressions.Regex) 物件導致的額外負荷。 接著，系統會使用 [Match](xref:System.Text.RegularExpressions.Match) 物件逐一查看字串中的所有相符項目。 

```csharp
private static void DumpHRefs(string inputString) 
{
   Match m;
   string HRefPattern = "href\\s*=\\s*(?:[\"'](?<1>[^\"']*)[\"']|(?<1>\\S+))";

   try {
      m = Regex.Match(inputString, HRefPattern, 
                      RegexOptions.IgnoreCase | RegexOptions.Compiled, 
                      TimeSpan.FromSeconds(1));
      while (m.Success)
      {
         Console.WriteLine("Found href " + m.Groups[1] + " at " 
            + m.Groups[1].Index);
         m = m.NextMatch();
      }   
   }
   catch (RegexMatchTimeoutException) {
      Console.WriteLine("The matching operation timed out.");
   }
}
```

```vb
Private Sub DumpHRefs(inputString As String) 
   Dim m As Match
   Dim HRefPattern As String = "href\s*=\s*(?:[""'](?<1>[^""']*)[""']|(?<1>\S+))"

   Try
      m = Regex.Match(inputString, HRefPattern, _ 
                      RegexOptions.IgnoreCase Or RegexOptions.Compiled,
                      TimeSpan.FromSeconds(1))
      Do While m.Success
         Console.WriteLine("Found href {0} at {1}.", _
                           m.Groups(1), m.Groups(1).Index)
         m = m.NextMatch()
      Loop   
   Catch e As RegexMatchTimeoutException
      Console.WriteLine("The matching operation timed out.")
   End Try
End Sub
```

下列範例說明如何呼叫 `DumpHRefs` 方法。

```csharp
public static void Main()
{
   string inputString = "My favorite web sites include:</P>" +
                        "<A HREF=\"http://msdn2.microsoft.com\">" +
                        "MSDN Home Page</A></P>" +
                        "<A HREF=\"http://www.microsoft.com\">" +
                        "Microsoft Corporation Home Page</A></P>" +
                        "<A HREF=\"http://blogs.msdn.com/bclteam\">" +
                        ".NET Base Class Library blog</A></P>";
   DumpHRefs(inputString);                     

}
// The example displays the following output:
//       Found href http://msdn2.microsoft.com at 43
//       Found href http://www.microsoft.com at 102
//       Found href http://blogs.msdn.com/bclteam at 176
```

```vb
Public Sub Main()
   Dim inputString As String = "My favorite web sites include:</P>" & _
                               "<A HREF=""http://msdn2.microsoft.com"">" & _
                               "MSDN Home Page</A></P>" & _
                               "<A HREF=""http://www.microsoft.com"">" & _
                               "Microsoft Corporation Home Page</A></P>" & _
                               "<A HREF=""http://blogs.msdn.com/bclteam"">" & _
                               ".NET Base Class Library blog</A></P>"
   DumpHRefs(inputString)                     
End Sub
' The example displays the following output:
'       Found href http://msdn2.microsoft.com at 43
'       Found href http://www.microsoft.com at 102
'       Found href http://blogs.msdn.com/bclteam/) at 176
```

規則運算式模式 `href\s*=\s*(?:["']&#40;?<1>[^"']*)["']|(?<1>\S+))` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`href` | 比對常值字串 "href"。 該比對不區分大小寫。
`\s*` | 比對零個以上的空白字元。
`=` |比對等號。
`\s*` | 比對零個以上的空白字元。
`(?:["']&#40;?<1>[^"']*)"&#124;(?<1>\S+))` | 比對下列項目之一，而不將結果指派給擷取的群組：引號 (或單引號)，後面加上零個或多個引號 (或單引號) 以外的任何字元，再加上引號 (或單引號)。 此模式中包含名為 `1` 的群組。 -或者- 一個或多個非空白字元。 此模式中包含名為 `1` 的群組。
`(?<1>[^"']*)` | 將零個或多個引號 (或單引號) 以外的任何字元指派給名為 `1` 的擷取端群組。
`"(?<1>\S+)` | 將一或多個非空白字元指派給名為 `1` 的擷取群組。
 
## <a name="match-result-class"></a>比對結果類別

搜尋的結果會儲存在 [Match](xref:System.Text.RegularExpressions.Match) 類別中，其可讓您存取搜尋所擷取的所有子字串。 它也會記住要搜尋的字串與所用的規則運算式，使其能呼叫 [Match.NextMatch](xref:System.Text.RegularExpressions.Match.NextMatch) 方法，以從最後一個搜尋結束的位置開始執行其他搜尋。

## <a name="explicitly-named-captures"></a>明確命名的擷取

在傳統的規則運算式中，會自動將擷取括號依序編號。 這會導致兩個問題。 第一，如果修改規則運算式時，是以插入或移除一組括號來進行，就必須重新撰寫所有參考已編號擷取的程式碼，以反映新的編號。 第二，不同的括號通常用來提供兩個替代運算式以進行可接受的比對，因此可能難以判斷這兩個運算式是哪一個實際傳回結果。

為了解決這些問題，[Regex](xref:System.Text.RegularExpressions.Regex) 類別支援 `(?<name>…)` 的語法，可將比對擷取至指定位置 (該位置可以使用字串或整數命名；使用整數則可以更快速地重新叫用)。 因此，相同字串的所有替代比對皆可導向相同的位置。 萬一發生衝突時，最後一個進入位置的比對就是成功的比對 (不過，您可以使用單一位置之多個比對的完整清單。 請參閱 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 集合，以取得詳細資訊)。

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)

[規則運算式範例](regex-examples.md)




<!--HONumber=Nov16_HO3-->


