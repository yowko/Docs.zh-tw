---
title: 物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410331"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic 中的物件變數

除了直接儲存值之外，變數也可以參考物件。 將物件指派給變數的原因，是因為您將任何值指派給變數：

- 變數名稱通常比存取物件本身所需之方法和屬性的完整路徑更短且更容易記憶。

- 使用參考物件的變數會比透過必要的方法或屬性重複存取物件本身更有效率。

- 當您的程式碼正在執行時，您可以變更變數來參考其他物件。

## <a name="making-code-shorter"></a>使程式碼更短

您可以使用物件變數來縮短您必須輸入的程式碼。 下列範例會使用方法和屬性的完整路徑來存取 <xref:System.Windows.Forms.Control> 物件。

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

如果您使用控制項的物件變數，可以縮短此程式碼並加快執行速度。 您應該使用您想要指派給它的特定類別（ `Control` 在此案例中為）來宣告物件變數。 將物件指派給變數之後，您就可以將它視為您處理它所參考的物件完全相同。 您可以設定或取出物件的屬性，或使用其任何方法。 下列範例會使用物件變數來簡化上述範例中的程式碼。

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>另請參閱

- [變數宣告](variable-declaration.md)
- [如何：加快存取具有限定性條件長路徑的物件](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [物件變數宣告](object-variable-declaration.md)
- [物件變數指派](object-variable-assignment.md)
- [物件變數值](object-variable-values.md)
