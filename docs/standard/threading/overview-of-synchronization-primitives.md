---
title: 同步處理原始物件概觀
description: 了解用來同步對共用資源的存取或控制執行緒互動的 .NET 執行緒同步處理原始物件
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d1010069e9d95488a99133f949ca112dc08f0e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201594"
---
# <a name="overview-of-synchronization-primitives"></a>同步處理原始物件概觀

.NET 提供可用來同步對共用資源的存取或協調執行緒互動的一系列類型。

> [!IMPORTANT]
> 使用相同的同步處理原始物件執行個體，來保護對共用資源的所有存取。 如果您使用不同的同步處理原始物件執行個體，來保護對資源或程式碼會直接存取資源之部分的存取，則多個執行緒便可以並行存取某個資源。

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle 類別和輕量型同步處理類別

衍生自 <xref:System.Threading.WaitHandle?displayProperty=nameWithType> 類別的多個 .NET 同步處理原始物件，它能封裝原生作業系統同步處理控制代碼，並針對執行緒互動使用訊號機制。 那些類別包括：

- <xref:System.Threading.Mutex?displayProperty=nameWithType>，它能授與對共用資源的獨佔存取權。 如果沒有任何執行緒擁有 Mutex，則 Mutex 的狀態為已發出訊號。
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>，它能限制可以同時存取共用資源或資源集區的執行緒數目。 旗號的狀態會在其計數大於零時設定為已收到訊號，並在計數為零時設定為未收到訊號。
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>，它代表執行緒同步處理事件，並可以處於已收到訊號或未收到訊號的狀態。
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>，它衍生自 <xref:System.Threading.EventWaitHandle>，且在收到訊號時，會在發佈單一等候執行緒之後自動重設至未收到訊號的狀態。
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>，它衍生自 <xref:System.Threading.EventWaitHandle>，且在收到訊號時會持續處於已收到訊號的狀態，直到 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法被呼叫為止。

在 .NET Framework 中，由於 <xref:System.Threading.WaitHandle> 是衍生自 <xref:System.MarshalByRefObject?displayProperty=nameWithType>，因此這些類型可用來跨應用程式定義域界限同步處理執行緒的活動。

在 .NET Framework 與 .NET Core 中，這些類型有一部分可以代表具名系統同步處理控制代碼；其於整個作業系統中皆可見，並可以用來進行處理序間的同步處理：

- <xref:System.Threading.Mutex> (.NET Framework 與 .NET Core)，
- <xref:System.Threading.Semaphore> (Windows 上的 .NET Framework 與 .NET Core)，
- <xref:System.Threading.EventWaitHandle> (Windows 上的 .NET Framework 與 .NET Core)。

如需詳細資訊，請參閱 <xref:System.Threading.WaitHandle> API 參考。

輕量型同步處理類型不會仰賴基礎作業系統控制代碼，且通常能提供較佳的效能。 不過，它們並無法用於處理序間的同步處理。 請針對位於單一應用程式內的執行緒同步處理使用那些類型。

那些類型有一部分是衍生自 <xref:System.Threading.WaitHandle> 之類型的替代方案。 例如，<xref:System.Threading.SemaphoreSlim> 是 <xref:System.Threading.Semaphore> 的輕量型替代方案。

## <a name="synchronization-of-access-to-a-shared-resource"></a>對共用資源之存取的同步處理

.NET 提供一系列的同步處理原始物件，以控制多個執行緒對共用資源的存取。

### <a name="monitor-class"></a>Monitor 類別

<xref:System.Threading.Monitor?displayProperty=nameWithType> 類別會透過取得或釋放能識別共用資源之物件上的鎖定，來授與對該資源的互斥存取。 持有鎖定時，持有鎖定的執行緒可以再次取得並釋放鎖定。 其他執行緒將無法取得鎖定，且 <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> 方法會等待直到釋放鎖定為止。 <xref:System.Threading.Monitor.Enter%2A> 方法會取得已釋放的鎖定。 您也可以使用 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> 方法來指定執行緒嘗試取得鎖定的時間長度。 由於 <xref:System.Threading.Monitor> 類別具有執行緒同質性，因此取得鎖定的執行緒必須呼叫 <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> 方法來釋放鎖定。

您可以使用 <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>、<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> 與 <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> 方法來協調在相同物件上取得鎖定之執行緒的互動。

如需詳細資訊，請參閱 <xref:System.Threading.Monitor> API 參考。

> [!NOTE]
> 請使用以 C# 撰寫的 [lock](../../csharp/language-reference/keywords/lock-statement.md) 陳述式，以及使用 Visual Basic 撰寫的 [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) 陳述式來同步對共用資源的存取，而不要直接使用 <xref:System.Threading.Monitor>。 那些陳述式是使用 <xref:System.Threading.Monitor.Enter%2A> 與 <xref:System.Threading.Monitor.Exit%2A> 方法來實作，並會使用 `try…finally` 區塊以確保所取得的鎖定一律會被釋放。

