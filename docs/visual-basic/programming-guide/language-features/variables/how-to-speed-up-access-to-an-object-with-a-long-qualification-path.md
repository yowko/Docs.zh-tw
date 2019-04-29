---
title: HOW TO：加快存取具有限定性條件長路徑 (Visual Basic) 的物件
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769040"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>HOW TO：加快存取具有限定性條件長路徑 (Visual Basic) 的物件
如果您經常存取的物件需要的一些方法和屬性的限定性條件路徑，您可以加快您的程式碼不重複的限定性條件路徑。  
  
 有兩種方式，您可以避免重複的限定性條件路徑。 您可以將物件指派給變數，或將它使用於`With`...`End With`區塊。  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>若要加快存取大量限定的物件將它指派給變數  
  
1. 宣告您經常存取的物件類型的變數。 指定限定性條件路徑，在宣告中初始化的一部分。  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. 您可以使用變數來存取物件的成員。  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>若要加快存取大量限定的物件使用 With...With...end With 區塊  
  
1. 限定性條件路徑放入`With`陳述式。  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. 存取內部物件的成員`With`之前封鎖`End With`陳述式。  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
