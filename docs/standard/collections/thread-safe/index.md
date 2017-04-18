---
title: "安全執行緒集合 | Microsoft Docs"
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
  - "安全執行緒集合，概觀"
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# 安全執行緒集合
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 引入了 <xref:System.Collections.Concurrent?displayProperty=fullName> 命名空間，其中包括許多同時屬於安全執行緒和可擴充的集合類別。  多個執行緒可以安全且有效率地在這些集合中加入或移除項目，而不需要在使用者程式碼中使用其他同步處理。  如果您要撰寫新的程式碼，每當集合將以並行方式寫入多個執行緒時，請使用並行集合類別。  如果您只要從共用集合讀取，就可以在 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間中使用這些類別。  除非您必須以 .NET Framework 1.1 或舊版的執行階段為目標，否則我們建議您不要使用 1.0 集合類別。  
  
## .NET Framework 1.0 和 2.0 集合中的執行緒同步處理  
 您可以在 <xref:System.Collections?displayProperty=fullName> 命名空間中找到 .NET Framework 1.0 所引入的集合。  這些集合 \(包括常用的 <xref:System.Collections.ArrayList> 和 <xref:System.Collections.Hashtable>\) 會透過 `Synchronized` 屬性提供一些執行緒安全性，以便在集合周圍傳回安全執行緒的包裝函式。  此包裝函式的運作方式是在每次加入或移除作業時鎖定整個集合。  因此，嘗試存取集合的每個執行緒都必須等候以輪流取得單一鎖定。  這項作業無法擴充，而且對於大型集合而言，可能會導致效能大幅降低。  此外，這種設計無法完全避免競爭情形。  如需詳細資訊，請參閱 MSDN 網站上的 [在泛型集合同步處理](http://go.microsoft.com/fwlink/?LinkID=161130)。  
  
 您可以在 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間中找到 .NET Framework 2.0 所引入的集合類別。  這些類別包括 <xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.Dictionary%602> 等等。  與 .NET Framework 1.0 類別相較之下，這些類別會提供改善的型別安全和效能。  不過，.NET Framework 2.0 集合類別不會提供任何執行緒同步處理。當多個執行緒以並行方式加入或移除項目時，使用者程式碼必須提供所有同步處理。  
  
 我們建議使用 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 中的並行集合類別，因為它們不僅提供了 .NET Framework 2.0 集合類別的型別安全，而且它們所提供的執行緒安全性比 [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] 集合更有效率且更完整。  
  
## 細部鎖定和無鎖定機制  
 某些並行集合型別會使用輕量型同步處理機制，例如 <xref:System.Threading.SpinLock>、<xref:System.Threading.SpinWait>、<xref:System.Threading.SemaphoreSlim> 和 <xref:System.Threading.CountdownEvent>，而這些都是 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 新增的機制。  這些同步處理型別通常會先暫時使用「*忙碌空轉*」\(Busy Spinning\)，然後再讓執行緒進入真正的等候狀態。  當等候時間預期非常短暫時，空轉所耗費的運算資源就遠低於等候，因為等候涉及了高度耗費資源的核心轉換。  對於使用空轉的集合類別而言，這種效率表示多個執行緒可以用非常高的速率加入和移除項目。  如需空轉 v.s. 阻塞的詳細資訊，請參閱 [SpinLock](../../../../docs/standard/threading/spinlock.md) 和 [SpinWait](../../../../docs/standard/threading/spinwait.md)。  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601> 類別完全不會使用鎖定。  而是，它們會仰賴 <xref:System.Threading.Interlocked> 作業來達成執行緒安全性。  
  
> [!NOTE]
>  因為並行集合類別支援 <xref:System.Collections.ICollection>，所以它們會提供 <xref:System.Collections.ICollection.IsSynchronized%2A> 和 <xref:System.Collections.ICollection.SyncRoot%2A> 屬性的實作，即使這些屬性無關也一樣。  `IsSynchronized` 一定會傳回 `false` 而且 `SyncRoot` 一律為 `null` \(Visual Basic 中的 `Nothing`\)。  
  
 下表列出 <xref:System.Collections.Concurrent?displayProperty=fullName> 命名空間中的集合型別。  
  
|型別|描述|  
|--------|--------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|針對實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 的任何型別提供界限和封鎖功能。  如需詳細資訊，請參閱[BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|機碼值組之字典的安全執行緒實作。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|FIFO \(先進先出\) 佇列的安全執行緒實作。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|LIFO \(後進先出\) 堆疊的安全執行緒實作。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|未排序項目集合的安全執行緒實作。|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|型別必須實作才能用於 `BlockingCollection` 的介面。|  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|描述 <xref:System.Collections.Concurrent.BlockingCollection%601> 型別所提供的功能。|  
|[如何：在 ConcurrentDictionary 中加入和移除項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|描述如何在 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 中加入和移除項目。|  
|[如何：從 BlockingCollection 個別加入和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|描述如何在封鎖集合中加入和擷取項目，而不使用唯讀列舉程式。|  
|[如何：將界限和封鎖功能加入至集合](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|描述如何使用任何集合類別當做 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 集合的基礎儲存機制。|  
|[如何：使用 ForEach 來移除 BlockingCollection 中的項目](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|描述如何使用 `foreach` \(Visual Basic 中的 `For Each`\) 來移除封鎖集合中的所有項目。|  
|[如何：在管線中使用封鎖集合的陣列](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|描述如何同時使用多個封鎖集合來實作管線。|  
|[如何：使用 ConcurrentBag 建立物件集區](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|示範如何使用並行 Bag，在能夠重複使用物件而非繼續建立新物件的情況下改善效能。|  
  
## 參考資料  
 <xref:System.Collections.Concurrent?displayProperty=fullName>