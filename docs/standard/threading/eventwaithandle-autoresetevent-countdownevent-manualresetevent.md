---
title: EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9c858d7c76fdcc1b3e02485eb0b459f4e7555c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47205914"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent

事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。 這些同步處理事件是以作業系統等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。  
  
在與 <xref:System.Threading.Monitor> 類別相同的許多同步處理案例中，事件等候控制代碼很有用。 事件等候控制代碼通常會比 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> 方法更容易使用，而且它們更能掌控訊號的傳送。 具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。  
  
## <a name="in-this-section"></a>本節內容

 [EventWaitHandle](eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 類別可代表自動或手動重設事件以及本機事件或具名系統事件。  
  
 [AutoResetEvent](autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表會自動重設的本機事件。  
  
 [ManualResetEvent 和 ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表必須手動重設的本機事件。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別是更快速的輕量型版本，可用於相同處理序中的事件。  
  
 [CountdownEvent](countdownevent.md)  
 <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 類別提供一個簡化的方式，可在使用等候控制代碼的程式碼中實作分支/聯結平行處理原則模式。  

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [執行緒物件和功能](threading-objects-and-features.md)
- [Managed 執行緒處理的基本概念](managed-threading-basics.md)
