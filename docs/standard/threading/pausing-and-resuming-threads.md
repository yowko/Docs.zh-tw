---
title: 暫停和中斷執行緒
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b66881a8a42c0c34b5c2119f7404fe7787c8f3f2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137521"
---
# <a name="pausing-and-interrupting-threads"></a>暫停和中斷執行緒

最常見之同步處理執行緒活動的方式為封鎖及釋放執行緒、鎖定物件或程式碼區域。 如需有關這些鎖定和封鎖機制的詳細資訊，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 您也可以讓執行緒自己進入睡眠。 當執行緒已封鎖或睡眠中，您可以使用 <xref:System.Threading.ThreadInterruptedException> 解除其等候狀態。  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep 方法

 呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 方法會導致立即封鎖目前執行緒，封鎖時間為您傳遞至方法的毫秒數或時間間隔，並且會將剩餘的時間配量讓與另一個執行緒。 該時間間隔過去後，睡眠中的執行緒便會繼續執行。  
  
 執行緒無法呼叫另一個執行緒上的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>。  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 是一律會導致目前執行緒進入睡眠的靜態方法。  
  
 呼叫具有 <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> 值的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 會造成執行緒進入睡眠，直到被另一個在睡眠中執行緒上呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 的執行緒中斷，或直到它由其 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法的呼叫終止。  下列範例說明這兩種可中斷睡眠中執行緒的方法。  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>中斷執行緒

 您可藉由在封鎖的執行緒上呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 方法來中斷等候中的執行緒，以擲回 <xref:System.Threading.ThreadInterruptedException>，這會中斷執行緒的封鎖呼叫。 執行緒應該攔截 <xref:System.Threading.ThreadInterruptedException>並執行任何適合繼續進行的工作。 如果執行緒忽略例外狀況，則執行階段會攔截例外狀況，並停止執行緒。  
  
> [!NOTE]
>  在呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 時，如果未封鎖目標執行緒，則到封鎖之前，執行緒不會中斷。 如果執行緒永不封鎖，它可在沒有任何中斷的情況下完成。  
  
 如果等候是 Managed 等候，那麼 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 兩者都會立即喚醒執行緒。 如果等候是非受控的等候 (例如，平台叫用 Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) 函式的呼叫)，則 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 都無法控制執行緒，直到它傳回或呼叫受控程式碼為止。 在 Managed 程式碼中，行為如下所示：  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadInterruptedException> 在目的執行緒中被擲回。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadAbortException> 在執行緒中被擲回。 如需詳細資訊，請參閱[終結執行緒](../../../docs/standard/threading/destroying-threads.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadInterruptedException>  
- <xref:System.Threading.ThreadAbortException>  
- [執行緒處理](../../../docs/standard/threading/index.md)  
- [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)  
- [同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
