---
title: "暫止和繼續執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a>暫止和繼續執行緒
最常見之同步處理執行緒活動的方式為封鎖及釋放執行緒、鎖定物件或程式碼區域。 如需有關這些鎖定和封鎖機制的詳細資訊，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 您也可以讓執行緒自己進入睡眠。 當執行緒已封鎖或睡眠中，您可以使用 <xref:System.Threading.ThreadInterruptedException> 解除其等候狀態。  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep 方法  
 呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>方法會導致目前的執行緒可立即封鎖毫秒，或是您傳遞給方法的時間間隔的數目，並產生另一個執行緒的時間配量的其餘部分。 該時間間隔過去後，睡眠中的執行緒便會繼續執行。  
  
 執行緒無法呼叫另一個執行緒上的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>是一律會導致目前的執行緒睡眠的靜態方法。  
  
 呼叫<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>值是<xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>造成執行緒睡眠，直到另一個執行緒呼叫中斷<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>方法睡眠中的執行緒，或直到它就會終止由呼叫其<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>方法。  下列範例說明這兩種可中斷睡眠中執行緒的方法。  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>中斷執行緒  
 您可以藉由呼叫中斷等候執行緒<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>方法擲回封鎖的執行緒上<xref:System.Threading.ThreadInterruptedException>，這會中斷的封鎖呼叫執行緒。 執行緒應該攔截 <xref:System.Threading.ThreadInterruptedException>並執行任何適合繼續進行的工作。 如果執行緒忽略例外狀況，則執行階段會攔截例外狀況，並停止執行緒。  
  
> [!NOTE]
>  在呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 時，如果未封鎖目標執行緒，則到封鎖之前，執行緒不會中斷。 如果執行緒永不封鎖，它可在沒有任何中斷的情況下完成。  
  
 如果等候是 Managed 等候，那麼 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 兩者都會立即喚醒執行緒。 如果等候是 unmanaged 的等候 (例如平台叫用呼叫 Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx)函式)，都沒有<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>也<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>可能需要控制執行緒，直到它傳回或呼叫 managed 程式碼。 在 Managed 程式碼中，行為如下所示：  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadInterruptedException> 在目的執行緒中被擲回。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>喚醒時可能會在中，並造成任何等候執行緒<xref:System.Threading.ThreadAbortException>執行緒上擲回。 如需詳細資訊，請參閱[終結執行緒](../../../docs/standard/threading/destroying-threads.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)  
 [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
