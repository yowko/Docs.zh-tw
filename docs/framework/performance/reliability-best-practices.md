---
title: "可靠性最佳作法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "非同步例外狀況處理"
  - "退回程式碼"
  - "區塊, 可靠性"
  - "catch 區塊"
  - "CER"
  - "清除作業"
  - "限制的執行區域"
  - "跨應用程式定義域的共用狀態"
  - "服務拒絕攻擊"
  - "Fiber"
  - "完成項, 可靠性"
  - "finally 子句"
  - "GC.KeepAlive 方法"
  - "識別鎖定"
  - "模擬"
  - "遺漏的資源 [.NET Framework]"
  - "鎖定, 可靠性"
  - "Managed 執行緒處理"
  - "標記鎖定"
  - "記憶體, 可靠性"
  - "整個處理序的定義域共用狀態"
  - "重新啟動資料庫"
  - "可靠性 [.NET Framework]"
  - "可靠性合約 [.NET Framework]"
  - "SafeHandle 類別, 可靠性"
  - "共用狀態"
  - "單一執行緒 COM 元件"
  - "緩慢遺漏"
  - "SQL Server [.NET Framework], 可靠性"
  - "與 STA 相依的功能"
  - "暫止執行緒"
  - "同步, 可靠性"
  - "執行緒處理 [.NET Framework], 可靠性"
  - "Unmanaged 記憶體"
  - "編寫可靠的程式碼"
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# 可靠性最佳作法
下列可靠性規則是 SQL Server 導向，但是，也適用於任何主應用程式架構的伺服器應用程式。  類似 SQL Server 的伺服器不能遺漏資源，且不能被停機，這兩點極為重要。但是，這不能透過為更改物件狀態的每一個方法撰寫收回程式碼 \(Back\-out code\) 來完成；其目標不是要編寫百分之百可靠的 Managed 程式碼，讓任何具有收回程式碼的位置中的所有錯誤都可以修復，這樣會是成功機率很低，且讓人退縮的一項工作。Common Language Runtime \(CLR\) 無法輕易地為 Managed 程式碼提供強大的保證，讓完美程式碼的編寫變成可行。請注意，SQL Server 只會使用一個處理序，且一定要讓資料庫停機一段長到讓人無法接受的時間，才能回收此處理序，與 ASP.NET 不同。  
  
 在這些較弱的保證下執行於單一處理序中時，可靠性是以必要時結束執行緒或回收應用程式定義域為基礎，且會採取預防措施，確保類似控制代碼或記憶體這類的作業系統資源不會遺漏。即使有了這個較簡單的可靠性條件約束，仍然有一個重大的可靠性需求：  
  
-   絕對不會遺漏作業系統資源。  
  
-   向 CLR 識別所有形式的所有 Managed 鎖定。  
  
-   絕對不要中斷跨應用程式定義域的共用狀態，好讓 <xref:System.AppDomain> 回收順利運作。  
  
 雖然理論上來說可以編寫 Managed 程式碼來處理 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 和 <xref:System.OutOfMemoryException> 例外狀況，但是期望開發人員在整個應用程式中都編寫這類強固的程式碼，是一件不合理的事情。因此，Out\-of\-Band 例外狀況會讓執行中的執行緒結束；而且，如果結束的執行緒正在編輯共用狀態 \(這可以由該執行緒是否持有鎖定來判斷\)，則會卸載 <xref:System.AppDomain>。當正在編輯共用狀態的方法結束時，此狀態將會損毀，因為無法為共用狀態的更新編寫可靠的收回程式碼。  
  
 在 .NET Framework 2.0 版中，唯一需要可靠性的主應用程式是 SQL Server。如果您的組件將會在 SQL Server 上執行，您應該針對該組件的每一個部分執行可靠性工作，即使在資料庫中執行時有特定的功能已經停用。這是必要的處理方式，因為程式碼分析引擎會在組件層級檢查程式碼，且無法區分已停用的程式碼。  另一個 SQL Server 程式設計的考量是 SQL Server 會在一個處理序中執行所有項目，且 <xref:System.AppDomain> 回收會用來清除所有類似記憶體和作業系統控制代碼的資源。  
  
 您不能在收回程式碼上依賴完成項或解構函式或 `try/finally` 區塊；  它們可能會受到中斷，或是不會呼叫。  
  
 非預期的位置 \(可能是每一個機器指令\) 可能會擲回非同步例外狀況：<xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 和 <xref:System.OutOfMemoryException>。  
  
 在 SQL 中，Managed 執行緒不見得是 Win32 執行緒，有可能是 Fiber。  
  
 整個處理序中或跨應用程式定義域的可變共用狀態極難更改安全性，所以應該盡量避免。  
  
 記憶體不足狀況在 SQL Server 中不算罕見。  
  
 如果在 SQL Server 中裝載的程式庫未正確更新其共用狀態，則很有可能要等到重新啟動資料庫之後，才會復原程式碼。此外，在某些極端的狀況中，這可能會讓 SQL Server 處理序失敗，使得資料庫重新啟動。重新啟動資料庫可能會讓網站關閉或影響公司營運，讓可用性受到損害。緩慢遺漏類似記憶體或控制代碼這類的作業系統資源，可能會導致伺服器在沒有機會復原的情況下最後無法配置控制代碼，或者伺服器可能會緩慢降低效能，並降低客戶的應用程式可用性。我們希望能夠避免這些情況，這是顯而易見的。  
  
