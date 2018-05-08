---
title: 如何：隱藏與您的變數名稱相同的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: a7ebc4eb44592800decd5ef943750f0cd845afb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>如何：隱藏與您的變數名稱相同的變數 (Visual Basic)
您可以隱藏變數*遮蔽*它，也就是來重新定義具有相同名稱的變數。 您可以遮蔽的變數，您想要隱藏兩種方式：  
  
-   **透過範圍遮蔽。** 您可以透過範圍遮蔽它的宣告子區域的區域包含您想要隱藏的變數內。  
  
-   **透過繼承遮蔽。** 如果您想要隱藏的變數定義在類別層級，您可以透過繼承來遮蔽所遮蔽與[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)衍生類別中的關鍵字。  
  
## <a name="two-ways-to-hide-a-variable"></a>若要隱藏變數的兩種方式  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>若要隱藏變數來透過範圍遮蔽  
  
1.  判斷定義您想要隱藏，該的變數的區域，並判斷要重新定義它，以您的變數子區域。  
  
    |變數的區域|重新定義它的可允許子地區|  
    |-----------------------|-------------------------------------------|  
    |Module|在模組中的類別|  
    |類別|類別內的子類別<br /><br /> 類別內的程序|  
  
     您無法重新定義程序變數的區塊中的程序，例如在`If`...`End If`建構或`For`迴圈。  
  
2.  如果不存在，請予以建立。  
  
3.  在子區域中，撰寫[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告遮蔽的變數。  
  
     當子地區內的程式碼參考變數的名稱時，則編譯器會解析遮蔽的變數的參考。  
  
     下列範例示範如何透過範圍，以及略過遮蔽的參考遮蔽。  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     上述範例中宣告變數`num`在模組層級和程序層級 (在程序`show`)。 本機變數`num`遮蔽模組層級變數`num`內`show`，因此本機變數設定為 2。 不過，沒有任何區域變數至陰影`num`中`useModuleLevelNum`程序。 因此，`useModuleLevelNum`模組層級變數的值設定為 1。  
  
     `MsgBox`內呼叫`show`略過遮蔽的機制，來限定`num`模組名稱。 因此，它會顯示模組層級變數，而不是本機變數。  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>若要隱藏變數來透過繼承遮蔽  
  
1.  請務必在類別中，並在類別層級 （以外的任何程序） 中宣告了您想要隱藏的變數。 否則您無法透過繼承遮蔽它。  
  
2.  定義衍生自變數的類別，如果不存在的類別。  
  
3.  在衍生類別中，撰寫`Dim`陳述式來宣告變數。 包含[陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)宣告中的關鍵字。  
  
     當在衍生類別中的程式碼參考變數的名稱時，則編譯器會解析您變數的參考。  
  
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
 遮蔽導入了一個以上的版本具有相同名稱的變數。 當程式碼陳述式參考變數的名稱時，則編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定字串的目前狀態。 這會增加到錯誤版本的遮蔽的變數參考的風險。 您可以降低風險來完整限定所有遮蔽的變數參考。  
  
## <a name="see-also"></a>另請參閱  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [遮蔽和覆寫的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
