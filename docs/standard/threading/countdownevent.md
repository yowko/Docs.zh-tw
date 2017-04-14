---
title: "CountdownEvent | Microsoft Docs"
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
  - "synchronization primitives, CountdownEvent"
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=fullName> 是同步處理原始物件，在收到特定次數的訊號後，該物件會解除對其等待執行緒的封鎖。  <xref:System.Threading.CountdownEvent> 旨在用於以下案例：在傳送訊號至事件之前，您必須使用 <xref:System.Threading.ManualResetEvent> 或 <xref:System.Threading.ManualResetEventSlim> 並需手動遞減變數。  例如，在 fork\/join 案例中，您可以只建立具有 5 個訊號計數的 <xref:System.Threading.CountdownEvent>，然後在執行緒集區上啟動五個工作項目，並讓每個工作項目在完成時呼叫 <xref:System.Threading.CountdownEvent.Signal%2A>。  每次呼叫 <xref:System.Threading.CountdownEvent.Signal%2A> 都會將訊號計數遞減 1。  在主執行緒上，直到訊號計數為零，都會封鎖對 <xref:System.Threading.CountdownEvent.Wait%2A> 的呼叫。  
  
> [!NOTE]
>  若無需與舊版 .NET Framework 同步化 API程式碼互動，請考慮使用 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 物件和 \(或\) <xref:System.Threading.Tasks.Parallel.Invoke%2A> 方法，以更輕鬆的方式表示 fork\-join 平行處理原則。  
  
 <xref:System.Threading.CountdownEvent> 具有下列其他功能：  
  
-   使用取消語彙基元，可以取消等待作業。  
  
-   在建立執行個體之後，可以遞增其訊號計數。  
  
-   在透過呼叫 <xref:System.Threading.CountdownEvent.Reset%2A> 方法傳回  <xref:System.Threading.CountdownEvent.Wait%2A> 之後，可以重複使用執行個體。  
  
-   執行個體會公開一個 <xref:System.Threading.WaitHandle>，以便與其他 .NET Framework 同步化 API 整合，例如 <xref:System.Threading.WaitHandle.WaitAll%2A>。  
  
## 基本使用方式  
 下列範例示範如何使用 <xref:System.Threading.CountdownEvent> 搭配 <xref:System.Threading.ThreadPool> 工作項目。  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## 啟用取消作業的 CountdownEvent  
 下列範例示範如何使用取消語彙基元，取消 <xref:System.Threading.CountdownEvent> 的等待作業。  基本模式遵循統一的取消模型，該模型在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中引入。  如需詳細資訊，請參閱[Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)。  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 請注意，等待作業不會取消發出其信號的執行緒。  通常，取消會套用至邏輯操作，並且可以包含事件的等待以及等待正在同步化的所有工作項目。  在此範例中，每個工作項目都接收相同的取消語彙基元的副本，以便其可以回應取消要求。  
  
## 請參閱  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)