---
title: "\ Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.\"
  - "\"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, integer"
  - "integer division operator"
  - "zero, division by zero"
  - "arithmetic operators, division"
  - "division, by zero"
  - "backslash (\) [Visual Basic]"
  - "\ operator [Visual Basic]"
  - "integer quotient"
  - "math operators"
  - "quotients, integer"
  - "truncation, integer division"
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# \ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

兩數相除並傳回整數結果。  
  
## 語法  
  
```  
  
expression1 \ expression2  
```  
  
## 組件  
 `expression1`  
 必要項。  任何數值運算式。  
  
 `expression2`  
 必要項。  任何數值運算式。  
  
## 支援類型  
 所有數字型別，包括不帶正負號和浮點型別，以及 `Decimal`。  
  
## 結果  
 結果是 `expression1` 除以 `expression2` 的整數商數，這會捨棄任何餘數而只保留整數部分。  這稱為「*截斷*」。  
  
 結果資料型別會是數字型別，適用於 `expression1` 和 `expression2` 的資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」表。  
  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) 會傳回完整商數 \(其保留小數部分的餘數\)。  
  
## 備註  
 在執行除法之前，Visual Basic 會嘗試將任何浮點數值運算式轉換成 `Long`。  如果 `Option Strict` 為 `On`，則會發生編譯器錯誤。  如果 `Option Strict` 為 `Off`，則值在 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md) 的範圍之外時，可能會發生 <xref:System.OverflowException>。  轉換成 `Long` 也就是「*Banker's Rounding\)*」\(四捨六入五成雙。  如需詳細資訊，請參閱[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)中「小數部分」的部分。  
  
 如果 `expression1` 或 `expression2` 評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，即視為零。  
  
## 嘗試以零為除數  
 如果 `expression2` 評估為零，則 `\` 運算子會擲回 <xref:System.DivideByZeroException> 例外狀況。  這對運算元的所有數字資料型別而言都為 true。  
  
> [!NOTE]
>  `\` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例使用 `\` 運算子來執行整數除法。  結果是代表兩個運算元之整數商數的整數 \(捨棄餘數\)。  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 上述範例中的運算式會分別傳回值 2、3、33 和 \-22。  
  
## 請參閱  
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)