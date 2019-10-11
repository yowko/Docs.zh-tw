---
title: 宣告為結構成員的陣列無法以初始大小宣告
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250145"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>宣告為結構成員的陣列無法以初始大小宣告

結構中的陣列是以初始大小來宣告。 您無法初始化任何結構專案，而且宣告陣列大小是一種初始化形式。

**錯誤識別碼：** BC31043

## <a name="example"></a>範例

下列範例會產生 BC31043：

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 在您的結構中將陣列定義為動態（沒有初始大小）。

2. 如果您需要特定大小的陣列，當您的程式碼執行時，可以使用[ReDim 語句](../statements/redim-statement.md)來為動態陣列進行維數。 下面這個範例可說明這點：
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a>另請參閱

- [陣列](../../programming-guide/language-features/arrays/index.md)
- [如何：宣告結構](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
