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
ms.openlocfilehash: 64d21fe4aaf6fd34bf880373a7ab3067fb67820e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077055"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>如何：參考物件目前的執行個體 (Visual Basic)

目前的物件 *實例* 是程式碼目前執行所在的實例。  
  
 您可以使用 `Me` 關鍵字來參考目前的實例。  
  
### <a name="to-refer-to-the-current-instance"></a>參考目前的實例  
  
- 使用 `Me` 您通常會使用物件變數名稱的關鍵字。  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     雖然 `Me` 行為類似物件變數，但您無法將其宣告或指派給它。 `Me` 一律參考目前的實例。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](object-variables.md)
- [物件變數指派](object-variable-assignment.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
