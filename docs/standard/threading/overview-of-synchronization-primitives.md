---
title: 同步處理原始物件概觀
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35c2337ff7e416cb5f2c869f8ede160e05d369f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-synchronization-primitives"></a>同步處理原始物件概觀
<a name="top"></a>.NET Framework 提供同步處理原始物件的範圍，以便控制執行緒的互動，及避免競爭情形。 這些可以大致分為三個類別：鎖定、信號及連鎖作業。  
  
 這些分類不整齊，也未清楚定義：某些同步處理機制具有多個分類的特性，一次釋放單一執行緒的事件其作用就像是鎖定，釋放任何鎖定可以視為信號，而連鎖作業可以用來建構鎖定。 不過，類別仍然很有用。  
  
 請務必記得執行緒同步處理是合作式的。 如果即使一個執行緒略過同步處理機制，並直接存取受保護的資源，該同步處理機制便無法有效。  
  
 本概觀包含下列各節：  
  
-   [鎖定](#locking)  
  
-   [訊號](#signaling)  
  
-   [輕量型同步處理類型](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Interlocked 作業](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>鎖定  
 鎖定能提供資源的控制，一次給一個執行緒，或給指定數目的執行緒。 正在使用鎖定時要求獨佔鎖定的執行緒會封鎖，直到鎖定可用為止。  
  
### <a name="exclusive-locks"></a>獨佔鎖定  
 鎖定的最簡單形式是 C# 中的 `lock` 陳述式和 Visual Basic 中的 `SyncLock` 陳述式，它能控制程式碼區塊的存取權。 這類區塊經常稱為重要區段。 `lock` 陳述式是透過使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> 方法實作，且它會使用 `try…catch…finally` 區塊以確保釋放鎖定。  
  
 一般而言，使用 `lock` 或 `SyncLock` 陳述式保護小型區塊的程式碼，永遠不會跨越超出單一方法，是使用 <xref:System.Threading.Monitor> 類別最佳的方式。 雖然功能強大，但 <xref:System.Threading.Monitor> 類別容易發生遺棄的鎖定和死結。  
  
#### <a name="monitor-class"></a>Monitor 類別  
 <xref:System.Threading.Monitor> 類別會提供額外的功能，可以用於搭配 `lock` 陳述式：  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> 方法可讓遭到封鎖而等待資源的執行緒在指定的間隔之後放棄。 它會傳回布林值，指出成功或失敗，可用來偵測及避免可能的死結。  
  
-   <xref:System.Threading.Monitor.Wait%2A> 方法由重要區段中的執行緒呼叫。 它會放棄資源的控制權並封鎖直到資源再次可用為止。  
  
-   <xref:System.Threading.Monitor.Pulse%2A> 和 <xref:System.Threading.Monitor.PulseAll%2A> 方法可以讓即將要釋放鎖定，或呼叫 <xref:System.Threading.Monitor.Wait%2A> 的執行緒，將一或多個執行緒放入就緒佇列，使它們可以取得鎖定。  
  
 <xref:System.Threading.Monitor.Wait%2A> 方法多載上的等候逾時可讓等候中的執行緒可以逸出到就緒佇列。  
  
 <xref:System.Threading.Monitor> 類別可提供多個應用程式定義域中的鎖定 (如果用於鎖定的物件衍生自 <xref:System.MarshalByRefObject> 的話)。  
  
 <xref:System.Threading.Monitor> 具有執行緒相似性。 也就是進入監視器的執行緒必須藉由呼叫 <xref:System.Threading.Monitor.Exit%2A> 或 <xref:System.Threading.Monitor.Wait%2A> 結束。  
  
 <xref:System.Threading.Monitor> 類別無法具現化。 其方法是靜態的 (在 Visual Basic 中為 `Shared`)，並且會對可具現化的鎖定物件進行操作。  
  
 如需概念的概觀，請參閱[監視器](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)。  
  
#### <a name="mutex-class"></a>Mutex 類別  
 執行緒藉由呼叫其 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法的多載來要求 <xref:System.Threading.Mutex>。 會提供具有逾時的多載，好讓執行緒放棄等候。 不同於 <xref:System.Threading.Monitor> 類別，mutex 可以是本機或全域。 全域 mutex，也稱為具名 mutex，可在作業系統各處看到，並可以用來同步處理多個應用程式定義域或處理序中的執行緒。 本機 mutex 衍生自 <xref:System.MarshalByRefObject>，而且可以跨應用程式定義域界限使用。  
  
 此外，<xref:System.Threading.Mutex> 衍生自 <xref:System.Threading.WaitHandle>，這表示它可以搭配 <xref:System.Threading.WaitHandle> 所提供的發出訊號機制使用，例如 <xref:System.Threading.WaitHandle.WaitAll%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A> 和 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 方法。  
  
 像 <xref:System.Threading.Monitor> 一樣，<xref:System.Threading.Mutex> 具有執行緒相似性。 不同於 <xref:System.Threading.Monitor>，<xref:System.Threading.Mutex> 是可具現化的物件。  
  
 如需概念的概觀，請參閱 [Mutex](../../../docs/standard/threading/mutexes.md)。  
  
#### <a name="spinlock-class"></a>SpinLock 類別  
 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，當 <xref:System.Threading.Monitor> 所需的額外負荷降低效能時，您可以使用 <xref:System.Threading.SpinLock> 類別。 當 <xref:System.Threading.SpinLock> 遇到已鎖定的重要區段，它只會迴圈旋轉，直到鎖定可用為止。 如果鎖定維持的時間極短，旋轉可以提供比封鎖較佳的效能。 不過，如果鎖定維持時間超過數十個循環，<xref:System.Threading.SpinLock> 的效能和 <xref:System.Threading.Monitor> 相同，但會使用更多的 CPU 循環，因此可能會降低其他執行緒或處理序的效能。  
  
### <a name="other-locks"></a>其他鎖定  
 鎖定不需要獨佔。 允許有限數量的執行緒並行存取資源通常很有用。 號誌和 Reader-Writer 鎖定是設計來控制這種共用的資源存取。  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock 類別  
 <xref:System.Threading.ReaderWriterLockSlim> 類別會處理變更資料的執行緒 (寫入器) 必須對資源具有獨佔存取權的情況。 當寫入器不在使用中時，任何數目的讀取器都可以存取資源 (例如，藉由呼叫 <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> 方法)。 當執行緒要求獨佔存取權 (例如，藉由呼叫 <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> 方法)，後續的讀取器要求會封鎖直到所有現有讀取器都結束鎖定，且寫入器已進入並離開鎖定為止。  
  
 <xref:System.Threading.ReaderWriterLockSlim> 具有執行緒相似性。  
  
 如需概念的概觀，請參閱 [Reader-Writer 鎖定](../../../docs/standard/threading/reader-writer-locks.md)。  
  
#### <a name="semaphore-class"></a>Semaphore 類別  
 <xref:System.Threading.Semaphore> 類別可讓指定數目的執行緒存取資源。 要求資源的其他執行緒會封鎖直到執行緒釋放號誌為止。  
  
 和 <xref:System.Threading.Mutex> 類別一樣，<xref:System.Threading.Semaphore> 衍生自 <xref:System.Threading.WaitHandle>。 也像 <xref:System.Threading.Mutex> 一樣，<xref:System.Threading.Semaphore> 可以是本機或全域。 它可以跨應用程式定義域界限使用。  
  
 不同於 <xref:System.Threading.Monitor>，<xref:System.Threading.Mutex> 和 <xref:System.Threading.ReaderWriterLock>，<xref:System.Threading.Semaphore> 沒有執行緒相似性。 這表示它可用於一個執行緒取得號誌，而另一個釋放號誌的案例。  
  
 如需概念的概觀，請參閱 [Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)。  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> 是輕量型號誌，可用於在單一處理序界限內的同步處理。  
  
 [回到頁首](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Signaling  
 等待來自另一個執行緒之信號的最簡單方式，就是呼叫 <xref:System.Threading.Thread.Join%2A> 方法，它會封鎖直到另一個執行緒完成為止。 <xref:System.Threading.Thread.Join%2A> 有兩個多載，可讓封鎖的執行緒在經過指定的間隔之後突破等候。  
  
 等候控制代碼會提供一組更豐富的等候和信號功能。  
  
### <a name="wait-handles"></a>等候控制代碼  
 等候控制代碼衍生自 <xref:System.Threading.WaitHandle> 類別，而後者又是衍生自 <xref:System.MarshalByRefObject>。 因此，等候控制代碼可來跨應用程式定義域界限同步處理執行緒的活動。  
  
 執行緒會封鎖在等候控制代碼，方法是呼叫執行個體方法 <xref:System.Threading.WaitHandle.WaitOne%2A> 或其中一個靜態方法 <xref:System.Threading.WaitHandle.WaitAll%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A> 或 <xref:System.Threading.WaitHandle.SignalAndWait%2A>。 釋放的方式取決於所呼叫的方法，以及等候控制代碼的類型。  
  
 如需概念的概觀，請參閱[等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)。  
  
#### <a name="event-wait-handles"></a>事件等候控制代碼  
 事件等候控制代碼包括 <xref:System.Threading.EventWaitHandle> 類別和其衍生的類別，<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent>。 事件等候控制代碼藉由呼叫其 <xref:System.Threading.EventWaitHandle.Set%2A> 方法或使用 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 方法而收到信號時，執行緒會從事件等候控制代碼釋放。  
  
 事件等候控制代碼會自動重設自己 (就像是每次收到信號時只允許一個執行緒通過的閘門)，或必須手動重設 (就像是大門會關閉直到收到信號為止，然後開啟直到有人關閉它為止)。 顧名思義，<xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent> 分別代表前者與後者。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 是輕量型事件，可用於在單一處理序界限內的同步處理。  
  
 <xref:System.Threading.EventWaitHandle> 可以代表任一種事件，而且可以是本機或全域。 衍生的類別 <xref:System.Threading.AutoResetEvent> 和 <xref:System.Threading.ManualResetEvent> 一律是本機。  
  
 事件等候控制代碼沒有執行緒相似性。 任何執行緒可以發出信號給事件等候控制代碼。  
  
 如需概念的概觀，請參閱 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)。  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex 和 Semaphore 類別  
 因為 <xref:System.Threading.Mutex> 和 <xref:System.Threading.Semaphore> 類別衍生自 <xref:System.Threading.WaitHandle>，它們可以搭配 <xref:System.Threading.WaitHandle> 的靜態方法使用。 例如，執行緒可以使用 <xref:System.Threading.WaitHandle.WaitAll%2A> 方法等候，直到下列三個條件全都成立：<xref:System.Threading.EventWaitHandle> 收到信號、<xref:System.Threading.Mutex> 已釋放，且 <xref:System.Threading.Semaphore> 已釋放。 同樣地，執行緒可以使用 <xref:System.Threading.WaitHandle.WaitAny%2A> 方法等候，直到其中一個情況成立。  
  
 針對 <xref:System.Threading.Mutex> 或 <xref:System.Threading.Semaphore>，收到信號表示被釋放。 如果其中一種類型做為 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 方法的第一個引數，它會被釋放。 如果是具有執行緒相似性的 <xref:System.Threading.Mutex>，如果呼叫的執行緒未擁有 mutex，便會擲回例外狀況。 如先前所述，號誌沒有執行緒相似性。  
  
#### <a name="barrier"></a>屏障  
 <xref:System.Threading.Barrier> 類別提供循環同步處理多個執行緒的方法，使它們全都封鎖在相同的點，並等候所有其他執行緒完成。 當一或多個執行緒需要另一個執行緒的結果，才能繼續到演算法的下一個階段時，屏障很有用。 如需詳細資訊，請參閱[屏障](../../../docs/standard/threading/barrier.md)。  
  
 [回到頁首](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>輕量型同步處理類型  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，您可以使用同步處理原始物件，它們會藉由儘可能避免對 Win32 核心物件 (例如等候控制代碼) 的昂貴依賴，來提供快速效能。 一般而言，您應該在等候時間很短，且原始同步處理類型已經嘗試過且發現無法令人滿意時，才使用這些類型。 輕量型的類型無法用在需要跨處理序通訊的情節。  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> 是 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 的輕量版。  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 是 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 的輕量版。  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 代表當計數為零時收到信號的事件。  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> 可讓多個執行緒彼此同步處理，而不需要由主要執行緒控制。 屏障可防止每個執行緒繼續，直到所有執行緒都已達到指定的點。  
  
 [回到頁首](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，當執行緒必須等待事件收到訊號或符合條件，但實際的等待時間預期會少於使用等候控制代碼或以其他方式封鎖目前執行緒的等候時間時，您可以使用 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 結構。 使用 <xref:System.Threading.SpinWait>，您可以指定在等待時旋轉一小段時間，並且只有在指定的時間內未符合條件時放棄 (例如，藉由等待或睡眠)。  
  
 [回到頁首](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Interlocked 作業  
 連鎖的作業是由 <xref:System.Threading.Interlocked> 類別的靜態方法，在記憶體位置上執行的簡單不可部分完成作業。 這些不可部分完成的作業包括對 32 位元平台上之 64 位元值的相加、遞增和遞減、交換、根據比較結果的條件式交換，和讀取作業。  
  
> [!NOTE]
>  不可部分完成性保證僅限於個別作業；當必須執行多項作業當做一個單位時，必須使用更廣泛的同步處理機制。  
  
 雖然這些作業都不是鎖定或號誌，它們可用來建構鎖定和信號。 因為它們是 Windows 作業系統的原生作業，連鎖的作業都極為快速。  
  
 連鎖的作業可以搭配暫時性記憶體保證使用，撰寫呈現功能強大的非封鎖並行性的應用程式。 不過，它們需要精密、低階程式設計，因此大部分用途而言，簡單鎖定是較好的選擇。  
  
 如需概念的概觀，請參閱[連鎖作業](../../../docs/standard/threading/interlocked-operations.md)。  
  
## <a name="see-also"></a>請參閱  
 [同步處理多執行緒處理的資料](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [監視](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Mutex](../../../docs/standard/threading/mutexes.md)  
 [Semaphore 和 SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [等候控制代碼](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [Interlocked 作業](../../../docs/standard/threading/interlocked-operations.md)  
 [Reader-Writer 鎖定](../../../docs/standard/threading/reader-writer-locks.md)  
 [barrier](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
