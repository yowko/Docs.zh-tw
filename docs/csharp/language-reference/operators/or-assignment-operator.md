---
title: "|= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "|= 運算子 (OR 指派) [C#]"
  - "OR 指派運算子 (|=) [C#]"
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# |= 運算子 (C# 參考)
OR 指派運算子。  
  
## 備註  
 使用 `|=` 指派運算子的運算式，例如：  
  
```  
x |= y  
```  
  
 相等於  
  
```  
x = x | y  
```  
  
 不同的是，`x` 只被評估了一次。  [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md)會對整數運算元執行位元邏輯 OR 運算，會對 bool 運算元執行邏輯 OR 運算。  
  
 `|=` 運算子無法直接多載，但使用者定義型別可多載 [&#124; 運算子](../../../csharp/language-reference/operators/or-operator.md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)