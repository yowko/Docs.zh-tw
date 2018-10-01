---
title: Managed 執行緒狀態
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55409cd2c3bed2bc09db10622de1cceab934112
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47235279"
---
# <a name="managed-thread-states"></a>Managed 執行緒狀態
屬性 <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> 提供位元遮罩，表示執行緒的目前狀態。 執行緒一律是在 <xref:System.Threading.ThreadState> 列舉至少一個可能的狀態中，而且可能同時在多個狀態中。  
  
> [!IMPORTANT]
>  執行緒狀態只有在少數偵錯案例中有意義。 您的程式碼絕對不應該使用執行緒狀態來同步處理執行緒活動。  
  
 當您建立 Managed 執行緒時，它是在 <xref:System.Threading.ThreadState.Unstarted> 狀態。 執行緒會保留在 <xref:System.Threading.ThreadState.Unstarted> 狀態，直到它被作業系統移至啟動的狀態。 呼叫 <xref:System.Threading.Thread.Start%2A> 可讓作業系統知道，可以啟動執行緒，但不會變更執行緒的狀態。  
  
 進入 Managed 環境的 Unmanaged 執行緒已經處於啟動狀態。 一旦執行緒處於啟動狀態，有數個動作可能會導致它變更狀態。 下表列出會導致變更狀態的動作，以及對應的新狀態。  
  
|動作|產生新狀態|  
|------------|-------------------------|  
|呼叫 <xref:System.Threading.Thread> 類別的建構函式。|<xref:System.Threading.ThreadState.Unstarted>|  
|另一個執行緒呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.Unstarted>|  
|執行緒回應 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>，並開始執行。|<xref:System.Threading.ThreadState.Running>|  
|執行緒呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|執行緒對另一個物件呼叫 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|執行緒對另一個執行緒呼叫 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|另一個執行緒呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.SuspendRequested>|  
|執行緒回應 <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 要求。|<xref:System.Threading.ThreadState.Suspended>|  
|另一個執行緒呼叫 <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.Running>|  
|另一個執行緒呼叫 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.AbortRequested>|  
|執行緒回應 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。|<xref:System.Threading.ThreadState.Aborted>，然後 <xref:System.Threading.ThreadState.Stopped>|  
  
 因為 <xref:System.Threading.ThreadState.Running> 狀態的值為 0，不可能執行位元測試，以探索此狀態。 相反地，您可以使用下列測試 (在虛擬程式碼中)：  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 執行緒經常在任何指定時間處於多個狀態。 比方說，如果執行緒在 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 呼叫上被阻擋，而另一個執行緒對相同執行緒呼叫 <xref:System.Threading.Thread.Abort%2A>，執行緒就會同時處於 <xref:System.Threading.ThreadState.WaitSleepJoin> 和 <xref:System.Threading.ThreadState.AbortRequested> 狀態。 在此情況下，當執行緒從呼叫返回 <xref:System.Threading.Monitor.Wait%2A> 或是遭到中斷時，就會收到 <xref:System.Threading.ThreadAbortException>。  
  
 一旦執行緒因為呼叫 <xref:System.Threading.ThreadState.Unstarted> 而離開 <xref:System.Threading.Thread.Start%2A>狀態，它便無法再回到 <xref:System.Threading.ThreadState.Unstarted> 狀態。 執行緒永遠無法離開 <xref:System.Threading.ThreadState.Stopped> 狀態。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadState>  
- [執行緒處理](../../../docs/standard/threading/index.md)
