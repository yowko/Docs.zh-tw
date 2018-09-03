---
title: EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f818ecf52ae1179d6d32d0b76cea3cc2a8f36ea8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43416408"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。 這些同步處理事件是以 Win32 等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。  
  
 在與 <xref:System.Threading.Monitor> 類別相同的許多同步處理案例中，事件等候控制代碼很有用。 事件等候控制代碼通常會比 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> 方法更容易使用，而且它們更能掌控訊號的傳送。 具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。  
  
## <a name="in-this-section"></a>本節內容  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> 類別可代表自動或手動重設事件以及本機事件或具名系統事件。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表會自動重設的本機事件。  
  
 [ManualResetEvent 和 ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，並代表必須手動重設的本機事件。 <xref:System.Threading.ManualResetEventSlim> 類別是更快速的輕量型版本，可用於相同處理序中的事件。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> 類別提供一個簡化的方式，可在使用等候控制代碼的程式碼中實作分支/聯結平行處理原則模式。  
  
## <a name="related-sections"></a>相關章節  
 [等候控制代碼](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> 類別是 <xref:System.Threading.EventWaitHandle>、<xref:System.Threading.Semaphore> 及 <xref:System.Threading.Mutex> 類別的基底類別。 其中包含 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 和 <xref:System.Threading.WaitHandle.WaitAll%2A> 之類的靜態方法，在搭配所有類型的等候控制代碼運作時很實用。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Managed 執行緒處理的基本概念](../../../docs/standard/threading/managed-threading-basics.md)
