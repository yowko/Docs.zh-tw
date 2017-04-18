---
title: "傳回兩個序列的聯集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 傳回兩個序列的聯集
使用 <xref:System.Linq.Queryable.Union%2A> 運算子傳回兩個序列的集合聯集。  
  
## 範例  
 這個範例會使用 <xref:System.Linq.Queryable.Union%2A> 傳回 `Customers` 或 `Employees` 所在的所有國家\/地區序列。  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Union%2A> 運算子已針對多重集 \(Multiset\) 而定義為多重集的未排序串連 \(實際上為 SQL 中 `UNION ALL` 子句的結果\)。  
  
## 請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)   
 [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)