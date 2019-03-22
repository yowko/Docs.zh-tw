---
title: Null 條件運算子 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: b83435b8448b53eca63aac0519e9eed2f7dfa9f3
ms.sourcegitcommit: 344d82456f27d09a210671214a14cfd7daf1f97c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58348761"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. 和嗎？（） null 條件運算子 (Visual Basic)

測試的左運算元為 null 的值 (`Nothing`) 之前執行成員存取 (`?.`) 或索引 (`?()`) 作業; 會傳回`Nothing`如果左運算元評估為`Nothing`。 請注意，在正常情況下傳回實值類型的運算式中，null 條件運算子傳回<xref:System.Nullable%601>。

這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，尤其是遞減至資料結構。 例如: 

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

相較之下，這些運算式沒有 null 條件運算子的第一個替代程式碼是：

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Null 條件運算子會執行最少運算。  如果在條件式成員存取和索引作業鏈結中的一項作業會傳回`Nothing`，其餘的鏈結的執行會停止。  在下列範例中，`C(E)`如果不評估`A`， `B`，或`C`評估為`Nothing`。

```vb
A?.B?.C?(E);
```

Null 條件成員存取的另一個用途是要以更少的程式碼以執行緒安全的方式叫用委派。  下列範例會定義兩種類型，`NewsBroadcaster`和`NewsReceiver`。 新聞項目會傳送至由接收者`NewsBroadcaster.SendNews`委派。

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

如果在沒有項目`SendNews`引動過程清單`SendNews`委派擲回<xref:System.NullReferenceException>。 Null 條件運算子之前機器碼，類似下列確保委派引動過程清單不是`Nothing`:

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

新方法則更簡單：  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

新的方法可以保障執行緒安全，因為編譯器產生的程式碼只會評估 `SendNews` 一次，並將結果保留在暫存變數中。 由於沒有 Null 條件式委派引動過程語法 `SendNews?(String)`，因此您必須明確呼叫 `Invoke` 方法。  

## <a name="see-also"></a>另請參閱

- [運算子 (Visual Basic)](index.md)
- [Visual Basic 程式設計手冊](../../../visual-basic/programming-guide/index.md)
- [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)
