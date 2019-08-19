---
title: 物件變數指派 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 59dea45511ba8d7d10c95cf17e47981124c532e4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631050"
---
# <a name="object-variable-assignment-visual-basic"></a>物件變數指派 (Visual Basic)

您可以使用一般指派語句, 將物件指派給物件變數。 您可以指派物件運算式或不使用[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字, 如下列範例所示。

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

`Nothing`表示目前沒有任何物件指派給該變數。

## <a name="initialization"></a>初始化

當您的程式碼開始執行時, 您的物件`Nothing`變數會初始化為。 其宣告包含初始化的使用者會重新初始化為您在宣告語句執行時所指定的值。

您可以使用[New](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字, 在宣告中包含初始化。 下列宣告語句會宣告物件變數`testUri` , `ver`並將特定物件指派給它們。 每個都會使用適當類別的其中一個多載的函式來初始化物件。

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a>解除

設定物件變數以`Nothing`中止變數與任何特定物件的關聯。 這可防止您藉由變更變數而不小心變更物件。 它也可讓您測試物件變數是否指向有效的物件, 如下列範例所示。

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

如果您的變數所參考的物件位於另一個應用程式中, 則此測試無法判斷該應用程式是否已終止, 或只使物件失效。

值為的`Nothing`物件變數也稱為*null 參考*。

## <a name="current-instance"></a>目前的實例

目前物件的實例就是程式碼執行所在的*實例*。 由於所有程式碼都是在程式中執行, 因此目前的實例就是叫用此程式的其中一個。

`Me`關鍵字會作為參考目前實例的物件變數。 如果程式不是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的, 它可以使用`Me`關鍵字來取得目前實例的指標。 共用程式無法與類別的特定實例建立關聯。

使用`Me`特別適合用來將目前的實例傳遞至另一個模組中的程式。 例如, 假設您有多個 XML 檔, 而且想要在其中新增一些標準文字。 下列範例會定義執行這項操作的程式。

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

然後, 每個 XML 檔物件都可以呼叫程式, 並將其目前的實例當做引數傳遞。 下列範例為其示範。

```vb
addStandardText(Me)
```

## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：在 Visual Basic 中, 宣告物件變數並指派物件給它](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：讓物件變數不參考任何實例](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
