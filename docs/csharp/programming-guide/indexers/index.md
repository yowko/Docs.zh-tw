---
title: "索引子 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.indexers"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 索引子"
  - "索引子 [C#]"
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# 索引子 (C# 程式設計手冊)
索引子允許類別或結構的執行個體像陣列一樣地編製索引。  索引子和[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)類似，差異在於其存取子會採用參數。  
  
 在下列範例中，泛型類別由簡單的[取得](../../../csharp/language-reference/keywords/get.md)和[設定](../../../csharp/language-reference/keywords/set.md)存取子定義及提供，以作為指派和擷取值的方法。  `Program` 類別會建立此類別的執行個體以儲存字串。  
  
 [!code-cs[csProgGuideIndexers#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  如需更多範例，請參閱[相關章節](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)。  
  
## 運算式主體定義  
 使用直接隨運算式的結果立即傳回的索引子，是很常見的作法。  有個語法捷徑可以使用 `=>` 定義這些索引子：  
  
```c#  
public Customer this[long id] => store.LookupCustomer(id);  
  
```  
  
 索引子必須是唯讀狀態，而且您不會使用 `get` 存取子關鍵字。  
  
## 索引子概觀  
  
-   索引子可以讓物件利用與陣列類似的方式編製索引。  
  
-   `get` 存取子會傳回值。  `set` 存取子會指派值。  
  
-   [這個](../../../csharp/language-reference/keywords/this.md)關鍵字用來定義索引子。  
  
-   [值](../../../csharp/language-reference/keywords/value.md)關鍵字用來定義 `set` 索引子所指派的值。  
  
-   索引子不一定要由整數值編製索引。您可自行決定如何定義特定的查詢機制。  
  
-   索引子可以多載。  
  
-   索引子可具有一個以上的型式參數，例如，存取二維陣列時。  
  
##  <a name="BKMK_RelatedSections"></a> 相關章節  
  
-   [使用索引子](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [介面中的索引子](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [屬性與索引子之間的比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [限制存取子的存取範圍](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)