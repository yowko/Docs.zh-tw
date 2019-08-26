---
title: Managed 執行緒中的例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 689ee44980a4a41b6d46ed9b68306c1b08c49586
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960067"
---
# <a name="exceptions-in-managed-threads"></a>Managed 執行緒中的例外狀況
從 .NET Framework version 2.0 開始，通用語言執行平台允許執行緒中大多數未處理的例外狀況自然地繼續。 在大多數情況下，這表示未處理的例外狀況導致應用程式終止。  
  
> [!NOTE]
> 這是 .NET Framework 1.0 和 1.1 的重大變更，其針對許多未處理的例外狀況提供了防護網 — 例如，執行緒集區執行緒中的例外狀況。 請參閱本主題後面的[從舊版變更](#ChangeFromPreviousVersions)。  
  
 通用語言執行平台針對用於控制程式流程的特定未處理例外狀況提供了防護網︰  
  
- 因為呼叫了 <xref:System.Threading.Thread.Abort%2A>，而導致執行緒中擲回 <xref:System.Threading.ThreadAbortException>。  
  
- 因為正在卸載執行緒執行所在的應用程式定義域，而在執行緒中擲回 <xref:System.AppDomainUnloadedException>。  
  
- 通用語言執行平台或主機處理序會藉由擲回內部例外狀況來終止執行緒。  
  
 如果在通用語言執行平台所建立的執行緒中有上述任何未處理的例外狀況，則此例外狀況會終止執行緒，但通用語言執行平台不允許例外狀況進一步繼續作業。  
  
 如果未在主要執行緒中，或在從 Unmanaged 程式碼進入執行平台的執行緒中處理這些例外狀況，這些例外狀況會正常進行，而導致應用程式終止。  
  
> [!NOTE]
> 在任何 Managed 程式碼有機會安裝例外狀況處理常式之前，執行平台可能會擲回未處理的例外狀況。 即使 Managed 程式碼沒有機會處理這類例外狀況，但允許例外狀況自然地進行。  
  
## <a name="exposing-threading-problems-during-development"></a>公開開發期間的執行緒問題  
 若允許執行緒以無訊息模式失敗，而不終止應用程式，則可能偵測不到嚴重的程式設計問題。 這是長時間執行的服務和其他應用程式特有的問題。 因為執行緒失敗，所以程式狀態會逐漸變差。 應用程式效能可能會降低，或應用程式可能會停止回應。  
  
 允許執行緒中的未處理例外狀況自然地進行，直到作業系統終止程式，公開開發和測試期間的這類問題為止。 程式終止的錯誤報告可支援偵錯。  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>從舊版變更  
 最重大的變更與 Managed 執行緒有關。 在 .NET Framework 1.0 和 1.1 版中，通用語言執行平台會針對下列情況中未處理的例外狀況提供防護網：  
  
- 執行緒集區執行緒上不會有未處理的例外狀況。 當工作擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後將執行緒傳回到執行緒集區。  
  
- 使用 <xref:System.Threading.Thread> 類別的 <xref:System.Threading.Thread.Start%2A> 方法建立的執行緒上不會有未處理例外狀況之類的項目。 在此種執行緒上執行的程式碼擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後正常終止執行緒。  
  
- 完成項執行緒上不會有未處理的例外狀況。 當完成項擲回未處理的例外狀況時，執行平台會將例外狀況堆疊追蹤列印到主控台，然後允許完成項執行緒繼續執行完成項。  
  
 Managed 執行緒的前景或背景狀態不會影響此行為。  
  
 若為源自於 Unmanaged 程式碼的執行緒上未處理的例外狀況，差別更加細微。 對於已通過機器碼之執行緒上的 Managed 例外狀況或原生例外狀況而言，執行階段 JIT-attach 對話方塊的順序優先於作業系統對話方塊。 在所有情況下，此處理序會終止。  
  
### <a name="migrating-code"></a>移轉程式碼  
 一般而言，變更會公開先前無法辨識的程式設計問題，以便修正這些問題。 不過，在某些情況下，程式設計人員可能已利用執行階段防護網來終止執行緒。 視情況而定，它們應該考慮下列其中一個移轉策略︰  
  
- 重新建構程式碼，讓執行緒在收到訊號時依正常程序結束。  
  
- 使用 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 方法來中止執行緒。  
  
- 如果執行緒必須停止，處理序終止作業才能繼續，請讓執行緒成為背景執行緒，以便在處理序結束時自動終止。  
  
 在所有情況下，此策略應該遵循例外狀況的設計方針。 請參閱[例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)。  
  
### <a name="application-compatibility-flag"></a>應用程式相容性旗標  
 系統管理員可以在應用程式組態檔的 `<runtime>` 區段中放置相容性旗標，做為暫存的相容性度量。 這會導致通用語言執行平台還原為 1.0 和 1.1 版的行為。  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>主機覆寫  
 在 .NET Framework 2.0 版中，Unmanaged 主機可以使用裝載 API 中的 [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) 介面，覆寫通用語言執行平台的預設未處理例外狀況原則。 [Iclrpolicymanager:: Setunhandledexceptionpolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) 函數用來設定未處理例外狀況的原則。  
  
## <a name="see-also"></a>另請參閱

- [Managed 執行緒處理的基本概念](../../../docs/standard/threading/managed-threading-basics.md)
