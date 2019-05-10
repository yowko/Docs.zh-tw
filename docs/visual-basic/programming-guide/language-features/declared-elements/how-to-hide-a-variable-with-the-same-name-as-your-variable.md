---
title: HOW TO：隱藏與您的變數 (Visual Basic) 同名的變數
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
ms.openlocfilehash: 3230dac924e9c22231494bfc8b81cd74e356bca3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610321"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>HOW TO：隱藏與您的變數 (Visual Basic) 同名的變數
您可以隱藏變數*遮蔽*它，也就是藉由重新定義它，以相同名稱的變數。 您可以遮蔽您想要隱藏有兩種的變數：  
  
- **透過範圍遮蔽。** 您可以透過範圍遮蔽它的宣告包含您想要隱藏的變數的區域的子區域內。  
  
- **透過繼承遮蔽。** 如果您想要隱藏的變數定義在類別層級，您可以透過繼承來遮蔽藉由宣告它與[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)衍生類別中的關鍵字。  
  
## <a name="two-ways-to-hide-a-variable"></a>若要隱藏變數的兩種方式  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>若要隱藏的變數，來透過範圍遮蔽  
  
1. 判斷區域定義您想要隱藏此項目，該的變數，並判斷要在其中以您的變數重新定義它的子區域。  
  
    |變數的區域|重新定義它的可允許子區域|  
    |-----------------------|-------------------------------------------|  
    |Module|在模組中的類別|  
    |類別|在類別內的子類別<br /><br /> 在類別中的程序|  
  
     您無法重新定義程序變數的區塊中的程序中，例如在`If`...`End If`建構或`For`迴圈。  
  
2. 如果不存在，請予以建立。  
  
3. 在子區域中，撰寫[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)遮蔽變數宣告。  
  
     當子區域內的程式碼會參考變數的名稱時，編譯器會解析遮蔽變數的參考。  
  
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
  
     上述範例中宣告變數`num`在模組層級和程序層級 (在程序`show`)。 區域變數`num`遮蔽模組層級變數`num`內`show`，因此本機變數設為 2。 不過，沒有任何本機變數，以遮蔽`num`在`useModuleLevelNum`程序。 因此，`useModuleLevelNum`模組層級變數的值設定為 1。  
  
     `MsgBox`呼叫內`show`略過所限定的遮蔽的機制`num`的模組名稱。 因此，它會顯示模組層級變數，而不是本機變數。  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>若要隱藏的變數，來透過繼承遮蔽  
  
1. 請務必在您想要隱藏的變數宣告在類別中，並在類別層級 （以外的任何程序）。 否則您無法透過繼承遮蔽它。  
  
2. 定義衍生自變數的類別，如果不存在的類別。  
  
3. 在衍生類別中，撰寫`Dim`陳述式來宣告變數。 包含[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣告中的關鍵字。  
  
     當在衍生類別中的程式碼會參考變數的名稱時，編譯器會解析您變數的參考。  
  
     下列範例示範如何透過繼承遮蔽。 它可讓兩個參考，其中一個存取遮蔽的變數，略過遮蔽的其中一個。  
  
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
  
     上述範例中宣告變數`shadowString`基底類別中與遮蔽的衍生類別中。 此程序`showStrings`衍生類別中會顯示字串的遮蔽版本時名稱`shadowString`是非限定的。 然後它會顯示的遮蔽的版本時`shadowString`是以限定`MyBase`關鍵字。  
  
## <a name="robust-programming"></a>穩固程式設計  
 遮蔽導入了一個以上的版本，具有相同名稱的變數。 當程式碼陳述式參考的變數名稱時，編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定的字串存在。 這樣可以增加參考到非預期的版本的受遮蔽變數的風險。 您可以降低風險，來完整限定遮蔽變數的所有參考。  
  
## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [遮蔽和覆寫的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
