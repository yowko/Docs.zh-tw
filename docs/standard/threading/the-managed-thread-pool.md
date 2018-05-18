---
title: Managed 執行緒集區
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="the-managed-thread-pool"></a>Managed 執行緒集區
<xref:System.Threading.ThreadPool> 類別為您的應用程式提供了受到系統管理的背景工作執行緒集區，讓您專注於應用程式工作上，而不是執行緒的管理。 如果您有需要在背景處理的簡短工作，Managed 執行緒集區是利用多重執行緒的一個簡單方式。 例如，從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，您可以建立 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 物件，這兩個物件會在執行緒集區執行緒上執行非同步工作。  
  
> [!NOTE]
>  從 [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 開始，執行緒集區的輸送量在三個關鍵領域有了重大改進：佇列工作、分派執行緒集區執行緒，以及分派 I/O 完成執行緒。這三個領域在舊版 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中，被視為是瓶頸所在。 若要使用這項功能，您的應用程式應將目標設為 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] (含) 以後版本。  
  
 對於與使用者介面互動的背景工作而言，.NET Framework 2.0 版也提供了 <xref:System.ComponentModel.BackgroundWorker> 類別，這個類別透過使用者介面執行緒上所引發的事件來通訊。  
  
 .NET Framework 使用執行緒集區執行緒的目的有許多個，其中包括非同步的 I/O 完成、計時器回呼、註冊的等候作業、使用委派的非同步方法，以及 <xref:System.Net> 通訊端連接。  
  
## <a name="when-not-to-use-thread-pool-threads"></a>何時不該使用執行緒集區執行緒  
 有好幾種情況適合建立及管理自己的執行緒，而不是使用執行緒集區執行緒：  
  
-   您需要前景執行緒。  
  
-   您需要執行緒有特定的優先權。  
  
-   您有一些工作會造成執行緒封鎖一段很長的時間。 執行緒集區有執行緒數目上限，因此大量已封鎖的執行緒集區執行緒可能會導致工作無法啟動。  
  
-   您需要將執行緒放在單一執行緒 Apartment 中。 所有 <xref:System.Threading.ThreadPool> 執行緒都會在多執行緒 Apartment 中。  
  
-   您需要有一個與執行緒關聯的固定識別，或是讓執行緒專屬於某項工作。  
  
## <a name="thread-pool-characteristics"></a>執行緒集區特性  
 執行緒集區執行緒為背景執行緒。 請參閱[前景和背景執行緒](../../../docs/standard/threading/foreground-and-background-threads.md)。 每個執行緒都會使用預設堆疊大小、以預先優先權執行，並且位於多執行緒 Apartment 中。  
  
 每個處理序只有一個執行緒集區。  
  
### <a name="exceptions-in-thread-pool-threads"></a>執行緒集區執行緒中的例外狀況  
 執行緒集區執行緒上未處理的例外狀況會結束處理序。 這項規則有三個例外狀況：  
  
-   執行緒集區執行緒擲回 <xref:System.Threading.ThreadAbortException>，因為已呼叫 <xref:System.Threading.Thread.Abort%2A>。  
  
-   執行緒集區執行緒擲回 <xref:System.AppDomainUnloadedException>，因為正在卸載應用程式定義域。  
  
