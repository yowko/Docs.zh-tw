---
title: "&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39; | Microsoft Docs"
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
  - "bc30020"
  - "vbc30020"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30020"
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Is` 比較運算子會判斷兩個物件變數是否參考相同的執行個體。  此項比較不是為實值型別而定義的。  
  
 **錯誤 ID︰**BC30020  
  
### 若要更正這個錯誤  
  
-   使用適當的算術比較運算子或 `Like` 運算子，比較兩種實值型別。  
  
## 請參閱  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [Comparison Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)