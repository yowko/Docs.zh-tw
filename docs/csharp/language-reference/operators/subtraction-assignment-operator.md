---
title: "/= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/= (除法指派運算子) [C#]"
  - "除法指派運算子 (/=) [C#]"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# /= 運算子 (C# 參考)
除法指派運算子。  
  
## 備註  
 使用 `/=` 指派運算子的運算式，例如：  
  
```  
x /= y  
```  
  
 相等於  
  
```  
x = x / y  
```  
  
 不同的是，`x` 只被評估了一次。  [\/ 運算子](../../../csharp/language-reference/operators/division-operator.md)已為數字型別預先定義來執行除法。  
  
 `/=` 運算子無法直接多載，但使用者定義型別可多載 [\/ 運算子](../../../csharp/language-reference/operators/division-operator.md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  在所有複合指派運算子上，多載二元運算子即隱含多載對等的複合指派。  
  
## 範例  
 [!code-cs[csRefOperators#5](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#5)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)