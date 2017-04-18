---
title: "如何：將界限和封鎖功能加入至集合 | Microsoft Docs"
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
  - "安全執行緒集合，自訂封鎖集合"
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：將界限和封鎖功能加入至集合
這個範例會示範如何在自訂集合類別中實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> 介面，然後使用類別執行個體當做 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的內部儲存機制，藉以將界限和封鎖功能加入至自訂集合類別。  如需界限和封鎖的詳細資訊，請參閱 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。  
  
## 範例  
 自訂集合類別是一種基本優先權佇列，其中優先權層級會表示成 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> 物件的陣列。  每個佇列內部不會執行額外排序。  
  
 在用戶端程式碼中，系統會啟動三項工作。  第一項工作只會輪詢鍵盤按鍵，以便在執行期間的任何時間點啟用取消作業。  第二項工作是生產者執行緒。它會將新的項目加入至封鎖集合，並且根據隨機值提供優先權給每個項目。  第三項工作會在項目可用時，從集合中移除項目。  
  
 您可以讓其中一個執行緒的執行速度超過另一個執行緒，藉以調整應用程式的行為。  如果生產者的執行速度較快，您就會注意到界限功能，因為封鎖集合會防止系統加入項目 \(如果它已經包含建構函式中指定的項目數的話\)。  如果消費者的執行速度較快，您就會注意到封鎖功能，因為消費者會等候系統加入新的項目。  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 根據預設，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的儲存體是 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>。  
  
## 請參閱  
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)