---
title: CountdownEvent
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
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>是同步處理基本類型，會在之後解除封鎖其等候中執行緒收到信號特定次數。 <xref:System.Threading.CountdownEvent>設計案例中您原本必須使用<xref:System.Threading.ManualResetEvent>或<xref:System.Threading.ManualResetEventSlim>和手動遞減變數之前信號事件。 例如，在分岔/聯結的案例中，您可以只建立<xref:System.Threading.CountdownEvent>訊號計數為 5，且開始五個工作項目上的執行緒集區，然後讓每個工作項目呼叫<xref:System.Threading.CountdownEvent.Signal%2A>完成時。 每次呼叫<xref:System.Threading.CountdownEvent.Signal%2A>遞減訊號計數 1。 在主執行緒的呼叫上<xref:System.Threading.CountdownEvent.Wait%2A>會阻擋，直到訊號計數為零。  
  
> [!NOTE]
>  對於不需要與舊版.NET Framework 同步處理應用程式開發介面互動的程式碼，請考慮使用<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>物件或<xref:System.Threading.Tasks.Parallel.Invoke%2A>即使比較簡單的方式來表達分岔 / 聯結的平行處理原則的方法。  
  
 <xref:System.Threading.CountdownEvent>具有這些額外的功能：  
  
-   等候作業可以取消使用取消語彙基元。  
  
-   建立執行個體之後，可以遞增其訊號計數。  
  
-   之後可以重複使用執行個體<xref:System.Threading.CountdownEvent.Wait%2A>已藉由呼叫傳回<xref:System.Threading.CountdownEvent.Reset%2A>方法。  
  
-   執行個體公開<xref:System.Threading.WaitHandle>與其他.NET Framework 的同步處理應用程式開發介面的整合例如<xref:System.Threading.WaitHandle.WaitAll%2A>。  
  
## <a name="basic-usage"></a>基本使用方式  
 下列範例示範如何使用<xref:System.Threading.CountdownEvent>與<xref:System.Threading.ThreadPool>工作項目。  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>處理取消 CountdownEvent  
 下列範例示範如何取消之等候作業上<xref:System.Threading.CountdownEvent>使用取消語彙基元。 基本模式遵循針對統一的取消，在引進模型[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]。 如需詳細資訊，請參閱[Managed 執行緒中的取消](../../../docs/standard/threading/cancellation-in-managed-threads.md)。  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 請注意，等候作業並不會取消會通知的執行緒。 一般而言，取消套用邏輯作業，且可包括等候事件，以及同步處理在等候所有工作項目。 在此範例中，每個工作項目會傳遞一份相同的取消語彙基元，讓它可以回應取消要求。  
  
## <a name="see-also"></a>另請參閱  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
