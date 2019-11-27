---
title: 如何：參考物件目前的執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346887"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>如何：參考物件目前的執行個體 (Visual Basic)
目前物件的*實例*是程式碼執行所在的實例。  
  
 您可以使用 `Me` 關鍵字來參考目前的實例。  
  
### <a name="to-refer-to-the-current-instance"></a>若要參考目前的實例  
  
- 使用 `Me` 關鍵字，您通常會使用物件變數的名稱。  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     雖然 `Me` 的行為類似物件變數，但是您不能宣告它或將任何專案指派給它。 `Me` 一律會參考目前的實例。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
