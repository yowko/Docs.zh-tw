---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bd248133bd95ff05246eb36a8e250247fd7ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle>類別可讓執行緒信號和等候信號與對方進行通訊。 事件等候控制代碼 （也稱為事件） 都可以接收信號，才能發行一或多個等候中執行緒的等候控制代碼。 收到信號之後，手動或自動，會重設事件等候控制代碼。 <xref:System.Threading.EventWaitHandle>類別可代表其中一個本機事件等候控制代碼 （本機事件），或在具名的系統事件等候控制代碼 （名為可見的所有處理程序的系統事件）。  
  
> [!NOTE]
>  事件等候控制代碼不是在概念上，通常是由這個文字的.NET Framework 中的事件。 沒有委派或事件處理常式。 「 事件 」 用來描述它們，因為它們具有傳統上稱為作業系統事件，而且發出信號，等候控制代碼的動作表示等候中執行緒已發生事件。  
  
 這兩個本機和具名事件等候控制代碼使用系統同步處理物件，後者會受到保護<xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>包裝函式，以確保會釋放資源。 您可以使用<xref:System.Threading.WaitHandle.Dispose%2A>方法，當您完成使用物件立即釋放資源。  
  
## <a name="event-wait-handles-that-reset-automatically"></a>自動重設事件等候控制代碼  
 指定建立的自動重設事件<xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType>當您建立<xref:System.Threading.EventWaitHandle>物件。 正如其名，這個同步處理事件會自動重設時收到信號之後釋出單一的等候執行緒。 發出事件訊號藉由呼叫其<xref:System.Threading.EventWaitHandle.Set%2A>方法。  
  
 自動重設事件通常用於一次提供單一執行緒的獨佔存取權的資源。 執行緒藉由呼叫要求資源<xref:System.Threading.WaitHandle.WaitOne%2A>方法。 如果沒有其他執行緒正在等候控制代碼，則方法會傳回`true`和呼叫端執行緒可以控制的資源。  
  
> [!IMPORTANT]
>  如同所有的同步處理機制，您必須確定所有程式碼路徑等候適當的等候控制代碼上才能存取受保護的資源。 執行緒同步處理是合作式。  
  
 如果自動重設事件收到信號時沒有執行緒等候，它會保留信號直到執行緒嘗試在其上等候。 事件會釋放執行緒，並立即重設，封鎖後續的執行緒。  
  
## <a name="event-wait-handles-that-reset-manually"></a>事件等候控制代碼，手動重設  
 指定建立手動重設事件<xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType>當您建立<xref:System.Threading.EventWaitHandle>物件。 正如其名，這個同步處理事件必須手動重設之後尚未收到信號。 重設，藉由呼叫其<xref:System.Threading.EventWaitHandle.Reset%2A>方法，等候事件控制代碼的執行緒立即繼續進行而不會封鎖。  
  
 手動重設事件的作用與閘道圍欄一樣。 事件未收到信號時封鎖在其等候的執行緒，就像是圍欄中。 事件通知的時間，藉由呼叫其<xref:System.Threading.EventWaitHandle.Set%2A>方法，所有的等候中執行緒可用以繼續。 事件會保留已收到信號，直到其<xref:System.Threading.EventWaitHandle.Reset%2A>方法呼叫。 這可讓手動重設事件保留執行緒需要等候一個執行緒完成工作的理想方式。  
  
 就像是離開圍欄，這需要釋放執行緒排程作業系統，並繼續執行的時間。 如果<xref:System.Threading.EventWaitHandle.Reset%2A>方法在所有執行緒已都繼續執行之前呼叫，再次封鎖，剩餘的執行緒。 繼續執行與哪一個執行緒會封鎖取決於隨機因素，例如在系統上，執行緒數目負載等候排程器等等。 如果通知事件的執行緒結束後發出訊號，這是最常見的使用模式，這並不是問題。 如果您想要開始新的工作在所有對事件發出信號等候執行緒都繼續執行的執行緒，您必須有繼續所有等候中執行緒，直到它封鎖。 否則，您有競爭情形，，程式碼的行為無法預期。  
  
## <a name="features-common-to-automatic-and-manual-events"></a>自動和手動事件通用的功能  
 一般而言，一個或多個執行緒封鎖<xref:System.Threading.EventWaitHandle>之前解除封鎖的執行緒呼叫<xref:System.Threading.EventWaitHandle.Set%2A>方法，這個方法會釋放其中一個等候執行緒 （如果是自動重設事件），或全都 （如果是手動重設事件）。 執行緒可以發出信號<xref:System.Threading.EventWaitHandle>再封鎖，成為不可部分完成的作業，藉由呼叫靜態<xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType>方法。  
  
 <xref:System.Threading.EventWaitHandle>物件可以用具有靜態<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>和<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>方法。 因為<xref:System.Threading.EventWaitHandle>和<xref:System.Threading.Mutex>類別都衍生自<xref:System.Threading.WaitHandle>，您可以使用這兩個類別使用這些方法。  
  
### <a name="named-events"></a>具名的事件  
 Windows 作業系統可讓事件等候控制代碼具有的名稱。 具名的事件是全系統性的。 也就是說，一旦建立具名的事件時，即顯示所有處理序中的所有執行緒。 因此，具名的事件可用來同步處理程序及執行緒的活動。  
  
 您可以建立<xref:System.Threading.EventWaitHandle>物件，使用指定的事件名稱的建構函式的其中一個表示具名的系統事件。  
  
> [!NOTE]
>  因為具名的事件是全系統，所以可能有多個<xref:System.Threading.EventWaitHandle>物件，代表相同具名事件。 每次呼叫建構函式，或<xref:System.Threading.EventWaitHandle.OpenExisting%2A>方法中，新<xref:System.Threading.EventWaitHandle>建立物件。 重複指定相同的名稱，建立多個代表相同的具名的事件的物件。  
  
 請謹慎地使用具名事件。 因為它們是全系統時，會使用相同名稱的另一個處理序可以意外封鎖執行緒。 在同一部電腦上執行的惡意程式碼便可使用此點作為拒絕服務攻擊的基礎。  
  
 使用存取控制安全性來保護<xref:System.Threading.EventWaitHandle>物件，代表具名的事件，最好是使用指定的建構函式<xref:System.Security.AccessControl.EventWaitHandleSecurity>物件。 您也可以套用存取控制安全性使用<xref:System.Threading.EventWaitHandle.SetAccessControl%2A>方法，但這離開視窗中的弱點可能會建立事件等候控制代碼時受到保護的時間之間。 保護事件使用存取控制安全性可以協助防止惡意攻擊，但不能解決意外名稱衝突的問題。  
  
> [!NOTE]
>  不同於<xref:System.Threading.EventWaitHandle>類別，衍生的類別<xref:System.Threading.AutoResetEvent>和<xref:System.Threading.ManualResetEvent>可以在本機的代表等候控制代碼。 它們不能代表具名的系統事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
