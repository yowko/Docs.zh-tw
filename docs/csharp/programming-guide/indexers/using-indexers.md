---
title: "使用索引子 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "索引子 [C#], 關於索引子"
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 使用索引子 (C# 程式設計手冊)
索引子 \(Indexer\) 是一種語法上便於使用的工具，可讓您建立[類別](../../../csharp/language-reference/keywords/class.md)、[結構](../../../csharp/language-reference/keywords/struct.md)或[介面](../../../csharp/language-reference/keywords/interface.md)，讓用戶端應用程式如同存取陣列一般進行存取。  索引子最常在型別中予以實作，這些型別主要的用途是封裝內部集合或陣列。  例如，假設您有一個名為 TempRecord 的類別，用以表示在 24 小時內，十次不同的時間所記錄的華氏溫度。  該類別包含了名為 "temps" 的陣列來表示溫度，而其型別為浮點數 \(Float\)，並且也包含了 <xref:System.DateTime>，表示記錄溫度的日期。  透過在此類別中實作索引子，用戶端可以以 `float temp = tr[4]` 存取 TempRecord 執行個體中的溫度，而非 `float temp = tr.temps[4]`。  索引子標記法不但可簡化用戶端應用程式的語法，也會讓其他程式開發人員更直覺地了解類別及其用途。  
  
 若要在類別或結構上宣告索引子，請使用 [this](../../../csharp/language-reference/keywords/this.md) 關鍵字，如這個範例所示：  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
  
```  
  
## 備註  
 索引子的型別及其參數的型別都必須至少具有與索引子本身相同的可存取性。  如需存取範圍層級的詳細資訊，請參閱[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。  
  
 如需如何搭配使用索引子和介面的詳細資訊，請參閱[介面索引子](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)。  
  
 索引子的簽章 \(Signature\) 包含了編號和其型式參數的型別。  這並不包括索引子型別和該型式參數的名稱。  如果您在相同類別裡宣告了一個以上的索引子，則它們必須具有不同的簽章。  
  
 索引子值並不是歸類成變數，因此無法將索引子值當成 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數進行傳遞。  
  
 若要提供索引子其他語言都能使用的名稱，請在宣告中使用 `name` 屬性 \(Attribute\)。  例如：  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 這個索引子將擁有 `TheItem` 名稱。  若不提供名稱屬性，則會使 `Item` 成為預設名稱。  
  
## 範例 1  
  
### 描述  
 下列範例將示範如何宣告私用的陣列欄位 `temps` 和索引子。  索引子可允許直接存取 `tempRecord[i]` 執行個體。  可替代使用索引子的方法，是將該陣列宣告為 [public](../../../csharp/language-reference/keywords/public.md) 成員，並且直接存取其成員 `tempRecord.temps[i]`。  
  
 請注意，在評估索引子的存取時 \(例如，使用 `Console.Write` 陳述式\)，會叫用 [get](../../../csharp/language-reference/keywords/get.md) 存取子。  因此，如果沒有 `get` 存取子，便會發生編譯時期錯誤。  
  
### 程式碼  
 [!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## 使用其他的值進行索引  
 C\# 並未將索引型別限制為整數。  例如，搭配索引子使用字串可能非常有用。  藉由在集合中搜尋字串，並傳回適當的值，即可實作這類的索引子。  存取子可以多載，因此字串和整數版本可以同時存在。  
  
## 範例 2  
  
### 描述  
 在此範例中，會宣告儲存一週中每天的類別。  宣告的 `get` 存取子取得一個字串，也就是一天的名稱，並傳回對應的整數。  例如，Sunday \(星期日\) 會傳回 0，Monday \(星期一\) 會傳回 1，其他依此類推。  
  
### 程式碼  
 [!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## 健全的程式設計  
 有兩種主要方式能夠改進索引子的安全性和可靠性：  
  
-   請務必併入某些類型的錯誤處理策略，以處理用戶端程式碼傳遞至無效索引值的狀況。  在本主題前面的第一個範例中，TempRecord 類別會提供 Length 屬性，讓用戶端程式碼可在將輸入傳遞至索引子之前先予以驗證。  您也可以將錯誤處理程式碼放在索引子本身內。  請務必將您在索引子存取子內所擲回的任何例外狀況記錄下來，以供使用者參考。  
  
-   在合理的情況下，盡可能地限制 `get` 和 [set](../../../csharp/language-reference/keywords/set.md) 存取子的存取範圍。  這點對 `set` 存取子尤其重要。  如需詳細資訊，請參閱 [限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [索引子](../../../csharp/programming-guide/indexers/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)