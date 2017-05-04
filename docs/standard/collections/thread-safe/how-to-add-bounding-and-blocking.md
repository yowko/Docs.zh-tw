---
title: "如何：將界限和封鎖功能加入至集合 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: df159b1ab3f7c16564ce493a585246c4c461a8f9
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>如何：將界限和封鎖功能加入至集合
這個範例示範如何在類別中實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> 介面，然後使用類別執行個體作為 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的內部儲存機制，以將界限和封鎖功能加入至自訂集合類別。 如需界限和封鎖的詳細資訊，請參閱 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。  
  
## <a name="example"></a>範例  
 自訂集合類別是基本優先順序佇列，其中的優先順序層級會呈現為 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> 物件的陣列。 在每個佇列內不會執行額外的排序。  
  
 在用戶端程式碼中，會啟動三項工作。 第一項工作只會輪詢鍵盤按鍵，可在執行期間隨時取消。 第二項工作是生產者執行緒；它會將新的項目新增至封鎖回收，並根據隨機值來指定每個項目的優先順序。 第三項工作是在項目可供使用時將其從集合中移除。  
  
 您可以讓其中一個執行緒的執行速度快於另一個執行緒，來調整應用程式的行為。 如果生產者的執行速度較快，則會注意到界限功能，原因是封鎖回收在已包含建構函式中所指定的項目數時會防止新增項目。 如果消費者的執行速度較快，您會在消費者等待新增項目時注意到封鎖功能。  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 根據預設，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的儲存體是 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>。  
  
## <a name="see-also"></a>另請參閱  
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)
