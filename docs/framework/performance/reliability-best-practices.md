---
title: 可靠性最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- marking locks
- rebooting databases
- denial of service attacks
- back-out code
- SQL Server [.NET Framework], reliability
- synchronization, reliability
- single-threaded COM components
- slow leaks
- suspending threads
- asynchronous exception handling
- leaked resources [.NET Framework]
- unmanaged memory
- memory, reliability
- threading [.NET Framework], reliability
- process-wide domain shared states
- shared states
- SafeHandle class, reliability
- reliability contracts [.NET Framework]
- cleanup operations
- constrained execution regions
- CERs
- finalizers, reliability
- reliability [.NET Framework]
- blocks, reliability
- finally clauses
- cross-application domain shared states
- catch blocks
- identifying locks
- writing reliable code
- impersonation
- GC.KeepAlive method
- managed threading
- locks, reliability
- STA-dependent features
- fibers
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6f29d15297fc7faff6bb3bb07ee535647c2bb7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reliability-best-practices"></a>可靠性最佳作法
下列可靠性規則會導向至 SQL Server；不過，它們也會套用至任何主機型伺服器應用程式。 SQL Server 這類伺服器絕對不能流失資源，也不能關閉。  不過，撰寫每個改變物件狀態之方法的退出程式碼，無法完成該作業。  目標不是撰寫 100% 可靠的 Managed 程式碼，來復原每個具有退出程式碼的位置中的任何錯誤。  這會是成功機率很低的煩人工作。  Common Language Runtime (CLR) 無法輕易地強烈保證 Managed 程式碼可撰寫可行的完美程式碼。  請注意，與 ASP.NET 不同，SQL Server 只會使用一個無法回收的處理序，而不需要關閉資料庫一段無法接受的時間。  
  
 有了這些較弱的保證並執行單一處理序之後，必要時，可靠性是以終止中執行緒或回收中應用程式定義域為基礎，並採取預防措施來確保作業系統資源，例如控制代碼或記憶體未流失。  即使使用這個較簡單的可靠性條件約束，還是會有明顯的可靠性需求：  
  
-   絕不會流失作業系統資源。  
  
-   識別所有形式的 CLR 中的所有 Managed 鎖定。  
  
-   永遠不會中斷跨應用程式定義域共用狀態，並允許 <xref:System.AppDomain> 回收順暢地運作。  
  
 雖然理論上可能會撰寫 Managed 程式碼來處理 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 和 <xref:System.OutOfMemoryException> 例外狀況，但是開發人員必須撰寫整個應用程式的這類強固程式碼十分不合理。  基於這個原因，頻外例外狀況會導致終止執行中執行緒；如果已終止的執行緒處於編輯中共用狀態 (可由執行緒是否持有鎖定來判斷)，則會卸載 <xref:System.AppDomain>。  終止正在編輯共用狀態的方法時，狀態會損毀，因為無法撰寫共用狀態更新的可靠退出程式碼。  
  
 在 .NET Framework 2.0 版中，唯一需要可靠性的主機是 SQL Server。  如果將在 SQL Server 上執行您的組件，則應該針對該組件的每個部分執行可靠性工作，即使具有已在資料庫中執行時停用的特定功能也是一樣。  這是必要的，因為程式碼分析引擎會檢查組件層級的程式碼，而且無法區分已停用的程式碼。 另一個 SQL Server 程式設計考量是 SQL Server 在一個處理序中執行所有項目，而 <xref:System.AppDomain> 回收用於清除所有資源，例如記憶體和作業系統控制代碼。  
  
 您無法取決於完成項或解構函式或是退出程式碼的 `try/finally` 區塊。 它們可能是已中斷或未呼叫。  
  
 非同步例外狀況可能會在非預期的位置擲回，可能是每個電腦指令：<xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 和 <xref:System.OutOfMemoryException>。  
  
 Managed 執行緒不一定是 SQL 中的 Win32 執行緒；它們可能是 Fiber。  
  
 整個處理序或跨應用程式定義域可變動共用狀態很難安全地進行改變，應該盡可能避免。  
  
 在 SQL Server 中，經常發生記憶體不足的情況。  
  
 如果 SQL Server 中所裝載的程式庫未正確更新其共用狀態，則除非已重新啟動資料庫，否則極有可能不會復原程式碼。  此外，在某些極端的情況下，這可能會導致 SQL Server 處理序失敗，因而重新啟動資料庫。  重新啟動資料庫可以關閉網站或影響公司作業，進而損及可用性。  作業系統資源 (例如記憶體或控制代碼) 的緩慢流失可能會讓伺服器最後無法配置控制代碼並且無法進行復原，或者伺服器的效能可能會下降並降低客戶的應用程式可用性。  很明顯，我們會想要避免這些狀況。  
  
