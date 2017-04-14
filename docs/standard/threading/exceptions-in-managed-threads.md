---
title: "Exceptions in Managed Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unhandled exceptions,in managed threads"
  - "threading [.NET Framework],unhandled exceptions"
  - "threading [.NET Framework],exceptions in managed threads"
  - "managed threading"
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Exceptions in Managed Threads
在 .NET Framework 2.0 版中，Common Language Runtime 可讓執行緒中的大多數未處理的例外狀況可以自然地進行。  在多數情況下，這表示未處理的例外狀況會讓應用程式結束。  
  
> [!NOTE]
>  這是 .NET Framework 1.0 和 1.1 版之後的一項重大變更，可以為許多未處理的例外狀況提供類似捕手的機制；例如，執行緒集區執行緒中的未處理例外狀況。  請參閱本主題稍後的[舊版的變更](#ChangeFromPreviousVersions)。  
  
 Common Language Runtime 為某些用於控制程式流程的未處理之例外狀況提供了類似捕手的機制：  
  
-   在執行緒中擲回 <xref:System.Threading.ThreadAbortException>，因為已呼叫 <xref:System.Threading.Thread.Abort%2A>。  
  
-   在執行緒中擲回 <xref:System.AppDomainUnloadedException>，因為執行緒執行所在的應用程式定義域正在卸載。  
  
-   Common Language Runtime 或主應用程式處理序藉由擲回內部例外狀況來結束執行緒。  
  
 如果在 Common Language Runtime 建立的執行緒中有任何例外狀況未被處理，則此例外狀況會結束執行緒，但是 Common Language Runtime 不允許此例外狀況有進一步的動作。  
  
 如果這些例外狀況在主執行緒，或是從 Unmanaged 程式碼進入執行階段的執行緒中未被處理，則這些例外狀況會正常進行，因而造成應用程式終止。  
  
> [!NOTE]
>  執行階段有可能先擲回未處理的例外狀況之後，Managed 程式碼才會有機會安裝例外處理常式。  即使 Managed 程式碼沒有機會來處理這類例外狀況，還是允許此例外狀況自然地進行。  
  
## 在開發期間公開執行緒處理問題  
 當允許執行緒在無訊息模式下失敗，而不結束應用程式時，可能會有一些嚴重的程式設計問題未被偵測到，  這會特別是執行一段時間的服務和其他應用程式的問題。  當執行緒失敗時，程式狀態會逐漸損毀。  如此一來，應用程式效能可能會降低，或應用程式可能會無回應。  
  
 允許執行緒中未處理的例外狀況自然地進行，一直到作業系統結束程式為止，這樣的作法會在開發和測試期間暴露出這類的問題。  程式終止的錯誤報告可支援偵錯。  
  
<a name="ChangeFromPreviousVersions"></a>   
## 舊版之後的變更  
 最重大的變更與 Managed 執行緒有關。  在 .NET Framework 1.0 和 1.1 版中，在下列情況下，Common Language Runtime 會為未處理的例外狀況提供類似捕手的機制：  
  
-   並沒有所謂的執行緒集區執行緒上的未處理之例外狀況這一回事；  當工作擲回未處理的例外狀況時，執行階段會將此例外狀況堆疊追蹤列印到主控台，然後將執行緒傳回到執行緒集區。  
  
-   以 <xref:System.Threading.Thread> 類別的 <xref:System.Threading.Thread.Start%2A> 方法所建立的執行緒上，並沒有所謂的未處理之例外狀況這一回事。  在這類執行緒上執行的程式碼擲回未處理的例外狀況時，執行階段會將此例外狀況堆疊追蹤列印到主控台，然後以正常方式結束執行緒。  
  
-   並沒有所謂的完成項執行緒上的未處理之例外狀況這一回事；  當完成項擲回未處理的例外狀況時，執行階段會將此例外狀況堆疊追蹤列印到主控台，然後將允許此完成項執行緒繼續執行完成項。  
  
 Managed 執行緒的前景或背景狀態並不會影響這個行為。  
  
 對於源自 Unmanaged 程式碼的執行緒上的例外狀況而言，其差異比較敏感。  執行階段 JIT 附加的對話方塊會先佔有 Managed 例外狀況或原生例外狀況的作業系統對話方塊 \(這些例外狀況位於透過機器碼傳遞的執行緒上\)。  在所有情況下，此處理序都會結束。  
  
### 移轉程式碼  
 一般來說，此變更會暴露出之前未被辨認的程式設計問題，以便可以加以修復。  但是在某些情況下，程式設計人員可能利用了類似執行階段捕手機制這樣的好處來結束執行緒；  他們應該根據狀況來考量下列其中一個移轉策略：  
  
-   重組程式碼的結構，在收到信號時讓執行緒正常地結束。  
  
-   使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 方法來中止執行緒。  
  
-   如果一定要停止執行緒，才能進行處理序終止的作業，請讓此執行緒變成背景執行緒，讓它在處理序結束時會自動結束。  
  
 在所有情況下，這個策略都應該遵循例外狀況的設計方針。  請參閱[例外狀況的設計指導方針](../../../docs/standard/design-guidelines/exceptions.md)。  
  
### 應用程式相容性旗標  
 系統管理員可以將相容性旗標放在應用程式組態檔的 `<runtime>` 區段內，做為暫時性的相容性措施；  如此可讓 Common Language Runtime 還原成 1.0 和 1.1 版的行為。  
  
```  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## 主應用程式覆寫  
 在 .NET Framework 2.0 版中，Unmanaged 主應用程式可以使用裝載在 API 中的 [ICLRPolicyManager](../../../ocs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) 介面，以覆寫 Common Language Runtime 的預設未處理之例外狀況原則。  [ICLRPolicyManager::SetUnhandledExceptionPolicy](../Topic/ICLRPolicyManager::SetUnhandledExceptionPolicy%20Method.md) 函式是用來設定未處理的例外狀況之原則。  
  
## 請參閱  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)