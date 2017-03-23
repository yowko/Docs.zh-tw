---
title: "from 子句 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "from_CSharpKeyword"
  - "from"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "from 子句 [C#]"
  - "from 關鍵字 [C#]"
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# from 子句 (C# 參考)
查詢運算式必須以 `from` 子句開頭。  此外，查詢運算式可以包含子查詢，而子查詢也以 `from` 子句開頭。  `from` 子句會指定下列各項：  
  
-   在其上執行查詢或子查詢的資料來源。  
  
-   區域「*範圍變數*」\(Range Variable\)，代表來源序列中的每個項目。  
  
 範圍變數和資料來源都是強型別。  `from` 子句中參考的資料來源的型別必須是 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601> 或衍生的型別，例如 <xref:System.Linq.IQueryable%601>。  
  
 在下列範例中，`numbers` 是資料來源而 `num` 是範圍變數。  請注意，變數都是強型別，即使使用 [var](../../../csharp/language-reference/keywords/var.md) 關鍵字也一樣。  
  
 [!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## 範圍變數  
 編譯器會在資料來源實作 <xref:System.Collections.Generic.IEnumerable%601> 時推斷範圍變數的型別。  例如，如果來源的型別是 `IEnumerable<Customer>`，則範圍變數會推斷為 `Customer`。  您必須明確指定型別的唯一時機是當來源為非泛型 `IEnumerable` 型別 \(例如 <xref:System.Collections.ArrayList>\) 時。  如需詳細資訊，請參閱[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)。  
  
 在上述範例中，`num` 是推斷為型別 `int`。  因為範圍變數是強型別，所以您可以在其上呼叫方法或在其他作業中使用它。  例如，不撰寫 `select num`，您可以撰寫 `select num.ToString()` 讓查詢運算式傳回字串序列而非整數序列。  或者可以撰寫 `select n + 10` 讓運算式傳回序列 14、11、13、12、10。  如需詳細資訊，請參閱 [select 子句](../../../csharp/language-reference/keywords/select-clause.md)。  
  
 範圍變數如同 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式中的反覆運算變數，只有一個非常重要的差異：範圍變數永不實際儲存來源的資料。  它只是一種語法上便於使用的工具，讓查詢描述執行查詢時會發生的事件。  如需詳細資訊，請參閱[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。  
  
## 從子句複合  
 在某些情況下，來源序列中的每個項目本身就是序列或包含序列。  例如，您的資料來源可能是 `IEnumerable<Student>`，其中序列中的每個學生物件包含考試分數的清單。  若要存取每個 `Student` 項目的內部清單，您可以使用複合 `from` 子句。  這個技術如同使用巢狀 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式。  您可以將 [where](../../../csharp/language-reference/keywords/partial-method.md) 或 [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 子句加入至 `from` 子句以篩選結果。  下列範例顯示 `Student` 物件的序列，每個序列都包含代表考試分數的整數內部 `List`。  若要存取內部清單，請使用複合 `from` 子句。  您可以在必要時於兩個 `from` 子句之間插入子句。  
  
 [!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## 使用多個 from 子句執行聯結  
 複合 `from` 子句是用於存取單一資料來源中的內部集合。  但是，查詢也可以包含多個 `from` 子句，從獨立資料來源產生補充查詢。  此技術可以讓您執行特定類型的聯結作業，這些作業是無法使用 [join 子句](../../../csharp/language-reference/keywords/join-clause.md)來完成。  
  
 下列範例顯示如何使用兩個 `from` 子句，形成兩個資料來源完整的交叉聯結。  
  
 [!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 如需使用多個 `from` 子句之聯結作業的詳細資訊，請參閱 [如何：執行自訂聯結作業](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)。  
  
## 請參閱  
 [查詢關鍵字 \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)