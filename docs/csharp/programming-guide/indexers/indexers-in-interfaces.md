---
title: "介面中的索引子 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "存取子 [C#], 索引子"
  - "索引子 [C#], 介面中"
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 介面中的索引子 (C# 程式設計手冊)
索引子可以在[interface](../../../csharp/language-reference/keywords/interface.md) 上宣告。  介面索引子的存取子與[類別](../../../csharp/language-reference/keywords/class.md)索引子的存取子，兩者之間差異如下：  
  
-   介面存取子不使用修飾詞。  
  
-   介面存取子不具有主體。  
  
 因此，存取子的目的是為指示這個索引子是讀寫、唯讀或唯寫性質。  
  
 下列是介面索引子存取子的範例：  
  
 [!code-cs[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/indexers-in-interfaces_1.cs)]  
  
 索引子的簽章必須與宣告在相同介面的其他所有索引子的簽章不同。  
  
## 範例  
 下列範例將示範如何實作介面索引子。  
  
 [!code-cs[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/indexers-in-interfaces_2.cs)]  
  
 在上述範例中，您可以以完整的介面成員名稱來使用明確介面成員實作。  例如：  
  
```  
public string ISomeInterface.this   
{   
}   
```  
  
 然而，只有在這種類別以相同的索引子簽章來實作一個以上的介面時，才需要使用這種完整名稱，以避免模稜兩可 \(Ambiguity\) 的狀況。  例如，如果  `Employee` 類別實作 `ICitizen` 和 `IEmployee` 兩個介面，而且兩個介面都具有相同的索引子簽章 \(Indexer Signature\)，如此一來，就需要有明確介面成員實作。  也就是，下面這個索引子宣告：  
  
```  
public string IEmployee.this   
{   
}   
```  
  
 會實作在 `IEmployee` 介面上的索引子，而下面這段宣告：  
  
```  
public string ICitizen.this   
{   
}   
```  
  
 會實作在 `ICitizen` 介面上的索引子。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [介面](../../../csharp/programming-guide/interfaces/index.md)