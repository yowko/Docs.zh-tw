---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 0a7424e5dbfadd78c4071ba5b76086b7f6c9b94a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585849"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>宣告為結構成員的陣列無法以初始大小宣告
陣列結構中的宣告的初始大小。 您無法初始化任何結構項目，並宣告陣列大小是一種形式的初始化。  
  
 **錯誤 ID:** BC31043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  定義在結構中的陣列，為動態 （沒有初始大小）。  
  
2.  如果您需要特定大小的陣列，您可以重新維度化與動態陣列[ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)執行您的程式碼時。 下列範例將說明這點。  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [如何：宣告結構](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
