---
title: "HOW TO：處理查詢中的複合索引鍵 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：處理查詢中的複合索引鍵
有些運算子只能取用一個引數。  如果引數必須包括資料庫中的多個資料行，則必須建立匿名型別來表示此項組合。  
  
## 範例  
 下列範例顯示叫用 \(Invoke\) `GroupBy` 運算子的查詢，這個運算子只可以取用一個 `key` 引數。  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## 範例  
 聯結 \(Join\) 的情況也相同，如下列範例所示：  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## 請參閱  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)