---
title: "規則運算式中的替代建構"
description: "規則運算式中的替代建構"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 59ffac4d-fc6e-461f-8783-d9f8dc88ce2c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fa2a880e5bcc36354bd59d3dc032180c89984f1d
ms.lasthandoff: 03/02/2017

---

# <a name="alternation-constructs-in-regular-expressions"></a>規則運算式中的替代建構

替代建構會修改規則運算式來啟用二選一或條件式比對。 .NET 支援下列三種替代建構：

* 以 **|** 進行的模式比對

* 以 **(?(**_expression_**)**_yes_**|**_no_**)** 進行的條件式比對

* 依據有效擷取群組進行的條件式比對

## <a name="pattern-matching-with-"></a>以 | 進行的模式比對

您可以使用分隔號 (|) 字元來比對其中任一系列的模式，且 | 字元會分隔每一個模式。 

| 字元和正字元類別一樣，可以用來比對一些單一字元當中的任一字元。 下列範例同時使用正字元類別和透過 | 字元的二選一模式比對，在字串中尋找與單字 "gray" 或 "grey" 相符的項目。 在此案例中，| 字元會產生更詳細的規則運算式。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      // Regular expression using character class.
      string pattern1 = @"\bgr[ae]y\b";
      // Regular expression using either/or.
      string pattern2 = @"\bgr(a|e)y\b";

      string input = "The gray wolf blended in among the grey rocks.";
      foreach (Match match in Regex.Matches(input, pattern1))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
      Console.WriteLine();
      foreach (Match match in Regex.Matches(input, pattern2))
         Console.WriteLine("'{0}' found at position {1}", 
                           match.Value, match.Index);
   }
}
// The example displays the following output:
//       'gray' found at position 4
//       'grey' found at position 35
//       
//       'gray' found at position 4
//       'grey' found at position 35           
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      ' Regular expression using character class.
      Dim pattern1 As String = "\bgr[ae]y\b"
      ' Regular expression using either/or.
      Dim pattern2 As String = "\bgr(a|e)y\b"

      Dim input As String = "The gray wolf blended in among the grey rocks."
      For Each match As Match In Regex.Matches(input, pattern1)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
      Console.WriteLine()
      For Each match As Match In Regex.Matches(input, pattern2)
         Console.WriteLine("'{0}' found at position {1}", _
                           match.Value, match.Index)
      Next      
   End Sub
End Module
' The example displays the following output:
'       'gray' found at position 4
'       'grey' found at position 35
'       
'       'gray' found at position 4
'       'grey' found at position 35 
```

使用 | 字元的規則運算式 `\bgr(a|e)y\b,` 的解譯方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`gr` | 比對字元 "gr"。
`(a|e)` | 比對 "a" 或 "e"。
`y\b` |    比對字邊界上的 "y"。


| 字元也可以用來與多個字元或子運算式執行二選一的比對，這些字元或子運算式可以包含字元常值和規則運算式語言項目的任何組合。 然而，字元類別並不提供這項功能。下列範例使用 | 字元擷取其中任一組美國社會安全號碼 (SSN)，其為 *ddd-dd-dddd* 格式的 9 位數數字，或擷取美國雇主識別編號 (EIN)，其為 *dd-ddddddd* 格式的 9 位數數字。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

規則運算式 `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`(\d{2}-\d{7}|;\d{3}-\d{2}-\d{4})` | 比對下列其中一項：兩個十進位數字後接連字號再後接七個十進位數字，或是三個十進位數字、連字號、兩個十進位數字、另一個連字號及四個十進位數字。 
`\d` | 結束字緣比對。
                                         
## <a name="conditional-matching-with-an-expression"></a>使用運算式進行的條件式比對

這個語言項目會嘗試比對兩個模式的其中一個是否符合初始模式。 它的語法為：

**(?(**_expression_**)**_yes_**|**_no_**)**

其中 *expression* 是要比對的初始模式，*yes* 是符合 expression 時要比對的模式，而 *no* 是不符合 *expression* 時要比對的選擇性模式。 規則運算式引擎會將 *expression* 視為零寬度的判斷提示，也就是說，規則運算式引擎不會在評估 *expression* 之後於輸入資料流中前進。 因此，此建構等同於下列：

**(?(?**=_expression_**)**_yes_**|**_no_**)**

