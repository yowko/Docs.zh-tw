---
title: "If Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.IfOperator"
  - "IfOperator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ternary operators"
  - "conditional execution"
  - "If expressions [Visual Basic]"
  - "conditional operator [Visual Basic]"
  - "If Operator [Visual Basic]"
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# If Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

使用最少運算評估，有條件地傳回兩個值的其中一個。  `If` 運算子可以使用三個引數或兩個引數來進行呼叫。  
  
## 語法  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## 用三個引數呼叫 If 運算子  
 當使用三個引數呼叫 `If` 時，第一個引數必須評估為可轉換成 `Boolean` 的值。  該 `Boolean` 值會判斷要評估並傳回其餘兩個值中的哪一個。  使用三個引數呼叫 `If` 運算子時，適用下列清單。  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`argument1`|必要項。  `Boolean`.  判斷要評估及傳回哪一個剩下的引數。|  
|`argument2`|必要項。  `Object`.  如果 `argument1` 評估為 `True` 則加以評估及傳回。|  
|`argument3`|必要項。  `Object`.  評估並傳回 if `argument1`評估為`False`或`argument1`是 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean`變數，其值為[執行任何動作](../../../visual-basic/language-reference/nothing.md)。|  
  
 使用三個引數呼叫的 `If` 運算子，其作業方式類似 `IIf` 函式，不同的是前者使用最少運算評估。  `IIf` 函式一律會評估全部三個引數，而具有三個引數的 `If` 運算子則只會評估其中兩個。  評估第一個 `If` 引數後，結果會轉換為 `Boolean` 值：`True` 或 `False`。  如果值為 `True`，則評估`argument2` 並傳回其值，但是不會評估 `argument3`。  如果 `Boolean` 運算式的值為 `False`，則會評估 `argument3` 並傳回其值，但是不會評估 `argument2`。  下列範例說明使用三個引數時 `If` 的用法：  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 下列範例說明最少運算評估的值。  範例顯示除了 `divisor` 為零以外，將變數 `number` 除以變數 `divisor` 的兩次嘗試。  若除數為零則應傳回 0，且不應嘗試執行除法，因為會產生執行階段錯誤。  因為 `If` 運算式使用最少運算評估，因此會根據第一個引數的值決定是要評估第二個還是第三個引數。  如果第一個引數為 True，且除數不是零，則可安全評估第二個引數並執行除法。  如果第一個引數為 False，則只會評估第三個引數且傳回 0。  因此，當除數是 0 時，就不會嘗試執行除法，也不會產生錯誤。  而因為 `IIf` 不是使用最少運算評估，所以即使第一個引數為 False，還是會評估第二個引數。  這樣就會造成執行階段的除以零錯誤。  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## 用兩個引數呼叫 If 運算子  
 可以略過 `If` 的第一個引數。  這樣可以只使用兩個引數呼叫運算子。  使用兩個引數呼叫 `If` 運算子時，適用下列清單。  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`argument2`|必要項。  `Object`.  必須是參考或可為 Null 的型別。  當評估為 `Nothing` 以外的值時，進行評估及傳回。|  
|`argument3`|必要項。  `Object`.  如果 `argument2` 評估為 `Nothing` 則加以評估及傳回。|  
  
 當略過 `Boolean` 引數時，第一個引數必須是參考或可為 Null 的型別。  如果第一個引數評估為 `Nothing`，會傳回第二個引數的值。  在所有其他情況下，會傳回第一個引數的值。  下列範例說明此項評估如何運作。  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)