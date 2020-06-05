---
title: 多載
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: bd0931cab520f8580c0d7473a44e350752e287bb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392102"
---
# <a name="overloads-visual-basic"></a>Overloads (Visual Basic)

指定屬性或程序會重新宣告一或多個同名的現有屬性或程序。

## <a name="remarks"></a>備註

多*載是針對*相同範圍內的指定屬性或程式名稱提供一個以上定義的作法。 以不同的簽章重新宣告屬性或程式，有時稱為*依*簽章隱藏。

## <a name="rules"></a>規則

- **宣告內容。** 您 `Overloads` 只能在屬性或程式宣告語句中使用。

- **結合的修飾詞。** 您不能 `Overloads` 在相同的程式宣告中同時指定與[Shadows](shadows.md) 。

- **必要的差異。** 此*宣告中的*簽章必須與它多載之每個屬性或程式的簽章不同。 簽章包含屬性或程序名稱，以及下列項目：

  - 參數的數目

  - 參數的順序

  - 參數的資料類型

  - 類型參數的數目 (適用於泛型程序)

  - 傳回型別 (僅適用於轉換運算子程序)

  所有多載必須有相同的名稱，但每個多載的名稱在一或多個上述方面中必須和其他多載不同。 這可讓編譯器在程式碼呼叫屬性或程序時可識別要使用的版本。

- **不允許的差異。** 變更下列一或多個項目，對於多載屬性或程序是無效的，因為它們屬於簽章：

  - 是否傳回值 (適用於程序)

  - 傳回值的資料類型 (除了轉換運算子之外)

  - 參數或型別參數的名稱

  - 類型參數上的條件約束 (適用於泛型程序)

  - 參數修飾詞關鍵字 (例如 `ByRef` 或 `Optional`)

  - 屬性或程序修飾詞關鍵字 (例如 `Public` 或 `Shared`)

- **選擇性修飾詞。** `Overloads`當您在同一個類別中定義多個多載屬性或程式時，不需要使用修飾詞。 不過，如果您在其中一個宣告中使用 `Overloads`，您必須在全部的宣告中使用它。

- **遮蔽和多載。** `Overloads`也可以用來在基類中遮蔽現有的成員或一組多載成員。 以此方式使用 `Overloads` 時，即表示您會宣告同名的屬性或方法和相同的參數清單作為基底類別成員，而且您並未提供 `Shadows` 關鍵字。

如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。

`Overloads` 修飾詞可用於以下內容：

- [Function 陳述式](../statements/function-statement.md)

- [Operator Statement](../statements/operator-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub 陳述式](../statements/sub-statement.md)

## <a name="see-also"></a>另請參閱

- [Shadows](shadows.md)
- [程序多載化](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [運算子程序](../../programming-guide/language-features/procedures/operator-procedures.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
