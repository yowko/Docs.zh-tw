---
title: "如何：從 URL 擷取通訊協定和連接埠號碼"
description: "如何從 URL 擷取通訊協定和連接埠號碼"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d2462fb4-6d61-44ab-8466-73f1f06c3058
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 72e0c9401406dcac4eb693b056b88a531f2a0748

---

# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>如何：從 URL 擷取通訊協定和連接埠號碼

下列範例會從 URL 擷取通訊協定和連接埠號碼。 

## <a name="example"></a>範例

此範例會使用 [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) 方法來傳回通訊協定和連接埠號碼 (中間以冒號隔開)。 

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string url = "http://www.contoso.com:8080/letters/readme";

      Regex r = new Regex(@"^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                          RegexOptions.None, TimeSpan.FromMilliseconds(150));
      Match m = r.Match(url);
      if (m.Success)
         Console.WriteLine(r.Match(url).Result("${proto}${port}")); 
   }
}
// The example displays the following output:
//       http:8080
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim url As String = "http://www.contoso.com:8080/letters/readme.html" 
      Dim r As New Regex("^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/",
                         RegexOptions.None, TimeSpan.FromMilliseconds(150))

      Dim m As Match = r.Match(url)
      If m.Success Then
         Console.WriteLine(r.Match(url).Result("${proto}${port}"))
      End If   
   End Sub
End Module
' The example displays the following output:
'       http:8080
```

規則運算式模式 `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` 的解譯方式如下表所示。

模式 | 描述
------- | ----------- 
`^` | 在字串開頭開始比對。
`(?<proto>\w+)` | 比對一個或多個文字字元。 將這個群組命名為 proto。
`://` | 比對冒號加兩個斜線符號。
`[^/]+?` | 比對一個或多個 (但越少越好) 出現的任何字元，但不包括斜線符號。
`(?<port>:\d+)?` | 比對零個或一個出現的冒號外加一個或多個數字字元。 將這個群組命名為 port。
`/` | 比對斜線符號。
 
[Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) 方法會展開 `${proto}${port}` 取代序列，以將規則運算式模式中所擷取之兩個具名群組的值串連。 另一種方便的做法是將 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性所傳回集合物件中擷取的字串明確串連。

此範例會使用 [Match.Result](xref:System.Text.RegularExpressions.Match.Result(System.String)) 方法和兩個替代項目 `${proto}` 和 `${port}`，以將擷取群組加入輸出字串。 您可以改為從相符項目的 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中擷取該群組，如下列程式碼所示。

```csharp
Console.WriteLine(m.Groups["proto"].Value + m.Groups["port"].Value); 
```

```vb
Console.WriteLine(m.Groups("proto").Value + m.Groups("port").Value)
```

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)

[規則運算式範例](regex-examples.md)



<!--HONumber=Nov16_HO3-->


