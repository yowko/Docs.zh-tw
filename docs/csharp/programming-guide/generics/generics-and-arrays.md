---
title: "泛型和陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "陣列 [C#], 泛型"
  - "泛型 [C#], 陣列"
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 泛型和陣列 (C# 程式設計手冊)
在 C\# 2.0 和更新版本中，具有下限為零的一維陣列，會自動實作 <xref:System.Collections.Generic.IList%601>。  這能夠讓您建立可以使用相同程式碼逐一查看陣列和其他集合型別的泛型方法。  這項技術主要用在讀取集合中的資料。  <xref:System.Collections.Generic.IList%601> 介面無法用來在陣列中加入或移除元素。  如果嘗試呼叫 <xref:System.Collections.Generic.IList%601> 方法 \(例如此內容之陣列上的 <xref:System.Collections.Generic.IList%601.RemoveAt%2A>\)，將會擲回例外狀況。  
  
 下列程式碼範例會示範如何使用 <xref:System.Collections.Generic.IList%601> 輸入參數的單一泛型方法，逐一查看清單和陣列，在此案例中為整數陣列。  
  
 [!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/csharp/generics-and-arrays_1.cs)]  
  
## 請參閱  
 <xref:System.Collections.Generic>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [泛型](../Topic/Generics%20in%20the%20.NET%20Framework.md)