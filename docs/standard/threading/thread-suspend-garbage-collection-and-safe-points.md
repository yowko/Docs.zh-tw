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
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="d9507-102">Thread.Suspend、記憶體回收和安全點</span><span class="sxs-lookup"><span data-stu-id="d9507-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="d9507-103">當您呼叫<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>執行緒上、 系統資訊執行緒暫止要求，並且可讓執行緒執行，直到它到達之前實際暫止執行緒安全的點。</span><span class="sxs-lookup"><span data-stu-id="d9507-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="d9507-104">安全執行緒的點是在記憶體回收的集合可以執行其執行中的點。</span><span class="sxs-lookup"><span data-stu-id="d9507-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="d9507-105">一旦達到安全點時，執行階段可保證，暫停的執行緒不會進行任何進一步的處理 managed 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="d9507-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="d9507-106">執行 managed 程式碼以外的執行緒會一律安全地進行記憶體回收，而且它會嘗試繼續執行 managed 程式碼直到其執行。</span><span class="sxs-lookup"><span data-stu-id="d9507-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9507-107">若要執行記憶體回收，執行階段必須暫停執行回收的執行緒除外的所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="d9507-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="d9507-108">在暫停之前，必須讓每個執行緒安全的點。</span><span class="sxs-lookup"><span data-stu-id="d9507-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9507-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9507-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="d9507-110">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="d9507-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="d9507-111">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="d9507-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
