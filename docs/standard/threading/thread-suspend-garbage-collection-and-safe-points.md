---
title: "Thread.Suspend、記憶體回收和安全點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="37ebb-102">Thread.Suspend、記憶體回收和安全點</span><span class="sxs-lookup"><span data-stu-id="37ebb-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="37ebb-103">當您在執行緒上呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 時，系統會注意到已要求執行緒暫止，並允許執行緒在實際暫止執行緒之前執行，直到它到達安全點為止。</span><span class="sxs-lookup"><span data-stu-id="37ebb-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="37ebb-104">執行緒的安全點是在其執行中可執行記憶體回收的點。</span><span class="sxs-lookup"><span data-stu-id="37ebb-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="37ebb-105">一旦達到安全點之後，執行階段可保證暫止的執行緒將不會在受控碼中有任何進一步的進展。</span><span class="sxs-lookup"><span data-stu-id="37ebb-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="37ebb-106">在受控碼以外執行的執行緒一律可安全地進行記憶體回收，而且它的執行會繼續，直到它嘗試繼續執行受控碼為止。</span><span class="sxs-lookup"><span data-stu-id="37ebb-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37ebb-107">若要執行記憶體回收，執行階段必須暫止所有執行緒，但執行記憶體回收的執行緒除外。</span><span class="sxs-lookup"><span data-stu-id="37ebb-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="37ebb-108">每個執行緒都必須在暫止之前被帶至安全點。</span><span class="sxs-lookup"><span data-stu-id="37ebb-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ebb-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="37ebb-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="37ebb-110">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="37ebb-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="37ebb-111">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="37ebb-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
