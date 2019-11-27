---
title: '[覆寫]'
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351377"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。

## <a name="rules"></a>規則

- **宣告內容。** 您只能在屬性或程式宣告語句中使用 `Overrides`。

- **合併的修飾詞。** 您不能在相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。

- **符合的簽章。** 這個宣告的簽章必須與它所覆寫之屬性或*程式的簽*章完全相符。 這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。

  除了簽章，覆寫宣告也必須完全符合下列各項：

  - 存取層級

  - 傳回類型 (如果有的話)

- **一般簽章。** 在泛型程序中，簽章包含類型參數的個數。 因此，覆寫宣告在這方面也必須符合基底類別版本。

- **其他相符的。** 除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：

  - 存取層級修飾詞（例如[Public](../../../visual-basic/language-reference/modifiers/public.md)）

  - 每個參數的傳遞機制（[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)）

  - 泛型程序的每個類型參數的條件約束清單

- **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。

如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。

`Overrides` 修飾詞可用於以下內容：

- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)

- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)

- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overridable.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic 中的陰影](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [類型清單](../../../visual-basic/language-reference/statements/type-list.md)
