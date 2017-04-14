---
title: "AutoResetEvent | Microsoft Docs"
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
  - "threading [.NET Framework], AutoResetEvent class"
  - "AutoResetEvent class"
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# AutoResetEvent
<xref:System.Threading.AutoResetEvent> 類別代表區域等候控制代碼事件，該事件會在釋放一個等候執行緒後，於收到信號通知時自動重設。  這個類別代表其基底類別 \(Base Class\) <xref:System.Threading.EventWaitHandle> 的特別案例。  如需自動重設事件的使用方式及其功能的詳細資訊，請參閱 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) 概念文件。  
  
 在釋放一個等候執行緒後，系統會將 <xref:System.Threading.AutoResetEvent> 物件會自動重設為未收到信號通知的狀態。  如果沒有等候中的執行緒，事件物件 \(Event Object\) 會維持收到信號的狀態。  <xref:System.Threading.AutoResetEvent> 會指定 `bManualReset` 引數的 `false`，回應 Win32 `CreateEvent` 呼叫。  
  
 如需使用 <xref:System.Threading.AutoResetEvent> 的範例，請參閱 [Monitor](../Topic/Monitors.md)。  
  
## 請參閱  
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Monitor>   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)