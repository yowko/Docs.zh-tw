---
title: "限制的執行區域 | Microsoft Docs"
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
  - "CER"
  - "限制的執行區域"
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 限制的執行區域
限制的執行區域 \(CER\) 是用來撰寫可靠 Managed 程式碼之機制中的一部分；  CER 會定義一個區域，其中會限制 Common Language Runtime \(CLR\) 擲回 Out\-of\-Band 例外狀況 \(此例外狀況會讓此區域內的程式碼無法完整執行\)。  在該區域中，會限制使用者程式碼執行將導致 Out\-of\-Band 例外狀況擲回的程式碼。  <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法必須緊接在 `try` 區塊的前面，並將 `catch`、`finally` 和 `fault` 區塊標記為限制的執行區域。  一旦標記為限制的區域之後，程式碼只能以效力充分之可靠性合約呼叫其他程式碼，且程式碼不應該配置或發出未準備或不可靠方法的虛擬呼叫，除非此程式碼已準備好可處理失敗。  CLR 會針對在 CER 中執行的程式碼延遲執行緒中止。  
  
 除了加註的 `try` 區塊之外、在衍生自 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> 類別的類別中執行之格外重要的完成項，以及使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 方法執行的程式碼之外，限制的執行區域也會在 CLR 中以不同的形式來使用。  
  
## CER 事先準備  
 CLR 會預先準備 CER，以避免發生記憶體不足的情況。  事先準備是必要的工作，可讓 CLR 不會造成在 Just\-in\-Time 編譯或型別載入期間發生記憶體不足的狀況。  
  
 開發人員必須要指示程式碼區域為 CER：  
  
-   最上層 CER 區域以及在完整呼叫圖形中已套用 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 屬性之方法已事先準備好。  <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 只能陳述 <xref:System.Runtime.ConstrainedExecution.Cer> 或 <xref:System.Runtime.ConstrainedExecution.Cer> 的保證。  
  
-   如果是無法以靜態方式判斷的呼叫 \(例如虛擬分派\)，將無法執行事先準備工作；  在這些情況下，請使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法。  當使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> 方法時，應該套用 <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> 屬性來清除程式碼。  
  
## 條件約束  
 使用者在他們可於 CER 中編寫的程式碼類型有受到限制。  此程式碼不能造成 Out\-of\-Band 例外狀況，而此例外狀況可能是因為下列作業所造成：  
  
-   明確配置。  
  
-   Boxing。  
  
-   取得鎖定。  
  
-   以虛擬方式呼叫未準備的方法。  
  
-   以弱式或不存在的可靠性合約呼叫方法。  
  
 在 .NET Framework 2.0 版中，這些條件約束為方針；  可透過程式碼分析工具來提供診斷。  
  
## 可靠性合約  
 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> 是一個自訂屬性，它可記錄指定之方法的可靠性保證和損毀狀態。  
  
### 可靠性保證  
 由 <xref:System.Runtime.ConstrainedExecution.Cer> 列舉值表示的可靠性保證，可指示指定之方法的可靠性等級：  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  在例外情況下，此方法可能會失敗。  此時，此方法會回報給呼叫的方法，指示成功或失敗。  此方法必須包含在 CER 中，以確保它可以報告傳回值。  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  方法、型別或組件沒有 CER 的任何概念，所以如果沒有有效降低狀態損毀，則在 CER 中呼叫很可能會不安全；  它不會利用 CER 保證，  這暗示了下列情況：  
  
    1.  在例外情況下，此方法可能會失敗。  
  
    2.  此方法不一定會報告它失敗的情形。  
  
    3.  此方法未編寫為要使用 CER，這是最可能的情況。  
  
    4.  如果方法、型別或組件並未明確識別為成功，則會將它隱含識別為 <xref:System.Runtime.ConstrainedExecution.Cer>。  
  
