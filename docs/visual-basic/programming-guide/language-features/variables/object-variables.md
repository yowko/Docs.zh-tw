---
title: Visual Basic 中的物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352967"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic 中的物件變數

除了直接將值儲存，變數可以參考的物件。 您指派給變數物件的任何值指派給變數相同的原因：

- 變數的名稱通常是較短且更容易記住比方法和屬性來存取物件本身所需的完整路徑。

- 使用的變數來參考的物件會比重複地透過必要的方法或屬性存取物件本身更有效率。

- 您可以變更變數，以執行您的程式碼時，對其他物件參考。

## <a name="making-code-shorter"></a>縮短程式碼

您可以使用物件變數來縮短必須輸入的程式碼。 下列範例會使用的方法和屬性的完整路徑來存取<xref:System.Windows.Forms.Control>物件。

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

您可以縮短這段程式碼，並加速執行，如果您使用控制項的物件變數。 您應該宣告物件變數，您想要為其指派的特定類別 (`Control`在此情況下)。 一旦您將物件指派給變數時，您可以將它完全相同，您將它所參考的物件。 您可以設定或擷取物件的屬性，或使用它的任何方法。 下列範例會使用物件變數，以簡化在上述範例中的程式碼。

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>另請參閱

- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [如何：加快存取具有限定性條件長路徑的物件](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
