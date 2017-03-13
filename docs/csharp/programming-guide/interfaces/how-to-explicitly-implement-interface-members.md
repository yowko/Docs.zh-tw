---
title: "如何：明確實作介面成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "介面 [C#], 明確實作"
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 如何：明確實作介面成員 (C# 程式設計手冊)
本範例會宣告 [interface](../../../csharp/language-reference/keywords/interface.md)、`IDimensions`，以及明確實作介面成員 `getLength` 和 `getWidth` 的 `Box` 類別。  成員是經由介面執行個體 `dimensions` 來存取。  
  
## 範例  
 [!code-cs[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## 穩固程式設計  
  
-   請注意，`Main` 方法中的下面幾行程式碼已加上註解，因為它們會產生編譯錯誤。  被明確實作的介面成員無法從 [class](../../../csharp/language-reference/keywords/class.md) 執行個體中存取：  
  
     [!code-cs[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   同時請注意，`Main` 方法中的下面幾行程式碼將成功顯示方塊的大小，因為會從介面的執行個體呼叫方法：  
  
     [!code-cs[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [如何：明確實作兩個介面的成員](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)