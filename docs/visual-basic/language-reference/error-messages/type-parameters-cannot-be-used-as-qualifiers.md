---
title: 型別參數不能當做限定詞使用
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>型別參數不能當做限定詞使用
程式設計項目是使用限定性條件字串，其中包含的型別參數人選。  
  
 型別參數代表的需求，要建構的泛型型別時提供的類型。 它不代表已定義的特定類型。 限定性條件字串必須包含在編譯時期所定義的項目。  
  
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
  
1.  從限定性條件字串中，移除型別參數，或取代已定義的類型。  
  
2.  如果您需要找出在合格的程式設計項目時，用於建構的類型，您必須使用其他程式邏輯。  
  
## <a name="see-also"></a>另請參閱  
 [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
