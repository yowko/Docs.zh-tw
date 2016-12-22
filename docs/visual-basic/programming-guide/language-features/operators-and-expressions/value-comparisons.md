---
title: "Value Comparisons (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], comparing values"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "comparison operators, comparing expressions"
  - "numeric expressions"
  - "operators [Visual Basic], comparison"
  - "expressions [Visual Basic], comparing"
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Value Comparisons (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

比較運算子可用來建構比較數值變數值的運算式。  這些運算式會根據比較結果是否為 True 或 False 來傳回 `Boolean` 值。  以下為這類運算式的範例。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 第一個運算式評估為 `True`，因為 45 大於 26。  第二個運算式評估為 `False`，因為 26 沒有大於 45。  
  
 您也可以使用此方式比較數值運算式。  要進行比較的運算式本身可能是複雜的運算式，如下列範例所示。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 前面複雜的運算式包括常值 \(Literal\)、變數及函式呼叫 \(Function Call\)。  比較運算子兩邊的運算式都會經過評估，然後使用 `>=` 比較運算子比較結果值。  如果左邊的運算式值大於或等於右邊的運算式值，則整個運算式會評估為 `True`，否則，評估為 `False`。  
  
 比較數值的運算式最常用於 `If...Then` 語法結構中，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=` 符號是比較運算子及指派運算子。  做為比較運算子使用時，它會評估左邊的值是否等於右邊的值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 您也可在任何需要 `Boolean` 值的地方使用比較運算式 \(例如，在 `If`、`While`、`Loop` 或 `ElseIf` 陳述式中\)，或是在將值指派或傳送至 `Boolean` 變數時使用比較運算式。  在下列範例中，會將比較運算式傳回的值指派給 `Boolean` 變數。  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## 請參閱  
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)