---
title: 如何：控制變數的範圍 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 6e8d1178398711226b88fee7e6defd5162b91fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>如何：控制變數的範圍 (Visual Basic)
一般來說，變數是在*範圍*，或顯示整個區域宣告它的參考。 在某些情況下，變數的*存取層級*可能會影響其範圍。  
  
 如需詳細資訊，請參閱[在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## <a name="scope-at-block-or-procedure-level"></a>在區塊或程序層級的範圍  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>若要在區塊內才可見變數  
  
-   位置[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)變數之間的初始和終止宣告陳述式的區塊，例如之間`For`和`Next`陳述式的`For`迴圈。  
  
     您可以參考此變數只能在區塊內。  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>若要在程序內才可見變數  
  
-   位置`Dim`變數，程序內但是超出任何區塊陳述式 (例如`With`...`End With`區塊)。  
  
     您可以參考此變數只會從內的程序，包括任何程序中所含的區塊內。  
  
## <a name="scope-at-module-or-namespace-level"></a>在模組或命名空間層級的範圍  
 為了方便起見，單一詞彙*模組層級*同樣適用於模組、 類別和結構。 模組層級變數的存取層級會決定其範圍。 包含模組、 類別或結構的命名空間也會影響範圍。  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>若要顯示整個模組、 類別或結構變數  
  
1.  位置`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。  
  
2.  包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字`Dim`陳述式。  
  
3.  您可以參考變數，從模組、 類別或結構中的任何位置，而不是從外部。  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>若要顯示在命名空間變數  
  
1.  位置`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。  
  
2.  包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字`Dim`陳述式。  
  
3.  您可以從任何地方參考此變數包含模組、 類別或結構的命名空間內。  
  
## <a name="example"></a>範例  
 下列範例會宣告一個變數，在模組層級，並限制其可見性的模組中的程式碼。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 在上述範例中，所有的程序則是在模組中定義`demonstrateScope`可以參考`String`變數`strMsg`。 當`usePrivateVariable`呼叫程序時，便會顯示字串變數的內容`strMsg`對話方塊中。  
  
 與上述範例中，字串變數將`strMsg`可以參考其宣告的命名空間中的程式碼。  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>穩固程式設計  
 範圍愈小的變數，您的意外來取代另一個具有相同名稱的變數參考到的機會。 您也可以減少問題的參考相符。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 變數的範圍愈小，惡意程式碼不適當的機會使用它。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
