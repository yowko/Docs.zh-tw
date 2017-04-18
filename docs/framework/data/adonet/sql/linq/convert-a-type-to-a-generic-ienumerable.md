---
title: "將型別轉換為泛型 IEnumerable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 將型別轉換為泛型 IEnumerable
使用 <xref:System.Linq.Enumerable.AsEnumerable%2A> 傳回型別設為泛型 `IEnumerable` 的引數。  
  
## 範例  
 在此範例中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] \(使用預設泛型 `Query`\) 會嘗試將查詢轉換為 SQL，並且在伺服器上執行查詢。  但是，`where` 子句會參考使用者定義的用戶端方法 \(`isValidProduct`\)，而該方法無法轉換為 SQL。  
  
 解決方案為指定 `where` 的用戶端泛型 <xref:System.Collections.Generic.IEnumerable%601> 實作，以取代泛型 <xref:System.Linq.IQueryable%601>。  您可藉由叫用 \(Invoke\) <xref:System.Linq.Enumerable.AsEnumerable%2A> 運算子來完成這項作業。  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## 請參閱  
 [查詢範例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)