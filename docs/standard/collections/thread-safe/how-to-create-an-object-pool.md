---
title: "如何：使用 ConcurrentBag 建立物件集區 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "物件集區，在 .NET Framework 中"
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：使用 ConcurrentBag 建立物件集區
這個範例示範如何使用並行 Bag 實作物件集區。  在您需要多個類別執行個體，而建立或終結類別較昂貴時，物件集區可以改善應用程式效能。  當用戶端程式要求新物件時，物件集區會先嘗試提供已建立並傳回至集區的物件。  如果沒有可用的物件，才會建立新物件。  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> 可用來儲存物件，因為它支援快速插入和移除，尤其是相同執行緒同時加入和移除項目時。  這個範例可進一步擴大針對 Bag 資料結構實作的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 建置，就如同 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601>。  
  
## 範例  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## 請參閱  
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)