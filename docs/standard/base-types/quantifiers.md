---
title: "規則運算式中的數量詞"
description: "規則運算式中的數量詞"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8e5124c4-20b5-4c57-ab68-301d1d7311c4
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cd47cc351fb926bcf444bdcbd12f3cd61d9fb327
ms.lasthandoff: 03/02/2017

---

# <a name="quantifiers-in-regular-expressions"></a>規則運算式中的數量詞

數量詞指定輸入中要有多少字元、群組或字元類別的執行個體，才能找到相符項目。 下表列出 .NET 支援的數量詞。

Greedy (窮盡) 數量詞 | Lazy (最少) 數量詞 | 說明
----------------- | --------------- | ----------- 
**\*** | **\*?** | 比對零或多次。
**+** | **+?** | 比對一或多次。
**?** | **??** | 比對零或一次。
**{**_n_**}** | **{**_n_**}?** | 確實比對 n 次。
**{**_n_**,}** | **{**_n_**,}?** | 至少比對 n 次。
**{**_n_**,**_m_**}** | **{**_n_**,**_m_**}?** | 比對 n 到 m 次。
 
數量 *n* 和 *m* 都是整數常數。 數量詞通常是 Greedy (窮盡)。其會讓規則運算式引擎盡可能多地從每次出現的特定模式進行比對。 在數量詞中加上 `?` 字元會使它 Lazy (最少)，造成規則運算式引擎比對的項目愈少愈好。 如需 Greedy (窮盡) 與 Lazy (最少) 數量詞差異的完整說明，請參閱本主題後文的 [Greedy (窮盡) 與 Lazy (最少) 數量詞](#greedy-and-lazy-quantifiers)一節。

> [!IMPORTANT]
> 巢狀數量詞 (如規則運算式模式 `(a*)*` 所做) 會增加規則運算式引擎必須執行的比較次數，如輸入字串中的字元數指數函數一樣。 如需此行為及其因應措施的詳細資訊，請參閱[規則運算式中的回溯](backtracking.md)。

## <a name="regular-expression-quantifiers"></a>規則運算式的數量詞

下列章節會列出 .NET 規則運算式支援的數量詞。 

> [!NOTE]
> 如果在規則運算式模式中同時出現了 \*、+、?、{ 和 } 字元，除非它們包含在[字元類別](classes.md)中，否則規則運算式引擎會將它們解譯為數量詞或數量詞建構的一部分。 若要在字元類別外將這些字元解譯為常值字元，您必須在它們前面加上反斜線以逸出字元。 例如，字串 `\*` 在規則運算式模式中會解譯成常值星號 ("*") 字元。

### <a name="match-zero-or-more-times-"></a>比對零或多次：\*

\* 數量詞會比對前置元素零次或多次。 它相當於 **{0,}** 數量詞。 **\*** 是 Greedy (窮盡) 數量詞，其 lazy (最少) 對等項目是 **\*?**。

下例會示範此規則運算式。 在輸入字串的九個數字中，有五個符合模式，四個 (`95`、`929`、`9129` 和 `9919`) 不符合。

```csharp
string pattern = @"\b91*9*\b";   
string input = "99 95 919 929 9119 9219 999 9919 91119";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       '99' found at position 0.
//       '919' found at position 6.
//       '9119' found at position 14.
//       '999' found at position 24.
//       '91119' found at position 33.
```

```vb
Dim pattern As String = "\b91*9*\b"   
Dim input As String = "99 95 919 929 9119 9219 999 9919 91119"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '99' found at position 0.
'       '919' found at position 6.
'       '9119' found at position 14.
'       '999' found at position 24.
'       '91119' found at position 33.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`91*` | 比對後面接著零或多個 "1" 字元的 "9"。
`9*` | 比對零或多個 "9" 字元。
`\b` | 在字邊界結束。
 
### <a name="match-one-or-more-times-"></a>比對一或多次：+

**+** 數量詞會比對前置元素一次或多次。 相當於 **{1,}**。 **+** 是 Greedy (窮盡) 數量詞，其 Lazy (最少) 對等項目是 **+?**。

例如，規則運算式 `\ban+\w*?\b` 會嘗試比對以字母 `a` 開頭、接著一或多個字母 `n` 的單字。 下例會示範此規則運算式。 規則運算式會比對出單字 `an`、`annual`、`announcement` 和 `antique`，而不會比對出 `autumn` 和 `all`。

```csharp
string pattern = @"\ban+\w*?\b";

string input = "Autumn is a great time for an annual announcement to all antique collectors.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//       'an' found at position 27.
//       'annual' found at position 30.
//       'announcement' found at position 37.
//       'antique' found at position 57.      
```

```vb
Dim pattern As String = "\ban+\w*?\b"

Dim input As String = "Autumn is a great time for an annual announcement to all antique collectors."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next   
' The example displays the following output:   
'       'an' found at position 27.
'       'annual' found at position 30.
'       'announcement' found at position 37.
'       'antique' found at position 57. 
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`an+` | 比對 "a" 接著一或多個 "n" 字元。 
`\w*?` | 比對單字字元零或多次，但次數愈少愈好。
`\b` | 在字邊界結束。
 
### <a name="match-zero-or-one-time-"></a>比對零或一次：?

**?** 數量詞會比對前置元素零或一次。 相當於 **{0,1}**。 **?** 是 Greedy (窮盡) 數量詞，其 Lazy (最少) 對等項目是 **??**。

例如，規則運算式 `\ban?\b` 會嘗試比對以字母 `a` 開頭、接著零或一個字母 `n` 的單字。 換言之，它會嘗試比對單字 `a` 和 `an`。 下例會示範此規則運算式。

```csharp
string pattern = @"\ban?\b";
string input = "An amiable animal with a large snount and an animated nose.";
foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

// The example displays the following output:   
//        'An' found at position 0.
//        'a' found at position 23.
//        'an' found at position 42.
```

```vb
Dim pattern As String = "\ban?\b"
Dim input As String = "An amiable animal with a large snount and an animated nose."
For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next  
' The example displays the following output:   
'       'An' found at position 0.
'       'a' found at position 23.
'       'an' found at position 42.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`an?` | 比對 "a" 接著零或一個 "n" 字元。 
`\b` | 在字邊界結束。
 
### <a name="match-exactly-n-times-n"></a>精確比對 n 次：{n}

**{**_n_**}** 數量詞會確實比對 *n* 次前置元素，其中 *n* 是任何整數。 **{**_n_**}** 是 Greedy (窮盡) 數量詞，其 Lazy (最少) 對等項目是 **{**_n_**}?**。

例如，規則運算式 `\b\d+\,\d{3}\b` 會嘗試比對出字邊界、接著一或多個十進位數字、再接三個十進位數字、接著字邊界的項目。 下例會示範此規則運算式。 

```csharp
string pattern = @"\b\d+\,\d{3}\b";
string input = "Sales totaled 103,524 million in January, " + 
                      "106,971 million in February, but only " + 
                      "943 million in March.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:   
//        '103,524' found at position 14.
//        '106,971' found at position 45.
```

```vb
Dim pattern As String = "\b\d+\,\d{3}\b"
Dim input As String = "Sales totaled 103,524 million in January, " + _
                      "106,971 million in February, but only " + _
                      "943 million in March."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:   
'       '103,524' found at position 14.
'       '106,971' found at position 45.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`\d+` | 比對一個或多個十進位數字。 
`\,` | 比對逗號字元。
`\d{3}` | 比對三個十進位數字。
`\b` | 在字邊界結束。
 
### <a name="match-at-least-n-times-n"></a>至少比對 n 次：{n,}

**{**_n_**,}** 數量詞至少會比對 *n* 次前置元素，其中 *n* 是任何整數。 **{**_n_**,}** 是 Greedy (窮盡) 數量詞，其 Lazy (最少) 對等項目是 **{**_n_**}?**。

例如，規則運算式 `\b\d{2,}\b\D+` 會嘗試比對出字邊界、接著至少兩個數字、再接字邊界、然後非數字字元的項目。 下例會示範此規則運算式。 規則運算式無法比對出片語「7 天」，因為它只包含一個十進位數字，但會成功比對出片語「10 週和 300 年」。

```csharp
string pattern = @"\b\d{2,}\b\D+";   
string input = "7 days, 10 weeks, 300 years";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '10 weeks, ' found at position 8.
// 
``` 

```vb
Dim pattern As String = "\b\d{2,}\b\D+"  
 Dim input As String = "7 days, 10 weeks, 300 years"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '10 weeks, ' found at position 8.
'       '300 years' found at position 18.
      '300 years' found at position 18.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`\d{2,}` | 至少比對兩個十進位數字。 
`\b` | 比對字邊界。
`\D+` | 至少比對一個非十進位數字。
 
### <a name="match-between-n-and-m-times-nm"></a>比對 n 到 m 次：{n,m}

**{**_n_**,**_m_**}** 數量詞至少比對 *n* 次前置元素，但不超過 *m* 次，其中 *n* 和 *m* 都是整數。 **{**_n_**,**_m_**}** 是 Greedy (窮盡) 數量詞，其 Lazy (最少) 對等項目是 **{**_n_**,**_m_**}?**。

在下例中，規則運算式 `(00\s){2,4}` 會嘗試比對&2; 至&4; 次兩個數字零後接空格的項目。 請注意，輸入字串有此模式的最後部分出現了五次，而非上限四次。 但只有這個子字串的初始部分 (最多到空格和第五對零) 符合規則運算式模式。

```csharp
string pattern = @"(00\s){2,4}";
string input = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        '00 00 ' found at position 8.
//        '00 00 00 ' found at position 23.
//        '00 00 00 00 ' found at position 35.
```

```vb
Dim pattern As String = "(00\s){2,4}"
Dim input As String = "0x00 FF 00 00 18 17 FF 00 00 00 21 00 00 00 00 00"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       '00 00 ' found at position 8.
'       '00 00 00 ' found at position 23.
'       '00 00 00 00 ' found at position 35.
```

### <a name="match-zero-or-more-times-lazy-match-"></a>比對零或多次 (Lazy (最少) 比對)：\*?

**\*?** 數量詞會比對零或多次前置元素，但次數愈少愈好。 它是 Greedy (窮盡) 數量詞 **\*** 的對應 Lazy (最少)。

在下例中，規則運算式 `\b\w*?oo\w*?\b` 會比對包含字串 `oo` 的所有文字。 

```csharp
 string pattern = @"\b\w*?oo\w*?\b";
 string input = "woof root root rob oof woo woe";
 foreach (Match match in Regex.Matches(input, pattern, RegexOptions.IgnoreCase))
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

 //  The example displays the following output:
//        'woof' found at position 0.
//        'root' found at position 5.
//        'root' found at position 10.
//        'oof' found at position 19.
//        'woo' found at position 23.
```

```vb
Dim pattern As String = "\b\w*?oo\w*?\b"
 Dim input As String = "woof root root rob oof woo woe"
 For Each match As Match In Regex.Matches(input, pattern, RegexOptions.IgnoreCase)
    Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
 Next 
 ' The example displays the following output:
'       'woof' found at position 0.
'       'root' found at position 5.
'       'root' found at position 10.
'       'oof' found at position 19.
'       'woo' found at position 23.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 從字緣開始。
`\w*?` | 比對零或多個單字字元，但字元愈少愈好。 
`oo` | 比對字串 "oo"。
`\w*?` | 比對零或多個單字字元，但字元愈少愈好。
`\b` | 在字邊界結束。
 
### <a name="match-one-or-more-times-lazy-match-"></a>比對零或多次 (Lazy (最少) 比對)：+?

**+?** 數量詞會比對一或多次前置元素，但次數愈少愈好。 它是 Greedy (窮盡) 數量詞 **+** 的對應 Lazy (最少)。

例如，規則運算式 `\b\w+?\b` 會比對一或多個以字邊界分隔的字元。 下例會示範此規則運算式。

```csharp
string pattern = @"\b\w+?\b";
string input = "Aa Bb Cc Dd Ee Ff";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Aa' found at position 0.
//        'Bb' found at position 3.
//        'Cc' found at position 6.
//        'Dd' found at position 9.
//        'Ee' found at position 12.
//        'Ff' found at position 15.
```

```vb
Dim pattern As String = "\b\w+?\b"
 Dim input As String = "Aa Bb Cc Dd Ee Ff"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Aa' found at position 0.
'       'Bb' found at position 3.
'       'Cc' found at position 6.
'       'Dd' found at position 9.
'       'Ee' found at position 12.
'       'Ff' found at position 15.
```

### <a name="match-zero-or-one-time-lazy-match-"></a>比對零或一次 (Lazy (最少) 比對)：??

**??** 量詞會比對零或一次前置元素，但次數愈少愈好。 它是 Greedy (窮盡) 量詞 **?** 的對應 Lazy (最少)。

例如，規則運算式 `^\s*(System.)??Console.Write(Line)??\(??` 會嘗試比對字串 "Console.Write" 或 "Console.WriteLine"。 字串也可以在 "Console" 前包含 "System."， 後面也可以是左括號。 字串必須位在行的開頭，雖然前面可以是空格。 下例會示範此規則運算式。

```csharp
string pattern = @"^\s*(System.)??Console.Write(Line)??\(??";
string input = "System.Console.WriteLine(\"Hello!\")\n" + 
                      "Console.Write(\"Hello!\")\n" + 
                      "Console.WriteLine(\"Hello!\")\n" + 
                      "Console.ReadLine()\n" + 
                      "   Console.WriteLine";
foreach (Match match in Regex.Matches(input, pattern, 
                                      RegexOptions.IgnorePatternWhitespace | 
                                      RegexOptions.IgnoreCase | 
                                      RegexOptions.Multiline))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'System.Console.Write' found at position 0.
//        'Console.Write' found at position 36.
//        'Console.Write' found at position 61.
//        '   Console.Write' found at position 110.
```

```vb
Dim pattern As String = "^\s*(System.)??Console.Write(Line)??\(??"
Dim input As String = "System.Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.Write(""Hello!"")" + vbCrLf + _
                      "Console.WriteLine(""Hello!"")" + vbCrLf + _
                      "Console.ReadLine()" + vbCrLf + _
                      "   Console.WriteLine"
For Each match As Match In Regex.Matches(input, pattern, _
                                         RegexOptions.IgnorePatternWhitespace Or RegexOptions.IgnoreCase Or RegexOptions.MultiLine)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'System.Console.Write' found at position 0.
'       'Console.Write' found at position 36.
'       'Console.Write' found at position 61.
'       '   Console.Write' found at position 110.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | ----------- 
`^` | 比對輸入資料流的開頭。
`\s*` | 比對零個以上的空白字元。
`(System.)??` | 比對出現零或一次的字串 "System."。
`Console.Write` | 比對字串 "Console.Write"。
`(Line)??` | 比對出現零或一次的字串 "Line"。
`\(??` | 比對出現零或一次的左括號。
 
### <a name="match-exactly-n-times-lazy-match-n"></a>精確比對 n 次 (Lazy (最少) 比對)：{n}?

**{**_n_**}?** 數量詞會確實比對 *n* 次前置元素，其中 *n* 是任何整數。 它是 Greedy (窮盡) 數量詞 **{**_n_**}+** 的對應 Lazy (最少)。

下例會使用規則運算式 `\b(\w{3,}?\.){2}?\w{3,}?\b` 來識別網站位址。 請注意它會比對 "www.microsoft.com" 和 "msdn.microsoft.com"，但不比對 "mywebsite" 或 "mycompany.com"。

```csharp
string pattern = @"\b(\w{3,}?\.){2}?\w{3,}?\b";
string input = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'www.microsoft.com' found at position 0.
//        'msdn.microsoft.com' found at position 18.
```

```vb
Dim pattern As String = "\b(\w{3,}?\.){2}?\w{3,}?\b"
 Dim input As String = "www.microsoft.com msdn.microsoft.com mywebsite mycompany.com"
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next     
' The example displays the following output:
'       'www.microsoft.com' found at position 0.
'       'msdn.microsoft.com' found at position 18.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`(\w{3,}?\.)` | 比對至少 3 個單字字元，但字元愈少愈好，後面接著點或句號字元。 這是第一個擷取群組。
`(\w{3,}?\.){2}?` | 比對兩次第一個群組中的模式，但次數愈少愈好。
`\b` | 結束字邊界比對。
 
### <a name="match-at-least-n-times-lazy-match-n"></a>至少比對 n 次 (Lazy (最少) 比對)：{n,}?

**{**_n_**,}?** 數量詞至少會比對 *n* 次前置元素，其中 *n* 是任何整數，但次數愈少愈好。 它是 Greedy (窮盡) 數量詞 **{**_n_**,}** 的對應 Lazy (最少)。

請參閱上一節示範的 **{**_n_**}?** 數量詞範例。 在該例中，規則運算式使用 **{**_n_**,}** 數量詞來比對至少三個字元後接句號的字串。

### <a name="match-between-n-and-m-times-lazy-match-nm"></a>比對 n 到 m 次 (Lazy ( 最少) 比對)：{n,m}?

**{**_n_**,**_m_**}?** 數量詞比對 *n* 至 *m* 次前置元素，其中 *n* 和 *m* 是任何整數，但次數愈少愈好。 它是 Greedy (窮盡) 數量詞 **{**_n_**,**_m_**}** 的對應 Lazy (最少)。

在下例中，規則運算式 `\b[A-Z](\w*\s+){1,10}?[.!?]` 會比對包含一到十個單字的句子。 它會比對輸入字串中的所有句子，除了包含 18 個字的句子。

```csharp
string pattern = @"\b[A-Z](\w*?\s*?){1,10}[.!?]";
string input = "Hi. I am writing a short note. Its purpose is " + 
                      "to test a regular expression that attempts to find " + 
                      "sentences with ten or fewer words. Most sentences " + 
                      "in this note are short.";
foreach (Match match in Regex.Matches(input, pattern))
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index);

//  The example displays the following output:
//        'Hi.' found at position 0.
//        'I am writing a short note.' found at position 4.
//        'Most sentences in this note are short.' found at position 132.
```

```vb
Dim pattern As String = "\b[A-Z](\w*\s?){1,10}?[.!?]"
Dim input As String = "Hi. I am writing a short note. Its purpose is " + _
                      "to test a regular expression that attempts to find " + _
                      "sentences with ten or fewer words. Most sentences " + _
                      "in this note are short."
For Each match As Match In Regex.Matches(input, pattern)
   Console.WriteLine("'{0}' found at position {1}.", match.Value, match.Index)
Next 
' The example displays the following output:
'       'Hi.' found at position 0.
'       'I am writing a short note.' found at position 4.
'       'Most sentences in this note are short.' found at position 132.
```

規則運算式模式的定義如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`[A-Z]` | 比對從 A 到 Z 的大寫字元。
`(\w*\s+)` | 比對零或多個後接一或多個空白字元的單字字元。 這是第一個擷取群組。
`{1,10}?` | 比對 1 到 10 次上一個模式，但次數愈少愈好。
`[.!?]` | 比對任一標點符號字元 "."、"!" 或 "?"。
 
## <a name="greedy-and-lazy-quantifiers"></a>Greedy (窮盡) 與 Lazy (最少) 數量詞

數個數量詞有兩種版本︰ 

* Greedy (窮盡) 版本。 

  Greedy (窮盡) 數量詞會嘗試盡可能多次比對項目。 


* • 非 Greedy (窮盡) (或 Lazy (最少)) 版本。 

 非 Greedy (窮盡) 數量詞會嘗試盡可能少比對項目。 只要加上 **?** 就可以將 Greedy (窮盡) 數量詞變成 Lazy (最少) 數量詞。

請考慮要擷取數字字串末四碼的簡單規則運算式，例如信用卡號碼。 使用 **\*** Greedy (窮盡) 數量詞的規則運算式版本為 `\b.*([0-9]{4})\b`。 但若字串包含兩組數字，這個規則運算式只會比對第二組數字的末四碼，如下列範例所示。

```csharp
string greedyPattern = @"\b.*([0-9]{4})\b";
string input1 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input1, greedyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******1999.
```

```vb
Dim greedyPattern As String = "\b.*([0-9]{4})\b"
Dim input1 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input1, greedypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next
' The example displays the following output:
'       Account ending in ******1999.
```

規則運算式無法比對第一組數字，因為 **\*** 數量詞嘗試在整個字串中盡可能多次比對上一個元素，所以在字串的結尾找到符合項目。

這不是我們所要的結果。 您可以改用 **\*?** 兩個數字的確實位數的 Lazy (最少) 數量詞，如下例所示。

```csharp
string lazyPattern = @"\b.*?([0-9]{4})\b";
string input2 = "1112223333 3992991999";
foreach (Match match in Regex.Matches(input2, lazyPattern))
   Console.WriteLine("Account ending in ******{0}.", match.Groups[1].Value);

// The example displays the following output:
//       Account ending in ******3333.
//       Account ending in ******1999.
```

```vb
Dim lazyPattern As String = "\b.*?([0-9]{4})\b"
Dim input2 As String = "1112223333 3992991999"
For Each match As Match In Regex.Matches(input2, lazypattern)
   Console.WriteLine("Account ending in ******{0}.", match.Groups(1).Value)
Next     
' The example displays the following output:
'       Account ending in ******3333.
'       Account ending in ******1999.
```

在大部分情況下，有 Greedy (窮盡) 和 Lazy (最少) 數量詞的規則運算式會傳回相同的結果。 與萬用字元 (**.**) 中繼字元一起使用時最常傳回不同的結果，會比對任何字元。 

## <a name="quantifiers-and-empty-matches"></a>數量詞與空白比對

找到擷取的最小數字時，數量詞 **\***、**+** 和 **{**_n_**,**_m_**}** 及其 Lazy (最少) 對等項在空白比對後絕不重複。 當可能群組擷取的最大數目是無限或接近無限時，此規則可防止數量詞在碰到空白子運算式比對時進入無限迴圈。

例如，下列程式碼顯示以比對零或多次零或一個 "a" 字元的規則運算式模式 `(a?)*,` 呼叫 [Regex.Match](xref:System.Text.RegularExpressions.Regex.Match(System.String)) 方法的結果。 請注意，單一擷取群組會擷取每個 "a" 以及 [String.Empty](xref:System.String.Empty)，但沒有第二個空白符合項目，因為第一個空白符合項目讓數量詞停止重複。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = "(a?)*";
      string input = "aaabbb";
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         GroupCollection groups = match.Groups;
         for (int grpCtr = 1; grpCtr <= groups.Count - 1; grpCtr++) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups[grpCtr].Value,
                              groups[grpCtr].Index);
            int captureCtr = 0;
            foreach (Capture capture in groups[grpCtr].Captures) {
               captureCtr++;
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index);
            }
         } 
      }   
   }
}
// The example displays the following output:
//       Match: 'aaa' at index 0
//          Group 1: '' at index 3
//             Capture 1: 'a' at index 0
//             Capture 2: 'a' at index 1
//             Capture 3: 'a' at index 2
//             Capture 4: '' at index 3
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "(a?)*"
      Dim input As String = "aaabbb"
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at index {1}", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         Dim groups As GroupCollection = match.Groups
         For grpCtr As Integer = 1 To groups.Count - 1
            Console.WriteLine("   Group {0}: '{1}' at index {2}", 
                              grpCtr, 
                              groups(grpCtr).Value,
                              groups(grpCtr).Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In groups(grpCtr).Captures
               captureCtr += 1
               Console.WriteLine("      Capture {0}: '{1}' at index {2}", 
                                 captureCtr, capture.Value, capture.Index)
            Next
         Next 
      End If   
   End Sub
End Module
' The example displays the following output:
'       Match: 'aaa' at index 0
'          Group 1: '' at index 3
'             Capture 1: 'a' at index 0
'             Capture 2: 'a' at index 1
'             Capture 3: 'a' at index 2
'             Capture 4: '' at index 3
```

若要查看定義擷取數目上下限的擷取群組和定義固定擷取數目的擷取群組之間的實際差異，請考慮規則運算式模式 `(a\1|(?(1)\1)){0,2}` 和 `(a\1|(?(1)\1)){2}`。 這兩個規則運算式都是由單一擷取群組組成，如下表所示加以定義。 

模式 | 描述
------- | -----------
`(a\1` | 比對 "a" 及第一個擷取的群組值...
`&#124;(?(1)` | … 或測試第一個擷取的群組是否已定義。 (請注意，**(?(1)** 建構不會定義擷取群組。)
`\1))` | 如果第一個擷取的群組存在，即比對其值。 如果群組不存在，群組會比對 [String.Empty](xref:System.String.Empty)。 
 
第一個規則運算式嘗試比對這種模式零到兩次，第二個不多不少就兩次。 因為第一個模式達到其第一個 [String.Empty](xref:System.String.Empty) 擷取的擷取數目下限，所以絕不會重複嘗試比對 `a\1;`，`{0,2}` 數量詞在最後一個反覆項目中只允許空白比對。 相反地，第二個規則運算式不比對 "a"，因為它會評估 `a\1` 第二次，反覆的下限 2，會強制引擎在空白比對後重複。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern, input;

      pattern = @"(a\1|(?(1)\1)){0,2}";
      input = "aaabbb"; 

      Console.WriteLine("Regex pattern: {0}", pattern);
      Match match = Regex.Match(input, pattern);
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
      Console.WriteLine();

      pattern = @"(a\1|(?(1)\1)){2}";
      Console.WriteLine("Regex pattern: {0}", pattern);
      match = Regex.Match(input, pattern);
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index);
      if (match.Groups.Count > 1) {
         for (int groupCtr = 1; groupCtr <= match.Groups.Count - 1; groupCtr++)
         {
            Group group = match.Groups[groupCtr];         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index);
            int captureCtr = 0;
            foreach (Capture capture in group.Captures) {
               captureCtr++;
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index);
            }   
         }
      }
   }
}
// The example displays the following output:
//       Regex pattern: (a\1|(?(1)\1)){0,2}
//       Match: '' at position 0.
//          Group: 1: '' at position 0.
//             Capture: 1: '' at position 0.
//       
//       Regex pattern: (a\1|(?(1)\1)){2}
//       Matched 'a' at position 0.
//          Group: 1: 'a' at position 0.
//             Capture: 1: '' at position 0.
//             Capture: 2: 'a' at position 0.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern, input As String

      pattern = "(a\1|(?(1)\1)){0,2}"
      input = "aaabbb" 

      Console.WriteLine("Regex pattern: {0}", pattern)
      Dim match As Match = Regex.Match(input, pattern)
      Console.WriteLine("Match: '{0}' at position {1}.", 
                        match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
      Console.WriteLine()

      pattern = "(a\1|(?(1)\1)){2}"
      Console.WriteLine("Regex pattern: {0}", pattern)
      match = Regex.Match(input, pattern)
         Console.WriteLine("Matched '{0}' at position {1}.", 
                           match.Value, match.Index)
      If match.Groups.Count > 1 Then
         For groupCtr As Integer = 1 To match.Groups.Count - 1
            Dim group As Group = match.Groups(groupCtr)         
            Console.WriteLine("   Group: {0}: '{1}' at position {2}.", 
                              groupCtr, group.Value, group.Index)
            Dim captureCtr As Integer = 0
            For Each capture As Capture In group.Captures
               captureCtr += 1
               Console.WriteLine("      Capture: {0}: '{1}' at position {2}.", 
                                 captureCtr, capture.Value, capture.Index)
            Next   
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Regex pattern: (a\1|(?(1)\1)){0,2}
'       Match: '' at position 0.
'          Group: 1: '' at position 0.
'             Capture: 1: '' at position 0.
'       
'       Regex pattern: (a\1|(?(1)\1)){2}
'       Matched 'a' at position 0.
'          Group: 1: 'a' at position 0.
'             Capture: 1: '' at position 0.
'             Capture: 2: 'a' at position 0.
```

## <a name="see-also"></a>請參閱

[規則運算式語言 - 快速參考](quick-ref.md)

[規則運算式中的回溯](backtracking.md)


