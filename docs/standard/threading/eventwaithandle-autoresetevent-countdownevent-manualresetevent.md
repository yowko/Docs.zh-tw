---
title: "EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
事件等候控制代碼可讓執行緒藉由互相發出訊號並等候彼此的信號來同步處理活動。 這些同步處理事件是以 Win32 等候控制代碼為基礎，可以分成兩種類型︰收到訊號時自動重設的事件，以及手動重設的事件。  
  
 事件等候控制代碼可用於許多相同的同步處理案例，做為<xref:System.Threading.Monitor>類別。 事件等候控制代碼通常會比容易使用<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>和<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>方法，而且它們提供更充分掌控發出訊號。 具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是位於應用程式定義域內。  
  
## <a name="in-this-section"></a>本章節內容  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle>類別可代表可能是自動或手動重設事件，以及其中一個本機事件，或具名系統事件。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent>類別衍生自<xref:System.Threading.EventWaitHandle>和表示本機事件，會自動重設。  
  
 [ManualResetEvent 和 ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent>類別衍生自<xref:System.Threading.EventWaitHandle>代表必須以手動方式重設本機事件。 <xref:System.Threading.ManualResetEventSlim>類別是輕量型、 更快速的版本可以用於在相同的程序中的事件。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent>類別會提供一個簡化的方式來使用等候控制代碼的程式碼中實作分岔/聯結的平行處理原則的模式。  
  
## <a name="related-sections"></a>相關章節  
 [等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle>類別是基底類別<xref:System.Threading.EventWaitHandle>， <xref:System.Threading.Semaphore>，和<xref:System.Threading.Mutex>類別。 其中包含靜態方法，例如<xref:System.Threading.WaitHandle.SignalAndWait%2A>和<xref:System.Threading.WaitHandle.WaitAll%2A>使用所有類型的等候控制代碼時，會很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Managed 執行緒處理的基本概念](../../../docs/standard/threading/managed-threading-basics.md)
