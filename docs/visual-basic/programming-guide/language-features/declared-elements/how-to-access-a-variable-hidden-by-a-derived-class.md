---
title: 如何：存取衍生類別所隱藏的變數
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392853"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>如何：存取衍生類別所隱藏的變數 (Visual Basic)

當衍生類別中的程式碼存取變數時，編譯器通常會將參考解析成最接近的可存取版本，也就是可存取的版本，最少的 derivational 步驟是從存取類別回溯。 如果變數是在衍生類別中定義，則程式碼通常會存取該定義。

如果衍生類別變數遮蔽基類中的變數，則會隱藏基類版本。 不過，您可以使用關鍵字來限定基類變數來存取它 `MyBase` 。

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>存取衍生類別所隱藏的基類變數

- 在運算式或指派語句中，在變數名稱前面加上 `MyBase` 關鍵字和句點（ `.` ）。

    編譯器會解析變數的基底類別版本參考。

    下列範例說明透過繼承的遮蔽。 它會建立兩個參考，一個存取遮蔽變數，另一個則會略過遮蔽。

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

    上述範例 `shadowString` 會在基類中宣告變數，並將其遮蔽在衍生類別中。 `showStrings`當名稱未限定時，衍生類別中的程式會顯示字串的遮蔽版本 `shadowString` 。 然後，它 `shadowString` 會在以關鍵字限定時顯示陰影版本 `MyBase` 。

## <a name="robust-programming"></a>穩固程式設計

若要降低參照非預期版本的陰影變數的風險，您可以完整限定遮蔽變數的所有參考。 遮蔽導入了一個以上具有相同名稱的變數版本。 當程式碼語句參考變數名稱時，編譯器解析參考的目標版本取決於程式碼語句的位置，以及符合資格的字串是否存在等因素。 這可能會增加參考錯誤版本的變數的風險。

## <a name="see-also"></a>另請參閱

- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的遮蔽功能](shadowing.md)
- [遮蔽和覆寫的差異](differences-between-shadowing-and-overriding.md)
- [如何：隱藏與您的變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：隱藏繼承的變數](how-to-hide-an-inherited-variable.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [覆寫](../../../language-reference/modifiers/overrides.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../objects-and-classes/inheritance-basics.md)
