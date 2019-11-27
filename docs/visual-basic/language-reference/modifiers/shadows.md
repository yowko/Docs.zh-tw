---
title: Shadows
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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351268"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

指定宣告的程式設計專案會在基類中重新宣告並隱藏具有相同名稱的專案或多載元素的集合。

## <a name="remarks"></a>備註

遮蔽的主要目的（也稱為「*依名稱隱藏*」）是保留類別成員的定義。 基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。 如果發生這種情況，`Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。

遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。

## <a name="rules"></a>規則

- **宣告內容。** 您只能在類別層級使用 `Shadows`。 這表示 `Shadows` 元素的宣告內容必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

  您只能在單一宣告語句中宣告一個遮蔽元素。

- **合併的修飾詞。** 您不能在相同的宣告中同時指定 `Shadows` 與 `Overloads`、`Overrides`或 `Static`。

- **元素類型。** 您可以使用任何其他類型遮蔽任何一種已宣告的項目。 如果您使用另一個屬性或程式來遮蔽屬性或程式，參數和傳回型別就不需要與基類屬性或程式中的相同。

- **正在.** 基類中的陰影元素通常無法從遮蔽它的衍生類別中使用。 不過，下列考慮適用于。

  - 如果無法從參考的程式碼存取遮蔽專案，則會將參考解析為陰影專案。 例如，如果 `Private` 專案遮蔽基類元素，則沒有許可權存取 `Private` 專案的程式碼會改為存取基類元素。

  - 如果您遮蔽某個元素，仍然可以透過以基類類型宣告的物件來存取陰影元素。 您也可以透過 `MyBase`來存取它。

`Shadows` 修飾詞可用於以下內容：

- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [共用](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [多載](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
