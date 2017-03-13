---
title: "How to: Test Whether Two Objects Are the Same (Visual Basic) | Microsoft Docs"
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
  - "variables [Visual Basic], reference"
  - "Is operator [Visual Basic], comparing objects"
  - "reference variables"
  - "variables [Visual Basic], referring to same object"
  - "objects [Visual Basic], variables referring to same"
  - "Visual Basic code, operators"
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Test Whether Two Objects Are the Same (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果您有兩個變數會參考物件，則可以使用 `Is` 或 `IsNot` 運算子 \(或同時使用\)，判斷這些變數是否參考同一個執行個體。  
  
### 若要測試兩個物件是否相同  
  
-   將這兩個變數當做運算元使用 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) 或 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)。  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 您可能想要視兩個物件是否參考同一個執行個體，採取特定的動作。  上述範例會比較控制項 `c` 與表單 `f` 上的使用中控制項。  如果沒有使用中控制項，或如果有使用中控制項但不是 `c` 的同一個控制項執行個體，則 `If` 陳述式 \(Statement\) 會失敗，並且程序會返回而不做進一步處理。  
  
 使用 `Is` 還是 `IsNot` 全視您個人方便。  在指定的運算式中，一個陳述式可能會比另一個容易讀取。  
  
## 請參閱  
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)