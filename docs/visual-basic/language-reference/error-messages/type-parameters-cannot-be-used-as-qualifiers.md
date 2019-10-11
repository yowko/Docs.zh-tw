---
title: 類型參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 3ff4b189539bf119351a94dabadd596c336ac723
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250333"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>類型參數不能當做限定詞使用

程式設計專案是以包含型別參數的限定性字串來限定。

型別參數代表在結構化泛型型別時要提供的型別需求。 它不代表特定的已定義型別。 限定性字串必須僅包含在編譯時期定義的元素。

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
  
2. 如果您需要使用已結構化的類型來尋找限定的程式設計項目，則必須使用其他程式邏輯。  
  
## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [類型清單](../statements/type-list.md)
