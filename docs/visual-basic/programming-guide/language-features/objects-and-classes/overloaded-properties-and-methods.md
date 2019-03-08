---
title: 多載的屬性和方法 (Visual Basic)
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
ms.openlocfilehash: 8d7341370d9770d2e57f786ac7c68277e66a9bbd
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677392"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>多載的屬性和方法 (Visual Basic)

多載會建立一個以上的程序、 執行個體建構函式或具有相同名稱但不同的引數類型的類別中的屬性。

## <a name="overloading-usage"></a>多載的使用方式

物件模型會要求您採用相同的名稱，在不同的資料類型上運作的程序時，多載會特別有用。 例如，可以顯示數種不同的資料類型的類別可能會有`Display`看起來像這樣的程序：

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

沒有多載，您必須建立不同的名稱，每個程序，即使它們是一樣，如下所示：

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

多載可讓您更輕鬆地使用屬性或方法，因為它提供了可用的資料類型的選擇。 例如，多載`Display`所討論的方法之前可以呼叫任何的下列程式碼行：

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

在執行階段，Visual Basic 會呼叫正確的程序，根據您指定的參數資料類型。

## <a name="overloading-rules"></a>多載規則

 您可以新增兩個或多個屬性具有相同名稱的方法，以建立類別的多載的成員。 除了多載衍生的成員，每個多載的成員必須具有不同的參數清單，而多載屬性或程序時，無法做為區別的功能使用下列項目：

- 修飾詞，例如`ByVal`或`ByRef`，套用到成員或成員的參數。

- 參數的名稱

- 程序的傳回型別

`Overloads`多載時，關鍵字是選擇性，但如果有多載成員使用`Overloads`關鍵字，則所有其他多載的成員，具有相同名稱也必須指定此關鍵字。

在衍生的類別可以多載繼承的成員與具有相同參數和參數型別，這道程序的成員*依名稱和簽章，以遮蔽*。 如果`Overloads`遮蔽依名稱和簽章，衍生的類別實作的成員會用而不是在基底類別中，實作並為該成員的其他所有多載可使用的執行個體時，會使用關鍵字在衍生的類別。

如果`Overloads`多載繼承的成員與具有相同參數和參數類型的成員時省略關鍵字，則多載會呼叫*以名稱遮蔽*。 以名稱遮蔽取代繼承的成員，實作，它會使其他所有多載無法供衍生的類別和及其子系的執行個體。

`Overloads`和`Shadows`修飾詞不能同時搭配相同的屬性或方法。

### <a name="example"></a>範例

下列範例會建立多載的方法可接受任一`String`或`Decimal`金額和傳回包含營業稅的字串表示。

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>若要使用此範例來建立多載的方法

1. 開啟新的專案，並加入名為類別`TaxClass`。

2. 將下列程式碼加入 `TaxClass` 類別。

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. 將下列程序新增至您的表單。

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. 將按鈕新增至您的表單並呼叫`ShowTax`程序從`Button1_Click`按鈕的事件。

5. 執行專案，然後按一下要測試的多載表單上的按鈕`ShowTax`程序。

在執行階段，編譯器會選擇符合所使用之參數的適當多載函式。 當您按一下按鈕時，使用第一次呼叫多載的方法`Price`參數是字串和訊息，「 價格會是字串。 稅務為 $5.12 」 顯示。 `TaxAmount` 使用呼叫`Decimal`值第二次和訊息，「 價格會是十進位數。 稅務為 $5.12 」 顯示。

## <a name="see-also"></a>另請參閱

- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [繼承的基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
