---
title: "搭配陣列使用 foreach (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "陣列 [C#], foreach"
  - "foreach 陳述式 [C#], 搭配陣列使用"
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 搭配陣列使用 foreach (C# 程式設計手冊)
C\# 還提供 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式。  這個陳述式提供了一個簡單且清楚的方法來逐一查看陣列中或任何可列舉集合中的元素。  `foreach` 陳述式會依照陣列或集合類型的列舉值傳回的順序處理元素，通常是從第 0 個元素到最後一個元素。  例如，下列程式碼會建立名為 `numbers` 的陣列，並使用 `foreach` 陳述式逐一查看該陣列：  
  
 [!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/csharp/using-foreach-with-arrays_1.cs)]  
  
 使用多維陣列時，就可以使用相同的方法來逐一查看元素，例如：  
  
 [!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/csharp/using-foreach-with-arrays_2.cs)]  
  
 但是在使用多維陣列時，使用巢狀 [for](../../../csharp/language-reference/keywords/for.md) 迴圈能夠讓您進一步控制陣列元素。  
  
## 請參閱  
 <xref:System.Array>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [不規則陣列](../../../csharp/programming-guide/arrays/jagged-arrays.md)