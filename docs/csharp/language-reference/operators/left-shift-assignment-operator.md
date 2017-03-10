---
title: "&lt;&lt;= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<<= 運算子 (左移指派) [C#]"
  - "左移指派運算子 (<<=) [C#]"
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &lt;&lt;= 運算子 (C# 參考)
左移 \(Left Shift\) 指派運算子。  
  
## 備註  
 這種形式的運算式  
  
```  
x <<= y  
```  
  
 將評估為  
  
```  
x = x << y  
```  
  
 不同的是，`x` 只被評估了一次。  [\<\< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md)將 `x` 向左移動 `y` 所指定的位元數。  
  
 `<<=` 運算子不可直接被多載，但使用者定義的型別可多載 [\<\< 運算子](../../../csharp/language-reference/operators/left-shift-operator.md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#12)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)