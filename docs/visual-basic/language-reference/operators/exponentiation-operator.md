---
title: ^ 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 54de9c91d4e166b8ca1733952dfa9c98ebf11ffe
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674090"
---
# <a name="-operator-visual-basic"></a>^ 運算子 (Visual Basic)

引發到另一個數字乘冪的數字。

## <a name="syntax"></a>語法

```
number ^ exponent
```

## <a name="parts"></a>組件

`number`\
必要項。 任何數值運算式。

`exponent`\
必要項。 任何數值運算式。

## <a name="result"></a>結果

結果是`number`的乘冪`exponent`，一律為`Double`值。

## <a name="supported-types"></a>支援的型別

`Double`. 任何不同類型的運算元會轉換成`Double`。

## <a name="remarks"></a>備註

Visual Basic 一律會執行中的乘冪[Double 資料型別](../../../visual-basic/language-reference/data-types/double-data-type.md)。

值`exponent`可以是小數、 負數，或兩者。

在單一運算式中，執行一個以上的乘冪時`^`時發現從左到右評估運算子。

> [!NOTE]
> `^`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="example"></a>範例

下列範例會使用`^`運算子引發的指數乘冪數字。 結果會是第一個運算元具有乘冪數的第二個。

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

上述範例會產生下列結果：

`exp1` 設為 4 (平方 2)。

`exp2` 設定為 19683 (3 立方，然後該值立方)。

`exp3` 設定為-125 (-5 立方)。

`exp4` 設定為 625 (第四個的乘冪的-5)。

`exp5` 設定為 2 （8 個的立方根）。

`exp6` 設定為 0.5 (除以 8 的立方根 1.0)。

請注意在上述範例中的運算式中的括號的重要性。 由於*運算子優先順序*，通常會先執行 Visual Basic`^`運算子，再執行其他的甚至是一元`–`運算子。 如果`exp4`和`exp6`已計算沒有括號，則可能產生下列結果：

`exp4 = -5 ^ 4` 會計算為 (第四個的乘冪 5)，這會導致-625。

`exp6 = 8 ^ -1.0 / 3.0` 會計算為 (-1 的電力或 0.125 8) 除以可得到 0.041666666666666666666666666666667 3.0。

## <a name="see-also"></a>另請參閱

- [^= 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
