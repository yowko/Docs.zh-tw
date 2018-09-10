---
title: 執行緒物件和功能
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483654"
---
# <a name="threading-objects-and-features"></a>執行緒物件和功能

除了 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別以外，.NET 還會提供一些類別來協助您開發多執行緒應用程式。 下列文章概述這些類別：

|標題|描述|  
|-----------|-----------------|  
|[受控執行緒集區](the-managed-thread-pool.md)|描述 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別，這個類別提供 .NET 受控背景工作執行緒集區。|  
|[計時器](timers.md)|說明可用於多執行緒環境的計時器。|
|[同步處理原始物件概觀](overview-of-synchronization-primitives.md)|描述可用來同步對資料的存取或控制執行緒互動的類別。|
|[EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。|
|[Mutex](mutexes.md)|說明如何使用 <xref:System.Threading.Mutex?displayProperty=nameWithType> 同步對物件的存取，或建置自己的同步處理機制。|
|[Interlocked 作業](interlocked-operations.md)|描述 <xref:System.Threading.Interlocked?displayProperty=nameWithType> 類別，這個類別為多個執行緒共用的變數提供不可部分完成的作業。|
|[Reader-Writer 鎖定](reader-writer-locks.md)|描述 <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> 類別，這個類別提供單一寫入器/多個讀取器語意。|
|[Semaphore 和 SemaphoreSlim](semaphore-and-semaphoreslim.md)|描述 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 類別，並說明如何用以控制對有限資源的存取。|
|[barrier](barrier.md)|描述 <xref:System.Threading.Barrier?displayProperty=nameWithType> 類別，這個類別會實作屏障模式以便協調階段式作業中的執行緒。|
|[SpinLock](spinlock.md)|描述 <xref:System.Threading.SpinLock?displayProperty=nameWithType> 類別，這是適用於特定低階案例之 <xref:System.Threading.Monitor?displayProperty=nameWithType> 類別的輕量型替代方案。|
|[SpinWait](spinwait.md)|描述 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 類別，這是在起始核心架構等候之前，執行忙碌空轉的低階同步處理原始物件。|

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [使用執行緒和執行緒處理](using-threads-and-threading.md)
- [非同步檔案 I/O](../io/asynchronous-file-i-o.md)
- [平行程式設計](../parallel-programming/index.md)
- [工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)
