---
title: 適用於平行程式設計的資料結構
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6453e9983086dcb5b97ec134db9d74160d7a47cf
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836468"
---
# <a name="data-structures-for-parallel-programming"></a>適用於平行程式設計的資料結構
.NET Framework 4 版導入了數個適用於平行程式設計的新類型，包括一系列並行集合類別、輕量型同步處理原始物件，以及適用於延遲初始設定的類型。 您可以搭配任何多執行緒應用程式程式碼使用這些類型，其中包括工作平行程式庫和 PLINQ。  
  
## <a name="concurrent-collection-classes"></a>並行集合類別  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType> 命名空間中的集合類別能提供安全執行緒新增和移除作業，以盡量避免鎖定情況，並在需要鎖定時使用細部鎖定。 並行集合類別與在 .NET Framework 1.0 和 2.0 版中導入的集合不同，它並不會要求使用者程式碼在存取項目時採用任何鎖定。 並行集合類別可在多執行緒針對集合新增和移除項目的案例中，大幅提升 <xref:System.Collections.ArrayList?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (搭配使用者實作的鎖定) 等類型的效能。  
  
 下表列出新的並行集合類別：  
  
|類型|描述|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|提供安全執行緒集合適用的封鎖和界限容量，這個集合會實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>。 在沒有可用插槽或集合已滿的情況下封鎖產生者執行緒。 在集合為空的情況下封鎖取用者執行緒。 此類型也支援由取用者和產生者所進行的非封鎖存取。 <xref:System.Collections.Concurrent.BlockingCollection%601> 可以作為基底類別或備份存放區使用，以針對任何支援 <xref:System.Collections.Generic.IEnumerable%601>的集合類別提供封鎖和繫結。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|能提供可調整之新增和取得作業的安全執行緒包實作。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|並行且可調整的字典類型。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|並行且可調整的 FIFO 佇列。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|並行且可調整的 LIFO 堆疊。|  
  
 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
## <a name="synchronization-primitives"></a>同步處理原始物件  
 <xref:System.Threading?displayProperty=nameWithType> 中的新同步處理原始物件能透過避免舊版多執行緒程式碼中耗費資源的鎖定機制，提供細微的並行及更快的效能。 某些新的類型 (例如 <xref:System.Threading.Barrier?displayProperty=nameWithType> 和 <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>) 在較舊版本的 .NET Framework 中並沒有相對應的項目。  
  
 下表列出新的同步處理類型：  
  
|類型|描述|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|透過提供一個點，可讓每個工作發出其抵達的訊號並在部分或所有工作皆已抵達之前持續封鎖，來使多執行緒能以平行方式處理演算法。 如需詳細資訊，請參閱[屏障](../../../docs/standard/threading/barrier.md)。|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|透過提供簡單的會合機制來簡化分岔和連結案例。 如需詳細資訊，請參閱 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)。|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|與 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類似的同步處理原始物件。 <xref:System.Threading.ManualResetEventSlim> 雖為輕量型，但只能用於內部處理序通訊。 如需詳細資訊，請參閱 [ManualResetEvent 和 ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)。|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|能限制可並行存取資源或資源集區之執行緒數目的同步處理原始物件。 如需詳細資訊，請參閱 [Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)。|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|能使嘗試取得鎖定的執行緒在產生其配量之前，於迴圈中等候 (或*旋轉*) 一段時間的互斥鎖定原始物件。 在預期等候鎖定時間較短的案例中，<xref:System.Threading.SpinLock> 能提供比其他鎖定形式更佳的效能。 如需詳細資訊，請參閱 [SpinLock](../../../docs/standard/threading/spinlock.md)。|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|會旋轉一段特定的時間，並於最終超過旋轉計數時將執行緒置於等候狀態的小型輕量型類型。  如需詳細資訊，請參閱 [SpinWait](../../../docs/standard/threading/spinwait.md)。|  
  
 如需詳細資訊，請參閱:  
  
-   [操作說明：使用 SpinLock 進行低階同步處理](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [如何：使用屏障同步處理並行作業](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)。  
  
## <a name="lazy-initialization-classes"></a>延遲初始設定類別  
 使用延遲初始設定時，物件的記憶體只會在有需要時才會配置。 延遲初始設定可透過將物件配置平均分配於程式的存留期來提升效能。 您可以透過包裝類型 <xref:System.Lazy%601>，來針對任何自訂類型啟用延遲初始設定。  
  
 下表列出延遲初始設定類型：  
  
|類型|描述|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|提供輕量型的安全執行緒延遲初始設定。|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|以針對每個執行緒的方式提供延遲初始化的值，其中每個執行緒都會延遲叫用初始化函式。|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|提供能避免需要指派專用延遲初始設定執行個體的靜態方法。 反之，它們會使用參考以確保目標在被存取時已經初始化。|  
  
 如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。  
  
## <a name="aggregate-exceptions"></a>彙總例外狀況  
 <xref:System.AggregateException?displayProperty=nameWithType> 類型可以用來擷取在個別執行緒上並行擲出的多個例外狀況，並將它們以單一例外狀況的形式傳回聯結執行緒。 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 類型，以及 PLINQ 都會針對此目的廣泛使用 <xref:System.AggregateException>。 如需詳細資訊，請參閱[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)和[如何：處理 PLINQ 查詢中的例外狀況](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- <xref:System.Threading?displayProperty=nameWithType>  
- [平行程式設計](../../../docs/standard/parallel-programming/index.md)
