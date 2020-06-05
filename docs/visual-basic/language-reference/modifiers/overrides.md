---
title: 覆寫
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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392024"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。

## <a name="rules"></a>規則

- **宣告內容。** 您 `Overrides` 只能在屬性或程式宣告語句中使用。

- **結合的修飾詞。** 您不能在 `Overrides` `Shadows` 相同的宣告中搭配或一起指定 `Shared` 。 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。

- **相符簽章。** 這個宣告的簽章必須與它所覆寫之屬性或*程式的簽*章完全相符。 這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。

  除了簽章，覆寫宣告也必須完全符合下列各項：

  - 存取層級

  - 傳回類型 (如果有的話)

- **泛型簽章。** 在泛型程序中，簽章包含類型參數的個數。 因此，覆寫宣告在這方面也必須符合基底類別版本。

- **其他符合。** 除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：

  - 存取層級修飾詞（例如[Public](public.md)）

  - 每個參數的傳遞機制（[ByVal](byval.md)或[ByRef](byref.md)）

  - 泛型程序的每個類型參數的條件約束清單

- **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的陰影](../../programming-guide/language-features/declared-elements/shadowing.md)。

如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。

`Overrides` 修飾詞可用於以下內容：

- [Function 陳述式](../statements/function-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub 陳述式](../statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [New](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overrides](overridable.md)
- [關鍵字](../keywords/index.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Type List](../statements/type-list.md)
