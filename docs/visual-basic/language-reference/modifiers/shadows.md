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
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402703"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

指定宣告的程式設計專案會在基類中重新宣告並隱藏具有相同名稱的專案或多載元素的集合。

## <a name="remarks"></a>備註

遮蔽的主要目的（也稱為「*依名稱隱藏*」）是保留類別成員的定義。 基類可能會進行一項變更，以建立一個與您已定義的專案名稱相同的元素。 如果發生這種情況， `Shadows` 修飾詞會強制透過類別的參考解析成您所定義的成員，而不是新的基類元素。

遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。

## <a name="rules"></a>規則

- **宣告內容。** 您 `Shadows` 只能在類別層級使用。 這表示元素的宣告內容 `Shadows` 必須是類別，而且不能是原始程式檔、命名空間、介面、模組、結構或程式。

  您只能在單一宣告語句中宣告一個遮蔽元素。

- **結合的修飾詞。** 您不能 `Shadows` `Overloads` `Overrides` 在相同的宣告中，搭配、或來指定 `Static` 。

- **元素類型。** 您可以使用任何其他類型遮蔽任何一種已宣告的項目。 如果您使用另一個屬性或程式來遮蔽屬性或程式，參數和傳回型別就不需要與基類屬性或程式中的相同。

- **正在.** 基類中的陰影元素通常無法從遮蔽它的衍生類別中使用。 不過，下列考慮適用于。

  - 如果無法從參考的程式碼存取遮蔽專案，則會將參考解析為陰影專案。 例如，如果專案 `Private` 遮蔽基類元素，則沒有許可權存取專案的程式碼會改為存取 `Private` 基類元素。

  - 如果您遮蔽某個元素，仍然可以透過以基類類型宣告的物件來存取陰影元素。 您也可以透過來存取它 `MyBase` 。

`Shadows` 修飾詞可用於以下內容：

- [Class 陳述式](../statements/class-statement.md)

- [Const 陳述式](../statements/const-statement.md)

- [Declare Statement](../statements/declare-statement.md)

- [Delegate 陳述式](../statements/delegate-statement.md)

- [Dim 陳述式](../statements/dim-statement.md)

- [End 陳述式](../statements/enum-statement.md)

- [Event 陳述式](../statements/event-statement.md)

- [Function 陳述式](../statements/function-statement.md)

- [Interface 陳述式](../statements/interface-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Structure 陳述式](../statements/structure-statement.md)

- [Sub 陳述式](../statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [共用][](shared.md)
- [靜態](static.md)
- [私用](private.md)
- [Me、My、MyBase 及 MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [繼承基本概念](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [New](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [多載](overloads.md)
- [Overrides](overridable.md)
- [覆寫](overrides.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
