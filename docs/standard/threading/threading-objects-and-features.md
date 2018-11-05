---
title: 執行緒物件與功能
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ba47ece16c74555b58780733e14de9833718c33
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873303"
---
# <a name="threading-objects-and-features"></a>執行緒物件與功能

除了 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別以外，.NET 還會提供一些類別來協助您開發多執行緒應用程式。 下列文章概述這些類別：

|標題|描述|  
|-----------|-----------------|  
|[受控執行緒集區](the-managed-thread-pool.md)|描述 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別，這個類別提供 .NET 受控背景工作執行緒集區。|  
|[計時器](timers.md)|說明可用於多執行緒環境的 .NET 計時器。|
|[同步處理原始物件概觀](overview-of-synchronization-primitives.md)|描述可用來同步對共用資源的存取或控制執行緒互動的類型。|
|[EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。|
|[Mutex](mutexes.md)|描述 <xref:System.Threading.Mutex?displayProperty=nameWithType>，它能授與對共用資源的獨佔存取權。|
|[Interlocked 作業](interlocked-operations.md)|描述 <xref:System.Threading.Interlocked?displayProperty=nameWithType> 類別，這個類別為多個執行緒共用的變數提供不可部分完成的作業。|
|[Reader-Writer 鎖定](reader-writer-locks.md)|描述 <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> 類別，它能提供對共用資源的單一寫入器/多個讀取器存取。|
|[旗號與 SemaphoreSlim](semaphore-and-semaphoreslim.md)|描述 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 類別，它能限制可以同時存取共用資源或資源集區的執行緒數目。|
|[barrier](barrier.md)|描述 <xref:System.Threading.Barrier?displayProperty=nameWithType> 類別，這個類別會實作屏障模式以便協調階段式作業中的執行緒。|
|[SpinLock](spinlock.md)|描述 <xref:System.Threading.SpinLock?displayProperty=nameWithType> 結構，這是適用於特定低階鎖定案例之 <xref:System.Threading.Monitor?displayProperty=nameWithType> 類別的輕量型替代方案。|
|[SpinWait](spinwait.md)|描述 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 結構，它能提供微調式等候的支援。|

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [使用執行緒和執行緒處理](using-threads-and-threading.md)
- [Asynchronous File I/O](../io/asynchronous-file-i-o.md)
- [平行程式設計](../parallel-programming/index.md)
- [工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)
