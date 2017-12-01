---
title: "適用於平行程式設計的資料結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f35c5382455021f0a001604367e59204ce4ad93c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="data-structures-for-parallel-programming"></a>適用於平行程式設計的資料結構
.NET Framework 第 4 版導入了幾種新類型，可用於平行程式設計，包括並行的集合類別、 輕量型同步處理原始類型和延遲初始設定類型的一組。 您可以使用這些類型的任何多執行緒應用程式程式碼，包括工作平行程式庫和 PLINQ。  
  
## <a name="concurrent-collection-classes"></a>並行的集合類別  
 集合中的類別<xref:System.Collections.Concurrent?displayProperty=nameWithType>命名空間提供安全執行緒的新增和移除作業盡量避免鎖定，並使用更細緻鎖定鎖定所需的位置。 不同於.NET Framework 1.0 和 2.0 版中導入的集合，並行的集合類別不需要存取的項目時，使用任何鎖定的使用者程式碼。 並行的集合類別可大幅提升效能類型例如<xref:System.Collections.ArrayList?displayProperty=nameWithType>和<xref:System.Collections.Generic.List%601?displayProperty=nameWithType>（具有使用者實作鎖定） 多個執行緒加入並移除集合中的項目。  
  
 下表列出新的並行的集合類別：  
  
|類型|說明|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|提供安全執行緒集合適用的封鎖和界限容量，這個集合會實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>。 如果沒有位置可用，或如果集合已滿，就會封鎖產生者執行緒。 如果集合是空的取用者執行緒會封鎖。 這個型別也會支援取用者與生產者的非封鎖存取。 <xref:System.Collections.Concurrent.BlockingCollection%601>可用來當作基底類別，或備份存放區提供封鎖和界限為任何支援的集合類別<xref:System.Collections.Generic.IEnumerable%601>。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|提供可擴充的安全執行緒包實作加入和 get 作業。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|並行和可擴充的字典類型。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|並行和可擴充 FIFO 佇列中。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|並行和可擴充 LIFO 堆疊。|  
  
 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
## <a name="synchronization-primitives"></a>同步處理原始物件  
 在新的同步處理原始物件<xref:System.Threading?displayProperty=nameWithType>藉由避免昂貴的鎖定機制，在舊版的多執行緒程式碼中找到命名空間啟用更細緻的並行存取，以及更快的效能。 某些新的型別，例如<xref:System.Threading.Barrier?displayProperty=nameWithType>和<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>較舊版本的.NET Framework 中有沒有對應項目。  
  
 下表列出新的同步處理類型：  
  
|類型|說明|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|可讓多個執行緒的演算法以平行方式在工作提供的點上每項工作發出信號抵達，然後封鎖，直到到達部分或所有工作。 如需詳細資訊，請參閱[屏障](../../../docs/standard/threading/barrier.md)。|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|提供簡單 rendezvous 機制，以簡化分岔和聯結的案例。 如需詳細資訊，請參閱[CountdownEvent](../../../docs/standard/threading/countdownevent.md)。|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|同步處理原始物件類似於<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>。 <xref:System.Threading.ManualResetEventSlim>是輕量型但僅用於內部處理序通訊。 如需詳細資訊，請參閱[ManualResetEvent 和 ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)。|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|限制可以同時存取資源的執行緒數目或資源集區的同步處理原始物件。 如需詳細資訊，請參閱[Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)。|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|互斥鎖定基本作業，造成執行緒嘗試取得要在迴圈中，等待鎖定或*微調*，一段時間之前產生它的配量。 在等待鎖定是很短，預期有<xref:System.Threading.SpinLock>提供較佳的效能比其他形式的鎖定。 如需詳細資訊，請參閱[單一執行緒存取鎖](../../../docs/standard/threading/spinlock.md)。|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|指定的時間，最後將會微調的小型、 輕量類型進入執行緒等候狀態如果超過微調計數。  如需詳細資訊，請參閱[SpinWait](../../../docs/standard/threading/spinwait.md)。|  
  
 如需詳細資訊，請參閱:  
  
-   [操作說明：使用 SpinLock 進行低階同步處理](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [如何： 使用屏障同步處理並行作業](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)。  
  
## <a name="lazy-initialization-classes"></a>延遲初始設定類別  
 使用延遲初始設定，直到需要為止，不會配置的記憶體物件。 延遲初始設定可以改善效能平均分配在程式的存留期的物件配置。 您可以包裝類型，以啟用任何自訂類型的延遲初始設定<xref:System.Lazy%601>。  
  
 下表列出的延遲初始設定類型：  
  
|類型|說明|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|提供輕量型、 安全執行緒延遲初始化。|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|針對每個執行緒，提供延遲的方式叫用的初始化函式的每個執行緒執行延遲初始化的值。|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|提供靜態方法，即不需配置的專用、 延遲初始設定執行個體。 反之，他們使用的參考，以確保它們存取已初始化目標。|  
  
 如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。  
  
## <a name="aggregate-exceptions"></a>彙總的例外狀況  
 <xref:System.AggregateException?displayProperty=nameWithType>類型可以用來擷取多個例外狀況，就會擲回同時在不同的執行緒，並將其傳回為單一例外狀況的聯結執行緒。 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>和<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>類型和 PLINQ 使用<xref:System.AggregateException>廣泛用於此用途。 如需詳細資訊，請參閱[NIB： 如何： 處理例外狀況擲回的工作](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d)和[如何： 處理 PLINQ 查詢中的例外狀況](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)
