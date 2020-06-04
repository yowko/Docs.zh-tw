---
title: Null 條件運算子
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401468"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. 和?（） null 條件運算子（Visual Basic）

`Nothing`在執行成員存取（）或索引（）作業之前，先測試左邊運算元的值是否為 null （）， `?.` `?()` `Nothing` 如果左運算元評估為， `Nothing` 則傳回。 請注意，在通常會傳回實數值型別的運算式中，null 條件運算子會傳回 <xref:System.Nullable%601> 。

這些運算子可協助您撰寫較少的程式碼來處理 null 檢查，特別是當遞減至資料結構時。 例如：

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

為了進行比較，這些運算式中第一個不含 null 條件運算子的替代程式碼為：

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

有時候，您需要在可能是 null 的物件上採取動作，這是根據該物件上的 Boolean 成員值（如 `IsAllowedFreeShipping` 下列範例中的布林屬性）：

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

您可以使用 null 條件運算子來縮短您的程式碼，並避免手動檢查 null，如下所示：

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Null 條件運算子會執行最少運算。  如果條件式成員存取和索引作業鏈中的一項操作傳回，則會 `Nothing` 停止其餘的鏈執行。  在下列範例中， `C(E)` 如果 `A` 、 `B` 或 `C` 評估為，則不會評估 `Nothing` 。

```vb
A?.B?.C?(E)
```

Null 條件式成員存取的另一個用法是以更少的程式碼，以安全線程的方式叫用委派。  下列範例會定義兩個類型： `NewsBroadcaster` 和 `NewsReceiver` 。 由委派將新聞專案傳送給接收者 `NewsBroadcaster.SendNews` 。

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

如果調用清單中沒有任何元素，委派就會擲回 `SendNews` `SendNews` <xref:System.NullReferenceException> 。 在 null 條件運算子之前，如下所示的程式碼可確保委派調用清單不是 `Nothing` ：

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
- [Visual Basic 程式設計指南](../../programming-guide/index.md)
- [Visual Basic 語言參考](../index.md)
