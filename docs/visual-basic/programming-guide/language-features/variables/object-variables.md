---
title: Visual Basic 中的物件變數
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649109"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic 中的物件變數
除了直接儲存的值，變數可以參考的物件。 您指派給變數的物件相同的原因，您將任何值指派給變數：  
  
-   變數的名稱通常是短也更容易記住比方法和屬性存取的物件本身所需的完整路徑。  
  
-   使用的變數來參考的物件是比重複存取透過必要的方法或屬性的物件本身更有效率。  
  
-   您可以變更為您的程式碼執行時，參考到其他物件的變數。  
  
## <a name="making-code-shorter"></a>縮短程式碼  
 您可以使用物件變數來縮短必須輸入的程式碼。 下列範例會使用的方法和屬性的完整路徑來存取<xref:System.Windows.Forms.Control>物件。  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 您可以縮短這段程式碼，並加快執行時，如果您使用控制項的物件變數。 您應該宣告物件變數，您想要為其指派的特定類別 (`Control`在此情況下)。 一旦您將物件指派給變數時，您可以將它完全相同方式將它所參考的物件。 您可以設定或擷取物件的屬性，或使用任何方法。 下列範例會使用物件變數來簡化在上述範例程式碼。  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>另請參閱  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [如何：加快存取具有限定性條件長路徑的物件](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
