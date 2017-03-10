---
title: "* Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.*"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, multiplication"
  - "operators [Visual Basic], multiplication"
  - "* operator [Visual Basic]"
  - "multiplication operator, syntax"
  - "math operators"
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# * Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將兩個數值相乘。  
  
## 語法  
  
```  
  
number1 * number2  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`number1`|必要項。  任何數值運算式。|  
|`number2`|必要項。  任何數值運算式。|  
  
## 結果  
 結果是 `number1` 與 `number2` 的乘積。  
  
## 支援類型  
 所有數字型別，包括不帶正負號和浮點型別，以及 `Decimal`。  
  
## 備註  
 結果的資料型別視運算元的型別而定。  下表顯示結果資料型別的決定方式。  
  
|||  
|-|-|  
|運算元資料型別|結果資料型別|  
|這兩個運算式都是整數類資料型別 \(Integral Type\) \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\)|`number1` 和 `number2` 的資料型別都適用的數值資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」表。|  
|兩邊的運算式都是 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|兩邊的運算式都是 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|其中一個運算式是浮點數資料型別 \(`Single` 或 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)\)，但並非兩者都是 `Single` \(請注意，`Decimal` 不是浮點數資料型別\)|`Double`|  
  
 如果運算式評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，即視為零。  
  
## 多載化  
 `*` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 這個範例會使用 `*` 運算子，將兩個數值相乘。  結果是兩個運算元的乘積。  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/multiplication-operator_1.vb)]  
  
## 請參閱  
 [\*\= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)