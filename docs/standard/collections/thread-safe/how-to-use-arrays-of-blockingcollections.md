---
title: "如何：在管線中使用封鎖集合的陣列 | Microsoft Docs"
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
  - "安全執行緒集合，管線中的封鎖集合"
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在管線中使用封鎖集合的陣列
下列範例將示範如何使用 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 物件的陣列搭配靜態方法 \(例如 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A>\)，在元件之間實作快速且彈性的資料傳輸。  
  
## 範例  
 下列範例將示範基本管線實作，其中每個物件都會以並行方式從輸入集合中取得資料、轉換資料，然後將資料傳遞給輸出集合。  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)