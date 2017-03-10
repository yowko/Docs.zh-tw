---
title: "*= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "*=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "*= 運算子 [C#]"
  - "二進位乘法指派運算子 (*=) [C#]"
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# *= 運算子 (C# 參考)
二元 \(Binary\) 乘法指派運算子。  
  
## 備註  
 使用 `*=` 指派運算子的運算式，例如  
  
```  
x *= y  
```  
  
 相等於  
  
```  
x = x * y  
```  
  
 不同的是，`x` 只被評估了一次。  [\* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md)已為數字型別預先定義來執行乘法。  
  
 `*=` 運算子無法直接被多載，但使用者定義型別可多載 [\* 運算子](../../../csharp/language-reference/operators/multiplication-operator.md) \(請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#13)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)