-   <xref:System.Runtime.ConstrainedExecution.Cer>.  在例外情況下，保證此方法會成功。  為了達成這個等級的可靠性，您一定要在呼叫的方法周圍建構 CER，即使是在非 CER 區域內呼叫時亦然。  如果方法達成了它所應該做的工作，則表示成功 \(雖然成功的看法可能會很主觀\)。  例如，以 `ReliabilityContractAttribute(Cer.Success)` 標記 Count 暗示著當它在 CER 之下執行時，它一定會傳回 <xref:System.Collections.ArrayList> 的元素計數，且絕對不會讓內部欄位留在未定的狀態中。但是，<xref:System.Threading.Interlocked.CompareExchange%2A> 方法同樣也會標記為成功，其認知是成功可能意旨該值無法以新的值取代，因為有競爭情形的緣故。關鍵點在於，此方法的行為模式是根據文件記錄的內容，所以不需要將 CER 程式碼編寫為在正確但不可靠之程式碼的可能面貌之外，還預期會有任何不尋常的行為。  
  
### 損毀等級  
 由 <xref:System.Runtime.ConstrainedExecution.Consistency> 列舉值表示的損毀等級，可指示狀態在指定之環境內可能的損毀程度：  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  在例外情況下，Common Language Runtime \(CLR\) 不會對目前應用程式定義域中的狀態一致性做出任何保證。  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  在例外情況下，保證這個方法可將狀態損毀限制為目前的執行個體。  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency> \- 在例外情況下，CLR 不會對狀態一致性做出任何保證，也就是說，此狀況可能會損毀處理序。  
  
-   <xref:System.Runtime.ConstrainedExecution.Consistency>.  在例外情況下，保證此方法不會損毀狀態。  
  
## 可靠性 try\/catch\/finally  
 可靠性 `try/catch/finally` 是一個例外狀況處理機制，其可預測性保證的等級與 Unmanaged 版本相同。  `catch/finally` 區塊為 CER，  此區塊中的方法必須有事先準備，且不能中斷。  
  
 在 .NET Framework 2.0 版中，程式碼會緊接在 try 區塊之前呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>，向執行階段告知 try 是可靠的；  <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 是 <xref:System.Runtime.CompilerServices.RuntimeHelpers> \(亦即一種編譯器支援類別\) 的成員。  透過編譯器直接呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 來暫止它的可用性。  
  
## 不可中斷的區域  
 不可中斷的區域會將一組指令群組到 CER 中。  
  
 在 .NET Framework 2.0 版中，透過編譯器支援暫止可用性時，使用者程式碼會使用可靠的 try\/catch\/finally 建立不可中斷的區域 \(此 try\/catch\/finally 包含一個空的 try\/catch 區塊，此區塊前面有 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法呼叫\)。  
  
## 重要的完成項物件  
 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> 保證記憶體回收將會執行此完成項。  在配置之後，會事先準備此完成項和它的呼叫圖形。  此完成項方法會在 CER 中執行，且必須遵守 CER 和完成項上的所有條件約束。  
  
 保證任何衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 和 <xref:System.Runtime.InteropServices.CriticalHandle> 的型別都一定會讓其完成項在 CER 內執行。  在 <xref:System.Runtime.InteropServices.SafeHandle> 衍生類別中實作 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 可執行釋放控制代碼所需的任何程式碼。  
  
## CER 中不允許的程式碼  
 不允許在 CER 中進行下列作業：  
  
-   明確配置。  
  
-   取得鎖定。  
  
-   Boxing。  
  
-   多維陣列存取。  
  
-   透過反映的方法呼叫。  
  
-   <xref:System.Threading.Monitor.Enter%2A> 或 <xref:System.IO.FileStream.Lock%2A>。  
  
-   安全性檢查。  不要執行要求，只要連結要求。  
  
-   COM 物件和 Proxy 的 <xref:System.Reflection.Emit.OpCodes.Isinst> 和 <xref:System.Reflection.Emit.OpCodes.Castclass>。  
  
-   在 Transparent Proxy 上取得或設定欄位。  
  
-   序列化。  
  
-   函式指標和委派。  
  
## 請參閱  
 [可靠性最佳作法](../../../docs/framework/performance/reliability-best-practices.md)