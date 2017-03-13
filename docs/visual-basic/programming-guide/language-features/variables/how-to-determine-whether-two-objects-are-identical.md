---
title: "How to: Determine Whether Two Objects Are Identical (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "testing, objects"
  - "objects [Visual Basic], comparing"
  - "object variables, determining identity"
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Determine Whether Two Objects Are Identical (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

如果兩個物件的指標相同 \(也就是說，如果這兩個變數指向記憶體內的相同類別執行個體\)，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就會將這兩個變數參考視為相同的物件。  例如，在 Windows Forms 應用程式中，您可能會想要進行比較，藉此判斷目前的執行個體 \(`Me`\) 和特定執行個體 \(如 `Form2`\) 是否相同。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供兩種運算子來比較指標。  如果物件相同，[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) 會傳回 `True`；如果物件不相同，則 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) 會傳回 `True`。  
  
## 判斷兩個物件是否相同  
  
#### 若要判斷兩個物件是否相同  
  
1.  設定 `Boolean` 運算式來測試兩個物件。  
  
2.  在測試運算式中，使用 `Is` 運算子，並將兩個物件當做運算元。  
  
     如果這兩個物件指向相同的類別執行個體，則 `Is` 就會傳回 `True`。  
  
## 判斷兩個物件是否不同  
 有時候您想在兩個物件不同時執行動作，但是將 `Not` 和 `Is` 一起使用並不方便，例如 `If Not obj1 Is obj2`。  此時可以使用 `IsNot` 運算子。  
  
#### 若要判斷兩個物件是否不同  
  
1.  設定 `Boolean` 運算式來測試兩個物件。  
  
2.  在測試運算式中，使用 `IsNot` 運算子，並將兩個物件當做運算元。  
  
     如果這兩個物件沒有指向相同的類別執行個體，則 `IsNot` 就會傳回 `True`。  
  
## 範例  
 下列範例會測試各對 `Object` 變數，藉此檢查這些物件是否指向相同的類別執行個體。  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 上述範例會顯示下列輸出。  
  
 `objA different from objB?  True`  
  
 `objA identical to objC?  True`  
  
## 請參閱  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)