## <a name="best-practice-rules"></a>最佳做法規則  
 簡介著重於必須擷取在伺服器中執行之 Managed 程式碼的程式碼檢閱，來增加架構的穩定性和可靠性。 所有這些檢查一般都是不錯的做法，而且在伺服器上絕對必須進行。  
  
 面對死結或資源條件約束時，SQL Server 將中止執行緒或卸除 <xref:System.AppDomain>。  發生這種情況時，保證執行限制的執行區域 (CER) 中的退出程式碼。  
  
### <a name="use-safehandle-to-avoid-resource-leaks"></a>使用 SafeHandle 避免資源流失  
 如果是 <xref:System.AppDomain> 卸載，則無法取決於所執行的 `finally` 區塊或完成項，因此一定要透過 <xref:System.Runtime.InteropServices.SafeHandle> 類別來擷取所有作業系統資源存取，而不是 <xref:System.IntPtr>、<xref:System.Runtime.InteropServices.HandleRef> 或類似的類別。 這甚至可讓 CLR 追蹤和關閉您在 <xref:System.AppDomain> 終止程式碼案例中使用的控制代碼。  <xref:System.Runtime.InteropServices.SafeHandle> 將使用 CLR 一律會執行的重要完成項。  
  
 作業系統控制代碼除非予以釋放，否則在建立時即會儲存在安全控制代碼中。  沒有時間範圍，而在此時間範圍可能發生遺漏控制代碼的 <xref:System.Threading.ThreadAbortException>。  此外，平台叫用也會計算控制代碼的參考計數，以緊密追蹤控制代碼的存留期，防止 `Dispose` 與目前使用控制代碼之方法間的競爭條件安全性問題。  
  
 目前的完成項只能清除作業系統控制代碼的大部分類別都將不再需要完成項。 相反地，完成項會在 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別上。  
  
 請注意，<xref:System.Runtime.InteropServices.SafeHandle> 不是 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 的取代項目。  仍然可能具有資源爭用和效能優點，可明確地處置作業系統資源。  您只需要了解，明確處置資源的 `finally` 區塊可能未執行，無法完成。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> 可讓您實作自己的 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法，以執行控制代碼釋放工作，例如將狀態傳遞至作業系統控制代碼釋放常式，或釋放迴圈中的一組控制代碼。  CLR 保證會執行此方法。  <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作作者必須負責確保在所有情況下釋放控制代碼。 無法這麼做會導致控制代碼流失，這通常會造成與控制代碼建立關聯之原生資源的流失。 因此，請務必建構 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別，這樣 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作就不需要配置任何可能無法在叫用期間使用的資源。 請注意，允許呼叫在 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 實作內失敗的方法，前提是您的程式碼可以處理這類失敗，並且完成合約來釋放原生控制代碼。 為了進行偵錯，如果發生導致無法釋放資源的重大錯誤，則 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 的 <xref:System.Boolean> 傳回值可能設定為 `false`。 這麼做會啟用 [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA (啟用時)，協助識別問題。 它不會透過任何其他方法影響執行階段；將不會針對相同的資源再次呼叫<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>，因此控制代碼將流失。  
  
 在特定內容中，不適合使用 <xref:System.Runtime.InteropServices.SafeHandle>。  因為 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法可以在 <xref:System.GC> 完成項執行緒上執行，所以任何需要在特定執行緒上釋放的控制代碼不應該包裝在 <xref:System.Runtime.InteropServices.SafeHandle> 中。  
  
 CLR 不需要額外的程式碼就可以清除執行階段可呼叫包裝函式 (RCW)。  針對使用平台叫用並將 COM 物件視為 `IUnknown*` 或 <xref:System.IntPtr> 的程式碼，應該重寫程式碼以使用 RCW。  <xref:System.Runtime.InteropServices.SafeHandle> 對此案例而言可能不足，因為可能會將 Unmanaged 發行方法回呼至 Managed 程式碼。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 使用 <xref:System.Runtime.InteropServices.SafeHandle> 來封裝作業系統資源。 請不要使用 <xref:System.Runtime.InteropServices.HandleRef> 或是類型 <xref:System.IntPtr> 的欄位。  
  
### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>確定不需要執行完成項即可避免作業系統資源流失  
 請小心地檢閱完成項，確保即使它們未執行，重要作業系統資源也不會流失。  與應用程式以穩定狀態執行或 SQL Server 這類伺服器關閉時的一般 <xref:System.AppDomain> 卸載不同，在突然 <xref:System.AppDomain> 卸載期間不會完成物件。  因為無法保證應用程式正確性，所以請確定資源未在突然卸載時流失，但必須透過未流失資源來維護伺服器完整性。  使用 <xref:System.Runtime.InteropServices.SafeHandle> 來釋放任何作業系統資源。  
  
### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>確定不需要執行 finally 子句即可避免作業系統資源流失  
 `finally` 子句不一定會在 CER 外部執行，需要程式庫開發人員不依賴 `finally` 區塊內的程式碼來釋放 Unmanaged 資源。  使用 <xref:System.Runtime.InteropServices.SafeHandle> 是建議的解決方案。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 請使用 <xref:System.Runtime.InteropServices.SafeHandle> 來清除作業系統資源，而非 `Finalize`。 請不要使用 <xref:System.IntPtr>；請使用 <xref:System.Runtime.InteropServices.SafeHandle> 來封裝資源。 如果必須執行 finally 子句，請將它放在 CER 中。  
  
### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>所有鎖定都應該透過現有 Managed 鎖定程式碼  
 CLR 必須知道程式碼何時處於鎖定，才能知道要卸除 <xref:System.AppDomain>，而不只是中止執行緒。  中止執行緒可能十分危險，因為執行緒所操作的資料可能處於不一致的狀態。 因此，必須回收整個 <xref:System.AppDomain>。  無法識別鎖定的結果可以是發生死結或結果不正確。 使用 <xref:System.Threading.Thread.BeginCriticalRegion%2A> 和 <xref:System.Threading.Thread.EndCriticalRegion%2A> 方法來識別鎖定區域。  它們是 <xref:System.Threading.Thread> 類別上只套用至目前執行緒的靜態方法，有助於防止某個執行緒編輯另一個執行緒的鎖定計數。  
  
 <xref:System.Threading.Monitor.Enter%2A> 和 <xref:System.Threading.Monitor.Exit%2A> 內建此 CLR 通知，以建議使用它們，以及使用可使用這些方法的 [lock 陳述式](~/docs/csharp/language-reference/keywords/lock-statement.md)。  
  
 微調鎖定和 <xref:System.Threading.AutoResetEvent> 這類其他鎖定機制必須呼叫這些方法，向 CLR 通知將進入重要區段。  這些方法不會取得任何鎖定；它們會向 CLR 通知程式碼正在重要區段中執行，而且中止執行緒會讓共用狀態不一致。  如果您已經定義自己的鎖定類型 (例如自訂 <xref:System.Threading.ReaderWriterLock> 類別)，請使用這些鎖定計數方法。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 使用 <xref:System.Threading.Thread.BeginCriticalRegion%2A> 和 <xref:System.Threading.Thread.EndCriticalRegion%2A> 來標示並識別所有鎖定。 請不要在迴圈中使用 <xref:System.Threading.Interlocked.CompareExchange%2A>、<xref:System.Threading.Interlocked.Increment%2A> 和 <xref:System.Threading.Interlocked.Decrement%2A>。  請不要對這些方法的 Win32 變體執行平台叫用。  請不要在迴圈中使用 <xref:System.Threading.Thread.Sleep%2A>。  請不要使用 Volatile 欄位。  
  
### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>清除程式碼必須位在 finally 或 catch 區塊中，不能跟在 catch 後面  
 清除程式碼的後面絕對不應該是 `catch` 區塊；它應該位在 `finally` 或 `catch` 區塊本身中。  這應該是一般不錯的做法。  一般偏好使用 `finally` 區塊，因為它在擲回例外狀況以及正常發現 `try` 區塊結尾時執行相同的程式碼。  如果擲回未預期的例外狀況 (例如 <xref:System.Threading.ThreadAbortException>)，則不會執行清除程式碼。  在理想狀況下，任何將在 `finally` 中清除的 Unmanaged 資源都應該包裝在 <xref:System.Runtime.InteropServices.SafeHandle> 中，以防止外洩。  請注意，可以有效地使用 C# `using` 關鍵字來處置物件，包含控制代碼。  
  
 雖然 <xref:System.AppDomain> 回收可以清除完成項執行緒上的資源，但還是需要將清除程式碼放在正確的位置。  請注意，如果執行緒收到非同步例外狀況，但未持有鎖定，則 CLR 會嘗試結束執行緒本身，而不需要回收 <xref:System.AppDomain>。  確保更快清除資源而不是更慢清除資源會有所幫助，原因是提供更多資源，而且更恰當地管理存留期。  如果您未在某個錯誤碼路徑中明確地關閉檔案的控制代碼，則請等待 <xref:System.Runtime.InteropServices.SafeHandle> 完成項將它清除。程式碼下次執行時可能會失敗。如果尚未執行完成項，請嘗試存取完全相同的檔案。  基於這個原因，確保清除程式碼已存在並且正確運作，協助更乾淨且更快速地復原失敗，即使不是絕對必要也是一樣。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 `catch` 後面的清除程式碼需要位在 `finally` 區塊中。 將處置呼叫放在 finally 區塊中。  `catch` 區塊應該結束於 throw 或 rethrow 中。  雖然會有一些例外狀況，例如偵測是否可在可能收到任何大量例外狀況的位置建立網路連線的程式碼，但是在正常情況下需要攔截數個例外狀況的任何程式碼都應該指出應測試程式碼確認它是否成功。  
  
### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>應用程式定義域之間的整個處理序可變動共用狀態應該予以排除，或使用限制的執行區域  
 如簡介中所述，可能很難撰寫 Managed 程式碼，以可靠方式監視跨應用程式定義域的整個處理序共用狀態。  整個處理序共用狀態是在 Win32 程式碼中、CLR 內或使用遠端處理的 Managed 程式碼中應用程式定義域之間共用的任何一種資料結構。  很難使用 Managed 程式碼正確撰寫任何可變動共用狀態，而且撰寫任何靜態共用狀態都必須特別小心。  如果您有整個處理序或整部電腦共用狀態，請找到某種方法，以使用限制的執行區域 (CER) 排除它或保護共用狀態。  請注意，具有未識別和更正之共用狀態的任何程式庫都可能會讓需要全新 <xref:System.AppDomain> 卸載的主機 (例如 SQL Server) 當機。  
  
 如果程式碼使用 COM 物件，請避免在應用程式定義域之間共用該 COM 物件。  
  
### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>鎖定在整個處理序或是應用程式定義域之間未運作。  
 過去，使用 <xref:System.Threading.Monitor.Enter%2A> 和 [lock 陳述式](~/docs/csharp/language-reference/keywords/lock-statement.md)來建立全域處理序鎖定。  例如，鎖定 <xref:System.AppDomain> 敏捷式類別時會發生這種情況，例如非共用組件中的 <xref:System.Type> 執行個體、<xref:System.Threading.Thread> 物件、實習字串，以及使用遠端處理跨應用程式定義域共用的一些字串。  這些鎖定不再是針對整個處理序。  若要識別整個處理序應用程式間網域鎖定的目前狀態，請判斷鎖定內的程式碼是否使用任何外部持續性資源，例如磁碟上或可能是資料庫上的檔案。  
  
 請注意，如果受保護程式碼使用外部資源，則在 <xref:System.AppDomain> 內鎖定可能會導致問題，因為該程式碼可能會跨多個應用程式定義域同時執行。  寫入至一個記錄檔或是繫結至整個處理序的通訊端時，這可能會造成問題。  這些變更表示沒有簡單的方式可使用 Managed 程式碼來取得處理序全域鎖定，而非使用具名 <xref:System.Threading.Mutex> 或 <xref:System.Threading.Semaphore> 執行個體。  同時建立未在兩個應用程式定義域中執行的程式碼，或使用 <xref:System.Threading.Mutex> 或 <xref:System.Threading.Semaphore> 類別。  如果無法變更現有程式碼，請不要使用 Win32 具名 Mutex 來達成這項同步處理，因為以 Fiber 模式執行表示您無法保證相同的作業系統執行緒會取得和釋放 Mutex。  您必須使用 Managed <xref:System.Threading.Mutex> 類別或具名 <xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent> 或 <xref:System.Threading.Semaphore> 透過 CLR 所知的方式來同步處理程式碼鎖定，而不是使用 Unmanaged 程式碼來同步處理鎖定。  
  
#### <a name="avoid-locktypeofmytype"></a>避免 lock(typeof(MyType))  
 跨所有應用程式定義域只共用一份程式碼之共用組件中的私用和公用 <xref:System.Type> 物件也會產生問題。  針對共用組件，一個處理序只有一個 <xref:System.Type> 執行個體，這表示多個應用程式定義域會共用完全相同的 <xref:System.Type> 執行個體。  鎖定 <xref:System.Type> 執行個體會採用影響整個處理序的鎖定，而不只是 <xref:System.AppDomain>。  如果有一個 <xref:System.AppDomain> 取得 <xref:System.Type> 物件上的鎖定，然後該執行緒突然中止，則不會釋放鎖定。  此鎖定接著可能會讓其他應用程式定義域發生死結。  
  
 鎖定靜態方法的不錯方式包含將靜態內部同步處理物件新增至程式碼。  如果已有類別建構函式，則這可以在其中進行初始化，但如果沒有，則可以如下進行初始化：  
  
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
  
 然後，採用鎖定時，請使用 `InternalSyncObject` 屬性來取得要鎖定的物件。  如果您已經在類別建構函式中初始化內部同步處理物件，則不需要使用此屬性。  重複檢查鎖定初始化程式碼應該與此範例類似：  
  
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
  
#### <a name="a-note-about-lockthis"></a>Lock(this) 的注意事項  
 通常可以接受鎖定可公開存取的個別物件。  不過，如果物件是可能造成整個子系統發生死結的單一物件，也請考慮使用上述設計模式。  例如，一個 <xref:System.Security.SecurityManager> 物件上的鎖定可能會造成 <xref:System.AppDomain> 內發生死結，導致整個 <xref:System.AppDomain> 無法使用。 最好不要鎖定這類型的可公開存取物件。  不過，鎖定個別集合或陣列通常應該不會產生問題。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 請不要鎖定跨應用程式定義域使用的類型，或不要有強烈的身分識別感。 請不要在 <xref:System.Type>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.PropertyInfo>、<xref:System.String>、<xref:System.ValueType>、<xref:System.Threading.Thread> 或任何衍生自 <xref:System.MarshalByRefObject> 的物件上呼叫 <xref:System.Threading.Monitor.Enter%2A>。  
  
### <a name="remove-gckeepalive-calls"></a>移除 GC.KeepAlive 呼叫  
 大量的現有程式碼不會在應該使用時使用 <xref:System.GC.KeepAlive%2A>，或在不適當時使用它。  轉換至 <xref:System.Runtime.InteropServices.SafeHandle> 之後，類別不需要呼叫 <xref:System.GC.KeepAlive%2A>，並假設它們沒有完成項但依賴 <xref:System.Runtime.InteropServices.SafeHandle> 來完成作業系統控制代碼。  雖然重新訓練 <xref:System.GC.KeepAlive%2A> 呼叫的效能成本可能微不足道，但感知 <xref:System.GC.KeepAlive%2A> 呼叫是必要的或足以解決可能不再存在的存留期問題，都會讓程式碼更難維護。  不過，使用 COM Interop CLR 可呼叫包裝函式 (RCW) 時，程式碼仍然需要 <xref:System.GC.KeepAlive%2A>。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 移除 <xref:System.GC.KeepAlive%2A>。  
  
### <a name="use-the-host-protection-attribute"></a>使用主機保護屬性  
 <xref:System.Security.Permissions.HostProtectionAttribute> (HPA) 使用宣告式安全性動作來決定主機保護需求，甚至讓主機防止完全信任的程式碼呼叫不適用於指定主機的特定方法，例如 SQL Server 是 <xref:System.Environment.Exit%2A> 或 <xref:System.Windows.Forms.MessageBox.Show%2A>。  
  
 HPA 只會影響裝載 Common Language Runtime 以及實作主機保護的 Unmanaged 應用程式，例如 SQL Server。 套用時，安全性動作會根據類別或方法所公開的主機資源來建立連結要求。 如果在用戶端應用程式中或未受主機保護的伺服器上執行程式碼，則屬性會「消失」；它會偵測不到，因此不會進行套用。  
  
> [!IMPORTANT]
>  此屬性的目的是強制執行主機特定程式設計模型方針，而不是安全性行為。  雖然使用連結要求來檢查是否與程式設計模型需求一致，但是 <xref:System.Security.Permissions.HostProtectionAttribute> 不是安全性權限。  
  
 如果主機沒有程式設計模型需求，則不會發生連結要求。  
  
 此屬性可識別下列各項：  
  
-   方法或類別，不適合主機程式設計模型但為良性。  
  
-   方法或類別，不適合主機程式設計模型，而且可能導致伺服器所管理的使用者程式碼不穩定。  
  
-   方法或類別，不適合主機程式設計模型，而且可能導致伺服器處理序本身不穩定。  
  
> [!NOTE]
>  如果您所建立的類別庫是要由可在主機保護環境中執行的應用程式進行呼叫，則應該將此屬性套用至公開 <xref:System.Security.Permissions.HostProtectionResource> 資源分類的成員。 具有此屬性的 .NET Framework Class Library 成員只會檢查立即呼叫者。  程式庫成員也必須以相同的方式檢查其立即呼叫端。  
  
 請在 <xref:System.Security.Permissions.HostProtectionAttribute> 中尋找 HPA 詳細資訊。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 針對 SQL Server，用來介紹同步處理或執行緒處理的所有方法都必須使用 HPA 進行識別。 這包含共用狀態、已同步處理或管理外部處理序的方法。 可影響 SQL Server 的 <xref:System.Security.Permissions.HostProtectionResource> 值是 <xref:System.Security.Permissions.HostProtectionResource.SharedState>、<xref:System.Security.Permissions.HostProtectionResource.Synchronization> 和 <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>。 不過，HPA 應該識別任何 <xref:System.Security.Permissions.HostProtectionResource> 所公開的任何方法，而不只是使用會影響 SQL 之資源的方法。  
  
### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>不要透過 Unmanaged 程式碼無限期封鎖  
 因為 CLR 無法中止執行緒，所以使用 Unmanaged 程式碼進行封鎖可能會導致拒絕服務攻擊，而不是使用 Managed 程式碼進行封鎖。  已封鎖的執行緒會防止 CLR 卸載 <xref:System.AppDomain>，至少不執行一些非常不安全的作業。  使用 Win32 同步處理原始物件進行封鎖是不允許事項的清楚範例。  可以的話，應該避免通訊端上 `ReadFile` 呼叫中的封鎖 - 理想上，Win32 API 應該提供讓這類作業逾時的機制。  
  
 在理想情況下，所有呼叫原生的方法都應該使用具有合理有限逾時的 Win32 呼叫。  如果允許使用者指定逾時，則在沒有某種特定安全性權限時，不應該允許使用者指定無限逾時。  準則是，如果方法將封鎖超過 ~10 秒，則需要使用支援逾時的版本，或需要額外的 CLR 支援。  
  
 以下是一些造成問題之 API 的範例。  管道 (匿名和具名) 可以建立成包含逾時；不過，程式碼必須確定永遠不會使用 NMPWAIT_WAIT_FOREVER 來呼叫 `CreateNamedPipe` 和 `WaitNamedPipe`。  此外，即使指定逾時，還是會有未預期的封鎖。  除非寫入所有位元組，否則會封鎖在匿名管道上呼叫 `WriteFile`；這表示，如果緩衝區中有未讀取的資料，則除非讀取器已釋放管道緩衝區中的空間，否則會封鎖 `WriteFile` 呼叫。  通訊端應該一律使用接受逾時機制的某個 API。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 沒有使用 Unmanaged 程式碼之逾時的封鎖是拒絕服務攻擊。 請不要對 `WaitForSingleObject`、`WaitForSingleObjectEx`、`WaitForMultipleObjects`、`MsgWaitForMultipleObjects` 和 `MsgWaitForMultipleObjectsEx` 執行平台叫用呼叫。  請不要使用 NMPWAIT_WAIT_FOREVER。  
  
### <a name="identify-any-sta-dependent-features"></a>識別任何 STA 相依功能。  
 識別任何使用 COM 單一執行緒 Apartment (STA) 的程式碼。  在 SQL Server 處理序中，已停用 STA。  在 SQL Server 內，必須停用與 `CoInitialize` 相依的功能 (例如效能計數器或剪貼簿)。  
  
### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>確定完成項沒有同步處理問題  
 多個完成項執行緒可能存在於 .NET Framework 的未來版本中，這表示會同時執行相同類型之不同執行個體的完成項。  它們不需要完全具備執行緒安全；記憶體回收行程保證只有一個執行緒將執行所指定物件執行個體的完成項。  不過，完成項同時在多個不同的物件執行個體上執行時必須進行編碼，才能避免競爭情況和死結。  在完成項中使用任何外部狀態時 (例如寫入記錄檔)，必須處理執行緒問題。  請不要依賴可提供安全執行緒的最終處理。 請不要使用執行緒區域儲存區 (Managed 或原生)，將狀態儲存在完成項執行緒上。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 完成項必須沒有同步處理問題。 請不要在完成項中使用靜態可變動狀態。  
  
### <a name="avoid-unmanaged-memory-if-possible"></a>盡可能避免 Unmanaged 記憶體  
 Unmanaged 記憶體可能會流失，就像作業系統控制代碼一樣。  可能的話，請嘗試使用 [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) 或釘選 Managed 物件 (例如 [fixed 陳述式](~/docs/csharp/language-reference/keywords/fixed-statement.md)或使用 byte[] 的 <xref:System.Runtime.InteropServices.GCHandle>) 來使用堆疊上的記憶體。  <xref:System.GC> 最後會清除這些項目。  不過，如果您必須配置 Unmanaged 記憶體，請考慮使用衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的類別來包裝記憶體配置。  
  
 請注意，在至少一種情況下，<xref:System.Runtime.InteropServices.SafeHandle> 不足。  針對配置或釋放記憶體的 COM 方法呼叫，其中一個 DLL 通常會透過 `CoTaskMemAlloc` 來配置記憶體，另一個 DLL 則使用 `CoTaskMemFree` 來釋放該記憶體。  不適合在這些位置使用 <xref:System.Runtime.InteropServices.SafeHandle>，因為它會嘗試將 Unmanaged 記憶體的存留期繫結至 <xref:System.Runtime.InteropServices.SafeHandle> 的存留期，而不是允許另一個 DLL 控制記憶體的存留期。  
  
### <a name="review-all-uses-of-catchexception"></a>檢閱所有使用的 catch(Exception)  
 擷取所有例外狀況 (而非一個特定例外狀況) 的 catch 區塊現在也會擷取非同步例外狀況。  檢查每個 catch(Exception) 區塊，以尋找沒有可能跳過的重要資源釋放或退出程式碼，以及處理 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException> 或 <xref:System.OutOfMemoryException> 的 catch 區塊本身內可能不正確的行為。  請注意，此程式碼可能會記錄或進行一些假設，這些假設是只能看到某些例外狀況，或者僅針對一種特殊原因，只要發生例外狀況就失敗。  這些假設可能需要進行更新，以包含 <xref:System.Threading.ThreadAbortException>。  
  
 請考慮變更可擷取所有例外狀況的所有位置，而這些例外狀況是在擷取您預期要擲回之特定類型的例外狀況時發生，例如字串格式化方法的 <xref:System.FormatException>。  這會防止對非預期的例外狀況執行 catch 區塊，並且有助於確保程式碼因擷取到非預期的例外狀況而未隱藏 Bug。  因為一般規則絕不會處理程式庫程式碼中的例外狀況 (需要您擷取例外狀況的程式碼，可能指出所呼叫程式碼中的設計缺陷)。  在某些情況下，您可能想要擷取例外狀況，並擲回不同的例外狀況類型來提供更多資料。  在此情況下，請使用巢狀例外狀況，並將真正失敗原因儲存至新例外狀況的 <xref:System.Exception.InnerException%2A> 屬性中。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 檢閱所有使用 Managed 程式碼並擷取所有物件或擷取所有例外狀況的 catch 區塊。  在 C# 中，這表示同時加上旗標`catch`{}和`catch(Exception)` {}。  請考慮將例外狀況類型設為極為特別，或檢閱程式碼，確保它在擷取到非預期的例外狀況類型時不會以錯誤的方式操作。  
  
### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>不要假設 Managed 執行緒是 Win32 執行緒 - 它是 Fiber  
 使用 Managed 執行緒區域儲存區確實會運作，但您可能不會使用 Unmanaged 執行緒區域儲存區，或假設程式碼將再次於目前作業系統執行緒上執行。  請不要變更執行緒地區設定這類設定。  請不要透過平台叫用呼叫 `InitializeCriticalSection` 或 `CreateMutex`，因為它們需要進入鎖定的作業系統執行緒一併結束鎖定。  因為這不是使用 Fiber 的情況，所以 Win32 關鍵區段和 Mutex 不能直接用於 SQL 中。  請注意，Managed <xref:System.Threading.Mutex> 類別未處理這些執行緒親和性考量。  
  
 您可以在 Managed <xref:System.Threading.Thread> 物件上安全地使用大部分狀態，包含 Managed 執行緒區域儲存區和執行緒的目前 UI 文化特性 (Culture)。  您也可以使用 <xref:System.ThreadStaticAttribute>，只讓目前 Managed 執行緒存取現有靜態變數的值 (這是在 CLR 中執行 Fiber 本機儲存體的另一種方式)。  基於程式設計模型考量，在 SQL 中執行時，您不可以變更執行緒的目前文化特性。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 SQL Server 會以 Fiber 模式執行；請不要使用執行緒區域儲存區。 請避免對 `TlsAlloc`、`TlsFree`、`TlsGetValue` 和 `TlsSetValue.` 執行平台叫用呼叫。  
  
### <a name="let-sql-server-handle-impersonation"></a>讓 SQL Server 處理模擬  
 因為模擬是在執行緒層級上運作，而且 SQL 可以透過 Fiber 模式執行，所以 Managed 程式碼應該不會模擬使用者，並且應該不會呼叫 `RevertToSelf`。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 讓 SQL Server 處理模擬。 請不要使用 `RevertToSelf`、`ImpersonateAnonymousToken`、`DdeImpersonateClient`、`ImpersonateDdeClientWindow`、`ImpersonateLoggedOnUser`、`ImpersonateNamedPipeClient`、`ImpersonateSelf`、`RpcImpersonateClient`、`RpcRevertToSelf``RpcRevertToSelfEx` 或 `SetThreadToken`。  
  
### <a name="do-not-call-threadsuspend"></a>不要呼叫 Thread::Suspend  
 暫止執行緒的能力可能顯示為簡單作業，但可能會造成死結。  如果持有鎖定的執行緒是由第二個執行緒所暫止，然後第二個執行緒嘗試採用相同的鎖定，即會發生死結。  <xref:System.Threading.Thread.Suspend%2A> 目前可能會干擾安全性、類別載入、遠端處理和反映。  
  
#### <a name="code-analysis-rule"></a>程式碼分析規則  
 請不要呼叫 <xref:System.Threading.Thread.Suspend%2A>。 請考慮改成使用實際同步處理原始物件，例如 <xref:System.Threading.Semaphore> 或 <xref:System.Threading.ManualResetEvent>。  
  
### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>使用限制的執行區域和可靠性合約保護重要作業  
 執行可更新共用狀態或需要確定完全成功或完全失敗的複雜作業時，請確定它受到限制的執行區域 (CER) 的保護。 這保證程式碼可以在所有情況下執行，即使突然執行緒中止或突然 <xref:System.AppDomain> 卸載也是一樣。  
  
 CER 是前面緊接 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 呼叫的特定 `try/finally` 區塊。  
  
 這麼做會指示 Just-In-Time 編譯器在執行 `try` 區塊之前準備 finally 區塊中的所有程式碼。 這保證會建置 finally 區塊中的程式碼，而且在所有情況下都會執行該程式碼。 CER 中通常不會有空的 `try` 區塊。 使用 CER 可防止非同步執行緒中止和記憶體不足例外狀況。 請參閱 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>，以了解可額外處理極深層程式碼堆疊溢位的 CER 形式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.ConstrainedExecution>  
 [SQL Server 程式設計和主機保護屬性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
