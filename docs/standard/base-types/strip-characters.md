---
title: "如何：從字串中刪除無效的字元"
description: "如何：從字串中刪除無效的字元"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f1df4967-7887-41d2-b60f-0da9be67c8fa
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 2d5b0756ab8c34cca0c4ca7c1eb73f81a7a10b70

---

# <a name="how-to-strip-invalid-characters-from-a-string"></a>如何：從字串中刪除無效的字元

下列範例會使用靜態 [Regex.Replace](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) 方法，從字串中去除無效的字元。 

## <a name="example"></a>範例

您可以使用此範例中定義的 `CleanInput` 方法，去除使用者在文字欄位中可能已輸入的有害字元。 在此情況下，`CleanInput` 會去除句點 (.)、符號 ((@),) 及連字號 (-) 以外的所有非英數字元，並傳回剩餘的字串。 不過，您可以修改規則運算式模式，讓它去除輸入字串中不應包含的任何字元。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
    static string CleanInput(string strIn)
    {
        // Replace invalid characters with empty strings.
        try {
           return Regex.Replace(strIn, @"[^\w\.@-]", "", 
                                RegexOptions.None, TimeSpan.FromSeconds(1.5)); 
        }
        // If we timeout when replacing invalid characters, 
        // we should return Empty.
        catch (RegexMatchTimeoutException) {
           return String.Empty;   
        }
    }
}
```

```vb
Imports System.Text.RegularExpressions

Module Example
    Function CleanInput(strIn As String) As String
        ' Replace invalid characters with empty strings.
        Try
           Return Regex.Replace(strIn, "[^\w\.@-]", "")
        ' If we timeout when replacing invalid characters, 
        ' we should return String.Empty.
        Catch e As RegexMatchTimeoutException
           Return String.Empty         
        End Try
    End Function
End Module
```

規則運算式模式 `[^\w\.@-]` 會比對任何非文字字元的字元、句號、@ 符號或連字號。 文字字元是指任何字母、十進位數字或底線這類標點符號連接子。 如果任何字元符合這個模式，就會將其取代為 [String.Empty](xref:System.String.Empty) (這是由取代模式所定義的字串)。 若要允許使用者輸入其他字元，可將這些字元新增至規則運算式模式中的字元類別。 例如，規則運算式模式 `[^\w\.@-\\%]` 也允許在輸入字串中使用百分比符號與反斜線。

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)

[規則運算式範例](regex-examples.md)



<!--HONumber=Nov16_HO3-->


