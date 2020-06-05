---
title: 多載屬性和方法
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: 1672f12773ece012c580253b6dafbf9d0ac8f07c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389148"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>多載屬性和方法（Visual Basic）

多載是在具有相同名稱但不同引數類型的類別中，建立一個以上的程式、實例函數或屬性。

## <a name="overloading-usage"></a>多載使用

當您的物件模型指示您針對在不同資料類型上運作的程式使用相同的名稱時，多載特別有用。 例如，可以顯示數個不同資料類型的類別，其程式可能如下所示 `Display` ：

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

如果沒有多載，您就必須為每個程式建立不同的名稱，即使它們執行相同的動作，如下所示：

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

多載可讓您更輕鬆地使用屬性或方法，因為它會提供可供使用的資料類型選擇。 例如，您 `Display` 可以使用下列任何一行程式碼呼叫先前所討論的多載方法：

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

在執行時間，Visual Basic 會根據您指定之參數的資料類型，呼叫正確的程式。

## <a name="overloading-rules"></a>多載規則

 您可以藉由加入兩個或多個具有相同名稱的屬性或方法，來建立類別的多載成員。 除了多載的衍生成員之外，每個多載成員都必須有不同的參數清單，而且當多載屬性或程式時，無法使用下列專案做為區分功能：

- 套用 `ByVal` `ByRef` 至成員或成員之參數的修飾詞，例如或。

- 參數的名稱

- 傳回程序的類型

當多載 `Overloads` 時，關鍵字是選擇性的，但如果有任何多載成員使用 `Overloads` 關鍵字，則所有具有相同名稱的其他多載成員也必須指定此關鍵字。

衍生的類別可以多載繼承的成員，這些成員具有相同的參數和參數類型，這種*程式稱為依名稱和*簽章的遮蔽。 如果在 `Overloads` 依名稱和簽章進行遮蔽時使用關鍵字，將會使用衍生類別的成員執行，而不是基類中的實作為，而且該成員的所有其他多載都會提供給衍生類別的實例。

`Overloads`當使用具有相同參數和參數類型的成員多載繼承的成員時，如果省略了關鍵字，則會*依名稱*將多載稱為「遮蔽」。 依名稱遮蔽會取代成員的繼承實作為，並讓衍生類別的實例和其 decedents 無法使用所有其他多載。

和修飾詞 `Overloads` `Shadows` 不能同時用於相同的屬性或方法。

### <a name="example"></a>範例

下列範例會建立可接受 `String` 貨幣金額或標記法的多載方法， `Decimal` 並傳回包含銷售稅額的字串。

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>若要使用此範例來建立多載方法

1. 開啟新的專案，並新增名為的類別 `TaxClass` 。

2. 將下列程式碼新增至 `TaxClass` 類別。

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. 將下列程式新增至您的表單。

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. 將按鈕新增至表單，並 `ShowTax` 從按鈕的事件中呼叫程式 `Button1_Click` 。

5. 執行專案，然後按一下表單上的按鈕，以測試多載程式 `ShowTax` 。

在執行時間，編譯器會選擇符合所使用之參數的適當多載函式。 當您按一下此按鈕時，會先呼叫多載的方法，其 `Price` 參數為字串，而訊息為「價格為字串。 稅金為 $5.12」隨即顯示。 `TaxAmount`會以 `Decimal` 第二次和訊息的值呼叫，「價格是十進位。 稅金為 $5.12」隨即顯示。

## <a name="see-also"></a>另請參閱

- [物件和類別](index.md)
- [Visual Basic 中的遮蔽功能](../declared-elements/shadowing.md)
- [Sub 陳述式](../../../language-reference/statements/sub-statement.md)
- [繼承基本概念](inheritance-basics.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [ByVal](../../../language-reference/modifiers/byval.md)
- [RemoveHandler](../../../language-reference/modifiers/byref.md)
- [多載](../../../language-reference/modifiers/overloads.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
