---
title: 如何：隱藏繼承的變數
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
ms.openlocfilehash: f49bba0497f9f4f2774b01284c815bba9aaed119
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357266"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>如何：隱藏繼承的變數 (Visual Basic)

衍生類別會繼承其基類的所有定義。 如果您想要使用與基類之專案相同的名稱來定義變數，您可以在衍生類別中定義變數時，隱藏或*遮蔽*該基類元素。 如果您這樣做，衍生類別中的程式碼會存取您的變數，除非它明確略過遮蔽機制。

您可能會想要隱藏繼承的變數的另一個原因是要防止基底類別修訂。 基類可能會改變您所繼承的元素。 如果發生這種情況， `Shadows` 修飾詞會強制將衍生類別的參考解析為您的變數，而不是基類元素。

## <a name="to-hide-an-inherited-variable"></a>若要隱藏繼承的變數

1. 請確定您要隱藏的變數是在類別層級宣告（在任何程式之外）。 否則，您不需要將它隱藏。
  
2. 在您的衍生類別中，撰寫宣告變數的[Dim 語句](../../../language-reference/statements/dim-statement.md)。 使用與繼承之變數相同的名稱。

3. 在宣告中包含[Shadows](../../../language-reference/modifiers/shadows.md)關鍵字。

     當衍生類別中的程式碼參考變數名稱時，編譯器會解析變數的參考。

     下列範例說明如何遮蔽繼承的變數：
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     上述範例 `shadowString` 會在基類中宣告變數，並將其遮蔽在衍生類別中。 `ShowStrings`當名稱未限定時，衍生類別中的程式會顯示字串的遮蔽版本 `shadowString` 。 然後，它 `shadowString` 會在以關鍵字限定時顯示陰影版本 `MyBase` 。  
  
## <a name="robust-programming"></a>穩固程式設計

遮蔽導入了一個以上具有相同名稱的變數版本。 當程式碼語句參考變數名稱時，編譯器解析參考的目標版本取決於程式碼語句的位置，以及符合資格的字串是否存在等因素。 這可能會增加參考非預期版本的陰影變數的風險。 您可以藉由完整限定遮蔽變數的所有參考，來降低風險。

## <a name="see-also"></a>另請參閱

- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的遮蔽功能](shadowing.md)
- [遮蔽和覆寫的差異](differences-between-shadowing-and-overriding.md)
- [如何：隱藏與您的變數名稱相同的變數](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：存取衍生類別所隱藏的變數](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [覆寫](../../../language-reference/modifiers/overrides.md)
- [Me、My、MyBase 及 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../objects-and-classes/inheritance-basics.md)
