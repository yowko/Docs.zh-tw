---
title: 在委派中使用變異數（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169073"
---
# <a name="using-variance-in-delegates-visual-basic"></a>在委派中使用變異數（Visual Basic）

當您將方法指派給委派時，「共變數」和「反變數」可讓您彈性地比對委派類型和方法簽章。 共變數允許某個方法的傳回型別與定義於委派中的傳回型別相比，其衍生程度較大。 反變數允許某個方法的參數類型與委派類型中的參數類型相比，其衍生程度較小。

## <a name="example-1-covariance"></a>範例 1：共變數

### <a name="description"></a>描述

此範例示範如何搭配其傳回型別衍生自委派簽章中傳回型別的方法使用委派。 `DogsHandler` 所傳回的資料類型是 `Dogs` 類型，該類型衍生自定義於委派中的 `Mammals` 類型。

### <a name="code"></a>程式碼

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>範例 2：反變數

### <a name="description"></a>描述

此範例示範如何搭配其參數類型為委派簽章參數類型的基底類型方法來使用委派。 透過反變數，您可以使用一個事件處理常式，而不是不同的處理常式。 下列範例會使用兩個委派：

- <xref:System.Windows.Forms.KeyEventHandler> 委派會定義 [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) 事件的簽章。 其簽章為：

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <xref:System.Windows.Forms.MouseEventHandler> 委派會定義 [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) 事件的簽章。 其簽章為：

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

此範例以 <xref:System.EventArgs> 參數定義事件處理常式，然後使用它來處理 `Button.KeyDown` 和 `Button.MouseClick` 事件。 由於 <xref:System.EventArgs> 同時是 <xref:System.Windows.Forms.KeyEventArgs> 和 <xref:System.Windows.Forms.MouseEventArgs> 的基底類型，因此可以這麼做。

### <a name="code"></a>程式碼

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>另請參閱

- [委派中的變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [針對 Func 與 Action 泛型委派使用變異數 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
