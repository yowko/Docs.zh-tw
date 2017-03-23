---
title: "|| 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "||_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|| 運算子 [C#]"
  - "條件 OR 運算子 (||) [C#]"
  - "邏輯 OR 運算子 [C#]"
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# || 運算子 (C# 參考)
OR 條件運算子 \(\)`||`執行邏輯 OR 其 `bool` 運算元。  如果第一個運算元評估為 `true`，第二個運算元不會評估。  如果第一個運算元評估為 `false`，第二個運算子判斷或整個運算式是否可以評估為 `true` 或 `false`。  
  
## 備註  
 運算  
  
```  
x || y  
```  
  
 對應到這項運算  
  
```  
x | y  
```  
  
 但是，如果 `x` 是 `true`， `y` 不會評估 `y`，不論的值，因為或作業是 `true` 。  這個概念稱為「最少運算評估」。  
  
 OR 條件運算子無法多載，不過，標準邏輯運算子 [true](../../../csharp/language-reference/keywords/true.md) 和 [錯誤](../../../csharp/language-reference/keywords/false.md) 和運算子的多載，有某些限制，也視為條件邏輯運算子的多載。  
  
## 範例  
 在下列範例中，使用的 `||` 運算式只評估第一個運算元。  使用的運算式 `|`評估的兩個運算元。  在第二個範例中，則為，如果兩個運算元都評估為，則會產生執行階段例外狀況時發生。  
  
 [!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)