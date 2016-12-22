---
title: "- Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.Negate"
  - "vb.-"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "- operator [Visual Basic]"
  - "operators [Visual Basic], subtraction"
  - "operators [Visual Basic], difference"
  - "negation operator"
  - "operators [Visual Basic], arithmetic"
  - "subtraction operator, syntax"
  - "arithmetic operators, subtraction"
  - "difference operator"
  - "math operators"
  - "operators [Visual Basic], negation"
  - "minus operator [Visual Basic]"
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# - Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

傳回兩個數值運算式之間的差異，或數值運算式的負值。  
  
## 語法  
  
```  
  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## 組件  
 `expression1`  
 必要項。  任何數值運算式。  
  
 `expression2`  
 除非 `–` 運算子計算的是負值，否則為必要項。  任何數值運算式。  
  
## 結果  
 結果是 `expression1` 與 `expression2` 之間的差異，或 `expression1` 之相反的值。  
  
 結果資料型別會是數字型別，適用於 `expression1` 和 `expression2` 的資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」表。  
  
## 支援類型  
 所有數字型別 \(Numeric Type\)。  這包括不帶正負號和浮點型別，以及 `Decimal`。  
  
## 備註  
 在先前語法的第一個使用方式中，`–` 運算子是兩個數值運算式間之差異的「*二進位*」\(Binary\) 算術減法運算子。  
  
 在先前語法的第二個使用方式中，`–` 運算子是運算式之負值的「*一元*」\(Unary\) 負運算子。  在這種情況下，負運算即表示會反轉 `expression1` 的正負號，因此，如果 `expression1` 為負，則結果就是正數。  
  
 若運算式評估為 [Nothing](../../../visual-basic/language-reference/nothing.md)，`–`運算子會將其視為零。  
  
> [!NOTE]
>  `–` 運算子可以「*多載*」\(Overload\)，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，請確定了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `–` 運算子，來計算和傳回兩個數字間的差異，然後反轉數字的正負號。  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 遵循這些陳述式的執行，`binaryResult` 會包含 124.45，`unaryResult` 則包含 –334.90。  
  
## 請參閱  
 [\-\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)