---
title: 如何：加快存取具有限定性條件長路徑的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650195"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>如何：加快存取具有限定性條件長路徑的物件 (Visual Basic)
如果您經常存取的物件需要數個方法和屬性的限定性條件路徑，可以在不重複的限定性條件路徑，以加速您的程式碼。  
  
 有兩種方式，您可以避免重複的限定性條件路徑。 您可以將物件指派給變數，或您可以將它用於`With`...`End With`區塊。  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>若要加快存取大量限定的物件將它指派給變數  
  
1.  宣告您經常存取的物件類型的變數。 指定限定性條件路徑，初始化部分宣告中。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  您可以使用變數來存取物件的成員。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>若要加快存取大量限定的物件使用 With...End With 區塊  
  
1.  限定性條件路徑放入`With`陳述式。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  存取內部物件的成員`With`之前封鎖`End With`陳述式。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