## 最佳作法規則  
 這項簡介著重於必須攔截在伺服器中執行的 Managed 程式碼的哪些程式碼檢閱內容，才能夠提高架構的穩定性和可靠性。  這些檢查通常都是很好的作法，所以絕對必須在伺服器上採行。  
  
 在面臨死結或資源條件約束的情況下，SQL Server 將會中止執行緒或卸除 <xref:System.AppDomain>。當發生這個情況時，只會保證限制的執行區域 \(CER\) 中的收回程式碼能夠執行。  
  
### 使用 SafeHandle 來避免資源遺漏  
 在發生 <xref:System.AppDomain> 卸載時，您無法依賴正在執行的 `finally` 區塊或完成項，所以透過 <xref:System.Runtime.InteropServices.SafeHandle> 類別 \(而非 <xref:System.IntPtr>、<xref:System.Runtime.InteropServices.HandleRef> 或類似類別\) 來抽出所有的作業系統資源存取，是相當重要的。  如此可讓 CLR 追蹤及關閉您所在 <xref:System.AppDomain> 反組譯碼案例使用的控制代碼。 <xref:System.Runtime.InteropServices.SafeHandle> 使用 CLR 一定會執行的關鍵完成項。  
  
 當作業系統控制代碼建立時，它就會儲存在安全控制代碼中，一直到釋放它為止。沒有任何視窗可以讓 <xref:System.Threading.ThreadAbortException> 發生來遺漏控制代碼。此外，平台叫用將會參考計數此控制代碼，如此可以封閉方式追蹤此控制代碼的存留期，以避免在 `Dispose` 以及目前使用此控制代碼的方法之間因為競爭情形而發生安全性問題。  
  
 目前有完成項來清除作業系統控制代碼的大多數類別，將不再需要此完成項，  此完成項而是會位於 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別上。  
  
 請注意，<xref:System.Runtime.InteropServices.SafeHandle> 並不是 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 的取代，仍然可能會有資源競爭和效能優勢可用來明確處置作業系統資源；只需要了解，明確處置資源的 `finally` 區塊可能不會一直執行到完成。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> 可讓您實作自己的 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法來執行釋放控制代碼的工作，例如，將狀態傳遞給作業系統控制代碼，以釋放常式或釋放迴圈中的一組控制代碼。CLR 可保證這個方法一定會執行；確保此控制代碼在所有情況下都會釋放，是 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作之作者的責任。  如果無法這樣做，將會讓此控制代碼遺漏，而這樣通常會導致與此控制代碼有關的原生資源遺漏。  因此，組織 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別，好讓 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作不需要配置在叫用時可能無法使用的任何資源，是極為重要的一件事。  請注意，可允許呼叫可能在 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作內失敗的方法，前提是您的程式碼必須可以處理這類的失敗，並完成合約來釋放原生控制代碼。  為了要進行偵錯，<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 會有 <xref:System.Boolean> 傳回值；如果遇到了災難性的錯誤，而無法釋放資源時，這個值可以設定為 `false`。  這樣做時，將會啟動 [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA \(如果啟用的話\) 來協助問題的識別，  它不會以任何其他方式影響執行階段；相同資源上將不會再次呼叫 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>，因此，此控制代碼將不會遺漏。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> 在某些內容中是不適當的；由於 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法可以在 <xref:System.GC> 完成項執行緒上執行，所以任何需要在特定執行緒上釋放的控制代碼都不應該包裝在 <xref:System.Runtime.InteropServices.SafeHandle> 中。  
  
 CLR 可以清除執行階段可呼叫包裝函式 \(RCW\)，而不需要額外的程式碼。使用平台叫用以及將 COM 物件做為 `IUnknown*` 或 <xref:System.IntPtr>的程式碼，則應該重新編寫此程式碼來使用 RCW。 <xref:System.Runtime.InteropServices.SafeHandle> 可能無法滿足此案例因呼叫回到 Managed 程式碼的 Unmanaged 版本方法的可能性。  
  
#### 程式碼分析規則  
 使用 <xref:System.Runtime.InteropServices.SafeHandle> 封裝作業系統資源，  不要使用 <xref:System.Runtime.InteropServices.HandleRef> 或型別為 <xref:System.IntPtr> 的欄位。  
  
### 確定不需要執行完成項，也能夠避免遺漏作業系統資源  
 請謹慎地檢閱您的完成項，確定即使完成項不執行，也不會遺漏重大的作業系統資源。不像應用程式在穩定狀態下執行或是當類似 SQL Server 的伺服器關閉時的一般 <xref:System.AppDomain> 卸載，在 <xref:System.AppDomain> 突然卸載期間，不會先完成 \(finalize\) 物件。請確定在突然卸載時不會遺漏資源，因為無法保證應用程式的正確性，但是必須藉由不遺漏資源的方式來維護伺服器的完整性。請使用 <xref:System.Runtime.InteropServices.SafeHandle> 來釋放任何作業系統資源。  
  
### 確定不需要執行 finally 子句，也能夠避免遺漏作業系統資源  
 不保證 `finally` 子句一定會在 CER 外面執行，要求程式庫開發人員不要依賴 `finally` 區塊中的程式碼來釋放 Unmanaged 資源。建議的解決方法是使用 <xref:System.Runtime.InteropServices.SafeHandle>。  
  
#### 程式碼分析規則  
 使用 <xref:System.Runtime.InteropServices.SafeHandle> 來清除作業系統資源，而非 `Finalize`。  不要使用 <xref:System.IntPtr>，而是要使用 <xref:System.Runtime.InteropServices.SafeHandle> 來封裝資源。  如果必須執行 finally 子句，要將它放在 CER 中。  
  
### 所有的鎖定都應該經歷現有的 Managed 鎖定程式碼  
 CLR 必須知道程式碼何時會在鎖定內，讓它知道要卸除 <xref:System.AppDomain>，而不只是中止執行緒。中止執行緒可能是危險的動作，因為在執行緒上作業的資料可能會處於不一致的狀態。  因此，整個 <xref:System.AppDomain> 都必須回收。無法識別鎖定的後果，可能會產生死結或不正確的結果。  請使用 <xref:System.Threading.Thread.BeginCriticalRegion%2A> 和 <xref:System.Threading.Thread.EndCriticalRegion%2A> 方法來識別鎖定區域，這些是 <xref:System.Threading.Thread> 類別上只套用到目前執行緒的靜態方法，可協助避免一個執行緒編輯另一個執行緒的鎖定計數。  
  
 <xref:System.Threading.Monitor.Enter%2A> 和 <xref:System.Threading.Monitor.Exit%2A> 都已內建這個 CLR 告知，所以建議使用這兩個方法以及使用它們的 [lock 陳述式](../Topic/lock%20Statement%20\(C%23%20Reference\).md)。  
  
 其他鎖定機制 \(例如微調鎖定和 <xref:System.Threading.AutoResetEvent>\) 必須呼叫這些方法，才能告知 CLR，表示已進入關鍵區段。這些方法不會接受任何鎖定；它們會告知 CLR，表示程式碼正在關鍵區段內執行，而中止執行緒可能會讓共用狀態不一致。如果您已經定義自己的鎖定類型 \(例如，自訂 <xref:System.Threading.ReaderWriterLock> 類別\)，請使用這些鎖定計數方法。  
  
#### 程式碼分析規則  
 使用 <xref:System.Threading.Thread.BeginCriticalRegion%2A> 和 <xref:System.Threading.Thread.EndCriticalRegion%2A> 來標記及識別所有的鎖定；  不要在迴圈中使用 <xref:System.Threading.Interlocked.CompareExchange%2A>、<xref:System.Threading.Interlocked.Increment%2A> 和 <xref:System.Threading.Interlocked.Decrement%2A>。不要執行這些方法的 Win32 Variant 之平台叫用；不要在迴圈中使用 <xref:System.Threading.Thread.Sleep%2A>，也不要使用 Volatile 欄位。  
  
### 清除程式碼必須在 finally 或 catch 區塊中，而不是跟隨著 catch  
 清除程式碼絕對不能跟隨著 `catch` 區塊，而是應該在 `finally` 或 `catch` 區塊本身中，這應該是正常情況下很好的作法。通常會優先使用 `finally` 區塊，因為它在擲回例外狀況，以及在正常情況下遇到 `try` 區塊結尾時，都會執行相同的程式碼。萬一擲回非預期的例外狀況時 \(例如 <xref:System.Threading.ThreadAbortException>\)，將不會執行清除程式碼。在理想情況下，您在 `finally` 中清除的任何 Unmanaged 資源都應該包裝在 <xref:System.Runtime.InteropServices.SafeHandle> 中，以避免發生遺漏。請注意，C\# `using` 關鍵字可用來有效處置物件，包括控制代碼在內。  
  
 雖然 <xref:System.AppDomain> 回收可以清除完成項執行緒上的資源，但是將清除程式碼放在正確的位置中仍然很重要。請注意，如果執行緒收到非同步例外狀況，而未持有鎖定，則 CLR 會嘗試結束該執行緒本身，而不需要回收 <xref:System.AppDomain>。確定資源已盡早清除 \(而不要後來才清除\)，將有助於讓更多資源可用，並能夠更有效地管理存留期。如果您未明確關閉某個錯誤碼路徑中檔案的控制代碼，然後等候 <xref:System.Runtime.InteropServices.SafeHandle> 完成項來清除它，則下一次程式碼執行時，如果該完成項尚未執行，則嘗試存取完全相同的檔案時，可能會失敗。因此，確定清除程式碼存在並可正常運作，將有助於更巧妙而快速地從失敗中復原 \(雖然並未強制一定要這樣做\)。  
  
#### 程式碼分析規則  
 `catch` 之後的清除程式碼必須在 `finally` 區塊中；  在finally區塊放置處理的呼叫。 `catch` 區塊應該於擲回或重新擲回中結束。雖然會有一些例外狀況 \(例如，偵測是否可以在可取得大量例外狀況中任何一個的地方建立網路連接的程式碼\)，但是需要在正常情況下攔截許多例外狀況的任何程式碼都應該提供一個提示，表示程式碼應該經過測試，以了解它是否會成功。  
  
### 在應用程式定義域之間的整個整理序之可變動共用狀態應該予以排除，或使用限制的執行區域  
 如簡介內容中所述，要以可靠的方式編寫 Managed 程式碼來監視跨應用程式定義域的整個處理序之共用狀態，可能會非常困難。整個處理序之共用狀態是指在應用程式定義域之間共用的任何形式之資料結構，可能是位於 Win32 程式碼、位於 CLR 內，或是在使用遠端處理的 Managed 程式碼中。任何可變動的共用狀態都很難正確地使用 Managed 程式碼來編寫，而任何靜態的共用狀態只能以極小心的方式來處理。如果您有整個處理序或整個機器的共用狀態，請找出某個方法來排除它，或是使用限制的執行區域 \(CER\) 來保護此共用狀態。請注意，任何具有未識別及未更正的共用狀態之程式庫可能會造成需要乾淨 <xref:System.AppDomain> 卸載的主應用程式 \(例如 SQL Server\) 損毀。  
  
 如果程式碼使用 COM 物件，請避免在應用程式定義域之間共用此 COM 物件。  
  
### 鎖定無法在整個處理序或應用程式定義域之間運作  
 在過去，<xref:System.Threading.Monitor.Enter%2A> 和 [lock 陳述式](../Topic/lock%20Statement%20\(C%23%20Reference\).md) 都是用來建立全域處理序鎖定。例如，在類似以下的 <xref:System.AppDomain> 靈活類別上鎖定時，即會發生這個情況：非共用組件中的 <xref:System.Type> 執行個體、<xref:System.Threading.Thread> 物件、暫時字串，以及使用遠端處理在跨應用程式定義域之間共用的某些字串。這些鎖定將不再能夠在整個處理序中進行；若要識別是否有整個處理序的應用程式之間的定義域鎖定存在，請判斷鎖定內的程式碼是否有使用任何外部、保存的資源，例如磁碟上的檔案，也有可能是資料庫。  
  
 請注意，如果受保護的程式碼使用外部資源，則接受 <xref:System.AppDomain> 內的鎖定可能會發生問題，因為該程式碼可能會跨多個應用程式定義域同時執行。在整個處理序中寫入到一個記錄檔或繫結到通訊端時，這樣做可能會發生問題。這些變更表示無法輕鬆地使用 Managed 程式碼來取得整個處理序的鎖定，與使用具名的 <xref:System.Threading.Mutex> 或 <xref:System.Threading.Semaphore> 執行個體不同。請建立不會同時在兩個應用程式定義域中執行的程式碼，或是使用 <xref:System.Threading.Mutex> 或 <xref:System.Threading.Semaphore> 類別。如果無法變更現有的程式碼，請不要使用 Win32 具名 Mutex 來達成這項同步處理，因為在 Fiber 模式中執行表示，您無法保證相同的作業系統執行緒將會取得及釋放 Mutex。您必須使用 Managed <xref:System.Threading.Mutex> 類別，或具名的 <xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent> 或 <xref:System.Threading.Semaphore> 同步處理讓 CLR 能夠意識到的程式碼鎖定，而不要使用 Unmanaged 程式碼來同步處理鎖定。  
  
#### 避免 lock\(typeof\(MyType\)\)  
 共用組件中的私用和公用 <xref:System.Type> 物件 \(其中只具有一份跨所有應用程式定義域共用之程式碼複本\)，也有一些問題。對於共用組件而言，每一個處理序只有一個 <xref:System.Type> 執行個體，這表示會有多個應用程式定義域共用完全相同的 <xref:System.Type> 執行個體。在 <xref:System.Type> 執行個體上採用鎖定將會採用一個影響整個處理序的鎖定，而不只是 <xref:System.AppDomain>。如果一個 <xref:System.AppDomain> 採用 <xref:System.Type> 物件上的鎖定，然後該執行緒突然中止，則它將不會釋放此鎖定。然後，這個鎖定可能會讓其他應用程式定義域鎖死。  
  
 有一個不錯的方法可採用靜態方法中的鎖定，此方法與將靜態內部同步物件加入到程式碼有關。這樣可能會在類別建構函式中初始化 \(如果有類別建構函式存在\)；如果不存在，則會以類似下列的方式初始化：  
  
```  
private static Object s_InternalSyncObject;  
private static Object InternalSyncObject   
{  
    get   
    {  
        if (s_InternalSyncObject == null)   
        {  
            Object o = new Object();  
            Interlocked.CompareExchange(  
                ref s_InternalSyncObject, o, null);  
        }  
        return s_InternalSyncObject;  
    }  
}  
```  
  
 然後在採用鎖定時，可使用 `InternalSyncObject` 屬性來取得要採用鎖定的物件。如果您已經在類別建構函式中初始化內部同步物件，將不需要使用這個屬性。雙重檢查的鎖定初始化程式碼應該會類似以下範例：  
  
```  
public static MyClass SingletonProperty   
{  
    get   
    {  
        if (s_SingletonProperty == null)   
        {  
            lock(InternalSyncObject)   
            {  
                // Do not use lock(typeof(MyClass))   
                if (s_SingletonProperty == null)   
                {  
                    MyClass tmp = new MyClass(…);     
                    // Do all initialization before publishing  
                    s_SingletonProperty = tmp;  
                }  
            }  
        }  
        return s_SingletonProperty;  
    }  
}  
```  
  
#### 與 Lock\(this\) 有關的附註  
 通常可接受在可公開存取的個別物件上採用鎖定；但是，如果此物件是可能會造成整個子系統鎖死的單一物件，也請考慮使用上面的設計模式。例如，在一個 <xref:System.Security.SecurityManager> 物件上的鎖定可能會造成 <xref:System.AppDomain> 內的死結，而使得整個 <xref:System.AppDomain> 無法使用。  不要採用此型別的公開可存取物件上的鎖定，是一個不錯的作法；但是在一般情況下，個別集合或陣列上的鎖定應該不會產生問題。  
  
#### 程式碼分析規則  
 不要採用可跨應用程式定義域使用，或不具有強烈識別意識之型別上的鎖定；  不要呼叫 <xref:System.Type>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.PropertyInfo>、<xref:System.String>、<xref:System.ValueType>、<xref:System.Threading.Thread> 或任何衍生自 <xref:System.MarshalByRefObject> 的類別上的 <xref:System.Threading.Monitor.Enter%2A>。  
  
### 移除 GC.KeepAlive 呼叫  
 有極大量的現有程式碼不是在應該的時候沒有使用 <xref:System.GC.KeepAlive%2A>，就是在不適當的時候使用了它。在轉換成 <xref:System.Runtime.InteropServices.SafeHandle> 之後，類別不需要呼叫 <xref:System.GC.KeepAlive%2A>，前提是假設這些類別沒有完成項，但是卻依賴 <xref:System.Runtime.InteropServices.SafeHandle> 來完成作業系統控制代碼。雖然保留 <xref:System.GC.KeepAlive%2A> 的呼叫之效能上的成本可予以忽略，但是要察覺 <xref:System.GC.KeepAlive%2A> 的呼叫必須或足以解決可能不復存在的存留期問題，會讓程式碼更難維護。但是，在使用 COM Interop CLR 可呼叫包裝函式 \(RCW\) 時，程式碼仍需要 <xref:System.GC.KeepAlive%2A>。  
  
#### 程式碼分析規則  
 移除 <xref:System.GC.KeepAlive%2A>。  
  
### 使用主應用程式保護屬性  
 <xref:System.Security.Permissions.HostProtectionAttribute> \(HPA\) 可提供宣告式安全性動作的用法來判斷主應用程式保護需求，好讓主應用程式避免讓甚至是完全信任的程式碼呼叫對給定之主應用程式不適合的某些方法，例如，對 SQL Server 使用 <xref:System.Environment.Exit%2A> 或 <xref:System.Windows.Forms.MessageBox.Show%2A>。  
  
 此 HPA 只會影響裝載 Common Language Runtime 及實作主應用程式保護的 Unmanaged 應用程式，例如 SQL Server。  當套用此屬性時，安全性動作會根據類別或方法公開的主應用程式資源來建立連結需求。  如果程式碼在用戶端應用程式或是沒有主應用程式保護的伺服器上執行，則這個屬性會蒸發掉，這表示不會偵測到它，所以也不會套用它。  
  
> [!IMPORTANT]
>  這個屬性的目的是要強制使用主應用程式特定的程式設計模型方針，而不是安全性行為。雖然連結要求用於檢查與程式設計模型需求的一致性，但 <xref:System.Security.Permissions.HostProtectionAttribute> 並不是安全性權限。  
  
 如果主機沒有程式設計模型需求，則不會發生連結要求。  
  
 這個屬性會識別下列項目：  
  
-   不符合主機程式設計模型的方法或類別，但是良性的。  
  
-   不符合主機程式設計模型的方法或類別，可能會導致伺服器管理的使用者程式碼不穩定。  
  
-   不符合主機程式設計模型的方法或類別，可能會導致伺服器處理序本身不穩定。  
  
> [!NOTE]
>  如果您正在建立類別庫，該類別庫由可能在主機保護環境中執行的應用程式呼叫，則應該將這個屬性套用至公開 <xref:System.Security.Permissions.HostProtectionResource> 資源分類的成員。  具有這個屬性的 .NET Framework 類別庫成員會引起只檢查立即呼叫端。您的程式庫成員也必須以相同的方式讓它的立即呼叫端得到檢查。  
  
 請在 <xref:System.Security.Permissions.HostProtectionAttribute> 中尋找與 HPA 有關的資訊。  
  
#### 程式碼分析規則  
 對於 SQL Server 而言，必須以 HPA 來識別用來引入同步處理或執行緒處理的所有方法。  如此會加入可共用狀態、已同步處理，或管理外部處理序的方法。  影響 SQL Server 的 <xref:System.Security.Permissions.HostProtectionResource> 值有 <xref:System.Security.Permissions.HostProtectionResource>、<xref:System.Security.Permissions.HostProtectionResource> 和 <xref:System.Security.Permissions.HostProtectionResource>。  但是，公開任何 <xref:System.Security.Permissions.HostProtectionResource> 的任何方法都應該由 HPA 來識別，而不只是那些使用可影響 SQL 之資源的方法。  
  
### 不要在 Unmanaged 程式碼中無限期地封鎖  
 在 Unmanaged 程式碼 \(而非 Managed 程式碼\) 中封鎖，可能會造成服務拒絕攻擊，因為 CLR 無法中止執行緒。被封鎖的執行緒會使得 CLR 無法卸載 <xref:System.AppDomain>，且至少不會執行一些極不安全的作業。使用 Win32 同步處理原始物件進行封鎖是一個不允許使用的清楚範例；可能的話，應該避免在通訊端上的 `ReadFile` 呼叫內進行封鎖，在理想狀況下，Win32 API 應該為類似這樣的作業提供一個逾時機制。  
  
 在理想情況下，呼叫原生物件的任何方法在使用 Win32 呼叫時，都應該要有合理、有限的逾時。如果允許使用者指定逾時，則該使用者一定要有某些特定的安全性權限，才會允許使用者指定無限期的逾時。如果方法將會封鎖超過 ~10 秒以上，您應該使用可支援逾時的版本，或是需要額外的 CLR 支援，這是一般的指導原則。  
  
 以下是一些有問題的 API 範例。可以將管道 \(匿名和具名兩者\) 建立為具有逾時；但是，程式碼必須確定它絕對不會以 NMPWAIT\_WAIT\_FOREVER 呼叫 `CreateNamedPipe` 或 `WaitNamedPipe`。此外，即使有指定逾時，還是可能會發生非預期的封鎖。在匿名管道上呼叫 `WriteFile` 將會封鎖到所有位元組寫入為止，這表示如果緩衝區中有未讀的資料，`WriteFile` 呼叫將會一直封鎖，直到讀取器已釋放管道緩衝區中的空間為止。通訊端應該一直使用遵守逾時機制的某個 API。  
  
#### 程式碼分析規則  
 在 Unmanaged 程式碼中進行封鎖，卻沒有逾時，就是一種服務拒絕攻擊。  請不要執行對 `WaitForSingleObject`、`WaitForSingleObjectEx`、`WaitForMultipleObjects`、`MsgWaitForMultipleObjects` 和 `MsgWaitForMultipleObjectsEx` 的平台叫用呼叫，也不要使用 NMPWAIT\_WAIT\_FOREVER。  
  
### 識別任何與 STA 相依的功能  
 識別任何使用 COM 單一執行緒 Apartment \(STA\) 的程式碼；SQL Server 處理序中會停用 STA，相依於 `CoInitialize` 的功能 \(例如效能計數器或剪貼簿\) 也必須在 SQL Server 中停用。  
  
### 確定完成項沒有同步處理問題  
 可能會有多個完成項執行緒存在於將來的 .NET Framework 版本中，這表示相同型別的不同執行個體之完成項會於同時間執行；這些完成項不需要完全是執行緒安全，記憶體回收行程可保證只有一個執行緒會執行給定之物件執行個體的完成項。但是，當這些完成項同時間在多個不同的物件執行個體上執行時，必須將它們編寫為可以避開競爭情形和死結。在完成項中使用任何外部狀態 \(例如，寫入到記錄檔\) 時，必須要處理執行緒的問題。請勿依賴最終化來提供執行緒安全；  也不要使用執行緒區域儲存區 \(Managed 或原生型式\) 來儲存完成項執行緒上的狀態。  
  
#### 程式碼分析規則  
 完成項必須沒有任何同步處理問題；  請勿在完成項中使用靜態可變動狀態。  
  
### 盡量避免使用 Unmanaged 記憶體  
 Unmanaged 記憶體可能會遺漏，就像是作業系統控制代碼一樣。可能的話，請嘗試使用在利用 [stackalloc](../Topic/stackalloc%20\(C%23%20Reference\).md) 的堆疊上的記憶體，或是 Pin Managed 物件，例如 [fixed 陳述式](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) 或使用 byte\[\] 的 <xref:System.Runtime.InteropServices.GCHandle>。<xref:System.GC> 最後會將這些項目清除；但是，如果您必須配置 Unmanaged 記憶體，請考慮使用衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的類別來包裝記憶體配置。  
  
 請注意，至少會有一個案例發生 <xref:System.Runtime.InteropServices.SafeHandle> 不適用的情形。對於配置或釋放記憶體的 COM 方法呼叫而言，一個 DLL 透過 `CoTaskMemAlloc` 來配置記憶體，然後由另一個 DLL 使用 `CoTaskMemFree` 來釋放該記憶體，這是常見的情況。在這些地方使用 <xref:System.Runtime.InteropServices.SafeHandle> 是不適當的，因為它會嘗試將 Unmanaged 記憶體的存留期與 <xref:System.Runtime.InteropServices.SafeHandle> 的存留期連結起來，而不是讓其他 DLL 控制記憶體的存留期。  
  
### 檢閱 Catch\(Exception\) 的所有使用  
 攔截所有例外狀況 \(而非一個特定例外狀況\) 的 catch 區塊現在也會攔截非同步例外狀況；檢查每一個 catch\(Exception\) 區塊，尋找不重要的資源釋放或可能略過的收回程式碼，以及在 catch 區塊本身內用來處理 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 或 <xref:System.OutOfMemoryException> 的可能不正確的行為。請注意，此程式碼有可能記錄或做出某些假設，表示它可能只會看到某些例外狀況，或是每當發生例外狀況時，只會因為恰好一個特定的理由而失敗。這些假設可能需要更新，以便加入 <xref:System.Threading.ThreadAbortException>。  
  
 請考慮變更攔截所有例外狀況的所有地方，使其攔截您希望擲回的特定例外狀況型別，例如字串格式化方法中的 <xref:System.FormatException>。如此可防止 catch 區塊在非預期的例外狀況上執行，並可確保程式碼不會藉由攔截非預期的例外狀況來隱藏錯誤。絕對不要在程式庫程式碼中處理例外狀況 \(需要您擲回例外狀況的程式碼可能表示您所呼叫的程式碼中有設計上的缺陷\)，這是一般的規則。在某些情況下，您可能會想要攔截例外狀況，並擲回不同的例外狀況型別來提供更多的資料。在這種情況下，請使用巢狀例外狀況，將失敗的真正原因儲存在新例外狀況的 <xref:System.Exception.InnerException%2A> 屬性中。  
  
#### 程式碼分析規則  
 檢閱 Managed 程式碼中攔截所有物件或攔截所有例外狀況的所有 catch 區塊。在 C\# 中，這表示以旗標標示 `catch` {} 和 `catch(Exception)` {}。請考慮讓此例外狀況型別變得非常特別，或是檢閱程式碼，以確保當它攔截到非預期的例外狀況型別時，不會以不好的方式運作。  
  
### 不要假設 Managed 執行緒是 Win32 執行緒 – 它是 Fiber  
 使用 Managed 執行緒區域儲存區是有效的，但是您不可使用 Unmanaged 執行緒區域儲存區，或假設此程式碼將會再度於目前的作業系統執行緒上執行。請勿變更類似執行緒地區設定的設定，也不要透過平台叫用來呼叫 `InitializeCriticalSection` 或 `CreateMutex`，因為它們需要能夠進入鎖定同時也結束鎖定的作業系統執行緒。因為當使用 Fiber 時不會是這種情況，所以 Win32 關鍵區段和 Mutex 不能直接用於 SQL 中。請注意，Managed <xref:System.Threading.Mutex> 類別不會處理這些執行緒相似性的顧慮。  
  
 您可安心使用 Managed <xref:System.Threading.Thread> 物件上的大多數狀態，包括 Managed 執行緒區域儲存區和執行緒目前的 UI 文化特性。您也可使用 <xref:System.ThreadStaticAttribute>，此屬性可讓現有的靜態變數值只能由目前的 Managed 執行緒所存取 \(這是在 CLR 中製作 Fiber 區域儲存區的另一個方法\)。基於程式設計模型的理由，您不能在 SQL 中執行時變更執行緒的目前文化特性。  
  
#### 程式碼分析規則  
 SQL Server 會在 Fiber 模式下執行；請不要使用執行緒區域儲存區。  請避免使用對 `TlsAlloc`、`TlsFree`、`TlsGetValue` 和 `TlsSetValue.` 的平台叫用呼叫。  
  
### 讓 SQL Server 處理模擬  
 由於模擬會在執行緒層級上運作，且 SQL 可以在 Fiber 模式下執行，所以 Managed 程式碼不應該模擬使用者，也不應該呼叫 `RevertToSelf`。  
  
#### 程式碼分析規則  
 讓 SQL Server 處理模擬；  不要使用 `RevertToSelf`、`ImpersonateAnonymousToken`、`DdeImpersonateClient`、`ImpersonateDdeClientWindow`、`ImpersonateLoggedOnUser`、`ImpersonateNamedPipeClient`、`ImpersonateSelf`、`RpcImpersonateClient`、`RpcRevertToSelf`、`RpcRevertToSelfEx` 或 `SetThreadToken`。  
  
### 不要呼叫 Thread::Suspend  
 暫止執行緒的能力似乎是簡單的作業，但是卻有可能會發生死結。如果持有鎖定的執行緒因第二個執行緒而暫止，然後第二個執行緒嘗試採用相同的鎖定，即會發生死結。 <xref:System.Threading.Thread.Suspend%2A> 會同時干擾安全性、類別載入、遠端處理和反映。  
  
#### 程式碼分析規則  
 不要呼叫 <xref:System.Threading.Thread.Suspend%2A>，  請考慮改用真正的同步處理原始物件，例如 <xref:System.Threading.Semaphore> 或 <xref:System.Threading.ManualResetEvent>。  
  
### 使用限制的執行區域和可靠性合約來保護重要的作業  
 在執行可更新共用狀態或需要決定性的完全成功或完全失敗的複雜作業時，請務必讓該作業受到限制的執行區域 \(CER\) 所保護。  如此可保證此程式碼可以在每一種情況下執行，甚至是在執行緒突然中止或 <xref:System.AppDomain> 突然卸載時。  
  
 CER 是特定的 `try/finally` 區塊，它的前面會緊接著 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的呼叫。  
  
 這樣做會指示 Just\-in\-Time 編譯器先準備好 finally 區塊中的所有程式碼之後，再執行 `try` 區塊，  如此可確保 finally 區塊中的程式碼可以在所有情況下建置和執行。  在 CER 中有空的 `try` 區塊是常見的情況，  使用 CER 可防止非同步執行緒中止及記憶體不足的例外狀況。  請參閱 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>，以取得額外針對極深層的程式碼處理堆疊溢位的 CER 形式。  
  
## 請參閱  
 <xref:System.Runtime.ConstrainedExecution>   
 [SQL Server 程式設計和主機保護屬性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)