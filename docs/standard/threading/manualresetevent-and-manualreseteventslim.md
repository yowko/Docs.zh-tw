---
title: ManualResetEvent 和 ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85d0c5c291743c6daac549e15d479fcf332235c
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452819"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent 和 ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別代表必須在收到訊號之後手動重設的本機等候控制代碼事件。 此類別代表其基底類別 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 的特殊案例。 如需手動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 <xref:System.Threading.ManualResetEvent> 物件會維持收到訊號的狀態，直到其 <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> 方法被呼叫為止。 任何數目的等候執行緒或在收到訊號之後等候事件的執行緒，皆可在物件的狀態為收到訊號時加以釋放。
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以在預期等候時間非常短暫時，以及事件不會跨越處理序界限時，使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別來提升效能。 <xref:System.Threading.ManualResetEventSlim> 在等候事件變成收到訊號時會短暫使用忙碌微調。 若等候時間很短，旋轉功能的成本會遠低於使用等候控制代碼來等候。 不過，如果事件未在一定時間內變成收到訊號，<xref:System.Threading.ManualResetEventSlim> 就會訴諸於一般的事件控制代碼等候。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [AutoResetEvent](autoresetevent.md)  
- [SpinWait](spinwait.md)  
- [Semaphore 和 SemaphoreSlim](semaphore-and-semaphoreslim.md)
- [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [執行緒物件和功能](threading-objects-and-features.md)  
- [執行緒處理](index.md)  
