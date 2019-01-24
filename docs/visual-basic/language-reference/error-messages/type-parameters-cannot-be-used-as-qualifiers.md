---
title: 型別參數不能當做限定詞使用
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 8ee0fd5822c22da090aa0abee679e2f68e0fc1d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659695"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>型別參數不能當做限定詞使用
限定性條件字串，包含型別參數被限定的程式設計項目。  
  
 型別參數表示要建構的泛型型別時提供的類型的需求。 它不代表特定的定義的類型。 限定性條件字串必須包含在編譯時期所定義的項目。  
  
 下列陳述式可能會產生此錯誤。  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **錯誤 ID:** BC32098  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  移除限定性條件字串的型別參數，或取代已定義的類型。  
  
2.  如果您需要找出所限定的程式設計項目時，用以建構的類型，您必須使用其他程式邏輯。  
  
## <a name="see-also"></a>另請參閱
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
