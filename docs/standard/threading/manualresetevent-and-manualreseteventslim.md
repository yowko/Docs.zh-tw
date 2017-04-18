---
title: "ManualResetEvent and ManualResetEventSlim | Microsoft Docs"
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
  - "threading [.NET Framework], ManualResetEvent class"
  - "ManualResetEvent class, about ManualResetEvent class"
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# ManualResetEvent and ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=fullName> 類別表示本機等候控制代碼事件，它在收到信號之後必須以手動方式重設。  這個類別代表其基底類別 \(<xref:System.Threading.EventWaitHandle?displayProperty=fullName>\) 的特別案例。  如需手動重設事件的用法和功能，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 <xref:System.Threading.ManualResetEvent> 物件會一直維持收到信號的狀態，直到有人呼叫其 <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=fullName> 方法為止。  任何數目的等候執行緒，或是等候收到信號的事件之執行緒，都可以在收到物件狀態信號時釋放。  <xref:System.Threading.ManualResetEvent> 會指定 `bManualReset` 引數的 `true`，回應 Win32 `CreateEvent` 呼叫。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，當等候時間非常短暫時，以及事件不會處理序界限時，您可以使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>類別來提升效能。  在等候事件收到信號時，<xref:System.Threading.ManualResetEventSlim> 會使用短時間空轉忙碌中。  當等候時間很短暫時，空轉所耗用的資源，會遠比使用等候控制代碼來等候事件少得多。  但是，如果過了特定一段時間還是沒收到事件的信號，<xref:System.Threading.ManualResetEventSlim> 就會改為和一般情況一樣等候事件的控制代碼。  
  
## 請參閱  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)   
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)   
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)