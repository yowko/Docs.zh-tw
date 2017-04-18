---
title: "EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent | Microsoft Docs"
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
  - "wait handles"
  - "threading [.NET Framework], EventWaitHandle class"
  - "event wait handles [.NET Framework]"
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
事件等候控制代碼可允許執行緒同步處理活動，其透過的方式是向彼此發出信號，並互相等候對方的信號。  這些同步處理事件是以 Win32 等候控制代碼為根據，且可以分為兩種類型：當收到信號時會自動重設的事件，以及以手動方式重設的事件。  
  
 事件等候控制代碼在與 <xref:System.Threading.Monitor> 類別相同的許多同步處理案例中，會相當實用。  事件等候控制代碼通常要比 <xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> 和 <xref:System.Threading.Monitor.Pulse%2A?displayProperty=fullName> 方法更容易使用，且對於信號也提供了更大的控制權。  具名的事件等候控制代碼也可用來同步處理跨應用程式定義域和處理序的活動，而監視器則是在應用程式定義域的本機。  
  
## 在本節中  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> 類別可表示自動或手動重設事件，且可以是本機事件或具名系統事件。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，且表示可自動重設的本機事件。  
  
 [ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> 類別衍生自 <xref:System.Threading.EventWaitHandle>，且表示必須手動重設的本機事件。  <xref:System.Threading.ManualResetEventSlim> 屬於輕量類別，在相同處理序內可以較快速用於事件的版本。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> 類別提供簡化的方式利用使用等候控制代碼的程式碼，實作分岔\/聯結平行處理原則模式。  
  
## 相關章節  
 [Wait Handles](../Topic/Wait%20Handles.md)  
 <xref:System.Threading.WaitHandle> 類別是 <xref:System.Threading.EventWaitHandle>、<xref:System.Threading.Semaphore> 和 <xref:System.Threading.Mutex> 類別的基底類別。  它包含了在處理所有型別的等候控制代碼時很有用處的靜態方法，例如 <xref:System.Threading.WaitHandle.SignalAndWait%2A> 和 <xref:System.Threading.WaitHandle.WaitAll%2A>。  
  
## 請參閱  
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)