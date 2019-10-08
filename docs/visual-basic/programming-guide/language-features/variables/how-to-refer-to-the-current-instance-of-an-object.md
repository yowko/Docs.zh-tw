---
title: HOW TO：參考物件的目前實例（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005663"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>HOW TO：參考物件的目前實例（Visual Basic）
目前物件的*實例*是程式碼執行所在的實例。  
  
 您可以使用 `Me` 關鍵字來參考目前的實例。  
  
### <a name="to-refer-to-the-current-instance"></a>若要參考目前的實例  
  
- 使用 `Me` 關鍵字，通常會使用物件變數的名稱。  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     雖然 `Me` 的行為就像物件變數一樣，但您不能宣告它或將任何專案指派給它。 `Me` 一律是指目前的實例。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
