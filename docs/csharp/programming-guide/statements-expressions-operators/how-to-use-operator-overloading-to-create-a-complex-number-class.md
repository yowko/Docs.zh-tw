---
title: "如何：使用運算子多載建立複數類別 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "類別 [C#], 運算子多載"
  - "複數 [C#]"
  - "運算子多載 [C#], 複數"
  - "運算子多載 [C#], 用來建立類別"
  - "運算子 [C#], 多載來建立 complex number 類別"
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：使用運算子多載建立複數類別 (C# 程式設計手冊)
本範例介紹如何使用運算子多載化來建立一個定義複數加法的複數類別 `Complex`。  這個程式會顯示數值的虛數和實數部分，以及使用 `ToString` 方法之覆寫的加法運算結果。  
  
## 範例  
 [!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-use-operator-over_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [為什麼 C\# 中多載的運算子一定是靜態的？](http://go.microsoft.com/fwlink/?LinkId=112383)