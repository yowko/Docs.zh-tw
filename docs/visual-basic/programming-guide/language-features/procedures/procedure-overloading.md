---
title: 程序多載
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352591"
---
# <a name="procedure-overloading-visual-basic"></a>程序多載化 (Visual Basic)

多載程式表示使用相同名稱但不同的參數清單，在多個版本中定義它。 多載的目的是要定義程式的數個緊密相關版本，而不需要依名稱區分。 您可以藉由改變參數清單來執行這項操作。

## <a name="overloading-rules"></a>多載規則

當您多載程式時，適用下列規則：

- **相同名稱**。 每個多載的版本都必須使用相同的程式名稱。

- **不同**的簽章。 每個多載的版本都必須與所有其他多載版本的差異，至少為下列其中一個方面：

  - 參數數目

  - 參數的順序

  - 參數的資料類型

  - 型別參數的數目（適用于泛型程式）

  - 傳回類型（僅適用于轉換運算子）

  加上程式名稱，前面的專案統稱為*程式的簽*章。 當您呼叫多載程式時，編譯器會使用簽章來檢查呼叫是否正確符合定義。

- **專案不是簽章的一部分**。 您無法多載程式，而不會改變簽章。 特別的是，您無法藉由只改變下列一個或多個專案，來多載程式：

  - 程式修飾詞關鍵字，例如 `Public`、`Shared`和 `Static`

  - 參數或類型參數名稱

  - 類型參數條件約束（適用于泛型程式）

  - 參數修飾詞關鍵字，例如 `ByRef` 和 `Optional`

  - 是否傳回值

  - 傳回值的資料類型（轉換運算子除外）

  上述清單中的專案不是簽章的一部分。 雖然您無法使用它們來區別多載的版本，但您可以在多載的版本中，根據其簽章適當地區分它們。

- **晚期繫結引數**。 如果您想要將晚期繫結物件變數傳遞至多載版本，您必須將適當的參數宣告為 <xref:System.Object>。

## <a name="multiple-versions-of-a-procedure"></a>程式的多個版本

假設您正在撰寫一個 `Sub` 程式，以根據客戶的餘額來張貼交易，而且您希望能夠依名稱或帳戶號碼來參考客戶。 為了配合此，您可以定義兩個不同的 `Sub` 程式，如下列範例所示：

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>多載版本

另一個方法是多載單一程式名稱。 您可以使用[Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字，為每個參數清單定義程式的版本，如下所示：

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>其他多載

如果您也想要接受 `Decimal` 或 `Single`中的交易量，您可以進一步多載 `post`，以允許這種變化。 如果您對上述範例中的每個多載執行此操作，則會有四個 `Sub` 程式，全都具有相同的名稱，但具有四個不同的簽章。

## <a name="advantages-of-overloading"></a>多載的優點

多載程式的優點是呼叫的彈性。 若要使用上述範例中所宣告的 `post` 程式，呼叫程式碼可以取得客戶識別做為 `String` 或 `Integer`，然後在任一情況下呼叫相同的程式。 下面這個範例可說明這點：

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
