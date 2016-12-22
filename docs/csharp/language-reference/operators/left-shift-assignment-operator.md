---
title: "&lt;&lt;= 運算子 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
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
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;&lt;= 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
  
 不同的是，`x` 只被評估了一次。  [\<\< 運算子](../Topic/%3C%3C%20Operator%20\(C%23%20Reference\).md)將 `x` 向左移動 `y` 所指定的位元數。  
  
 `<<=` 運算子不可直接被多載，但使用者定義的型別可多載 [\<\< 運算子](../Topic/%3C%3C%20Operator%20\(C%23%20Reference\).md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)