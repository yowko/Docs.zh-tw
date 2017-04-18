---
title: "Pausing and Resuming Threads | Microsoft Docs"
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
  - "resuming threads"
  - "threading [.NET Framework], pausing"
  - "pausing threads"
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Pausing and Resuming Threads
最常見之同步處理執行緒活動的方式為封鎖及釋放執行緒、鎖定物件或程式碼區域。  如需有關這些鎖定和封鎖機制的詳細資訊，請參閱[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 您也可以讓執行緒自己進入睡眠。  當執行緒已封鎖或睡眠中，您可以使用 <xref:System.Threading.ThreadInterruptedException> 解除其等候狀態。  
  
## Thread.Sleep 方法  
 呼叫 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> 方法會導致立即封鎖目前執行緒，封鎖時間為傳遞至 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> 的毫秒數，讓剩餘的時間配量讓與另一個執行緒。  執行緒無法呼叫另一個執行緒上的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>。  
  
 呼叫具有 <xref:System.Threading.Timeout.Infinite?displayProperty=fullName> 的 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> 會造成執行緒睡眠，直到被另一個呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 的執行緒中斷，或直到它由 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 終止。  
  
## 中斷執行緒  
 您可藉由呼叫在封鎖的執行緒上的 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 來中斷等候中的執行緒，擲回 <xref:System.Threading.ThreadInterruptedException>，這會中斷執行緒的封鎖呼叫。  執行緒應該攔截 <xref:System.Threading.ThreadInterruptedException>並執行任何適合繼續進行的工作。  如果執行緒忽略例外狀況，則執行階段會攔截例外狀況，並停止執行緒。  
  
> [!NOTE]
>  在呼叫 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 時，如果未封鎖目標執行緒，則到封鎖之前，執行緒不會中斷。  如果執行緒永不封鎖，它可在沒有任何中斷的情況下完成。  
  
 如果等候是 Managed 等候，那麼 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 兩者都會立即喚醒執行緒。  如果等候是 Unmanaged 等候 \(例如平台叫用呼叫 Win32 `WaitForSingleObject` 函式\)，則 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 或 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 都不會控制執行緒，直到它傳回或呼叫 Managed 程式碼。  在 Managed 程式碼中，行為如下所示：  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 會從任何可能的等候中喚醒執行緒，並造成 <xref:System.Threading.ThreadInterruptedException> 在目的執行緒中被擲回。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 類似於 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName>，不過它會造成 <xref:System.Threading.ThreadAbortException> 在執行緒上被擲回。  如需詳細資訊，請參閱[終結執行緒](../../../docs/standard/threading/destroying-threads.md)。  
  
## 暫停和繼續 \(已過時\)  
 對於暫停和繼續執行緒，<xref:System.Threading.Thread> 類別包含兩個方法，<xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName>。  不過，不建議使用這些方法。  
  
> [!IMPORTANT]
>  從 .NET Framework 2.0 版開始， <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> 方法已標記為過時，並且將在未來的版本中移除。  
>   
>  <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> 方法對於應用程式而言通常不實用，而且不應該與同步處理機制混淆。  因為 <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> 不依賴受控制執行緒之間的合作，所以干擾較多，且可導致嚴重的應用程式問題，像是死結 \(例如，如果您暫停執行緒，且該執行緒持有另一個執行緒所需的資源\)。  
  
 有些應用程式需要控制執行緒的優先順序，以提升效能。  若要這樣做，您應該使用 <xref:System.Threading.Thread.Priority%2A?displayProperty=fullName> 屬性而非 <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>。  
  
## 請參閱  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadInterruptedException>   
 <xref:System.Threading.ThreadAbortException>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)