其中 **(?**=_expression_**)** 是零寬度的判斷提示建構 (如需詳細資訊，請參閱[規則運算式中的群組建構](grouping.md))。因為規則運算式引擎會將 *expression* 解譯為錨點 (寬度為零的判斷提示)，所以 *expression* 必須是寬度為零的判斷提示 (如需詳細資訊，請參閱[規則運算式中的錨點](anchors.md))，或同樣包含在 *yes* 中的子運算式。 否則就無法比對 *yes* 模式。 

> [!NOTE]
> 若 *expression* 為具名或編號的擷取群組，則替代建構會被解譯為擷取測試。如需詳細資訊，請參閱下節的[對有效的擷取群組進行條件式比對](#conditional-matching-based-on-a-valid-captured-group)。 換句話說，規則運算式引擎不會嘗試比對擷取的子字串，而會測試群組是否存在。
 

下列範例是上一節中使用的範例變化。 它使用條件式比對，來判斷字邊界後的前三個字元是否為兩個位數後接連字號。 如果是，它會嘗試比對美國美國雇主識別碼 (EIN)。 如果不是，它會嘗試比對美國社會安全碼 (SSN)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

規則運算式模式 `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`(?(\d{2}-)` | 判斷接下來三個字元是否為兩個數字後接連字號。
`\d{2}-\d{7}` | 如果上一個模式符合，便會比對兩個數字，後接連字號，再後接七個數字。
`\d{3}-\d{2}-\d{4}` | 如果上一個模式不符合，便會比對三個十進位數字、連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。 
`\b` | 比對字邊界。
 
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>依據有效擷取群組進行的條件式比對

這個語言項目會嘗試根據它是否已經比對指定的擷取群組，比對兩種模式的其中一種。 它的語法為：

**(?(**_name_**)**_yes_**|**_no_**)**

或

**(?(**_number_**)**_yes_**|**_no_**)**

其中 *name* 是名稱，而 *number* 是擷取群組的數目，*yes* 是 name 或 number 其中之一相符時要比對的運算式，而 *no* 則是不符合時要比對的選擇性運算式。

如果 *name* 並未對應到規則運算式模式中所使用的擷取群組名稱，則替代建構會解譯為運算式測試，如上一節中所說明。 通常，這表示 expression 判斷值為 `false`。 如果 `number` 沒有對應到規則運算式模式中所使用的編號擷取群組，則規則運算式引擎會擲回 [ArgumentException](xref:System.ArgumentException)。

下列範例是上一節中使用的範例變化。 它會使用名為 `n2` 的擷取群組，其由兩個數字後接連字號所組成。 替代建構會測試是否已在輸入字串中比對這個擷取群組。 如果是，替代建構會嘗試比對九位數雇主識別碼 (EIN) 的末七碼。美國雇主識別碼 (EIN)。 如果不是，則會嘗試比對九位數美國社會安全碼 (SSN)。社會安全碼 (SSN)。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example displays the following output:
//       Matches for \b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
```

規則運算式模式 `\b(?<n2>\d{2}-)*(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` 的解譯方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 從字緣開始。
`(?<n2>\d{2}-)*` | 比對出現零次或一次且後接連字號的兩個數字。 將此擷取群組命名為 `n2`。
`(?(n2)` | 測試 `n2` 在輸入字串中是否相符。 
`)\d{7}` | 如果 `n2` 相符，則會比對七個十進位數字。
`|;\d{3}-\d{2}-\d{4}` | 如果 `n2` 不相符，則會比對三個十進位數字、一個連字號、兩個十進位數字、另一個連字號，以及四個十進位數字。 
`\b` | 比對字邊界。
 
此範例是使用編號的群組而不是具名群組的一種變化，如下所示。 它的規則運算式模式是 `\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b";
      string input = "01-9999999 020-333333 777-88-9999";
      Console.WriteLine("Matches for {0}:", pattern);
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index);
   }
}
// The example display the following output:
//       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
//          01-9999999 at position 0
//          777-88-9999 at position 22
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b"
      Dim input As String = "01-9999999 020-333333 777-88-9999"
      Console.WriteLine("Matches for {0}:", pattern)
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("   {0} at position {1}", match.Value, match.Index)
      Next   
   End Sub
End Module
' The example displays the following output:
'       Matches for \b(\d{2}-)*(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b:
'          01-9999999 at position 0
'          777-88-9999 at position 22
```

另請參閱

[規則運算式語言 - 快速參考](quick-ref.md)