### <a name="mutex-class"></a>Mutex 類別

<xref:System.Threading.Mutex?displayProperty=nameWithType> 類別，它和 <xref:System.Threading.Monitor> 相同，能授與對共用資源的獨佔存取權。 使用其中一個 [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) 方法多載來要求 Mutex 的擁有權。 與 <xref:System.Threading.Monitor> 類似，<xref:System.Threading.Mutex> 具有執行緒同質性，且取得 Mutex 的執行緒必須呼叫 <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> 方法來釋放它。

與 <xref:System.Threading.Monitor> 不同，<xref:System.Threading.Mutex> 類別可以用於處理序間的同步處理。 若要這麼做，請使用具名 Mutex，這能使其於整個作業系統中皆可見。 若要建立具名 Mutex 執行個體，請使用能指定名稱的 [Mutex 建構函式](<xref:System.Threading.Mutex.%23ctor%2A>)。 您也可以呼叫 <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> 方法來開啟現有的具名系統 Mutex。
  
如需詳細資訊，請參閱 [Mutex](mutexes.md) 文章與 <xref:System.Threading.Mutex> API 參考文件。

### <a name="spinlock-structure"></a>SpinLock 結構

<xref:System.Threading.SpinLock?displayProperty=nameWithType> 結構與 <xref:System.Threading.Monitor> 類似，能根據鎖定的可用性授與對共用資源的獨佔存取。 當 <xref:System.Threading.SpinLock> 嘗試取得不可用的鎖定時，它會在迴圈中等候並重複檢查，直到該鎖定變得可用為止。

如需使用微調鎖定之優缺點的詳細資訊，請參閱 [SpinLock](spinlock.md) 文章與 <xref:System.Threading.SpinLock> API 參考。

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim 類別

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> 類別會授與對共用資源進行寫入的獨佔存取權，並允許多個執行緒同時存取該資源以進行讀取。 您應該使用 <xref:System.Threading.ReaderWriterLockSlim> 來同步對支援安全執行緒讀取作業，但需要獨佔存取以執行寫入作業之共用資料結構的存取。 當執行緒要求獨佔存取權 (例如，透過呼叫 <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> 方法)，後續的讀取器要求會封鎖直到所有現有讀取器都結束鎖定，且寫入器已進入並離開鎖定為止。
  
如需詳細資訊，請參閱 [Reader-Writer 鎖定](reader-writer-locks.md)文章與 <xref:System.Threading.ReaderWriterLockSlim> API 參考。

### <a name="semaphore-and-semaphoreslim-classes"></a>旗號與 SemaphoreSlim 類別

<xref:System.Threading.Semaphore?displayProperty=nameWithType> 與 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> 類別能限制可以同時存取共用資源或資源集區的執行緒數目。 要求資源的其他執行緒需等候，直到執行緒釋放旗號為止。 由於旗號不具有執行緒同質性，因此某個執行緒可以取得旗號，並由另一個執行緒釋放它。

<xref:System.Threading.SemaphoreSlim> 是 <xref:System.Threading.Semaphore> 的輕量型替代方案，並僅可用於在單一處理序界限內進行同步處理。

在 Windows 上，您可以使用 <xref:System.Threading.Semaphore> 以進行處理序間的同步處理。 若要這麼做，請使用其中一個能指定名稱的[旗號建構函式](<xref:System.Threading.Semaphore.%23ctor%2A>)或 <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> 方法，建立代表具名系統旗號的 <xref:System.Threading.Semaphore> 執行個體。 <xref:System.Threading.SemaphoreSlim> 不支援具名系統旗號。

如需詳細資訊，請參閱[旗號與 SemaphoreSlim](semaphore-and-semaphoreslim.md) 文章，以及 <xref:System.Threading.Semaphore> 或 <xref:System.Threading.SemaphoreSlim> API 參考。

## <a name="thread-interaction-or-signaling"></a>執行緒互動 (或訊號處理)

執行緒互動 (或執行緒訊號處理) 表示執行緒必須等候來自一或多個執行緒的通知 (或訊號)，才能繼續執行。 例如，如果執行緒 A 呼叫執行緒 B 的 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 方法，在執行緒 B 完成之前，執行緒 A 將會被封鎖。 上一節所描述的同步處理原始物件能提供不同的訊號處理機制：執行緒可以透過釋放鎖定，來通知另一個執行緒其可以取得鎖定來繼續執行。

此節描述由 .NET 提供的其他訊號處理建構。

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle、AutoResetEvent、ManualResetEvent 與 ManualResetEventSlim 類別

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> 類別代表執行緒同步處理事件。

