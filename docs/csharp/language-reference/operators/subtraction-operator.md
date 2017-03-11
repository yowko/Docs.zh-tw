---
title: "- 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "-_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "- 運算子 [C#]"
  - "減法運算子 (-) [C#]"
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# - 運算子 (C# 參考)
`-` 運算子可做為一元 \(Unary\) 或二元 \(Binary\) 運算子。  
  
## 備註  
 已為所有數字型別預先定義一元 `-` 運算子。  數字型別的一元 `-` 運算結果為運算元的負值。  
  
 已為所有數字型別和列舉型別預先定義二元 `-` 運算子為從第一個運算元減去第二個運算元。  
  
 委派型別也有提供會執行委派移除的二元 `-` 運算子。  
  
 使用者定義型別可多載一元 `-` 和二元 `-` 運算子。  如需詳細資訊，請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)。  
  
## 範例  
 [!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#40)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)