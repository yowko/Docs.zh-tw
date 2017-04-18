---
title: "SpinWait | Microsoft Docs"
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
  - "synchronization primitives, SpinWait"
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# SpinWait
<xref:System.Threading.SpinWait?displayProperty=fullName> 是一種輕量型同步處理型別，可讓您用於低階案例中，避免核心事件所需卻高度耗費資源的內容切換和核心轉換。  在多核心電腦上，當某個資源不應該長期保存時，讓等候中的執行緒在使用者模式中空轉數十個或數百個循環，然後再重試取得資源可能會比較有效率。  如果資源在空轉之後可供使用，您就節省了數千個循環。  如果資源仍然無法使用，您也只花費少數循環，而且仍然可以進入核心架構等候。  這種空轉並等候的組合有時候也稱為「*兩階段等候作業*」\(Two\-Phase Wait Operation\)。  
  
 <xref:System.Threading.SpinWait> 是設計成搭配包裝核心事件的 .NET Framework 型別使用，例如 <xref:System.Threading.ManualResetEvent>。  您也可以針對單一程式中的基本空轉功能，單獨使用 <xref:System.Threading.SpinWait>。  
  
 <xref:System.Threading.SpinWait> 不只是空白的迴圈而已。  您可以仔細地實作此型別，以便提供適用於一般案例的正確空轉行為，而且如果它的空轉時間夠長 \(大略等於核心轉換所需的時間長度\)，就會自行起始內容切換。  例如，在單核心電腦上，<xref:System.Threading.SpinWait> 會立即產生執行緒的時間量，因為空轉會封鎖所有執行緒的順向進度。  即使在多核心電腦上，<xref:System.Threading.SpinWait> 也是如此，可避免等候中的執行緒封鎖較高優先權的執行緒或記憶體回收行程。  因此，如果您要在兩階段等候作業中使用 <xref:System.Threading.SpinWait>，我們建議您在 <xref:System.Threading.SpinWait> 自行起始內容切換之前叫用核心等候。  <xref:System.Threading.SpinWait> 會提供 <xref:System.Threading.SpinWait.NextSpinWillYield%2A> 屬性，讓您在每次呼叫 <xref:System.Threading.SpinWait.SpinOnce%2A> 之前先行檢查。  當此屬性傳回 `true` 時，請起始您自己的等候作業。  如需範例，請參閱 [How to: Use SpinWait to Implement a Two\-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)。  
  
 如果您不要執行兩階段等候作業，但是只要空轉，直到某個條件成立為止，就可以讓 <xref:System.Threading.SpinWait> 執行其內容切換，以便成為 Windows 作業系統環境中的好公民。  下列基本範例顯示無鎖定堆疊中的 <xref:System.Threading.SpinWait>。  如果您需要高效能的安全執行緒堆疊，請考慮使用 <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName>。  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## 請參閱  
 <xref:System.Threading.Thread.SpinWait%2A>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)