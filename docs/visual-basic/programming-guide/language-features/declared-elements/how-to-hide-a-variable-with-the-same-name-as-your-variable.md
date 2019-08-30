---
title: 作法：隱藏與您的變數名稱相同的變數 (Visual Basic)
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
ms.openlocfilehash: 487e0a15ba6b52f92ab39fe0bae4ab15fa92707f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629995"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>作法：隱藏與您的變數名稱相同的變數 (Visual Basic)

您可以藉由將變數*遮蔽*來加以隱藏, 也就是使用相同名稱的變數重新加以定義。 您可以透過兩種方式遮蔽要隱藏的變數:

- **透過範圍遮蔽。** 您可以透過範圍來遮蔽它, 方法是在包含您要隱藏之變數的區域的子領域內重新宣告它。

- **透過繼承進行遮蔽。** 如果您要隱藏的變數是在類別層級定義的, 您可以在衍生類別中使用[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)關鍵字重新宣告, 藉以透過繼承來遮蔽它。

## <a name="two-ways-to-hide-a-variable"></a>隱藏變數的兩種方式

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>藉由在範圍內遮蔽來隱藏變數

1. 判斷定義您想要隱藏之變數的區域, 並決定要在其中使用變數重新定義的子領域。

    |變數的區域|用於重新定義它的允許子領域|
    |-----------------------|-------------------------------------------|
    |Module|模組中的類別|
    |類別|類別內的子類別<br /><br /> 類別中的程式|

    您不能在該程式內的區塊中重新定義過程變數, 例如在`If`...`End If` 結構`For`或迴圈。

2. 建立子領域 (如果尚未存在的話)。

3. 在子領域內, 撰寫用來宣告遮蔽變數的[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)。

    當子領域內的程式碼參考變數名稱時, 編譯器會解析遮蔽變數的參考。

    下列範例說明如何透過範圍進行遮蔽, 以及略過遮蔽的參考。

    ```vb
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

    上述範例會在模組層`num`級和程式層級宣告變數 (在程式中`show`)。 區域變數`num`會遮蔽`num` 中`show`的模組層級變數, 所以區域變數會設定為2。 不過, 程式中沒有可遮蔽`num`的`useModuleLevelNum`本機變數。 因此, `useModuleLevelNum`會將模組層級變數的值設定為1。

    `num`內部`MsgBox` 的呼叫會透過以模組名稱限定來略過遮蔽的機制。`show` 因此, 它會顯示模組層級變數, 而不是本機變數。

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>藉由透過繼承來遮蔽變數以加以隱藏

1. 請確定您要隱藏的變數是在類別中宣告, 而在類別層級 (在任何程式之外) 宣告。 否則, 您就無法透過繼承來遮蔽它。

2. 定義衍生引數類別的類別 (如果尚未存在的話)。

3. 在衍生類別中, 撰寫宣告`Dim`變數的語句。 在宣告中包含[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)關鍵字。

    當衍生類別中的程式碼參考變數名稱時, 編譯器會解析變數的參考。

    下列範例說明透過繼承的遮蔽。 它會建立兩個參考, 一個存取遮蔽變數, 另一個則會略過遮蔽。

    ```vb
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

    上述範例會在基類中`shadowString`宣告變數, 並將其遮蔽在衍生類別中。 當名稱`shadowString`未限定時, 衍生類別中的程式會顯示字串的遮蔽版本。`showStrings` 然後, 它會在`shadowString` `MyBase`以關鍵字限定時顯示陰影版本。

## <a name="robust-programming"></a>穩固程式設計

遮蔽導入了一個以上具有相同名稱的變數版本。 當程式碼語句參考變數名稱時, 編譯器解析參考的目標版本取決於程式碼語句的位置, 以及符合資格的字串是否存在等因素。 這可能會增加參考非預期版本的陰影變數的風險。 您可以藉由完整限定遮蔽變數的所有參考, 來降低風險。

## <a name="see-also"></a>另請參閱

- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic 中的陰影](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [遮蔽和覆寫的差異](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [如何：隱藏繼承的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [如何：存取衍生類別所隱藏的變數](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
