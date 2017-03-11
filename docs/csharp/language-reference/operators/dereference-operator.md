---
title: "-&gt; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "->_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-> 運算子 [C#]"
  - "成員存取運算子 (->) [C#]"
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# -&gt; 運算子 (C# 參考)
`->` 運算子結合了指標取值和成員存取。  
  
## 備註  
 這種形式的運算式，  
  
```  
x->y  
```  
  
 \(其中 `x` 為 `T*` 型別的指標，而 `y` 為 `T` 的成員\) 相等於  
  
```  
(*x).y  
```  
  
 `->` 運算子只能在標示為 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的程式碼中使用。  
  
 `->` 運算子無法多載。  
  
## 範例  
 [!code-cs[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#15)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)