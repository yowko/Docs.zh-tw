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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>是輕量型同步處理類型，您可以使用低層級的案例中，以避免昂貴的內容切換和核心轉換所需的核心事件。 多核心電腦上，當資源不會保留很長一段時間，可能很少數數十個或少數幾個數百個週期，微調以使用者模式，然後重試以取得此資源等候執行緒比較有效率。 如果在旋轉之後有可用資源，就會儲存數個數千個循環。 如果仍然無法使用的資源，您只有少數的循環花了，並且輸入核心為基礎的等候。 這種旋轉然後等待組合有時稱為*兩階段等候作業*。  
  
 <xref:System.Threading.SpinWait>設計為可搭配.NET Framework 型別，例如包裝核心事件<xref:System.Threading.ManualResetEvent>。 <xref:System.Threading.SpinWait>也可用本身在只有一個程式中執行基本微調功能。  
  
 <xref:System.Threading.SpinWait>是不只是空的迴圈。 小心地實作一般案例中，提供正確的旋轉行為，並且將本身起始內容切換如果旋轉表示足夠的時間 （大約核心轉換所需的時間長度）。 例如，在單一核心電腦<xref:System.Threading.SpinWait>之執行緒的時間配量，會產生立即因為微調區塊轉送所有執行緒上的進度。 <xref:System.Threading.SpinWait>若要防止封鎖較高優先權的執行緒或記憶體回收行程等候執行緒的多核心電腦上，甚至也會產生。 因此，如果您使用<xref:System.Threading.SpinWait>在兩階段等候作業中，我們建議您叫用核心等候<xref:System.Threading.SpinWait>本身會起始內容切換。 <xref:System.Threading.SpinWait>提供<xref:System.Threading.SpinWait.NextSpinWillYield%2A>屬性，您可以檢查之前的每個呼叫<xref:System.Threading.SpinWait.SpinOnce%2A>。 當屬性傳回`true`，起始您自己的等候作業。 如需範例，請參閱[How to： 使用 SpinWait 實作兩階段等候作業](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)。  
  
 如果您不會執行兩階段等候作業，但正在只微調，直到某些條件為真，您可以啟用<xref:System.Threading.SpinWait>執行其內容會切換以便在 Windows 作業系統環境中的優良。 下列基本範例會示範<xref:System.Threading.SpinWait>無鎖定的堆疊中。 如果您需要高效能、 安全執行緒的堆疊，請考慮使用<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>。  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
