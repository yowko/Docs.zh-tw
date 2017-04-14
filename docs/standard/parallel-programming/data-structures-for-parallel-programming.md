---
title: "Data Structures for Parallel Programming | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data structures, multi-threading"
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Data Structures for Parallel Programming
.NET Framework 4 版引進數個在平行程式設計中很有用的新型別，包括一組並行集合類別、輕量型同步處理基本型別和用於延遲初始設定的型別。  您可以將這些型別用於任何多執行緒的應用程式程式碼中，包括工作平行程式庫和 PLINQ。  
  
## 並行集合類別  
 <xref:System.Collections.Concurrent?displayProperty=fullName> 命名空間中的集合類別提供具備執行緒安全的加入和移除作業，可以盡量避免鎖定，並在需要鎖定時採用細部鎖定。  與 .NET Framework 1.0 版和 2.0 版中所引進的集合不同，並行集合類別並不需要使用者程式碼在存取項目時取得任何鎖定。  在多個執行緒於集合中加入和移除項目的案例中，並行集合類別可以提供遠高於 <xref:System.Collections.ArrayList?displayProperty=fullName> 和 <xref:System.Collections.Generic.List%601?displayProperty=fullName> \(搭配使用者實作的鎖定\) 等其他型別的效能。  
  
 下表列出新的並行集合類別：  
  
|類型|說明|  
|--------|--------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>|提供安全執行緒集合適用的封鎖和界限容量，此集合會實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName>。  如果沒有位置可用或是集合已滿，則 Producer 執行緒會封鎖。  如果集合是空的，則 Consumer 執行緒會封鎖。  這個型別也支援讓消費者與生產者進行非封鎖性存取。  <xref:System.Collections.Concurrent.BlockingCollection%601> 可以做為基底類別或備份存放區，以提供封鎖和界限給任何支援 <xref:System.Collections.Generic.IEnumerable%601> 的集合類別。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>|執行緒安全的陣列實作，提供可擴充的加入和取得作業。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>|並行和可擴充的字典型別。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>|並行和可擴充的 FIFO 佇列。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName>|並行和可擴充的 LIFO 堆疊。|  
  
 如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
## 同步處理原始物件  
 <xref:System.Threading?displayProperty=fullName> 命名空間中新的同步處理原始型別可以達到更細部的並行處理，並且透過避免舊版多執行緒程式碼中高度耗費資源的鎖定機制，達到更快的效能。  部分新型別 \(例如 <xref:System.Threading.Barrier?displayProperty=fullName> 和 <xref:System.Threading.CountdownEvent?displayProperty=fullName>\) 在舊版 .NET Framework 中有沒有對應的版本。  
  
 下表列出新的同步處理型別：  
  
|類型|說明|  
|--------|--------|  
|<xref:System.Threading.Barrier?displayProperty=fullName>|透過提供一個點讓每個工作告知其已抵達，然後封鎖到部分或所有工作都已抵達為止的方式，讓多個執行緒以平行方式處理演算法。  如需詳細資訊，請參閱[Barrier](../../../docs/standard/threading/barrier.md)。|  
|<xref:System.Threading.CountdownEvent?displayProperty=fullName>|提供簡易 Rendezvous 機制來簡化分岔和聯結案例。  如需詳細資訊，請參閱[CountdownEvent](../../../docs/standard/threading/countdownevent.md)。|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>|與 <xref:System.Threading.ManualResetEvent?displayProperty=fullName> 類似的同步處理基本型別。  <xref:System.Threading.ManualResetEventSlim> 屬於輕量型基本型別，但只能用於同處理序通訊。  如需詳細資訊，請參閱[ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)。|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=fullName>|同步處理基本型別，限制可以並行存取資源或資源集區的執行緒數目。  如需詳細資訊，請參閱[Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)。|  
|<xref:System.Threading.SpinLock?displayProperty=fullName>|互斥鎖定基本型別，會讓嘗試取得鎖定的執行緒先在迴圈中等候 \(或「*空轉*」\(Spin\)\) 一段時間再產生配量。  在預期不需等太久時間來取得鎖定的案例中，<xref:System.Threading.SpinLock> 會比其他鎖定形式提供更好的效能。  如需詳細資訊，請參閱[SpinLock](../../../docs/standard/threading/spinlock.md)。|  
|<xref:System.Threading.SpinWait?displayProperty=fullName>|小型、輕量的型別，會空轉一段指定的時間，並在最後超過空轉計數時，讓執行緒進入等候狀態。如需詳細資訊，請參閱[SpinWait](../../../docs/standard/threading/spinwait.md)。|  
  
 如需詳細資訊，請參閱：  
  
-   [How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## 延遲初始設定類別  
 使用延遲初始設定時，只有在需要物件時才會配置物件的記憶體。  延遲初始設定可以將物件的配置均勻分散在程式的整個存留期中，進而改善效能。  您可以透過包裝 <xref:System.Lazy%601> 型別，來針對任何自訂型別啟用延遲初始設定。  
  
 下表列出延遲初始設定型別：  
  
|類型|說明|  
|--------|--------|  
|<xref:System.Lazy%601?displayProperty=fullName>|提供輕量、具備執行緒安全的延遲初始設定。|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=fullName>|以個別執行緒為單位提供延遲初始化值，每個執行緒都會延遲叫用初始設定函式。|  
|<xref:System.Threading.LazyInitializer?displayProperty=fullName>|提供靜態方法，這些方法使得專門配置一個延遲初始設定執行個體變得不再需要。  它們會改用參考來確保所存取的目標已初始化。|  
  
 如需詳細資訊，請參閱[延遲初始設定](../../../docs/framework/performance/lazy-initialization.md)。  
  
## 彙總例外狀況  
 <xref:System.AggregateException?displayProperty=fullName> 型別可用來擷取不同執行緒同時擲回的多個例外狀況，然後將這些例外狀況當成單一例外狀況傳回給聯結的執行緒。  <xref:System.Threading.Tasks.Task?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> 型別以及 PLINQ 會廣泛地使用 <xref:System.AggregateException> 來達成這個目的。  如需詳細資訊，請參閱[NIB: How to: Handle Exceptions Thrown by Tasks](http://msdn.microsoft.com/zh-tw/d6c47ec8-9de9-4880-beb3-ff19ae51565d)與[How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)。  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 <xref:System.Threading?displayProperty=fullName>   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)