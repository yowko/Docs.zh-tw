---
title: "如何：執行自訂聯結作業 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "自訂聯結 [C#]"
  - "聯結 [C#], 自訂"
  - "查詢 [C# 中的 LINQ], 聯結"
  - "查詢運算式 [C# 中的 LINQ], 聯結"
ms.assetid: a05e2ab1-410d-4a1d-8ada-af93539682c9
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：執行自訂聯結作業 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下列範例顯示如何執行無法使用 `join` 子句完成的聯結作業。  在查詢運算式中，`join` 子句受限於等聯結 \(Equijoin\)，並且也針對等聯結進行最佳化，而等聯結是聯結作業最常見的類型。  執行等聯結時，您可以藉由使用 `join` 子句而一律取得最佳效能。  
  
 但是，在下列情況下無法使用 `join` 子句：  
  
-   在不等比較 \(非等聯結\) 運算式上預測有聯結時。  
  
-   在多個等號比較或不等比較運算式上預測有聯結時。  
  
-   當您必須在聯結作業前引入右側 \(內部\) 序列的暫時範圍變數時。  
  
 若要執行非等聯結的聯結，您可以使用多個 `from` 子句個別引入每個資料來源。  然後將 `where` 子句中的述詞 \(Predicate\) 運算式套用至每個來源的範圍變數。  運算式也可以採用方法呼叫的形式。  
  
> [!NOTE]
>  請勿將這類型的自訂聯結作業與使用多個 `from` 子句以存取內部集合混淆。  如需詳細資訊，請參閱 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)。  
  
## 範例  
 下列範例中的第一個方法顯示簡單的交叉聯結。  交叉聯結必須小心使用，因為它們會產生相當大的結果集。  但是，它們在某些建立來源序列 \(會針對這些序列執行額外的查詢\) 的情況中相當有用。  
  
 第二個方法會產生所有產品的序列，產品的分類 ID 列在左側的分類清單中。  使用 `let` 子句和 `Contains` 方法建立暫時陣列時請特別注意。  另外也可以在查詢和排除第一個 `from` 子句之前建立陣列。  
  
 [!code-cs[csProgGuideLINQ#64](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_1.cs)]  
  
## 範例  
 在下列範例中，在 join 子句之前無法取得內部 \(右側\) 序列的情況下，查詢必須根據相符的索引鍵聯結兩個序列。  如果此聯結是使用 `join` 子句執行，則必須針對每個項目呼叫 `Split` 方法。  使用多個 `from` 子句可以讓查詢避免重複方法呼叫的負荷。  但是，由於 `join` 已最佳化，因此在這個特殊案例中，它的速度可能仍然比使用多個 `from` 子句快。  結果主要會依據方法呼叫耗費的資源而有所不同。  
  
 [!code-cs[csProgGuideLINQ#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_2.cs)]  
  
## 編譯程式碼  
  
-   建立以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 \(含\) 以後版本為目標的 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 主控台應用程式專案。  根據預設，專案有 System.Core.dll 的參考，以及 System.Linq 命名空間的 `using` 指示詞。  
  
-   將 `Program` 類別取代為前述範例中的程式碼。  
  
-   依照 [How to: Join Content from Dissimilar Files \(LINQ\)](../Topic/How%20to:%20Join%20Content%20from%20Dissimilar%20Files%20\(LINQ\).md) 中的指示，設定資料檔、scores.csv 和 names.csv。  
  
-   按 F5 編譯和執行程式。  
  
-   按任何鍵離開主控台視窗。  
  
## 請參閱  
 [LINQ 查詢運算式](../../../visual-basic/reference/command-line-compiler/index.md)   
 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [如何：排序 Join 子句的結果](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)