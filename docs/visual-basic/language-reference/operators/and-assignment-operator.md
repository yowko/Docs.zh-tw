---
title: "&amp;= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.&="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator &="
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "&= operator [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# &amp;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將 `String` 運算式串連到 `String` 變數或屬性 \(Property\)，然後將結果指派給變數或屬性。  
  
## 語法  
  
```  
  
variableorproperty &= expression  
```  
  
## 組件  
 `variableorproperty`  
 必要項。  任何 `String` 變數或屬性。  
  
 `expression`  
 必要項。  任何 `String` 運算式。  
  
## 備註  
 位於 `&=` 運算子左邊的項目可以是簡單的純量 \(Scalar\) 變數、屬性或陣列元素。  變數或屬性不能為 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  `&=`運算子串連`String`右邊的運算式`String`變數或屬性，它的左邊，並將結果指派給變數或它左邊的屬性。  
  
## 多載化  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) 可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `&` 運算子會影響 `&=` 運算子的行為。  如果您的程式碼在多載 `&` 之類別或結構上使用 `&=`，就一定要先了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `&=` 運算子，來串連兩個 `String` 變數，並將結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/and-assignment-operator_1.vb)]  
  
## 請參閱  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)