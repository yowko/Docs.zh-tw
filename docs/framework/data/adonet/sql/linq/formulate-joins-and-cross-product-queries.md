---
title: "制定聯結和叉積查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 制定聯結和叉積查詢
下列範例顯示如何合併多張資料表中的結果。  
  
## 範例  
 下列範例在 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 的 `From` 子句 \(在 C\# 中是 `from` 子句\) 中使用外部索引鍵巡覽，選取倫敦客戶的所有訂單。  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## 範例  
 下列範例在 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 的 `Where` 子句 \(在 C\# 中是 `where` 子句\) 中使用外部索引鍵巡覽，篩選 `Supplier` 在美國的缺貨 `Products`。  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## 範例  
 下列範例在 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 的 `From` 子句 \(在 C\# 中是 `from` 子句\) 中使用外部索引鍵巡覽，篩選位於西雅圖的員工並列出他們的領域。  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## 範例  
 下列範例在 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 的 `Select` 子句 \(在 C\# 中是 `select` 子句\) 中使用外部索引鍵巡覽，篩選員工配對，而在這組配對中，其中一位員工要向另一位員工報告，而且兩位員工都是來自相同的 `City`。  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## 範例  
 下列 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 範例會尋找所有客戶和訂單、確定訂單與客戶相符，而且確保該清單中的每位客戶都提供有連絡人名稱。  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## 範例  
 下列範例明確聯結 \(Join\) 兩張資料表，並規劃來自這兩張資料表的結果。  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## 範例  
 下列範例明確聯結三張資料表，並規劃來自每張資料表的結果。  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## 範例  
 下列範例顯示如何使用 `DefaultIfEmpty()` 來達成 `LEFT OUTER JOIN`。  如果 `Employee` 沒有 `Order`，則 `DefaultIfEmpty()` 方法會傳回 null。  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## 範例  
 下列範例會規劃透過聯結產生的 `let` 運算式。  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## 範例  
 下列範例顯示具有複合索引鍵的 `join`。  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## 範例  
 下列範例顯示如何建構 `join`，其中另一端可以為 null，而另一端則不可以。  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## 請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)