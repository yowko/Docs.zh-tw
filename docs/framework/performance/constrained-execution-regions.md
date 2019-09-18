---
title: 限制的執行區域
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0561ff5212fd6bc4e9015bea8da1d1082dd027e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046700"
---
# <a name="constrained-execution-regions"></a>限制的執行區域
限制的執行區域 (CER) 是編寫可靠 Managed 程式碼的機制一部分。 CER 定義一個區域，其中限制 Common Language Runtime (CLR) 擲回頻外例外狀況，而頻外例外狀況會防止執行區域中的整個程式碼。 在該區域內，使用者程式碼無法執行導致擲回頻外例外狀況的程式碼。 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的前面必須緊接著 `try` 區塊，並將 `catch`、`finally` 和 `fault` 區塊標記為限制的執行區域。 標記為限制的區域之後，程式碼只能呼叫具有強式可靠性合約的其他程式碼；而且，除非程式碼已準備好處理失敗，否則程式碼不應該配置非預期或不可靠的方法，或是對其進行虛擬呼叫。 CLR 會針對在 CER 中執行的程式碼延遲執行緒中止。  
  
 除了已標註的 `try` 區塊之外，限制的執行區域還會以不同的形式用於 CLR 中，值得注意的是在衍生自 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> 類別的類別以及使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 方法執行之程式碼中執行的重要完成項。  
  
## <a name="cer-advance-preparation"></a>CER 事先準備  
 CLR 會事先準備 CER，以避免記憶體不足的情況。 需要事先準備，讓 CLR 不會在 Just-In-Time 編譯或類型載入期間導致記憶體不足。  
  
 開發人員需要指出程式碼區域為 CER：  
  
- 完整呼叫歷程圖中已套用 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 屬性的最上層 CER 區域和方法會事先備妥。 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 只能是狀態保證 <xref:System.Runtime.ConstrainedExecution.Cer.Success> 或 <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>。  
  
- 針對無法靜態判斷的呼叫 (例如虛擬分派)，無法進行事先準備。 在這些情況下，請使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法。 使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 方法時，應該將 <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> 屬性套用至清除程式碼。  
  
## <a name="constraints"></a>條件約束  
 使用者只能使用他們以 CER 撰寫的程式碼類型。 程式碼不會導致頻外例外狀況，例如可能是下列作業所導致：  
  
- 明確配置。  
  
- Boxing。  
  
- 取得鎖定。  
  
- 幾乎會呼叫未備妥的方法。  
  
- 呼叫具有弱式或不存在可靠性合約的方法。  
  
 在 .NET Framework 版本 2.0 中，這些條件約束是指導方針。 診斷是透過程式碼分析工具所提供。  
  
## <a name="reliability-contracts"></a>可靠性合約  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 是一個自訂屬性，記載所指定方法的可靠性保證和損毀狀態。  
  
### <a name="reliability-guarantees"></a>可靠性保證  
 可靠性保證是以 <xref:System.Runtime.ConstrainedExecution.Cer> 列舉值呈現，指出所指定方法的可靠性程度：  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. 在例外狀況下，此方法可能會失敗。 在此情況下，此方法會向呼叫端方法回報成功還是失敗。 此方法必須包含在 CER 中，確保它可以報告傳回值。  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. 方法、類型或組件沒有 CER 的概念，而且很可能無法在 CER 內安全地呼叫，進而大幅降低狀態損毀。 它不會利用 CER 保證。 這具有如下表示：  
  
    1. 在例外狀況下，此方法可能會失敗。  
  
    2. 此方法不一定會報告失敗。  
  
    3. 不會寫入此方法來使用 CER，這是最常見案例。  
  
    4. 如果未將方法、類型或組件明確地識別為成功，則會將它隱含地識別為 <xref:System.Runtime.ConstrainedExecution.Cer.None>。  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. 在例外狀況下，此方法一定會成功。 為了達到這個層級的可靠性，您應該一律建構所呼叫方法的 CER，即使是從非 CER 區域內呼叫它也是一樣。 如果方法如預期完成，則方法會成功，但可以主觀檢視成功。 例如，將 Count 標上 `ReliabilityContractAttribute(Cer.Success)` 表示在 CER 下執行時，一律會傳回 <xref:System.Collections.ArrayList> 中的項目計數，而且絕不會讓內部欄位處於未定狀態。  不過，也會將 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法標記為成功，並了解成功可能表示因競爭條件而無法將值取代為新值。  重點在於此方法會依記載的運作方式運作，而且不需要寫入 CER 程式碼，以預期正確行為以外的任何異常行為，但不可靠程式碼看起來都一樣。  
  
