---
title: 受控執行緒集區
description: 了解提供背景工作執行緒的 .NET 執行緒集區
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7721ffaebfefadee332c923d867e68204b5205f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003681"
---
# <a name="the-managed-thread-pool"></a>受控執行緒集區

<xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別為您的應用程式提供了受到系統管理的背景工作執行緒集區，讓您專注於應用程式工作上，而不是執行緒的管理。 如果您有需要在背景處理的簡短工作，Managed 執行緒集區是利用多重執行緒的一個簡單方式。 相較於舊版，使用 Framework 4 及更新版本中的執行緒集區容易許多，因為您可以建立<xref:System.Threading.Tasks.Task> 及 <xref:System.Threading.Tasks.Task%601> 物件，對執行緒集區的執行緒執行非同步工作。  
  
.NET 執行緒集區的執行緒有多種用途，包括[工作平行程式庫 (TPL)作業](../parallel-programming/task-parallel-library-tpl.md)、非同步 I/O 完成、[計時器](timers.md)回呼、註冊的等候作業、使用委派的非同步方法，以及 <xref:System.Net?displayProperty=nameWithType> 通訊端連線。  

## <a name="thread-pool-characteristics"></a>執行緒集區的特性

執行緒集區的執行緒為[背景](foreground-and-background-threads.md)執行緒。 每個執行緒都會使用預設堆疊大小、以預先優先權執行，並且位於多執行緒 Apartment 中。 當執行緒集區的執行緒完成其工作時，會返回等候中的執行緒佇列。 當其返回佇列時，就能重複使用。 這項重複使用可讓應用程式避免建立每個工作之新執行緒的成本。
  
每個處理序只有一個執行緒集區。  
  
### <a name="exceptions-in-thread-pool-threads"></a>執行緒集區執行緒的例外狀況

執行緒集區的執行緒中如有未處理的例外狀況，將會終止該處理序。 這項規則有三個例外狀況：  
  
- 因為呼叫了 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>，所以會在執行緒集區的執行緒中擲回 <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType>。  
- 因為正在卸載應用程式定義域，所以在執行緒集區的執行緒中擲回 <xref:System.AppDomainUnloadedException?displayProperty=nameWithType>。  
- Common Language Runtime 或主應用程式處理序會結束這個執行緒。  
  
如需詳細資訊，請參閱[受控執行緒中的例外狀況](exceptions-in-managed-threads.md)。  
  
### <a name="maximum-number-of-thread-pool-threads"></a>執行緒集區執行緒數的上限

可以排入執行緒集區佇列的作業數，受限於可用記憶體的數量， 但執行緒集區會限制能在處理序中同時作用的執行緒數。 當所有執行緒集區執行緒都在忙碌時，其他工作項目會排入佇列中，直到有執行緒可以執行這些工作為止。 自 .NET Framework 4 起，處理序的執行緒集區預設大小取決於數個因素，例如虛擬位址空間的大小。 處理序可以呼叫 <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> 方法來決定執行緒數目。  
  
您可以使用 <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> 和 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法來控制執行緒最大數目。  

> [!NOTE]
> 裝載 Common Language Runtime 的程式碼，可以使用 [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) 方法設定大小。  
  
### <a name="thread-pool-minimums"></a>執行緒集區下限

執行緒集區會視需要提供新的背景工作執行緒或 I/O 完成執行緒，直到達到每個分類的指定最小值為止。 您可以使用 <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> 方法取得這些最小值。  
  
> [!NOTE]
> 當需求很低時，執行緒集區執行緒的實際數目可能低於最小值。  
  
當達到最小值時，執行緒集區可以建立額外的執行緒，或是等候部分工作完成。 自 .NET Framework 4 起，執行緒集區會建立及終結背景工作執行緒，以最佳化輸送量。輸送量是指每個時間單位所能完成的工作數。 執行緒太少可能無法最有效地利用可用資源，而執行緒太多則可能增加資源爭用的情況。  
  
> [!CAUTION]
> 您可以使用 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法來提高閒置執行緒的數目下限。 不過，不必要地增加這些值，可能會造成效能問題。 如果太多工作同時啟動，則所有工作可能都會變慢。 在大部分情況下，執行緒集區使用自己的演算法來配置執行緒的效能較佳。  

## <a name="using-the-thread-pool"></a>使用執行緒集區

自 .NET Framework 4 起，使用執行緒集區最簡單的方式，就是使用[工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)。 根據預設，諸如 <xref:System.Threading.Tasks.Task> 與 <xref:System.Threading.Tasks.Task%601> 等 TPL 類型，都會使用執行緒集區的執行緒執行工作。

您也可以從受控程式碼呼叫 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> (或從 非受控程式碼呼叫 [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md))，再傳遞代表執行此工作之方法的 <xref:System.Threading.WaitCallback?displayProperty=nameWithType> 委派來使用執行緒集區。

使用執行緒集區的另一種方式，是使用 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法並傳遞 <xref:System.Threading.WaitHandle?displayProperty=nameWithType> (它在收到信號或逾時的時候會呼叫由 <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> 委派表示的方法)，藉以將與等候作業有關的工作項目排入佇列。 執行緒集區執行緒可用來叫用回呼方法。  

如需範例，請參閱所參考的 API 頁面。
  
## <a name="skipping-security-checks"></a>略過安全性檢查

執行緒集區也提供 <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> 和 <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> 方法。 只有在您確定呼叫端的堆疊與排入佇列之工作的執行期間所做的任何安全性檢查無關時，才能使用這些方法。 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> 和 <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> 都可擷取呼叫端的堆疊，這個堆疊會在執行緒開始執行工作時，合併到執行緒集區執行緒的堆疊中。 如果需要安全性檢查，則必須檢查整個堆疊。 雖然檢查能夠提供安全性，但是也帶來效能成本。  

## <a name="when-not-to-use-thread-pool-threads"></a>不應使用執行緒集區執行緒的時機

有好幾種情況適合建立及管理您自己的執行緒，而不是使用執行緒集區的執行緒：  
  
- 您需要前景執行緒。  
- 您需要執行緒有特定的優先權。  
- 您有一些工作會造成執行緒封鎖一段很長的時間。 執行緒集區有執行緒數目上限，因此大量已封鎖的執行緒集區執行緒可能會導致工作無法啟動。  
- 您需要將執行緒放在單一執行緒 Apartment 中。 所有 <xref:System.Threading.ThreadPool> 執行緒都會在多執行緒 Apartment 中。  
- 您需要有一個與執行緒關聯的固定識別，或是讓執行緒專屬於某項工作。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>  
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>  
- [工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)  
- [操作說明：傳回工作的值](../parallel-programming/how-to-return-a-value-from-a-task.md)  
- [執行緒物件和功能](threading-objects-and-features.md)  
- [執行緒和執行緒處理](threads-and-threading.md)  
- [非同步檔案 I/O](../io/asynchronous-file-i-o.md)  
- [計時器](timers.md)  
