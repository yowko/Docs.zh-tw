---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: e879819d945f3e7256edd34e87b9cae4a04c0829
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512732"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
指定宣告的程式設計項目會重新宣告並隱藏同名的項目或一組多載的項目，基底類別中。  
  
## <a name="remarks"></a>備註  
 遮蔽的主要目的 (也稱為*依名稱隱藏*) 是保留您的類別成員的定義。 基底類別可能進行的變更，會建立具有相同名稱做為其中一個已定義的項目。 如果發生這種情況，`Shadows`修飾詞強制參考透過您的類別成員解析您定義的而不是新的基底類別項目。  
  
 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱 < [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您可以使用`Shadows`只能在類別層級。 這表示的宣告內容`Shadows`項目必須是類別，，而且不能是原始程式檔、 命名空間、 介面、 模組、 結構或程序。  
  
     您可以宣告一個宣告陳述式中只能有一個遮蔽的項目。  
  
-   **結合的修飾詞。** 您無法指定`Shadows`連同`Overloads`， `Overrides`，或`Static`相同宣告中。  
  
-   **項目型別。** 您可以使用任何其他類型遮蔽任何一種已宣告的項目。 如果您遮蔽的屬性或程序與另一個屬性或程序，參數和傳回型別沒有以符合那些在基底類別屬性或程序。  
  
-   **存取。** 無法從遮蔽的衍生類別內通常使用遮蔽基底類別中的項目。 不過，適用下列考量。  
  
    -   如果遮蔽的項目不能從參考它的程式碼存取，則參考會解析為遮蔽的項目中。 例如，如果`Private`項目會遮蔽基底類別的項目，並沒有存取權限的程式碼`Private`項目改為存取基底類別項目。  
  
    -   如果遮蔽的項目時，您仍然可以透過使用基底類別的型別宣告的物件存取遮蔽的項目。 您也可以存取透過`MyBase`。  
  
 `Shadows` 修飾詞可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [多載](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
