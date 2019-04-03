---
title: HOW TO：隱藏繼承的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: 2b052b44043deba85c8b142a2bf1a684c1159809
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842508"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>HOW TO：隱藏繼承的變數 (Visual Basic)
在衍生的類別會繼承其基底類別的所有定義。 如果您想要定義為基底類別的項目使用相同名稱的變數，您可以將它隱藏，或*陰影*，當您在衍生類別中定義您的變數時，該基底類別項目。 如果您這麼做時，衍生類別中的程式碼會存取您的變數，除非它明確會略過的遮蔽的機制。  
  
 您可能想要隱藏繼承的變數的另一個原因是要保護修訂基底類別。 基底類別可能進行的變更會改變您繼承的項目。 如果發生這種情況，`Shadows`修飾詞會強制從衍生的類別，為您的變數，而不是解析至基底類別項目參考。  
  
### <a name="to-hide-an-inherited-variable"></a>若要隱藏繼承的變數  
  
1.  請務必在您想要隱藏的變數宣告類別層級 （以外的任何程序）。 否則您不需要加以隱藏。  
  
2.  在衍生類別中，撰寫[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告您的變數。 使用相同名稱的繼承的變數。  
  
3.  包含[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣告中的關鍵字。  
  
     當在衍生類別中的程式碼會參考變數的名稱時，編譯器會解析您變數的參考。  
  
     下列範例示範如何遮蔽的繼承的變數。  
  
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
- [如何：隱藏與您的變數名稱相同的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
