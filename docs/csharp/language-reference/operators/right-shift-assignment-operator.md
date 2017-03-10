---
title: "&gt;&gt;= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - ">>=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">>= 運算子 (右移指派) [C#]"
  - "右移指派運算子 (>>=) [C#]"
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# &gt;&gt;= 運算子 (C# 參考)
右移 \(Right Shift\) 指派運算子。  
  
## 備註  
 這種形式的運算式  
  
```  
x >>= y  
```  
  
 將評估為  
  
```  
x = x >> y  
```  
  
 不同的是，`x` 只被評估了一次。  [\>\> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md)將 `x` 向右移 `y` 所指定的量。  
  
 \>\>\= 運算子無法直接多載，但使用者定義型別可多載 [\>\> 運算子](../../../csharp/language-reference/operators/right-shift-operator.md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#11)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)