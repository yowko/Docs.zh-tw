---
title: "規則運算式範例：變更日期格式"
description: "規則運算式範例：變更日期格式"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3e196697-981c-4c1d-93dd-c3b236ef36dd
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8b333db10f7dc9d0e4701899b7af46f45f60aa8e

---

# <a name="regular-expression-example-changing-date-formats"></a>規則運算式範例：變更日期格式

下列程式碼範例會使用 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String)) 方法將 *mm/dd/yy* 格式的日期取代為 *dd-mm-yy* 格式的日期。

## <a name="example"></a>範例

```csharp
static string MDYToDMY(string input) 
{
   try {
      return Regex.Replace(input, 
            "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
            "${day}-${month}-${year}", RegexOptions.None,
            TimeSpan.FromMilliseconds(150));
   }         
   catch (RegexMatchTimeoutException) {
      return input;
   }
}
```

```vb
Function MDYToDMY(input As String) As String
   Try
      Return Regex.Replace(input, _
             "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
             "${day}-${month}-${year}", RegexOptions.None,
             TimeSpan.FromMilliseconds(150))
    Catch e As RegexMatchTimeoutException
       Return input
    End Try         
End Function
```

以下程式碼將說明如何在應用程式中呼叫 `MDYToDMY` 方法。 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class Class1
{
   public static void Main()
   {
      string dateString = DateTime.Today.ToString("d", 
                                        DateTimeFormatInfo.InvariantInfo);
      string resultString = MDYToDMY(dateString);
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString);
   }

   static string MDYToDMY(string input) 
   {
      try {
         return Regex.Replace(input, 
               "\\b(?<month>\\d{1,2})/(?<day>\\d{1,2})/(?<year>\\d{2,4})\\b",
               "${day}-${month}-${year}", RegexOptions.None,
               TimeSpan.FromMilliseconds(150));
      }         
      catch (RegexMatchTimeoutException) {
         return input;
      }
   }

}
// The example displays the following output to the console if run on 8/21/2007:
//      Converted 08/21/2007 to 21-08-2007.
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Module DateFormatReplacement
   Public Sub Main()
      Dim dateString As String = Date.Today.ToString("d", _
                                           DateTimeFormatInfo.InvariantInfo)
      Dim resultString As String = MDYToDMY(dateString)
      Console.WriteLine("Converted {0} to {1}.", dateString, resultString)
   End Sub

    Function MDYToDMY(input As String) As String
       Try
          Return Regex.Replace(input, _
                 "\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b", _
                 "${day}-${month}-${year}", RegexOptions.None,
                 TimeSpan.FromMilliseconds(150))
        Catch e As RegexMatchTimeoutException
           Return input
        End Try         
    End Function
End Module
' The example displays the following output to the console if run on 8/21/2007:
'      Converted 08/21/2007 to 21-08-2007.
```

## <a name="comments"></a>註解

規則運算式模式 `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`\b` | 開始字緣比對。
`(?<month>\d{1,2})` | 比對一個或兩個十進位數字。 這是 `month` 擷取群組。
`/` | 比對斜線符號。
`(?<day>\d{1,2})` | 比對一個或兩個十進位數字。 這是 `day` 擷取群組。
`/` | 比對斜線符號。
`(?<year>\d{2,4})` | 比對兩個到四個十進位數字。 這是 `year` 擷取群組。
`\b` | 結束字緣比對。
 
模式 `${day}-${month}-${year}` 會定義取代字串，如下表所示。

模式 | 描述
------- | ----------- 
`$(day)` | 加入 `day` 擷取群組所擷取的字串。
`-` | 加入連字號。
`$(month)` | 加入 `month` 擷取群組所擷取的字串。
`-` | 加入連字號。
`$(year)` | 加入 `year` 擷取群組所擷取的字串。
 
## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)

[規則運算式範例](regex-examples.md)



<!--HONumber=Nov16_HO1-->


