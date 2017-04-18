---
title: "傳回兩個序列的交集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 傳回兩個序列的交集
使用 <xref:System.Linq.Queryable.Intersect%2A> 運算子可傳回兩個序列的集合交集。  
  
## 範例  
 這個範例使用 <xref:System.Linq.Queryable.Intersect%2A> 傳回同時有 `Customers` 和 `Employees` 居住的所有國家 \(地區\) 序列。  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Linq.Queryable.Intersect%2A> 作業僅妥善定義於集合上。  尚未定義多重集 \(Multiset\) 的語意 \(Semantics\)。  
  
## 請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)   
 [標準查詢運算子轉譯](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)