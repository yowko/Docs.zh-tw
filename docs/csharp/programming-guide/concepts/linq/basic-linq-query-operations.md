---
title: "Basic LINQ Query Operations (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "orderby clause [LINQ in C#]"
  - "ordering data [LINQ in C#]"
  - "selecting data [LINQ in C#]"
  - "queries [LINQ in C#], basic operations"
  - "grouping data [LINQ in C#]"
  - "data sources [LINQ in C#]"
  - "sorting data [LINQ in C#]"
  - "projections [LINQ in C#]"
  - "filtering data [LINQ in C#]"
  - "joining data [LINQ in C#]"
  - "select clause [LINQ in C#]"
  - "LINQ [C#], basic query operations"
  - "join clause [LINQ in C#]"
  - "group clause [LINQ in C#]"
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
caps.handback.revision: 37
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Basic LINQ Query Operations (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

本主題會簡短介紹 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式，以及一些可以在查詢中執行的一般作業。  下列主題會提供更詳細的資訊：  
  
 [LINQ 查詢運算式](../../../../visual-basic/reference/command-line-compiler/index.md)  
  
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  如果您已經很熟悉 SQL 或 Xquery 之類的查詢語言，則可以略過本主題的大部分內容。  請閱讀下一節中的「`from` 子句」，以了解 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式中的子句順序。  
  
## 取得資料來源  
 在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，第一步是指定資料來源。  在 C\# 中，與大部分程式設計語言一樣，都必須先宣告變數，才可以使用變數。  在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢中，則會先使用 `from` 子句，以引入資料來源 \(`customers`\) 和「*範圍變數*」\(Range Variable\) \(`cust`\)。  
  
 [!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 範圍變數與 `foreach` 迴圈 \(Loop\) 中的反覆運算變數類似，不同處在於查詢運算式不會發生實際反覆運算。  執行查詢時，範圍變數會提供 `customers` 中每個連續項目的參考。  因為編譯器 \(Compiler\) 會推斷 `cust` 的型別，所以您不需要明確指定型別。  `let` 子句可以引入其他範圍變數。  如需詳細資訊，請參閱[let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。  
  
> [!NOTE]
>  如果是非泛型資料來源 \(如 <xref:System.Collections.ArrayList>\)，則必須明確指定範圍變數的型別。  如需詳細資訊，請參閱[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)與[from 子句](../../../../csharp/language-reference/keywords/from-clause.md)。  
  
## 篩選  
 最常見的查詢作業可能是套用布林值 \(Boolean\) 運算式形式的篩選條件。  篩選條件會使查詢只傳回讓運算式變成 true 的項目。  結果是使用 `where` 子句所產生。  篩選條件實際上會指定要從來源序列中排除的項目。  在下列範例中，只會傳回地址在 London 的 `customers`。  
  
 [!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 您可以 `where` 子句中使用熟悉的 C\# 邏輯運算子 `AND` 和 `OR`，套用所需數目的篩選條件運算式。  例如，若只要傳回來自 "London" `AND` 名為 "Devon" 的客戶，請撰寫下列程式碼：  
  
 [!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 若要傳回來自 London 或 Paris 的客戶，請撰寫下列程式碼：  
  
 [!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 如需詳細資訊，請參閱[where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。  
  
## Ordering  
 通常要排序傳回的資料會很方便。  `orderby` 子句會根據所排序型別的預設比較子 \(Comparer\)，來排序所傳回序列中的項目。  例如，可以將下列查詢擴充為根據 `Name` 屬性來排序結果。  因為 `Name` 是字串，所以預設比較子會執行依字母順序從 A 到 Z 的排序。  
  
 [!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 若要以相反方向排序結果 \(從 Z 到 A\)，請使用 `orderby…descending` 子句。  
  
 如需詳細資訊，請參閱[orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。  
  
## 群組  
 `group` 子句可以根據您所指定的索引鍵來分組結果。  例如，您可以指定應該根據 `City` 分組結果，讓所有來自 London 或 Paris 的客戶都位在個別群組中。  在此情況下，`cust.City` 是索引鍵。  
  
 [!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 查詢的結尾是 `group` 子句時，結果會是一份清單的清單。  整份清單中的每個項目都是一個物件，這個物件具有一個 `Key` 成員，以及一份根據該索引鍵分到一組的所有項目的清單。  逐一查看會產生群組序列的查詢時，必須使用巢狀 `foreach` 迴圈。  外部迴圈會逐一查看每個群組，而內部迴圈則會逐一查看每個群組的成員。  
  
 如果您必須參考群組作業的結果，可以使用 `into` 關鍵字建立可供進一步查詢的識別項。  下列查詢只會傳回包含不止兩個客戶的群組：  
  
 [!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 如需詳細資訊，請參閱[group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。  
  
## 聯結  
 聯結作業會在沒有在資料來源中明確設定關聯模式的序列之間建立關聯。  例如，您可以執行聯結，尋找所有位於相同地點的客戶和經銷商。  在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，`join` 子句，一律是處理物件集合，而不是直接處理資料庫資料表。  
  
 [!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 因為 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中的外部索引鍵在物件模型中是以保留項目集合的屬性表示，所以在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 中，使用 `join` 的頻率不需要像在 SQL 中那樣地頻繁。  例如，`Customer` 物件包含 `Order` 物件的集合。  您可以使用點標記法 \(而不是執行聯結\) 來存取訂單：  
  
```  
from order in Customer.Orders...  
```  
  
 如需詳細資訊，請參閱[join 子句](../../../../csharp/language-reference/keywords/join-clause.md)。  
  
## 選取 \(投影\)  
 `select` 子句會產生查詢結果，並指定每個所傳回項目的「型態」或型別。  例如，您可以指定結果要包含完整 `Customer` 物件、只包含一個成員、包含成員子集，還是包含根據計算或所建立新物件而得到的完全不同的結果型別。  如果 `select` 子句的產物不是來源項目的複本，則這項作業稱為「*投影*」\(Projection\)。  使用規劃來轉換資料，是 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢運算式的一項強大功能。  如需詳細資訊，請參閱[使用 LINQ 轉換資料 \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)與[select 子句](../../../../csharp/language-reference/keywords/select-clause.md)。  
  
## 請參閱  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ 查詢運算式](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [查詢關鍵字 \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [基本查詢作業 \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)