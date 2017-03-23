---
title: "OrElse Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "OrElse"
  - "vb.OrElse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "short-circuiting"
  - "operators [Visual Basic], short-circuiting"
  - "operators [Visual Basic], disjunction"
  - "short-circuit evaluation"
  - "OrElse operator [Visual Basic]"
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# OrElse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

對兩個運算式執行最少運算 \(Short\-Circuiting\) 內含邏輯分離 \(Logical Disjunction\)。  
  
## 語法  
  
```  
  
result = expression1 OrElse expression2  
```  
  
## 組件  
 `result`  
 必要項。  任何 `Boolean` 運算式。  
  
 `expression1`  
 必要項。  任何 `Boolean` 運算式。  
  
 `expression2`  
 必要項。  任何 `Boolean` 運算式。  
  
## 備註  
 若已編譯的程式碼依其他運算式的結果，能略過運算式的評估，則邏輯運算式就稱為「*最少運算*」\(Short\-Circuiting\)。  若所評估之第一個運算式的結果會決定運算的最終結果，則不需評估第二個運算式，因其無法改變最終結果。  若略過的是複雜或包含程序呼叫的運算式，則最少運算便可以提升效能。  
  
 如果兩個運算式的任一個或兩者都評估為 `True`，則 `result` 為 `True`。  下表說明如何決定 `result`。  
  
|如果 `expression1` 為|且 `expression2` 是|`result` 的值為|  
|------------------------|-----------------------|------------------|  
|`True`|\(不評估\)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## 資料型別  
 `OrElse` 運算子只針對 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) 定義。  Visual Basic 會在必要時將每個運算元轉換成 `Boolean`，並且完全以 `Boolean` 執行運算。  若將結果指派給數字型別，Visual Basic 就會將它從 `Boolean` 轉換成該型別。  這可能會產生未預期的行為。  例如，轉換成 `Integer` 時，`5 OrElse 12` 會導致 `–1`。  
  
## 多載化  
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) 和 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  多載 `Or` 和 `IsTrue` 運算子會影響 `OrElse` 運算子的行為。  如果您的程式碼在多載 `Or` 和 `IsTrue` 之類別或結構上會使用 `OrElse`，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例會使用 `OrElse` 運算子，對兩個運算式執行邏輯分離。  結果是代表兩個運算式的任一項是否為 True 的 `Boolean` 值。  如果第一個運算式為 `True`，則不評估第二個運算式。  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 前一個範例分別產生 `True`、`True` 和 `False` 的結果。  在計算 `firstCheck` 時，不會評估第二個運算式，因為第一個運算式已經為 `True`。  不過，在計算 `secondCheck` 時會評估第二個運算式。  
  
## 範例  
 下列範例顯示包含兩個程序呼叫的 `If`...`Then` 陳述式。  如果第一個呼叫傳回 `True`，就不會呼叫第二個程序。  如果第二個程序執行了當這個程式碼區段執行時應一律執行的重要工作，這可能會產生無法預期的結果。  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## 請參閱  
 [Logical\/Bitwise Operators](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)