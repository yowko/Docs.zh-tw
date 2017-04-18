---
title: "統計序列中的項目數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 統計序列中的項目數
使用 <xref:System.Linq.Enumerable.Count%2A> 運算子計算序列中的項目數。  
  
 如果對 Northwind 範例資料庫執行這個查詢，會產生輸出 `91`。  
  
## 範例  
 下列範例會計算資料庫中的 `Customers` 數目。  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## 範例  
 下列範例計算資料庫中未停產的產品項目。  
  
 如果對 Northwind 範例資料庫執行這個範例，會產生輸出 `69`。  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## 請參閱  
 [彙總查詢](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)   
 [下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)