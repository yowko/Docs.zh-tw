---
title: 使用 ConcurrentBag 建立物件集區
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287857"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="41a24-102">使用 ConcurrentBag 建立物件集區</span><span class="sxs-lookup"><span data-stu-id="41a24-102">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="41a24-103">這個範例示範如何使用 <xref:System.Collections.Concurrent.ConcurrentBag%601> 來執行物件集區。</span><span class="sxs-lookup"><span data-stu-id="41a24-103">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="41a24-104">在需要多個類別執行個體的情況下，物件集區可以改善應用程式效能，而且類別的建立或終結成本相當高。</span><span class="sxs-lookup"><span data-stu-id="41a24-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="41a24-105">用戶端程式要求新的物件時，物件集區會先嘗試提供已建立並傳回給集區的物件。</span><span class="sxs-lookup"><span data-stu-id="41a24-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="41a24-106">如果沒有，則只會建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="41a24-106">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="41a24-107"><xref:System.Collections.Concurrent.ConcurrentBag%601>是用來儲存物件，因為它支援快速插入和移除，特別是當相同執行緒同時新增和移除專案時。</span><span class="sxs-lookup"><span data-stu-id="41a24-107">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="41a24-108">此範例無法進一步擴大來建置 bag 資料結構所實作的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>，這與 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601> 相同。</span><span class="sxs-lookup"><span data-stu-id="41a24-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="41a24-109">本文定義如何使用基礎並行類型來撰寫您自己的物件集區，以儲存要重複使用的物件。</span><span class="sxs-lookup"><span data-stu-id="41a24-109">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="41a24-110">不過，此 <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> 類型已經存在於 <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> 命名空間之下。</span><span class="sxs-lookup"><span data-stu-id="41a24-110">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="41a24-111">在建立您自己的執行之前，請考慮使用可用的類型，其中包含許多額外的功能。</span><span class="sxs-lookup"><span data-stu-id="41a24-111">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="41a24-112">範例</span><span class="sxs-lookup"><span data-stu-id="41a24-112">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="41a24-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41a24-113">See also</span></span>

- [<span data-ttu-id="41a24-114">安全線程集合</span><span class="sxs-lookup"><span data-stu-id="41a24-114">Thread-Safe Collections</span></span>](index.md)
