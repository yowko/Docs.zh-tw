---
title: "如何：明確實作兩個介面的成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "繼承 [C#], 明確實作介面成員"
  - "介面 [C#], 明確使用繼承實作"
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：明確實作兩個介面的成員 (C# 程式設計手冊)
明確[介面](../../../csharp/language-reference/keywords/interface.md)實作 \(Implementation\) 也可讓程式設計人員實作成員名稱相同的兩個介面，並針對每個介面成員提供獨立的實作。  這個範例同時以公制和英制單位顯示方塊的尺寸。  Box [類別](../../../csharp/language-reference/keywords/class.md)會實作 IEnglishDimensions 和 IMetricDimensions 這兩個介面，它們代表不同的度量系統。  這兩個介面有相同的成員名稱：Length 和 Width。  
  
## 範例  
 [!code-cs[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## 穩固程式設計  
 如果您想要將英制單位做為預設的度量單位，請正常實作方法 Length 和 Width，並明確實作 IMetricDimensions 介面的 Length 和 Width 方法：  
  
 [!code-cs[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 在本範例中，您可以從類別執行個體中存取英制單位和從介面執行個體中存取公制單位：  
  
 [!code-cs[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)   
 [如何：明確實作介面成員](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)