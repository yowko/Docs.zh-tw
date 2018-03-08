---
title: SpinWait
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1e67dd59464de09a35941d91ef984db6b7779b8c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> 是一個輕量型同步處理類型，您可以在低階案例中使用此類型，來避免核心事件所需且成本昂貴的環境切換和核心轉換。 在多核心電腦上，預期資源不會長時間保留時，若等待中的執行緒要在使用者模式中進行數十個或數百個週期的微調，然後進行重試以取得資源，此類型可能會更有效率。 如果資源在微調之後可供使用，則您節省了數千個週期。 如果資源仍然無法使用，則您只花費了數個週期，仍可進入以核心為基礎的等候。 這個微調然後等候的組合有時稱為「兩階段等候作業」。  
  
 <xref:System.Threading.SpinWait> 是設計來與 .NET Framework 類型搭配使用，這些類型會包裝諸如 <xref:System.Threading.ManualResetEvent> 的核心事件。 <xref:System.Threading.SpinWait> 也可單獨用來只在一個程式中進行基本微調功能。  
  
 <xref:System.Threading.SpinWait> 不只是個空白迴圈。 謹慎地實作它以針對一般案例提供正確的調整行為，而且如果它微調的時間夠長 (大約是核心轉換所需的時間長度)，將會自己起始環境切換。 例如，在單一核心電腦上，<xref:System.Threading.SpinWait> 會立即產生執行緒的時間配量，因為微調區塊會轉送所有執行緒上的進度。 即使在多核心電腦上，<xref:System.Threading.SpinWait> 也會產生以防止等候中的執行緒封鎖較高優先順序的執行緒或記憶體回收行程。 因此，如果您在兩階段等候作業中使用 <xref:System.Threading.SpinWait>，我們建議您在 <xref:System.Threading.SpinWait> 自己起始環境切換之前，先叫用核心等候。 <xref:System.Threading.SpinWait> 提供 <xref:System.Threading.SpinWait.NextSpinWillYield%2A> 屬性，您可以在進行每個對 <xref:System.Threading.SpinWait.SpinOnce%2A> 的呼叫之前檢查此屬性。 當屬性傳回 `true` 時，起始您自己的等候作業。 如需範例，請參閱[如何：使用 SpinWait 實作兩階段等候作業](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)。  
  
 如果您並未執行兩階段等候作業，而只是進行微調，直到某些條件成立，則您可以啟用 <xref:System.Threading.SpinWait> 來執行它的環境切換，讓它成為 Windows 作業系統環境中的好公民。 下列基本範例示範無鎖定堆疊中的 <xref:System.Threading.SpinWait>。 如果您需要高效能、安全執行緒的堆疊，請考慮使用 <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>。  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
