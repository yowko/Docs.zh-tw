---
title: "在 Visual Basic 中的運算子優先順序 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6532fc0c26db3b736c863be075571570a3d25eef
ms.lasthandoff: 03/13/2017

---
# <a name="operator-precedence-in-visual-basic"></a>Visual Basic 中的運算子優先順序
每個部分數個作業發生時在運算式中，評估並解決在預先定義的順序呼叫*運算子優先順序*。  
  
## <a name="precedence-rules"></a>優先順序規則  
 當運算式包含運算子，從多個類別時，會評估根據下列規則︰  
  
-   算術和串連運算子有下列的一節所述的優先順序，而且全都有更高的優先順序高於比較、 邏輯和位元運算子。  
  
-   所有比較運算子優先順序都都相同，且只需要較高的優先順序高於邏輯和位元運算子，但低於算術和串連運算子。  
  
-   邏輯和位元運算子有下列的一節所述的優先順序，而且全都有較低的優先順序高於算術、 串連運算子和比較運算子。  
  
-   具有相同優先順序的運算子會向左到右評估運算式中出現的順序。  
  
## <a name="precedence-order"></a>優先順序  
 運算子會依下列優先順序進行評估︰  
  
### <a name="await-operator"></a>Await 運算子  
 Await  
  
### <a name="arithmetic-and-concatenation-operators"></a>算術和串連運算子  
 乘冪 (`^`)  
  
 一元識別和否定 (`+`， `–`)  
  
 乘法和除法浮點數 (`*`， `/`)  
  
 整數除法 (`\`)  
  
 模數算術 (`Mod`)  
  
 加法和減法 (`+`， `–`)  
  
 字串串連 (`&`)  
  
 算術的位元移位 (`<<`， `>>`)  
  
### <a name="comparison-operators"></a>比較運算子  
 All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)  
  
### <a name="logical-and-bitwise-operators"></a>邏輯和位元運算子  
 否定 (`Not`)  
  
 搭配使用 (`And`， `AndAlso`)  
  
 內含分離 (`Or`， `OrElse`)  
  
 排除分離 (`Xor`)  
  
### <a name="comments"></a>註解  
 `=`運算子只是等號比較運算子，指派運算子。  
  
 字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。  
  
 `Is`和`IsNot`運算子是物件參考的比較運算子。 它們不會比較兩個物件的值這些檢查只是為了確定是否兩個物件變數參考相同物件執行個體。  
  
## <a name="associativity"></a>順序關聯性  
 相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估為遇到它從左到右每項作業。 下列範例將說明這點。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 第一個運算式會評估除法 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。 因為編譯器會判斷值為作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。 同時`n1`和`n2`有三個結果。 相較之下，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。  
  
 基於此行為，運算子可以說是*左向*中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
## <a name="overriding-precedence-and-associativity"></a>覆寫優先順序和順序關聯性  
 您可以使用括號強制優先評估運算式的某些部分。 優先順序和左順序關聯性，也可以覆寫。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]永遠執行之前以外的括號括住的作業。 不過，在括號括住，它會維護一般優先順序和關聯性，除非您使用括號括號內。 下列範例將說明這點。  
  
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
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
