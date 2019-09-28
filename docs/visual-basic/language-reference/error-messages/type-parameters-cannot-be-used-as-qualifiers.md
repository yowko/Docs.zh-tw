---
title: 類型參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592141"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>類型參數不能當做限定詞使用
程式設計專案是以包含型別參數的限定性字串來限定。  
  
 型別參數代表在結構化泛型型別時要提供的型別需求。 它不代表特定的已定義型別。 限定性字串必須僅包含在編譯時期定義的元素。  
  
 下列陳述式可能會產生此錯誤。  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **錯誤識別碼：** BC32098  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請從限定性字串中移除類型參數，或將它取代為已定義的類型。  
  
2. 如果您需要使用已結構化的類型來尋找限定的程式設計項目，則必須使用其他程式邏輯。  
  
## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
