---
title: 使用執行緒和執行緒處理
description: 瞭解如何在 .NET 中使用執行緒和執行緒，讓您可以撰寫應用程式，同時 (多執行緒) 執行許多作業。
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 127ea9e28d9ce303270512bf86bf4eecf2f86437
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188701"
---
# <a name="using-threads-and-threading"></a>使用執行緒和執行緒處理

使用 .NET，您可以撰寫同時執行多項作業的應用程式。 可能妨礙其他作業的作業可以在另外的執行緒上執行，這類處理序稱為「多執行緒」  或「無限制執行緒」  。  
  
使用多執行緒的應用程式回應使用者輸入會更快，因為當處理器密集工作在另外的執行緒上執行時，使用者介面會保持使用中。 當您建立可擴充的應用程式時，多執行緒也很有幫助，因為您可以隨著工作負載增加而新增執行緒。

> [!NOTE]
> 如果您需要對應用程式執行緒行為有更大的掌控力，您可以自行管理執行緒。 不過，多執行緒程式設計透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別（ [平行 LINQ (PLINQ) ](../parallel-programming/introduction-to-plinq.md)、命名空間中的並行集合類別，以及以工作 <xref:System.Collections.Concurrent?displayProperty=nameWithType> （而非執行緒）概念為基礎的程式設計模型，大幅簡化。 如需詳細資訊，請參閱[平行程式設計](../parallel-programming/index.md)和[工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md)。

## <a name="how-to-create-and-start-a-new-thread"></a>如何：建立及啟動新的執行緒

您可以透過建立 <xref:System.Threading.Thread?displayProperty=nameWithType> 類別的新執行個體，並將您希望在新的執行緒上執行的方法名稱提供給建構函式，來建立新的執行緒。 若要啟動已建立的執行緒，請呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法。 如需詳細資訊和範例，請參閱[建立執行緒並在啟動時傳遞資料](creating-threads-and-passing-data-at-start-time.md)一文和 <xref:System.Threading.Thread> API 參考。

## <a name="how-to-stop-a-thread"></a>如何：停止執行緒

若要終止執行緒的執行，請使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 。 它會提供統一的方式，以合作方式停止執行緒。 如需詳細資訊，請參閱 [managed 執行緒中的取消](cancellation-in-managed-threads.md)。

有時無法合作地停止執行緒，因為它會執行協力廠商程式碼，而不是針對合作式取消所設計。 在此情況下，您可能想要強制終止其執行。 若要強制終止執行緒的執行，您可以在 .NET Framework 中使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法。 該方法會在叫用該方法的執行緒上引發 <xref:System.Threading.ThreadAbortException>。 如需詳細資訊，請參閱[終結執行緒](destroying-threads.md)。 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.Net Core 不支援此方法。 如果您需要在 .NET Core 中強制終止協力廠商程式碼的執行，請在個別的進程中執行，並使用 <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> 。

<xref:System.Threading.CancellationToken?displayProperty=nameWithType>.NET Framework 4 之前無法使用。 若要停止較舊 .NET Framework 版本中的執行緒，請使用執行緒同步處理技術手動執行合作式取消。 例如，您可以建立 volatile 布林值欄位 `shouldStop` ，並用它來要求執行緒所執行的程式碼停止。 如需詳細資訊，請參閱在 c # 中 [Volatile](../../csharp/language-reference/keywords/volatile.md) 參考和 <xref:System.Threading.Volatile?displayProperty=nameWithType> 。

您 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 可以使用方法，讓呼叫執行緒等候停止的執行緒終止。

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

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [執行緒和執行緒處理](threads-and-threading.md)
- [平行程式設計](../parallel-programming/index.md)
