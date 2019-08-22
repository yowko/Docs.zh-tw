---
title: Visual Basic 中的運算子優先順序
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: df40aced45442c9c7895c8d10ece64b21e292508
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659931"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的運算子優先順序
當運算式中發生數個作業時, 每個元件都會以預先決定的順序 (稱為*運算子優先順序*) 進行評估和解析。

## <a name="precedence-rules"></a>優先順序規則
 當運算式包含來自多個類別的運算子時, 會根據下列規則進行評估:

- 算術和串連運算子具有下一節所描述的優先順序順序, 而且所有的優先順序高於比較、邏輯和位運算子。

- 所有比較運算子都具有相同的優先順序, 而且所有的優先順序高於邏輯和位運算子, 但較低的優先順序高於算術和串連運算子。

- 邏輯和位運算子具有下一節所描述的優先順序順序, 而且所有的優先順序都低於算術、串連和比較運算子。

- 具有相等優先順序的運算子會依其在運算式中出現的順序向右評估。

## <a name="precedence-order"></a>優先順序
 運算子會依照下列優先順序來進行評估:

### <a name="await-operator"></a>Await 運算子
 遇到

### <a name="arithmetic-and-concatenation-operators"></a>算術和串連運算子
 乘冪`^`()

 一元識別和否定 (`+`, `–`)

 乘法和浮點除法 (`*`,) `/`

 整數除法 (`\`)

 模組化算術`Mod`()

 加法和減法 (`+`, `–`)

 字串串連 (`&`)

 算術位移位 (`<<`, `>>`)

### <a name="comparison-operators"></a>比較運算子
 所有比較運算子 (`=`、 `<>` `<` `<=` 、、`>`、、 、`>=`、、 、...`TypeOf` `Like` `Is` `IsNot``Is`)

### <a name="logical-and-bitwise-operators"></a>邏輯運算子和位元運算子
 否定 (`Not`)

 結合 (`And`、 `AndAlso`)

 內含析取`Or`( `OrElse`,)

 獨佔分離 (`Xor`)

### <a name="comments"></a>註解
 `=`運算子只是相等比較運算子, 而不是指派運算子。

 字串串連運算子 (`&`) 不是算術運算子, 但優先順序會與算術運算子群組在一起。

 `Is` 和`IsNot`運算子是物件參考比較運算子。 它們不會比較兩個物件的值。它們只會檢查以判斷兩個物件變數是否參考相同的物件實例。

## <a name="associativity"></a>順序關聯性
 當相等優先順序的運算子同時出現在運算式中時 (例如乘法和除法), 編譯器會在每個作業從左至右遇到時進行評估。 下列範例將說明這點。

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 第一個運算式會評估除法 96/8 (這會產生 12), 然後是除法 12/4, 這會產生三個。 因為編譯器會`n1`從左至右評估的作業, 所以當明確`n2`指出該順序時, 評估會是相同的。 `n1` 和`n2`都有三個結果。 相反地, `n3`的結果為 48, 因為括弧會強制編譯器先評估 8/4。

 基於此行為, 運算子稱為 Visual Basic 中的*左關聯*。

## <a name="overriding-precedence-and-associativity"></a>覆寫優先順序和關聯性
 您可以使用括弧來強制評估運算式的某些部分。 這可能會覆寫優先順序和左側關聯性的順序。 Visual Basic 一律會執行以括弧括住的作業, 而不是在外部。 不過, 在括弧內, 除非您在括弧內使用括弧, 否則會維持一般優先順序和關聯性。 下列範例將說明這點。

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a>另請參閱

- [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await 運算子](../../../visual-basic/language-reference/operators/await-operator.md)
- [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
