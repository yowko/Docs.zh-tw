---
title: 執行緒物件和功能
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02f88faab6ddbaa026e73ad61bc63fbe8e5e00ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="threading-objects-and-features"></a>執行緒物件和功能
.NET Framework 提供一些物件，可協助您建立及管理多執行緒應用程式。 Managed 執行緒是以 <xref:System.Threading.Thread> 類別來表示。 <xref:System.Threading.ThreadPool> 類別可讓您輕鬆建立及管理多執行緒的背景工作。 <xref:System.ComponentModel.BackgroundWorker> 類別會針對與使用者介面互動的工作執行相同的作業。 <xref:System.Threading.Timer> 類別會定期執行背景工作。  
  
 此外，還有一些類別會同步處理執行緒的活動，其中包括在 .NET Framework 2.0 版中引入的 <xref:System.Threading.Semaphore> 和 <xref:System.Threading.EventWaitHandle> 類別。 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)中將比較這些類別的功能。  
  
## <a name="in-this-section"></a>本節內容  
 [Managed 執行緒集區](../../../docs/standard/threading/the-managed-thread-pool.md)  
 說明 **ThreadPool** 類別，這個類別可讓您要求執行緒執行工作，而不需要自行進行任何執行緒管理。  
  
 [計時器](../../../docs/standard/threading/timers.md)  
 說明如何使用 **Timer** 來指定要在指定時間呼叫的委派。  
  
 [監視](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 說明如何使用 **Monitor** 類別來同步存取成員，或建置自己的執行緒管理型別。  
  
 [等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 描述 <xref:System.Threading.WaitHandle> 類別，這是事件等候控制代碼、Mutex 和信號的抽象基底類別，可用來等候多個同步處理事件。  
  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 描述 Managed 事件等候控制代碼，可藉由發出信號和等候信號來同步處理執行緒活動。  
  
 [Mutex](../../../docs/standard/threading/mutexes.md)  
 說明如何使用 <xref:System.Threading.Mutex> 來同步處理對物件的存取，或建置自己的同步處理機制。  
  
 [Interlocked 作業](../../../docs/standard/threading/interlocked-operations.md)  
 說明如何使用 <xref:System.Threading.Interlocked> 類別來遞增或遞減值，並在單一不可部分完成的作業中儲存這個值。  
  
 [Reader-Writer 鎖定](../../../docs/standard/threading/reader-writer-locks.md)  
 定義實作單一寫入器/多個讀取器語意的鎖定。  
  
 [Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 描述 <xref:System.Threading.Semaphore> 物件，並說明如何使用這些物件來控制對有限資源的存取。  
  
 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 比較提供用以鎖定及同步處理 Managed 執行緒之 .NET Framework 類別的功能。  
  
 [barrier](../../../docs/standard/threading/barrier.md)  
 描述 <xref:System.Threading.Barrier> 物件，這些物件會實作屏障模式以便協調階段式作業中的執行緒。  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 描述 <xref:System.Threading.SpinLock>，這是適用於特定低階案例之 Monitor 類別的輕量型替代方案。  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 描述 <xref:System.Threading.SpinWait>，這是在起始核心架構等候之前執行忙碌空轉的低階同步處理原始物件。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Threading.Thread>  
 提供 **Thread** 類別的參考文件，不論這個類別是來自 Unmanaged 程式碼或是在 Managed 應用程式中建立，都會代表 Managed 執行緒。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 啟用與使用者介面互動的背景工作，透過使用者介面執行緒上引發的事件來通訊。  
  
## <a name="related-sections"></a>相關章節  
 [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 描述 I/O 非同步完成通訊埠如何使用執行緒集區，要求只有在輸入/輸出作業完成時才進行處理。  
  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 描述在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] (含) 以後版本中進行多執行緒程式設計的建議方法。
