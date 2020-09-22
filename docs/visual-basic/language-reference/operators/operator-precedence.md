---
title: 運算子優先順序
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
ms.openlocfilehash: b5649cd2a58fd8d300df58c563aebeed8976c4f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874789"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的運算子優先順序

當運算式中發生數個作業時，系統會依預先決定的順序來評估並解析每個元件，稱為「 *運算子優先順序*」。

## <a name="precedence-rules"></a>優先順序規則

 當運算式包含來自一個以上類別的運算子時，會根據下列規則進行評估：

- 算術和串連運算子具有下一節中描述的優先順序，而且全部都具有比比較、邏輯和位運算子更高的優先順序。

- 所有比較運算子都有相等的優先順序，而且所有的優先順序都比邏輯和位運算子更高，但優先順序比算術和串連運算子低。

- 邏輯和位運算子具有下一節中描述的優先順序，而且所有的優先順序都比算術、串連和比較運算子低。

- 具有相等優先順序的運算子會依照它們在運算式中出現的順序，從左至右評估。

## <a name="precedence-order"></a>優先順序

 系統會依照下列優先順序來評估運算子：

### <a name="await-operator"></a>Await 運算子

 等待

### <a name="arithmetic-and-concatenation-operators"></a>算術和串連運算子

  () 的乘冪 `^`

 一元識別和否定 (`+` ， `–`) 

 乘法和浮點數除法 (`*` ， `/`) 

 整數除法 (`\`) 

 模組化算術 (`Mod`) 

 加法和減法 (`+` ， `–`) 

 字串串連 (`&`) 

 算術位移位 (`<<` ， `>>`) 

### <a name="comparison-operators"></a>比較運算子

 所有比較運算子 (`=` 、 `<>` 、 `<` 、 `<=` 、 `>` 、 `>=` 、、、 `Is` `IsNot` `Like` 、 `TypeOf` ... `Is`) 

### <a name="logical-and-bitwise-operators"></a>邏輯運算子和位元運算子

 否定 (`Not`) 

 結合 (`And` ， `AndAlso`) 

 包含分離 (`Or` 、 `OrElse`) 

 獨佔分離 (`Xor`) 

### <a name="comments"></a>註解

 `=`運算子只是相等比較運算子，而不是指派運算子。

 字串串連運算子 (`&`) 不是算術運算子，但優先順序則是與算術運算子群組。

 `Is`和 `IsNot` 運算子是物件參考比較運算子。 它們並不會比較兩個物件的值。它們只會檢查兩個物件變數是否參考相同的物件實例。

## <a name="associativity"></a>關聯性

 當相等優先順序的運算子同時出現在運算式中時（例如乘法和除法），編譯器會在每個作業從左至右遇到時進行評估。 下列範例將說明這點。

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 第一個運算式會評估相除的 96/8 (，這會導致 12) ，然後再產生三個除法 12/4。 因為編譯器 `n1` 會從左至右評估作業，所以當明確指出該順序時，評估會是相同的 `n2` 。 `n1`和都 `n2` 有三個結果。 相反地，會 `n3` 產生48的結果，因為括弧會強制編譯器先評估 8/4。

 由於這種行為，運算子在 Visual Basic 中稱為 *左關聯* 。

## <a name="overriding-precedence-and-associativity"></a>覆寫優先順序和關聯性

 您可以使用括弧來強制先評估運算式的某些部分，再進行其他部分。 這可以覆寫優先順序和左邊關聯性的順序。 Visual Basic 一律會執行以括弧括住的作業。 不過，除非您在括弧內使用括弧，否則它會維持一般優先順序和關聯性。 下列範例將說明這點。

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

- [= 運算子](assignment-operator.md)
- [Is 運算子](is-operator.md)
- [IsNot 運算子](isnot-operator.md)
- [Like 運算子](like-operator.md)
- [TypeOf 運算子](typeof-operator.md)
- [Await 運算子](await-operator.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