同步處理事件可以處於未收到訊號或已收到訊號的狀態。 當事件的狀態為未收到訊號時，呼叫該事件之 <xref:System.Threading.WaitHandle.WaitOne%2A?> 多載的執行緒會被封鎖，直到事件收到訊號為止。 <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> 方法會將事件的狀態設定為已收到訊號。

已收到訊號之 <xref:System.Threading.EventWaitHandle> 的行為會取決於其重設模式：

- 搭配 <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> 旗標建立的 <xref:System.Threading.EventWaitHandle>，會在發佈單一等候執行緒後自動重設。 它就像是在每次收到訊號時僅允許單一執行緒通過的十字轉門一般。 <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> 類別 (衍生自 <xref:System.Threading.EventWaitHandle>) 代表該行為。
- 搭配 <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> 旗標建立的 <xref:System.Threading.EventWaitHandle> 會維持已收到訊號的狀態，直到其 <xref:System.Threading.EventWaitHandle.Reset%2A> 方法被呼叫為止。 它就像是在收到訊號前會保持關閉，並在有人重新關閉它前會持續開啟的閘門一般。 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 類別 (衍生自 <xref:System.Threading.EventWaitHandle>) 代表該行為。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 類別是 <xref:System.Threading.ManualResetEvent> 的輕量型替代方案。

在 Windows 上，您可以使用 <xref:System.Threading.EventWaitHandle> 以進行處理序間的同步處理。 若要這麼做，請使用其中一個能指定名稱的 [EventWaitHandle 建構函式](<xref:System.Threading.EventWaitHandle.%23ctor%2A>)或 <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> 方法，建立代表具名系統同步處理事件的 <xref:System.Threading.EventWaitHandle> 執行個體。

如需詳細資訊，請參閱 [EventWaitHandle](eventwaithandle.md)、[AutoResetEvent](autoresetevent.md) 與 [ManualResetEvent 與 ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md) 文章。 如需 API 參考，請參閱 <xref:System.Threading.EventWaitHandle>、<xref:System.Threading.AutoResetEvent>、<xref:System.Threading.ManualResetEvent> 與 <xref:System.Threading.ManualResetEventSlim>。

### <a name="countdownevent-class"></a>CountdownEvent 類別

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 類別代表會在計數為零時被設定的事件。 在 <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> 大於零時，呼叫 <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> 的執行緒將會被封鎖。 呼叫 <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> 來使事件的計數遞減。

與可透過來自單一執行緒的訊號將多個執行緒解除封鎖的 <xref:System.Threading.ManualResetEvent> 或 <xref:System.Threading.ManualResetEventSlim> 相反，您可以使用 <xref:System.Threading.CountdownEvent> 以透過來自多個執行緒的訊號，將一或多個執行緒解除封鎖。

如需詳細資訊，請參閱 [CountdownEvent](countdownevent.md) 文章與 <xref:System.Threading.CountdownEvent> API 參考。

### <a name="barrier-class"></a>Barrier 類別

<xref:System.Threading.Barrier?displayProperty=nameWithType> 類別代表執行緒執行屏障。 呼叫 <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> 方法的執行緒會發出其已抵達屏障的訊號，並會持續等候，直到其他參與者執行緒也抵達屏障為止。 當所有參與者執行緒皆抵達屏障時，它們便會繼續執行，而該屏障也會重設並可供再次使用。

當有一或多個執行緒需要取得其他執行緒的結果以繼續至下個運算階段時，您可以使用 <xref:System.Threading.Barrier>。

如需詳細資訊，請參閱[屏障](barrier.md)文章與 <xref:System.Threading.Barrier> API 參考。

## <a name="interlocked-class"></a>Interlocked 類別

<xref:System.Threading.Interlocked?displayProperty=nameWithType> 類別可提供能針對變數執行簡易不可部分完成之作業的靜態方法。 那些不可部分完成的作業包括對 64 位元整數值的相加、遞增和遞減、根據比較的交換和條件式交換，以及讀取作業。

如需詳細資訊，請參閱 [Interlocked 作業](interlocked-operations.md)文章與 <xref:System.Threading.Interlocked> API 參考。

## <a name="spinwait-structure"></a>SpinWait 結構

<xref:System.Threading.SpinWait?displayProperty=nameWithType> 結構能提供微調式等候的支援。 當執行緒必須等待事件收到訊號或符合條件，但實際的等待時間預期會少於使用等候控制代碼或以其他方式封鎖執行緒的等候時間時，您便可以使用它。 使用 <xref:System.Threading.SpinWait>，您可以指定在等待時旋轉一小段時間，並且只有在指定的時間內未符合條件時放棄 (例如，藉由等待或睡眠)。

如需詳細資訊，請參閱 [SpinWait](spinwait.md) 文章與 <xref:System.Threading.SpinWait> API 參考。

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [安全執行緒集合](../collections/thread-safe/index.md)
- [執行緒物件與功能](threading-objects-and-features.md)
