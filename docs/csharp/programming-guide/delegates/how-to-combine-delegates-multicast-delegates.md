---
title: "如何：組合委派 (多點傳送委派) (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "委派 [C#], 組合"
  - "多點傳送委派 [C#]"
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 如何：組合委派 (多點傳送委派) (C# 程式設計手冊)
本範例示範如何建立多點傳送委派。  [delegate](../../../csharp/language-reference/keywords/delegate.md) 物件具有的一種有用屬性，就是可使用 `+` 運算子將多個物件指派給一個委派執行個體。  多點傳送委派包含已指派委派的清單。  呼叫多點傳送委派時，它會依順序叫用清單中的委派。  只有相同型別的委派才能加以結合。  
  
 `-` 運算子可用來從多點傳送委派中移除某個元件委派。  
  
## 範例  
 [!code-cs[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## 請參閱  
 <xref:System.MulticastDelegate>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)