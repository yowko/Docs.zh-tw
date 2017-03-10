---
title: "&lt; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "< 運算子 [C#]"
  - "小於運算子 (<) [C#]"
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# &lt; 運算子 (C# 參考)
所有的數字和列舉型別都定義了「小於」的關係運算子 \(`<`\)，當第一個運算元小於第二個運算元時會傳回 `true`；否則傳回 `false`。  
  
## 備註  
 使用者定義型別可多載 `<` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  如果多載 `<`，則也必須多載 [\>](../../../csharp/language-reference/operators/greater-than-operator.md)。  當多載二元 \(Binary\) 運算子時，同時隱含多載其對應的指派運算子 \(若有的話\)。  
  
## 範例  
 [!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#24)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)