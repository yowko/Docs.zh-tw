---
title: "/= 運算子 (C# 參考) | Microsoft Docs"
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
  - "/=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/= (除法指派運算子) [C#]"
  - "除法指派運算子 (/=) [C#]"
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /= 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [!code-cs[csRefOperators#5](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)