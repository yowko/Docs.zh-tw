---
title: "| 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "|_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "| 運算子 [C#]"
  - "二進位運算子 (|) [C#]"
  - "位元 OR 運算子 [C#]"
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# | 運算子 (C# 參考)
Binary        `|`  運算子已為整數類資料型別及 `bool` 預先定義其運算方式。  對於整數型別，  `|` 會針對其運算元進行位元 OR 運算。  針對 `bool` 運算元，  `|` 會針對其運算元進行邏輯 OR 運算，也就是說，唯有在兩個運算元皆為 `false` 時，結果才會是 `false`。  
  
## 備註  
 使用者定義型別可以多載           `|` 運算子 \(請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)\)。  
  
## 範例  
 [!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#31)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)