-   Common Language Runtime 或主應用程式處理序會結束這個執行緒。  
  
 如需詳細資訊，請參閱[受控執行緒中的例外狀況](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，Common Language Runtime 會以無訊息模式在執行緒集區執行緒中截獲未處理的例外狀況。 這可能會破壞應用程式狀態，最終導致應用程式沒有回應，而可能讓偵錯工作變得相當困難。  
  
### <a name="maximum-number-of-thread-pool-threads"></a>執行緒集區執行緒最大數目  
 可排入執行緒集區佇列中的作業數目只會受到可用記憶體的限制；不過，執行緒集區會限制可同時在處理序中使用的執行緒數目。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，處理序的執行緒集區預設大小取決於數個因素，例如虛擬位址空間的大小。 處理序可以呼叫 <xref:System.Threading.ThreadPool.GetMaxThreads%2A> 方法來決定執行緒數目。  
  
 您可以使用 <xref:System.Threading.ThreadPool.GetMaxThreads%2A> 和 <xref:System.Threading.ThreadPool.SetMaxThreads%2A> 方法來控制執行緒最大數目。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，無法從 Managed 程式碼設定執行緒集區的大小。 裝載 Common Language Runtime 的程式碼可以使用 mscoree.h 中定義的 `CorSetMaxThreads` 來設定大小。  
  
### <a name="thread-pool-minimums"></a>執行緒集區最小值  
 執行緒集區會視需要提供新的背景工作執行緒或 I/O 完成執行緒，直到達到每個分類的指定最小值為止。 您可以使用 <xref:System.Threading.ThreadPool.GetMinThreads%2A> 方法取得這些最小值。  
  
> [!NOTE]
>  當需求很低時，執行緒集區執行緒的實際數目可能低於最小值。  
  
 當達到最小值時，執行緒集區可以建立額外的執行緒，或是等候部分工作完成。 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，執行緒集區會建立並終結背景工作執行緒，以便最佳化輸送量，輸送量的定義為每個時間單位完成的工作數目。 執行緒太少可能無法最有效地利用可用資源，而執行緒太多則可能增加資源爭用的情況。  
  
> [!CAUTION]
>  您可以使用 <xref:System.Threading.ThreadPool.SetMinThreads%2A> 方法來提高閒置執行緒的數目下限。 不過，不必要地增加這些值，可能會造成效能問題。 如果太多工作同時啟動，則所有工作可能都會變慢。 在大部分情況下，執行緒集區使用自己的演算法來配置執行緒的效能較佳。  
  
## <a name="skipping-security-checks"></a>略過安全性檢查  
 執行緒集區也提供 <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> 和 <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法。 只有在您確定呼叫端的堆疊與排入佇列之工作的執行期間所做的任何安全性檢查無關時，才能使用這些方法。 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 和 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 都可擷取呼叫端的堆疊，這個堆疊會在執行緒開始執行工作時，合併到執行緒集區執行緒的堆疊中。 如果需要安全性檢查，則必須檢查整個堆疊。 雖然檢查能夠提供安全性，但是也帶來效能成本。  
  
## <a name="using-the-thread-pool"></a>使用執行緒集區  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，使用執行緒集區的最簡單方式是使用[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)。 根據預設，平行程式庫類型 (例如 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601>) 會使用執行緒集區執行緒來執行工作。 您也可以透過下列方式使用執行緒集區：從 Managed 程式碼呼叫 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> (或從 Unmanaged 程式碼呼叫 `CorQueueUserWorkItem`)，並傳遞代表執行工作之方法的 <xref:System.Threading.WaitCallback> 委派。 使用執行緒集區的另一種方式，是使用 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法並傳遞 <xref:System.Threading.WaitHandle> (它在收到信號或逾時的時候會呼叫由 <xref:System.Threading.WaitOrTimerCallback> 委派表示的方法)，藉以將與等候作業有關的工作項目排入佇列。 執行緒集區執行緒可用來叫用回呼方法。  
  
## <a name="threadpool-examples"></a>ThreadPool 範例  
 本節中的程式碼範例使用 <xref:System.Threading.Tasks.Task> 類別、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 方法和 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法，來示範執行緒集區。  
  
-   [使用工作平行程式庫執行非同步工作](#TaskParallelLibrary)  
  
-   [使用 QueueUserWorkItem 以非同步方式執行程式碼](#ExecuteCodeWithQUWI)  
  
-   [提供工作資料给 QueueUserWorkItem](#TaskDataForQUWI)  
  
-   [使用 RegisterWaitForSingleObject](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>使用工作平行程式庫執行非同步工作  
 下列範例示範如何透過呼叫 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 方法，建立及使用 <xref:System.Threading.Tasks.Task> 物件。 如需使用 <xref:System.Threading.Tasks.Task%601> 類別從非同步工作傳回值的範例，請參閱[如何：傳回工作的值](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)。  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>使用 QueueUserWorkItem 以非同步方式執行程式碼  
 下列範例使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法來查詢一個非常簡單的工作，這個工作是由 `ThreadProc` 方法表示。  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>提供工作資料给 QueueUserWorkItem  
 下列程式碼範例使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法將工作排入佇列，並提供工作的資料。  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>使用 RegisterWaitForSingleObject  
 下列範例示範幾個執行緒處理功能。  
  
-   使用 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> 方法將工作排入佇列，以供 <xref:System.Threading.ThreadPool> 執行緒執行。  
  
-   使用 <xref:System.Threading.AutoResetEvent> 向要執行的工作發出信號。 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)。  
  
-   使用 <xref:System.Threading.WaitOrTimerCallback> 委派處理逾時和信號。  
  
-   使用 <xref:System.Threading.RegisteredWaitHandle> 取消已排入佇列的工作。  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [操作說明：傳回工作的值](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [計時器](../../../docs/standard/threading/timers.md)
