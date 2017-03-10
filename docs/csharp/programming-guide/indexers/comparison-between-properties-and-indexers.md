---
title: "屬性與索引子之間的比較 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "索引子 [C#], 與屬性的比較"
  - "屬性 [C#], 和索引子的比較"
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 屬性與索引子之間的比較 (C# 程式設計手冊)
索引子 \(Indexer\) 就像是屬性。  除了下表所列的差異外，所有為屬性存取子定義的規則也適用於索引子存取子。  
  
|屬性|索引子|  
|--------|---------|  
|允許方法接受呼叫，就像是公用資料成員一樣。|允許使用物件本身的陣列標記法，存取物件的內部集合項目。|  
|透過簡單名稱存取。|透過索引存取。|  
|可以是靜態或執行個體成員。|必須是執行個體成員。|  
|屬性的 [get](../../../csharp/language-reference/keywords/get.md) 存取子沒有參數。|索引子的 `get` 存取子擁有與索引子相同的型式參數清單 \(Formal Parameter List\)。|  
|屬性的 [set](../../../csharp/language-reference/keywords/set.md) 存取子包含隱含的 `value` 參數。|除了 [value](../../../csharp/language-reference/keywords/value.md) 參數以外，索引子的 `set` 存取子還擁有與索引子相同的型式參數清單。|  
|支援縮短的語法，如[自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) 所示。|不支援縮短的語法。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)