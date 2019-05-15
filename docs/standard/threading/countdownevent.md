---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f25ffb16fa5feb382bb42c737440317cfb777b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666312"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> 是一個同步處理基本類型，在發出了特定次數的訊號給它之後，就會解除封鎖其等候中的執行緒。 <xref:System.Threading.CountdownEvent> 是針對下列案例所設計：您必須使用 <xref:System.Threading.ManualResetEvent> 或 <xref:System.Threading.ManualResetEventSlim>，並在發出訊號給事件之前手動遞減變數。 例如，在分支/聯結案例中，您可以只建立訊號計數為 5 的 <xref:System.Threading.CountdownEvent>，然後在執行緒集區上啟動五個工作項目，並讓每個工作項目在其完成時呼叫 <xref:System.Threading.CountdownEvent.Signal%2A>。 每次呼叫 <xref:System.Threading.CountdownEvent.Signal%2A> 就會將訊號計數遞減 1。 在主執行緒上，對 <xref:System.Threading.CountdownEvent.Wait%2A> 的呼叫將會封鎖，直到訊號計數為零為止。  
  
> [!NOTE]
>  對於不需與舊版 .NET Framework 同步處理 API 互動的程式碼，請考慮使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件或 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 方法，以甚至更簡單的方式表達分支-聯結的平行處理原則。  
  
 <xref:System.Threading.CountdownEvent> 具有下列其他功能：  
  
- 等候作業可以使用取消語彙基元來取消。  
  
- 建立執行個體之後，即可遞增其訊號計數。  
  
- 藉由呼叫 <xref:System.Threading.CountdownEvent.Reset%2A> 方法傳回 <xref:System.Threading.CountdownEvent.Wait%2A> 之後，就可重複使用執行個體。  
  
- 執行個體會公開 <xref:System.Threading.WaitHandle>，以便與其他 .NET Framework 同步處理 API 整合，例如 <xref:System.Threading.WaitHandle.WaitAll%2A>。  
  
## <a name="basic-usage"></a>基本使用方式  
 下列範例示範如何將 <xref:System.Threading.CountdownEvent> 與 <xref:System.Threading.ThreadPool> 工作項目搭配使用。  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>含有取消的 CountdownEvent  
 下列範例示範如何使用取消語彙基元，來取消 <xref:System.Threading.CountdownEvent> 上的等候作業。 基本模式會遵循適用於統一取消的模型，這是在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中引進的。 如需詳細資訊，請參閱[受控執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)。  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 請注意，等候作業不會取消正在發出訊號給它的執行緒。 一般而言，會將取消套用至邏輯作業，其中可以包括在事件上等候，以及正在同步處理等候的所有工作項目。 在此範例中，會針對每個工作項目傳遞相同取消語彙基元的複本，讓它可以回應取消要求。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
