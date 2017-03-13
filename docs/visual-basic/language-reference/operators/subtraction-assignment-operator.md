---
title: "\= Operator | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "\="
  - "vb.\="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "\= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator \= [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# \= Operator
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

將變數或屬性 \(Property\) 的值除以運算式的值，然後將整數結果指派給變數或屬性。  
  
## 語法  
  
```  
  
variableorproperty \= expression  
```  
  
## 組件  
 `variableorproperty`  
 必要項。  任何數字變數或屬性。  
  
 `expression`  
 必要項。  任何數值運算式。  
  
## 備註  
 位於 `\=` 運算子左邊的項目可以是簡單的純量 \(Scalar\) 變數、屬性或陣列元素。  變數或屬性不能為 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `\=`運算子將變數或屬性，它左邊的值，其右邊的值，並將整數結果指派給變數或屬性在其左邊  
  
 如需整數除法的詳細資訊，請參閱 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)。  
  
## 多載化  
 `\` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `\` 運算子會影響 `\=` 運算子的行為。  如果您的程式碼在多載 `\` 之類別或結構上使用 `\=`，就一定要先了解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `\=` 運算子，將一個 `Integer` 變數除以第二個變數，並且將整數結果指派給第一個變數。  
  
 [!code-vb[VbVbalrOperators#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## 請參閱  
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)