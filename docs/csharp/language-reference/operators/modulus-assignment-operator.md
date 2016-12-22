---
title: "%= 運算子 (C# 參考) | Microsoft Docs"
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
  - "%=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "%= 指派運算子 (模數指派) [C#]"
  - "模數指派運算子 (=%) [C#]"
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# %= 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

其餘的指派運算子。  
  
## 備註  
 使用 `%=` 指派運算子的運算式，例如  
  
```  
x %= y  
```  
  
 相等於  
  
```  
x = x % y  
```  
  
 不同的是，`x` 只被評估了一次。  已為數字型別 \(Numeric Type\) 預先定義 [% 運算子](../../../csharp/language-reference/operators/modulus-operator.md)，以計算除法的餘數。  
  
 `%=` 運算子無法直接多載，但使用者定義型別可多載 [% 運算子](../../../csharp/language-reference/operators/modulus-operator.md) \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)