---
title: 類型參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 14e6094b0cc129eba86db1808c0f0575955f5e75
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161188"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a>BC32098：類型參數不能當做限定詞使用

程式設計專案會以包含型別參數的限定性字串限定。

型別參數代表在建立泛型型別時所要提供的型別需求。 它不代表特定的定義型別。 限定性字串只能包含編譯時期所定義的元素。

下列程式碼可能會產生此錯誤：

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 **錯誤識別碼：** BC32098

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 請從限定性字串中移除類型參數，或將它取代為已定義的類型。

2. 如果您需要使用結構化的型別來找出要限定的程式設計項目，您必須使用其他程式邏輯。

## <a name="see-also"></a>另請參閱

- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Type List](../statements/type-list.md)
