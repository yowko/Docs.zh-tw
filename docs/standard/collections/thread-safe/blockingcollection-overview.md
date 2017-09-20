---
title: "BlockingCollection 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10e59c246914c17c4a0803de52cf891b2e0d3a3f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---
# <a name="blockingcollection-overview"></a>BlockingCollection 概觀
<xref:System.Collections.Concurrent.BlockingCollection%601> 是提供下列功能的安全執行緒集合類別︰  
  
-   生產者-消費者模式的實作。  
  
-   同時從多個執行緒新增和擷取項目。  
  
-   最佳最大容量。  
  
-   集合是空的或已滿時封鎖的插入和移除作業。  
  
-   不會封鎖或最多封鎖一段指定時間的插入和移除 "try" 作業。  
  
-   封裝任何可實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 的集合類別  
  
-   具有取消語彙基元的取消作業。  
  
-   `foreach` 的列舉有兩種 (在 Visual Basic 中為 `For Each`)：  
  
    1.  唯讀列舉。  
  
    2.  移除所列舉項目的列舉。  
  
## <a name="bounding-and-blocking-support"></a>界限和封鎖支援  
 <xref:System.Collections.Concurrent.BlockingCollection%601> 支援界限和封鎖。 界限表示您可以設定集合的最大容量。 界限在某些情況下十分重要，原因是它可讓您控制記憶體中集合的大小上限，並且防止產生執行緒移到使用執行緒的太前面。  
  
 多個執行緒或工作可以同時將項目新增至集合，如果集合達到其指定的最大容量，則會在移除項目之前封鎖產生執行緒。 多位消費者可以同時移除項目，如果集合變成空的，則會在生產者新增項目之前封鎖使用執行緒。 產生執行緒可以呼叫 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>，表示無法再新增項目。 消費者會監視 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 屬性，以得知集合何時變成空的，以及何時無法再新增項目。 下列範例示範界限容量為 100 的簡單 BlockingCollection。 只要符合某個外部條件，生產者工作就會將項目新增至集合，然後呼叫 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>。 在 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 屬性為 true 之前，消費者工作會擷取項目。  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 如需完整範例，請參閱[如何：從 BlockingCollection 個別新增和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)。  
  
## <a name="timed-blocking-operations"></a>計時封鎖作業  
 在界限集合的計時封鎖 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 作業上，方法會嘗試新增或擷取項目。 如果項目可用，則會將它置入依傳址所傳遞的變數，而且方法會傳回 true。 如果在指定的逾時期間之後未擷取任何項目，則方法會傳回 false。 執行緒接著可以先執行一些其他有用工作，再重新嘗試存取集合。 如需計時封鎖存取的範例，請參閱[如何：從 BlockingCollection 個別新增和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)中的第二個範例。  
  
## <a name="cancelling-add-and-take-operations"></a>取消新增和擷取作業  
 新增和擷取作業一般會透過迴圈形式執行。 您可以將 <xref:System.Threading.CancellationToken> 傳入 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 或 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法來取消迴圈，然後檢查每個反覆項目上語彙基元之 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性的值。 如果值為 true，則是由您決定透過清除任何資源並結束迴圈來回應取消要求。 下列範例示範採用取消語彙基元之 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 的多載，以及使用它的程式碼︰  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 如需如何新增取消支援的範例，請參閱[如何：從 BlockingCollection 個別新增和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)中的第二個範例。  
  
## <a name="specifying-the-collection-type"></a>指定集合類型  
 在您建立 <xref:System.Collections.Concurrent.BlockingCollection%601> 時，不僅可以指定界限容量，還可以指定要使用的集合類型。 例如，您可以針對先進先出 (FIFO) 行為指定 <xref:System.Collections.Concurrent.ConcurrentQueue%601>，或針對後進先出 (LIFO) 行為指定 <xref:System.Collections.Concurrent.ConcurrentStack%601>。 您可以使用任何可實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 介面的集合類別。 <xref:System.Collections.Concurrent.BlockingCollection%601> 的預設集合類型為 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。 下列程式碼範例示範如何建立容量為 1000 並使用 <xref:System.Collections.Concurrent.ConcurrentBag%601> 之字串的 <xref:System.Collections.Concurrent.BlockingCollection%601>：  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 如需詳細資訊，請參閱[操作說明：將界限和封鎖功能加入至集合](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)。  
  
## <a name="ienumerable-support"></a>IEnumerable 支援  
 <xref:System.Collections.Concurrent.BlockingCollection%601> 提供 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法讓消費者可以使用 `foreach` ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中的 `For Each`) 移除項目，直到收集完成為止；這表示集合會是空的，而且不會再新增任何項目。 如需詳細資訊，請參閱[如何：使用 ForEach 來移除 BlockingCollection 中的項目](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)。  
  
## <a name="using-many-blockingcollections-as-one"></a>將多個 BlockingCollection 當成一個使用  
 如果消費者需要同時從多個集合擷取項目，您可以建立 <xref:System.Collections.Concurrent.BlockingCollection%601> 陣列，並使用將新增至或擷取自陣列中任何集合的靜態方法 (例如 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A>)。 如果封鎖其中一個集合，則方法會立即嘗試另一個集合，直到找到可執行作業的集合為止。 如需詳細資訊，請參閱[如何：在管線中使用封鎖回收的陣列](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [集合和資料結構](../../../../docs/standard/collections/index.md)   
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)

