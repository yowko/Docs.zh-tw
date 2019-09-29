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
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592215"
---
# <a name="-operator-visual-basic"></a>^ 運算子 (Visual Basic)

將數位提高至另一個數位的乘冪。

## <a name="syntax"></a>語法

```vb
number ^ exponent
```

## <a name="parts"></a>組件

`number`\
必要項。 任何數值運算式。

`exponent`\
必要項。 任何數值運算式。

## <a name="result"></a>結果

結果為 `number`，`exponent` 的乘冪，一律為 `Double` 值。

## <a name="supported-types"></a>支援的型別

`Double`. 任何不同類型的運算元都會轉換成 `Double`。

## <a name="remarks"></a>備註

Visual Basic 一律會執行[Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)的乘冪。

@No__t-0 的值可以是小數、負數或兩者。

當單一運算式中執行一個以上的乘冪時，會評估 `^` 運算子，因為它是由左至右所遇到。

> [!NOTE]
> @No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="example"></a>範例

下列範例會使用 `^` 運算子，將數位提高至指數的乘冪。 結果是第一個運算元會引發到第二個運算元的乘冪。

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

上述範例會產生下列結果：

`exp1` 設定為4（2平方）。

`exp2` 設定為19683（3的立方，而該值為立方）。

`exp3` 設定為-125 （-5 的立方）。

`exp4` 設定為625（-5 到第四個電源）。

`exp5` 設定為2（cube 根目錄為8）。

`exp6` 設定為0.5 （1.0 除以8的 cube 根）。

請注意上述範例中運算式的括弧重要性。 由於*運算子的優先順序*，Visual Basic 通常會在任何其他專案之前執行 `^` 運算子，甚至是一元 `–` 運算子。 如果 `exp4` 和 `exp6` 的計算不含括弧，則會產生下列結果：

`exp4 = -5 ^ 4` 會計算為–（5到第四個電源），這會產生-625。

`exp6 = 8 ^ -1.0 / 3.0` 會計算為（8到-1 電源，或0.125）除以3.0，這會導致0.041666666666666666666666666666667。

## <a name="see-also"></a>另請參閱

- [^= 運算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
