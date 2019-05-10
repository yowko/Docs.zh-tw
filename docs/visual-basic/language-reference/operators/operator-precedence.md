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
ms.openlocfilehash: 95505fd593881ff27418c69550952d072b4e3949
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628864"
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的運算子優先順序
每個部分時數個作業發生時在運算式中，評估，以及在預先決定的順序呼叫中解決*運算子優先順序*。  
  
## <a name="precedence-rules"></a>優先順序規則  
 當運算式包含來自多個類別目錄的運算子時，會評估根據下列規則：  
  
- 算術和串連運算子有下列的一節所述的優先順序，都有更高的優先順序高於比較、 邏輯和位元運算子。  
  
- 所有的比較運算子具有相等的優先順序，及其所有具有較高的優先順序高於邏輯和位元運算子，但較低的優先順序高於算術和串連運算子。  
  
- 邏輯和位元運算子有下列的一節所述的優先順序，所有具有較低的優先順序高於算術運算子、 串連和比較運算子。  
  
- 具有相同優先順序的運算子會由左至右評估以其出現在運算式中的順序。  
  
## <a name="precedence-order"></a>優先順序  
 運算子會評估順序的優先順序如下：  
  
### <a name="await-operator"></a>Await 運算子  
 Await  
  
### <a name="arithmetic-and-concatenation-operators"></a>算術運算子和串連運算子  
 乘冪 (`^`)  
  
 一元 （unary) 身分識別和否定 (`+`， `–`)  
  
 乘法和浮點除法 (`*`， `/`)  
  
 整數除法 (`\`)  
  
 模數算術 (`Mod`)  
  
 加法和減法 (`+`， `–`)  
  
 字串串連 (`&`)  
  
 算術的位元移位 (`<<`， `>>`)  
  
### <a name="comparison-operators"></a>比較運算子  
 所有的比較運算子 (`=`， `<>`， `<`， `<=`， `>`， `>=`， `Is`， `IsNot`， `Like`， `TypeOf`...`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>邏輯運算子和位元運算子  
 否定 (`Not`)  
  
 搭配使用 (`And`， `AndAlso`)  
  
 內含分離 (`Or`， `OrElse`)  
  
 獨佔分離 (`Xor`)  
  
### <a name="comments"></a>註解  
 `=`運算子只是等號比較運算子，不是指派運算子。  
  
 字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。  
  
 `Is`和`IsNot`運算子是物件參考的比較運算子。 它們不會比較兩個物件; 的值他們檢查才能判斷兩個物件變數是否指向相同物件執行個體。  
  
## <a name="associativity"></a>順序關聯性  
 當相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估每個作業發生它從左到右。 下列範例將說明這點。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 第一個運算式會評估部門 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。 因為編譯器會評估的作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。 兩者`n1`和`n2`有三個結果。 相較之下，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。  
  
 由於這個行為，運算子可以說是*左向*Visual Basic 中。  
  
## <a name="overriding-precedence-and-associativity"></a>覆寫優先順序和關聯性  
 若要強制其他項目之前評估運算式的某些部分，您可以使用括號。 優先順序和左順序關聯性，也可以覆寫。 Visual Basic 一律會執行之前以外的括號括住的作業。 不過，在括號，它會維護一般優先順序和關聯性，除非您使用以括弧括住的括號。 下列範例將說明這點。  
  
```  
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
