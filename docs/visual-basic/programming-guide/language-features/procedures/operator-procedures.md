---
title: 運算子程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 46afbbe411a1adf27960e3c7d9d3ca98046ecec5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524535"
---
# <a name="operator-procedures-visual-basic"></a>運算子程序 (Visual Basic)

運算子程式是一系列的 Visual Basic 語句，可在您定義的類別或結構上定義標準運算子的行為（例如 `*`、`<>` 或 `And`）。 這也稱為「*運算子*多載」。

## <a name="when-to-define-operator-procedures"></a>定義運算子程式的時機

當您已定義類別或結構時，您可以將變數宣告為該類別或結構的類型。 有時候這類變數需要參與作業做為運算式的一部分。 若要這樣做，它必須是運算子的運算元。

Visual Basic 只會定義其基本資料類型的運算子。 當一或兩個運算元屬於您的類別或結構類型時，您可以定義運算子的行為。

如需詳細資訊，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。

## <a name="types-of-operator-procedure"></a>運算子程式的類型

運算子程式可以是下列其中一種類型：

- 一元運算子的定義，其中引數是您的類別或結構的類型。

- 二元運算子的定義，其中至少有一個引數屬於您的類別或結構的類型。

- 轉換運算子的定義，其中的引數是您的類別或結構的類型。

- 轉換運算子的定義，可傳回您的類別或結構的類型。

 轉換運算子一律是一元，而且您一律會使用 `CType` 做為您所定義的運算子。

## <a name="declaration-syntax"></a>宣告語法

宣告運算子程式的語法如下：

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

您只會在類型轉換運算子上使用 `Widening` 或 `Narrowing` 關鍵字。 類型轉換運算子的運算子符號一律是[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)。

您可以宣告兩個運算元來定義二元運算子，並宣告一個運算元來定義一元運算子，包括型別轉換運算子。 所有運算元都必須宣告 `ByVal`。

您可以用宣告[Sub 程式](./sub-procedures.md)參數的相同方式來宣告每個運算元。

### <a name="data-type"></a>資料類型

因為您是在已定義的類別或結構上定義運算子，所以至少有一個運算元必須是該類別或結構的資料類型。 若為類型轉換運算子，運算元或傳回類型必須是類別或結構的資料類型。

如需詳細資訊，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。

## <a name="calling-syntax"></a>呼叫語法

您可以在運算式中使用運算子符號，以隱含的方式叫用運算子程式。 提供運算元的方式與預先定義的運算子相同。

對運算子程式進行隱含呼叫的語法如下：

`Dim testStruct As`  *結構名稱*

`Dim testNewStruct As`  *結構名稱*  `= testStruct`  *運算子符號*  `10`

### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例

下列結構會將帶正負號的128位整數值儲存為組成高順序和低序位部分。 它會定義 `+` 運算子，以加入兩個 `veryLong` 值，並產生產生的 `veryLong` 值。

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

下列範例顯示 `veryLong` 上所定義之 `+` 運算子的一般呼叫。

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
