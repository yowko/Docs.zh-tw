---
title: 作法：加速存取具有完整限定性路徑的物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: a8e50a2ed04037b48091321dc0c9ac2ea1db35f4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631093"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>HOW TO：加速存取具有完整限定性路徑的物件 (Visual Basic)

如果您經常存取需要數個方法和屬性之限定性路徑的物件, 您可以藉由不重複限定性路徑來加速程式碼。

有兩種方式可以避免重複限定性路徑。 您可以將物件指派給變數, 也可以將它`With`用於 ...`End With`封鎖。

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>藉由將非常限定的物件指派給變數來加速其存取

1. 宣告您經常存取之物件類型的變數。 在宣告的初始化部分中指定限定性路徑。

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. 使用變數來存取物件的成員。

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>若要使用 [...] 來加速存取高度限定的物件結尾為 block

1. 將限定性路徑放在`With`語句中。

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. 在`With`區塊內, 于`End With`語句之前存取物件的成員。

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
