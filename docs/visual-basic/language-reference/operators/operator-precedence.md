---
title: Visual Basic 中的運算子優先順序
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d8de9deea84c7f0c11c91b55951cdfc200b017f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的運算子優先順序
每個組件時數個作業發生時在運算式中，評估，而且在呼叫預先定義的順序解決*運算子優先順序*。  
  
## <a name="precedence-rules"></a>優先順序規則  
 當運算式包含來自多個類別目錄的運算子時，它們會根據下列規則進行評估：  
  
-   算術和串連運算子具有的優先順序在下一節中所述，而且全都有更高的優先順序高於比較、 邏輯和位元運算子。  
  
-   所有比較運算子都有相同的優先順序，以及所有都具有較高的優先順序高於邏輯和位元運算子，但較低的優先順序高於算術和串連運算子。  
  
-   邏輯和位元運算子具有的優先順序在下一節中所述，而且全都有較低的優先順序高於算術、 串連運算子和比較運算子。  
  
-   具有相同優先順序的運算子會由左至右評估的運算式中出現的順序。  
  
## <a name="precedence-order"></a>優先順序  
 運算子會評估順序的優先順序如下：  
  
### <a name="await-operator"></a>Await 運算子  
 await  
  
### <a name="arithmetic-and-concatenation-operators"></a>算術運算子和串連運算子  
 乘冪 (`^`)  
  
 一元身分識別和否定 (`+`， `–`)  
  
 乘法和除法浮點 (`*`， `/`)  
  
 整數除法 (`\`)  
  
 模數算術 (`Mod`)  
  
 加法和減法 (`+`， `–`)  
  
 字串串連 (`&`)  
  
 算術的位元移位 (`<<`， `>>`)  
  
### <a name="comparison-operators"></a>比較運算子  
 所有比較運算子 (`=`， `<>`， `<`， `<=`， `>`， `>=`， `Is`， `IsNot`， `Like`， `TypeOf`...`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>邏輯和位元運算子  
 否定 (`Not`)  
  
 搭配使用 (`And`， `AndAlso`)  
  
 內含分離 (`Or`， `OrElse`)  
  
 排除分離 (`Xor`)  
  
### <a name="comments"></a>註解  
 `=`運算子只是等號比較運算子，不是指派運算子。  
  
 字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。  
  
 `Is`和`IsNot`運算子都是物件參考的比較運算子。 不會比較兩個物件的值他們檢查只是用來判斷兩個物件變數是否參考相同的物件執行個體。  
  
## <a name="associativity"></a>順序關聯性  
 相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估為遇到它從左到右每一項作業。 下列範例將說明這點。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 第一個運算式會評估除法 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。 因為編譯器會評估為作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。 同時`n1`和`n2`有三個結果。 相反地，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。  
  
 基於此行為，運算子可視為是*左向關聯*在 Visual Basic 中。  
  
## <a name="overriding-precedence-and-associativity"></a>覆寫優先順序和關聯性  
 您可以使用括號強制其他項目之前，在評估運算式的某些部分。 優先順序和左順序關聯性，也可以覆寫。 Visual Basic 一定會執行之前以外的括號括住的作業。 不過，在括號，它仍保留一般優先順序和關聯性，除非您使用括號括號內。 下列範例將說明這點。  
  
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
 [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md)  
 [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Await 運算子](../../../visual-basic/language-reference/operators/await-operator.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