### <a name="corruption-levels"></a>損毀層級  
 損毀層級是以 <xref:System.Runtime.ConstrainedExecution.Consistency> 列舉值呈現，指出所指定環境中有多少狀態可能損毀：  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. 在例外狀況下，Common Language Runtime (CLR) 不保證目前應用程式定義域中的狀態一致性。  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. 在例外狀況下，保證此方法將狀態損毀限制為目前執行個體。  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>：在例外狀況下，CLR 不保證相關狀態一致性；亦即，此狀況可能會損毀處理序。  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. 在例外狀況下，此方法一定不會損毀狀態。  
  
## <a name="reliability-trycatchfinally"></a>可靠性 try/catch/finally  
 可靠性 `try/catch/finally` 是一種例外狀況處理機制，且預測性保證的層級與未管理版本相同。 `catch/finally` 區塊是 CER。 區塊中的方法需要事先準備，而且必須為不可中斷。  
  
 在 .NET Framework 版本 2.0 中，程式碼會透過在 try 區塊之前立即呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>，以通知執行階段 try 是可靠的。 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 是 <xref:System.Runtime.CompilerServices.RuntimeHelpers> 的成員，即編譯器支援類別。 直接呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 以透過編譯器暫止可用性。  
  
## <a name="noninterruptible-regions"></a>不可中斷區域  
 不可中斷區域會將一組指示分組為 CER。  
  
 在 .NET Framework 版本 2.0 中，透過編譯器支援暫止可用性，使用者程式碼會建立不可中斷區域，而此不可中斷區域具有在 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法呼叫之前包含空 try/catch 區塊的可靠 try/catch/finally。  
  
## <a name="critical-finalizer-object"></a>關鍵完成項物件  
 記憶體回收將執行完成項的 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> 保證。 配置時，會事先準備完成項和其呼叫歷程圖。 完成項方法是在 CER 中執行，而且必須遵守 CER 和完成項的所有條件約束。  
  
 任何繼承自 <xref:System.Runtime.InteropServices.SafeHandle> 和 <xref:System.Runtime.InteropServices.CriticalHandle> 的類型都一定會在 CER 內執行其完成項。 在 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別中實作 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>，以執行釋放控制代碼所需的任何程式碼。  
  
## <a name="code-not-permitted-in-cers"></a>CER 中不允許的程式碼  
 CER 中不允許下列作業：  
  
- 明確配置。  
  
- 取得鎖定。  
  
- Boxing。  
  
- 多維陣列存取。  
  
- 透過反映的方法呼叫。  
  
- <xref:System.Threading.Monitor.Enter%2A> 或 <xref:System.IO.FileStream.Lock%2A>。  
  
- 安全性檢查。 請不要執行要求，而是連結要求。  
  
- COM 物件和 Proxy 的 <xref:System.Reflection.Emit.OpCodes.Isinst> 和 <xref:System.Reflection.Emit.OpCodes.Castclass>  
  
- 取得或設定 Transparent Proxy 上的欄位。  
  
- 序列化：  
  
- 函式指標和委派。  
  
## <a name="see-also"></a>另請參閱

- [可靠性最佳做法](reliability-best-practices.md)
