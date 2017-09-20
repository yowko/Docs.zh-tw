---
title: "如何：使用 ConcurrentBag 建立物件集區"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3e26e5954c886d52debbf3e2d41260767b94dc74
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>如何：使用 ConcurrentBag 建立物件集區
這個範例示範如何使用並行資料包來實作物件集區。 在需要多個類別執行個體的情況下，物件集區可以改善應用程式效能，而且類別的建立或終結成本相當高。 用戶端程式要求新的物件時，物件集區會先嘗試提供已建立並傳回給集區的物件。 如果沒有，則只會建立新的物件。  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> 用來儲存物件，原因是它支援快速插入和移除，特別是在相同的執行緒新增和移除項目時。 此範例無法進一步擴大來建置 bag 資料結構所實作的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>，這與 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601> 相同。  
  
## <a name="example"></a>範例  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>另請參閱  
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)

