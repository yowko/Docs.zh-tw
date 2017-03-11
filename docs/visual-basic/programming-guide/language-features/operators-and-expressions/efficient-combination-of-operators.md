---
title: "Efficient Combination of Operators (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressions [Visual Basic], parentheses"
  - "operators [Visual Basic], associativity"
  - "expressions [Visual Basic], operators"
  - "operators [Visual Basic], precedence"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "operators [Visual Basic], complex expressions"
  - "expressions [Visual Basic], complex"
  - "parentheses, complex expressions"
  - "numeric expressions"
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Efficient Combination of Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

複雜的運算式可包含許多不同的運算子。  下列範例將說明這點。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 建立複雜運算式 \(如前一個範例中的複雜運算式\) 需要徹底了解運算子優先順序 \(Operator Precedence\) 的規則。  如需詳細資訊，請參閱 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## 括號內的運算式  
 通常您會想要以不同於運算子優先順序所決定的順序進行運算。  參考下列範例：  
  
 `x = z * y + 4`  
  
 前一個範例會將 `z` 乘以 `y`，然後將結果與 `4` 相加。  但是，如果想要 `y` 與 `4` 先相加，再將結果乘以 `z`，您可以使用括號覆寫一般運算子優先順序。  藉由用括號將運算式括住，您可以強制先計算該運算式，而不管運算子優先順序。  若要強制上述範例先執行加法，您可以將它重寫，如下列範例所示。  
  
 `x = z * (y + 4)`  
  
 前一個範例會將 `y` 與 `4` 相加，然後將該總和乘以 `z`。  
  
### 巢狀括號運算式  
 您可以巢狀方式將運算式放在多層括號中，以進一步覆寫優先順序。  括號中最裡層巢狀的運算式會最先計算，接著是次裡層的巢狀，依此類推直到最外層的巢狀，最後計算括號外的運算式。  下列範例將說明這點。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在上述範例中，會最先計算 `z + 2`，接著是其他括號運算式。  乘冪運算通常具有比加法或乘法更高的優先順序，但是在本範例中，因為其他的運算式都是放在括號內，所以會最後計算乘冪運算。  
  
## 請參閱  
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)