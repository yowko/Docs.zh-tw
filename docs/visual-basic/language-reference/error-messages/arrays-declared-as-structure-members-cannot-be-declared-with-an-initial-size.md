---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701243"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>宣告為結構成員的陣列無法以初始大小宣告
結構中的陣列是以初始大小來宣告。 您無法初始化任何結構專案，而且宣告陣列大小是一種初始化形式。  
  
 **錯誤識別碼：** BC31043  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 在您的結構中將陣列定義為動態（沒有初始大小）。  
  
2. 如果您需要特定大小的陣列，當您的程式碼執行時，可以使用[ReDim 語句](../../../visual-basic/language-reference/statements/redim-statement.md)來為動態陣列進行維數。 下列範例將說明這點。  
  
    ```vb  
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

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [如何：宣告結構](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
