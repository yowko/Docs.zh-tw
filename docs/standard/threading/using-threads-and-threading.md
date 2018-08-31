---
title: 使用執行緒和執行緒處理
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 871a0a06c9f1cc09fb86f20c85163fb8fcdf4100
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934127"
---
# <a name="using-threads-and-threading"></a>使用執行緒和執行緒處理

使用 .NET，您可以撰寫同時執行多項作業的應用程式。 可能妨礙其他作業的作業可以在另外的執行緒上執行，這類處理序稱為「多執行緒」或「無限制執行緒」。  
  
使用多執行緒的應用程式回應使用者輸入會更快，因為當處理器密集工作在另外的執行緒上執行時，使用者介面會保持使用中。 當您建立可擴充的應用程式時，多執行緒也很有幫助，因為您可以隨著工作負載增加而新增執行緒。

> [!NOTE]
> 如果您需要對應用程式執行緒行為有更大的掌控力，您可以自行管理執行緒。 但是，從 .NET Framework 4 開始，多執行緒的程式設計已透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別、[平行 LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 命名空間中的新並行集合類別，以及以工作 (而非執行緒) 概念為基礎的新程式設計模型，而做出簡化。 如需詳細資訊，請參閱[平行程式設計](../parallel-programming/index.md)和[工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)。

## <a name="how-to-create-and-start-a-new-thread"></a>如何：建立及啟動新的執行緒

您可以透過建立 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別的新執行個體，並將您希望在新的執行緒上執行的方法名稱提供給建構函式，來建立新的執行緒。 若要啟動已建立的執行緒，請呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法。 如需詳細資訊和範例，請參閱[建立執行緒並在啟動時傳遞資料](creating-threads-and-passing-data-at-start-time.md)一文和 <xref:System.Threading.Thread> API 參考。

## <a name="how-to-stop-a-thread"></a>如何：停止執行緒

若要終止執行緒的執行，請使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法。 該方法會在叫用該方法的執行緒上引發 <xref:System.Threading.ThreadAbortException>。 如需詳細資訊，請參閱[終結執行緒](destroying-threads.md)。

從 .NET Framework 4 開始，您可以使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 來合作取消執行緒。 如需詳細資訊，請參閱[合作取消執行緒](canceling-threads-cooperatively.md)。

使用 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 方法讓呼叫的執行緒等待叫用該方法的執行緒終結。

## <a name="how-to-pause-or-interrupt-a-thread"></a>如何：暫停或插斷執行緒

您可以使用 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 方法在指定的時間內暫停目前的執行緒。 您可以透過呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 方法來插斷封鎖的執行緒。 如需詳細資訊，請參閱[暫停及插斷執行緒](pausing-and-resuming-threads.md)。

## <a name="thread-properties"></a>執行緒屬性

下表列出 <xref:System.Threading.Thread>屬性的一部分：  
  
|屬性|描述|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|若執行緒已啟動且尚未正常終止或中止，則傳回 `true`。|  
|<xref:System.Threading.Thread.IsBackground%2A>|取得或設定布林值，指出執行緒是否為背景執行緒。 背景執行緒與前景執行緒相似，但背景執行緒不會防止處理序停止。 一旦屬於處理程序的所有前景執行緒停止，通用語言執行平台會呼叫背景執行緒上仍在執行的 <xref:System.Threading.Thread.Abort%2A> 方法來結束處理程序。 如需詳細資訊，請參閱[前景與背景執行緒](foreground-and-background-threads.md)。|  
|<xref:System.Threading.Thread.Name%2A>|取得或設定執行緒名稱。 最常用於在偵錯時探索個別執行緒。|  
|<xref:System.Threading.Thread.Priority%2A>|取得或設定作業系統使用的 <xref:System.Threading.ThreadPriority> 值，以設定執行緒排程的優先權。 如需詳細資訊，請參閱[排程執行緒](scheduling-threads.md)和 <xref:System.Threading.ThreadPriority> 參考。|  
|<xref:System.Threading.Thread.ThreadState%2A>|取得包含執行緒目前狀態的 <xref:System.Threading.ThreadState> 值。|  

## <a name="see-also"></a>另請參閱

 <xref:System.Threading.Thread?displayProperty=nameWithType>  
 [執行緒和執行緒處理](threads-and-threading.md)  
 [平行程式設計](../parallel-programming/index.md)  
