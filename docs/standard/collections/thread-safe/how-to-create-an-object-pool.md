---
title: 如何：使用 ConcurrentBag 建立物件集區
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9239a38d1970a052567f111b57be2b6596f1e5f1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="fd015-102">如何：使用 ConcurrentBag 建立物件集區</span><span class="sxs-lookup"><span data-stu-id="fd015-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="fd015-103">這個範例示範如何使用並行資料包來實作物件集區。</span><span class="sxs-lookup"><span data-stu-id="fd015-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="fd015-104">在需要多個類別執行個體的情況下，物件集區可以改善應用程式效能，而且類別的建立或終結成本相當高。</span><span class="sxs-lookup"><span data-stu-id="fd015-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="fd015-105">用戶端程式要求新的物件時，物件集區會先嘗試提供已建立並傳回給集區的物件。</span><span class="sxs-lookup"><span data-stu-id="fd015-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="fd015-106">如果沒有，則只會建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="fd015-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="fd015-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> 用來儲存物件，原因是它支援快速插入和移除，特別是在相同的執行緒新增和移除項目時。</span><span class="sxs-lookup"><span data-stu-id="fd015-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="fd015-108">此範例無法進一步擴大來建置 bag 資料結構所實作的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>，這與 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601> 相同。</span><span class="sxs-lookup"><span data-stu-id="fd015-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd015-109">範例</span><span class="sxs-lookup"><span data-stu-id="fd015-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="fd015-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd015-110">See Also</span></span>  
 [<span data-ttu-id="fd015-111">安全執行緒集合</span><span class="sxs-lookup"><span data-stu-id="fd015-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
