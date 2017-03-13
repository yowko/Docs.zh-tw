---
title: "/ Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb./"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, floating point"
  - "floating-point numbers, division operator"
  - "slash (/) operator"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "arithmetic operators, division"
  - "division, by zero"
  - "operators [Visual Basic], division"
  - "division operator, syntax"
  - "/ operator [Visual Basic]"
  - "math operators"
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# / Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

兩數相除並傳回浮點結果。  
  
## 語法  
  
```  
  
expression1 / expression2  
```  
  
## 組件  
 `expression1`  
 必要項。  任何數值運算式。  
  
 `expression2`  
 必要項。  任何數值運算式。  
  
## 支援類型  
 所有數字型別，包括不帶正負號和浮點型別，以及 `Decimal`。  
  
## 結果  
 結果是 `expression1` 除以 `expression2` 的完整商數 \(包括任何餘數\)。  
  
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) 會傳回整數商數 \(捨棄餘數\)。  
  
## 備註  
 結果的資料型別視運算元的型別而定。  下表顯示結果資料型別的決定方式。  
  
|運算元資料型別|結果資料型別|  
|-------------|------------|  
|這兩個運算式都是整數類資料型別 \(Integral Type\) \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\)|`Double`|  
|一個運算式為 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) 資料型別，另一個不是 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|一個運算式為 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) 資料型別，另一個不是 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) 或 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|任一運算式可以是 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) 資料型別|`Double`|  
  
 在執行除法之前，會將任何整數數值運算式擴展成 `Double`。  如果將結果指派給整數類資料型別，則 Visual Basic 會嘗試將結果從 `Double` 轉換成該型別。  如果結果不適合該型別，則這會擲回例外狀況。  尤其，請參閱此說明網頁上「嘗試以零為除數」的部分。  
  
 如果 `expression1` 或 `expression2` 評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，即視為零。  
  
## 嘗試以零為除數  
 如果 `expression2` 評估為零，則 `/` 運算子對於不同運算元資料型別會有不同的行為。  下表顯示可能的行為。  
  
|運算元資料型別|`expression2` 為零時的行為|  
|-------------|--------------------------|  
|浮點數 \(`Single` 或 `Double`\)|傳回無限大 \(<xref:System.Double.PositiveInfinity> 或 <xref:System.Double.NegativeInfinity>\)，如果 `expression1` 也是零，則傳回 <xref:System.Double.NaN> \(非數字\)|  
|`Decimal`|擲回 <xref:System.DivideByZeroException>|  
|整數類 \(帶正負號或不帶正負號\)|嘗試轉換回整數類資料型別 \(Integral Type\) 會擲回 <xref:System.OverflowException>，因為整數類資料型別無法接受 <xref:System.Double.PositiveInfinity>、<xref:System.Double.NegativeInfinity> 或 <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 這個範例會使用 `/` 運算子來執行浮點除法。  結果是兩個運算元的商數。  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 上述範例中的運算式會傳回值 2.5 和 3.333333。  請注意，即使這兩個運算元都是整數常數，結果一律為浮點數 \(`Double`\)。  
  
## 請參閱  
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)