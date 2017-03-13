---
title: "明確介面實作 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "明確介面 [C#]"
  - "介面 [C#]，明確"
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 明確介面實作 (C# 程式設計手冊)
如果[類別](../../../csharp/language-reference/keywords/class.md)實作了兩個包含相同簽章之成員的介面，則在類別上實作該成員會導致兩個介面都將該成員當做實作 \(Implementation\) 使用。  在下列範例中，對 `Paint` 的呼叫所叫用的方法。  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 然而，如果兩個[介面](../../../csharp/language-reference/keywords/interface.md)成員並未執行同樣的功能，則可能造成其中一個介面 \(或兩者\) 實作不正確。  建立只能透過介面呼叫而且為該介面特有的類別成員，就可以明確地實作介面成員。  這項作業的完成方法為，以介面的名稱加上句號，為類別成員命名。  例如：  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 類別成員 `IControl.Paint` 只能透過 `IControl` 介面呼叫，而 `ISurface.Paint` 則只能透過 `ISurface` 加以呼叫。  這兩種方法實作都是獨立的，而且兩者都無法直接從類別上使用。  例如：  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 明確實作也可以用來解決兩個介面宣告不同成員但名稱相同的情況，例如屬性和方法：  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 若要實作兩個介面，類別必須為屬性 P 或方法 P \(或兩者\) 使用明確實作，以避免發生編譯器錯誤。  例如：  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)