---
title: 如何：存取衍生類別所隱藏的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 8dd59dff5b8123331237db905432bbb4e94d62ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648043"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>如何：存取衍生類別所隱藏的變數 (Visual Basic)
當在衍生類別中的程式碼存取的變數時，編譯器通常會將參考解析最接近的可存取版本，也就是可存取的版本之後的最少衍生步驟回溯存取的類別。 如果變數在衍生類別中定義，程式碼通常會存取該定義。  
  
 如果衍生的類別變數會遮蔽基底類別中的變數，它會隱藏基底類別版本。 不過，您可以存取的基底類別變數來限定它與`MyBase`關鍵字。  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>若要存取衍生類別所隱藏的基底類別變數  
  
-   在運算式或指派陳述式中，變數名稱前加`MyBase`關鍵字和句號 (`.`)。  
  
     編譯器會解析變數的基底類別版本的參考。  
  
     下列範例示範如何透過繼承遮蔽。 它可讓兩個參考會存取遮蔽的變數，一個略過遮蔽。  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     上述範例中宣告變數`shadowString`基底類別及陰影衍生類別中。 此程序`showStrings`衍生類別中會顯示遮蔽版本的字串時名稱`shadowString`不合格。 接著會顯示加上陰影的版本時`shadowString`是以限定`MyBase`關鍵字。  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要降低到錯誤版本的遮蔽的變數參考的風險，您可以完整限定遮蔽的變數的所有參考。 遮蔽導入了一個以上的版本具有相同名稱的變數。 當程式碼陳述式參考變數的名稱時，則編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定字串的目前狀態。 這會增加參考到變數的版本錯誤的風險。  
  
## <a name="see-also"></a>另請參閱  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [遮蔽和覆寫的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [如何：隱藏與您的變數名稱相同的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
