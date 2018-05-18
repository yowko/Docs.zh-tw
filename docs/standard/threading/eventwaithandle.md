---
title: EventWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697820b01bd629baa306d96002a98d92e44dab51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> 類別可讓執行緒藉由發出訊號及等候訊號來互相進行通訊。 事件等候控制代碼 (也簡單稱為事件) 是可接收訊號來釋出一或多個等候執行緒的等候控制代碼。 收到訊號之後，可以手動或自動重設事件等候控制代碼。 <xref:System.Threading.EventWaitHandle> 類別可以代表本機事件等候控制代碼 (本機事件) 或具名的系統事件等候控制代碼 (所有處理序都可看見的具名事件或系統事件)。  
  
> [!NOTE]
>  事件等候控制代碼的事件意義與該字在 .NET Framework 中通常所代表的意義不同。 其中並不涉及任何委派或事件處理常式。 「事件」一字是用來描述它們，因為傳統上將它們稱為作業系統事件，並且因為向等候控制代碼發出訊號的動作會向等候執行緒指出某個事件已發生。  
  
 本機和具名事件等候控制代碼都會使用系統同步處理作業物件，<xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> 包裝函式會保護這些物件以確保資源被釋出。 當您已使用完物件時，可以使用 <xref:System.Threading.WaitHandle.Dispose%2A> 方法來立即釋出資源。  
  
## <a name="event-wait-handles-that-reset-automatically"></a>自動重設的事件等候控制代碼  
 您可以在建立 <xref:System.Threading.EventWaitHandle> 物件時指定 <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType>，來建立自動重設事件。 正如其名，此同步處理事件在收到訊號並釋出一個等候執行緒之後，就會自動重設。 請呼叫事件的 <xref:System.Threading.EventWaitHandle.Set%2A> 方法來對事件發出訊號。  
  
 自動重設事件通常用來一次為一個執行緒提供資源的獨佔存取權。 執行緒會透過呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法來要求資源。 如果沒有任何其他執行緒持有等候控制代碼，該方法就會傳回 `true`，而發出呼叫的執行緒就會擁有資源的控制權。  
  
> [!IMPORTANT]
>  與使用所有同步處理機制時相同，您必須確保所有程式碼路徑在存取受保護的資源之前，先等候適當的等候控制代碼。 執行緒同步處理是採用合作方式。  
  
 如果自動重設事件在沒有任何執行緒處於等候狀態時收到訊號，它會維持收到訊號的狀態，直到有執行緒嘗試等候它為止。 此事件會釋出執行緒並立即重設，以阻斷後續的執行緒。  
  
## <a name="event-wait-handles-that-reset-manually"></a>手動重設的事件等候控制代碼  
 您可以在建立 <xref:System.Threading.EventWaitHandle> 物件時指定 <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType>，來建立手動重設事件。 正如其名，您必須在此同步處理事件收到訊號之後，以手動方式重設它。 在此事件被重設之前，等候事件控制代碼的執行緒可藉由呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法來立即繼續進行而不受阻斷。  
  
 手動重設事件就像圍欄的閘門一樣。 當事件沒有收到訊號時，等候它的執行緒會被阻斷，就像圍欄中的馬一樣。 當事件收到訊號時，只要呼叫其 <xref:System.Threading.EventWaitHandle.Set%2A> 方法，所有等候中的執行緒便可自由繼續進行。 事件會維持收到訊號的狀態，直到其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法被呼叫為止。 這使得手動重設事件成為一種理想的方式，來攔住必須等候某個執行緒完成工作的執行緒。  
  
 與離開圍欄的馬一樣，作業系統需要時間來排定釋出的執行緒並讓它們繼續執行。 如果在所有執行緒繼續執行之前呼叫 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法，剩餘的執行緒就會再次遭到阻斷。 哪些執行緒會繼續執行及哪些執行緒會遭到阻斷，取決於系統上的負載、等候排程器的執行緒數量等隨機因素。 如果向事件發出訊號的執行緒在發出訊號後結束，這就不成問題，這也是最常見的使用模式。 如果您想要讓向事件發出訊號的執行緒在所有等候中執行緒都繼續執行之後開始新的工作，就必須阻斷它，直到所有等候中執行緒都已繼續執行為止。 否則，會發生競爭情形，而無法預測您的程式碼行為。  
  
## <a name="features-common-to-automatic-and-manual-events"></a>自動和手動事件的常見功能  
 通常 <xref:System.Threading.EventWaitHandle> 上會有一或多個執行緒被阻斷，直到未遭阻斷的執行緒呼叫 <xref:System.Threading.EventWaitHandle.Set%2A> 方法為止，這會釋出其中一個等候中的執行緒 (在自動重設事件的案例中) 或所有等候中的執行緒 (在手動重設事件的案例中)。 執行緒可以藉由呼叫靜態 <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> 方法，向 <xref:System.Threading.EventWaitHandle> 發出訊號，然後被阻斷，整個作業一氣呵成。  
  
 <xref:System.Threading.EventWaitHandle> 物件可以與靜態的 <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> 方法搭配使用。 由於 <xref:System.Threading.EventWaitHandle> 和 <xref:System.Threading.Mutex> 類別都衍生自 <xref:System.Threading.WaitHandle>，因此您可以將這兩個類別與這些方法搭配使用。  
  
### <a name="named-events"></a>具名事件  
 Windows 作業系統允許事件等候控制代碼擁有名稱。 具名事件是全系統性的。 也就是說，一旦建立具名事件，所有處理序中的所有執行緒都可看到它。 因此，具名事件既可用來同步處理執行緒，也可用來同步處理處理序的活動。  
  
 您可以使用其中一個指定名稱的建構函式，來建立代表具名系統事件的 <xref:System.Threading.EventWaitHandle> 物件。  
  
> [!NOTE]
>  由於具名事件是全系統性的，因此可以有多個代表相同具名事件的 <xref:System.Threading.EventWaitHandle> 物件。 每次呼叫建構函式或 <xref:System.Threading.EventWaitHandle.OpenExisting%2A> 方法時，都會建立新的 <xref:System.Threading.EventWaitHandle> 物件。 如果重複指定相同的名稱，就會建立多個代表相同具名事件的物件。  
  
 使用具名事件時，請務必謹慎。 由於這些事件是全系統性的，因此如果有另一個處理序使用相同的名稱，就可能意外阻斷您的執行緒。 在同一部電腦上執行的惡意程式碼便可使用此點作為拒絕服務攻擊的基礎。  
  
 請使用存取控制安全性來保護代表具名事件的 <xref:System.Threading.EventWaitHandle> 物件，最好是使用指定 <xref:System.Security.AccessControl.EventWaitHandleSecurity> 物件的建構函式。 您也可以使用 <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> 方法來套用存取控制安全性，但這會在事件等候控制代碼的建立時間與受保護時間之間，留下一段有弱點的空窗期。 使用存取控制安全性來保護事件有助於防止惡意攻擊，但並無法解決意外名稱衝突問題。  
  
> [!NOTE]
>  不同於 <xref:System.Threading.EventWaitHandle> 類別，衍生的類別 <xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent> 只能代表本機等候控制代碼。 它們無法代表具名系統事件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
