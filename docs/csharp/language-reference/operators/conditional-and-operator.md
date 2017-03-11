---
title: "&amp;&amp; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "&& 運算子 [C#]"
  - "邏輯 AND 運算子 [C#]"
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# &amp;&amp; 運算子 (C# 參考)
AND 條件運算子 \(`&&`\) 會對其 `bool` 運算元執行 AND 邏輯運算，但只有在需要時才會評估第二個運算元。  
  
## 備註  
 運算  
  
```  
x && y  
```  
  
 對應到這項運算  
  
```  
x & y  
```  
  
 但是，如果`x` 是`false`， `y`則不評估，因為 AND 運算的結果是`false`無論何種值的`y` 是。  這就是所謂的「最少運算」\(Short\-Circuit\) 評估。  
  
 AND 條件運算子無法多載，但是在特定限制下，標準邏輯運算子與 [true](../../../csharp/language-reference/keywords/true.md) 和 [false](../../../csharp/language-reference/keywords/false.md) 運算子的多載，也視為條件邏輯運算子的多載。  
  
## 範例  
 在下列範例中，在第二個條件式運算式`if`陳述式只評估了第一個運算元運算元回傳因為`false`。  
  
 [!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#48)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)