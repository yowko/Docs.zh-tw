---
title: "-= 運算子 (C# 參考) | Microsoft Docs"
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
  - "-=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-= 運算子 (減法指派) [C#]"
  - "減法指派運算子 (-=) [C#]"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# -= 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

減法指派運算子。  
  
## 備註  
 使用 `-=` 指派運算子的運算式，例如  
  
```  
x -= y  
```  
  
 相等於  
  
```  
x = x - y  
```  
  
 不同的是，`x` 只被評估了一次。  [\- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md)的意義，與 `x` 和 `y` 的型別有關 \(數字運算元會相減，委派運算元會移除委派等等\)。  
  
 `-=` 運算子無法直接被多載，但使用者定義的型別可多載 [\- 運算子](../../../csharp/language-reference/operators/subtraction-operator.md) \(請參閱 [運算子](../../../csharp/language-reference/keywords/operator.md)\)。  
  
 \-\= 運算子也可以用於 C\# 中以取消訂閱事件。  如需詳細資訊，請參閱 [如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。  
  
## 範例  
 [!code-cs[csRefOperators#6](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-assignment-operator-1_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)