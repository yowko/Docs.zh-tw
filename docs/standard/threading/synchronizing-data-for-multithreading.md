---
title: "Synchronizing Data for Multithreading | Microsoft Docs"
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
  - "synchronization, threads"
  - "threading [.NET Framework], synchronizing threads"
  - "managed threading"
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Synchronizing Data for Multithreading
當多個執行緒可以呼叫單一物件的屬性 \(Property\) 和方法時，同步處理那些呼叫是很重要的。  否則，一執行緒可能中斷另一執行緒正在執行的動作，而物件可能會成為無效狀態。  類別的成員若能免於這種中斷，這個類別就稱為安全執行緒。  
  
 Common Language Infrastructure 提供幾個策略，以同步處理對個體與靜態成員的存取：  
  
-   同步程式碼區域 \-  您可以使用 <xref:System.Threading.Monitor> 類別或類別的編譯器支援，只針對需要的程式碼區塊進行同步處理，以增進效能。  
  
-   手動同步處理 \-   您可使用 .NET Framework 類別庫所提供的同步處理物件。  請參閱[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)，其中包括 <xref:System.Threading.Monitor> 類別的討論內容。  
  
-   同步內容 \-  您可以使用 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>，對 <xref:System.ContextBoundObject> 物件啟用簡單、自動化的同步處理。  
  
-   <xref:System.Collections.Concurrent?displayProperty=fullName> 命名空間中的集合類別。  這些類別會提供內建同步化加入和移除作業。  如需詳細資訊，請參閱[安全執行緒集合](../../../docs/standard/collections/thread-safe/index.md)。  
  
 Common Language Runtime 提供將類別分為幾種的執行緒模型，可根據需求以各種不同方式同步處理。  下表說明指定同步分類提供欄位和方法的同步支援。  
  
|分類|全域欄位|靜態欄位|靜態方法|執行個體欄位|執行個體方法|特定程式碼區塊|  
|--------|----------|----------|----------|------------|------------|-------------|  
|無同步處理|否|否|否|否|否|否|  
|同步內容|否|否|否|是|是|否|  
|同步程式碼區域|否|否|標記的才有|否|標記的才有|標記的才有|  
|手動同步|Manual|Manual|Manual|Manual|Manual|Manual|  
  
## 無同步處理  
 這是物件的預設值。  任何執行緒可隨時存取任何方法或欄位。  一次只能有一個執行緒存取這些物件。  
  
## 手動同步  
 .NET Framework 類別庫提供了許多可用來同步處理執行緒的類別。  請參閱[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
## 同步程式碼區域  
 您可以使用 <xref:System.Threading.Monitor> 類別或編譯器關鍵字來同步處理程式碼區塊、執行個體方法和靜態方法。  同步靜態欄位則無支援。  
  
 Visual Basic 和 C\# 支援以特定的語言關鍵字標示程式碼區塊、在 C\# 內使用 `lock` 陳述式或是在 Visual Basic 內使用 `SyncLock` 陳述式。  當程式碼由執行緒執行時，會嘗試取得鎖定。  如果已由另一個執行緒取得鎖定，則執行緒區塊會等候到可以使用鎖定為止。  當執行緒結束程式碼的同步化區塊時，鎖定會被釋放，不管執行緒如何結束該區塊。  
  
> [!NOTE]
>  `lock` 和 `SyncLock` 陳述式是使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> 和 <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> 所實作，好讓 <xref:System.Threading.Monitor> 的其他方法可以在同步化區域內與其搭配使用。  
  
 您也可以使用 **MethodImplAttribute** 和 **MethodImplOptions.Synchronized** 來裝飾方法，這樣產生的作用與使用 **Monitor** 或其中一個編譯器關鍵字來鎖定整個方法主體的作用相同。  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 可用來中斷執行緒繼續進行區塊化作業，例如等候存取程式碼的同步區域。  **Thread.Interrupt** 也可用來中斷執行緒繼續進行作業，例如 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>。  
  
> [!IMPORTANT]
>  請勿為了保護 `static` 方法 \(Visual Basic 內的 `Shared` 方法\) 而鎖定型別，也就是 C\# 內的 `typeof(MyType)`、Visual Basic 內的 `GetType(MyType)` 或 C\+\+ 內的 `MyType::typeid`。  請改用私用靜態物件。  同樣地，不要在 C\# 中使用 `this` \(Visual Basic 中為 `Me`\) 來鎖定執行個體方法，  請改用私用物件。  類別或執行個體可能會被您自己以外的程式碼鎖定，這樣可能會造成死結或效能問題。  
  
### 編譯器支援  
 Visual Basic 和 C\# 都支援使用 <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> 和 <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> 來鎖定物件的語言關鍵字。  Visual Basic 支援 [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) 陳述式，C\# 支援 [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) 陳述式。  
  
 在這兩種情況下，如果程式碼區塊中擲回例外狀況，則 **lock** 會取得鎖定，或是 **SyncLock** 會自動釋出。  C\# 和 Visual Basic 編譯器會發出 **try**\/**finally** 區塊，其中 **Monitor.Enter** 在 try 的開頭，而 **Monitor.Exit** 在 **finally** 區塊中。  如果 **lock** 或 **SyncLock** 區塊中擲回例外狀況，則會執行 **finally** 處理常式，讓您進行任何清除工作。  
  
## 同步內容  
 您可在任何 **ContextBoundObject** 上使用 **SynchronizationAttribute** 來同步處理所有執行個體方法和欄位。  同一內容領域中的所有物件都共用相同的鎖定。  多個執行緒可存取方法和欄位，不過只能以一次一個執行緒的方式進行。  
  
## 請參閱  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)   
 [SyncLock Statement](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md)   
 [lock 陳述式](../Topic/lock%20Statement%20\(C%23%20Reference\).md)