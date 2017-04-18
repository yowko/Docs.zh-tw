---
title: "BlockingCollection 概觀 | Microsoft Docs"
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
  - "BlockingCollection，概觀"
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# BlockingCollection 概觀
<xref:System.Collections.Concurrent.BlockingCollection%601> 是安全執行緒集合，可提供下列功能：  
  
-   實作生產者與消費者模式。  
  
-   並行加入和擷取多個執行緒的項目。  
  
-   可選擇最大容量。  
  
-   當集合為空白或已滿時，封鎖插入和移除作業。  
  
-   不封鎖或封鎖特定時段的插入和移除 "try" 作業。  
  
-   封裝任何實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 的集合型別。  
  
-   啟用取消語彙基元的取消作業。  
  
-   含有 `foreach` \(在 Visual Basic 中為 `For Each`\) 的兩種列舉：  
  
    1.  唯讀列舉。  
  
    2.  可在列舉項目時移除項目的列舉。  
  
## 界限和封鎖支援  
 <xref:System.Collections.Concurrent.BlockingCollection%601> 支援界限和封鎖。  界限表示您可以設定集合的最大容量。  在特定案例中界限是很重要的，因為它可讓您控制記憶體中集合的最大大小，並防止生產執行緒移到消費執行緒之前太遠。  
  
 多個執行緒或工作可以並行地將項目加入集合，如果集合達到指定的最大容量，則會封鎖生產執行緒，直到移除項目為止。  多個消費者可以並行地移除項目，如果集合變為空白，則會封鎖消費執行緒，直到生產者加入項目為止。  生產執行緒可以呼叫 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> 以指出不會加入其他項目。  消費者可監視 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 屬性，以了解何時集合為空白，以及不會加入其他項目。  下列範例示範簡單的 BlockingCollection，其界限容量為 100。  生產者工作會在部分特定條件為 true 時，將項目加入集合，然後呼叫 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>。  消費者工作會擷取項目，直到 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 屬性為 true 為止。  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 如需完整的範例，請參閱 [如何：從 BlockingCollection 個別加入和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)。  
  
## 計時的封鎖作業  
 在界限集合的計時封鎖 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 作業中，方法會嘗試加入或擷取項目。  如果項目可用，則會放置在以傳址方式傳遞的變數中，並且此方法會傳回 true。  如果在指定的逾時期間之後沒有擷取項目，此方法會傳回 false。  然後，執行緒可任意執行其他有用的工作，然後嘗試重新存取集合。  如需計時封鎖存取的範例，請參閱 [如何：從 BlockingCollection 個別加入和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)中的第二個範例。  
  
## 取消加入和擷取作業  
 加入和擷取作業通常在迴圈中執行。  您可以取消迴圈，方法是將 <xref:System.Threading.CancellationToken> 傳遞至 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 或 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法，然後在每個反覆項目上檢查語彙基元的 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性值。  如果該值為 true，則您可決定回應取消要求，清除任何資源並結束迴圈。  下列範例顯示接受取消語彙基元的 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 多載，以及使用它的程式碼：  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 如需如何加入取消支援的範例，請參閱 [如何：從 BlockingCollection 個別加入和擷取項目](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)中的第二個範例。  
  
## 指定集合型別  
 當您建立 <xref:System.Collections.Concurrent.BlockingCollection%601> 時，您不僅可以指定界限容量，也可以指定要使用的集合型別。  例如，您可以針對先進先出 \(FIFO\) 行為指定 <xref:System.Collections.Concurrent.ConcurrentQueue%601>，或針對後進先出 \(LIFO\) 行為指定 <xref:System.Collections.Concurrent.ConcurrentStack%601>。  您可以使用任何實作 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 介面的集合類別。  <xref:System.Collections.Concurrent.BlockingCollection%601> 的預設集合型別是 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。  下列程式碼範例中，顯示如何建立字串的 <xref:System.Collections.Concurrent.BlockingCollection%601> \(其容量為 1000，並且使用 <xref:System.Collections.Concurrent.ConcurrentBag%601>\)：  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 如需詳細資訊，請參閱[如何：將界限和封鎖功能加入至集合](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)。  
  
## IEnumerable 支援  
 <xref:System.Collections.Concurrent.BlockingCollection%601> 提供 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法，可讓消費者使用 `foreach` \(在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中為 `For Each`\) 來移除項目，直到集合已完成為止，這表示集合為空白，且不會加入其他項目。  如需詳細資訊，請參閱[如何：使用 ForEach 來移除 BlockingCollection 中的項目](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)。  
  
## 將多個 BlockingCollection 做為一個使用  
 如果消費者需要同時從多個集合擷取項目，則您可以建立 <xref:System.Collections.Concurrent.BlockingCollection%601> 的陣列，並使用靜態方法 \(例如 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A>\)，加入或擷取陣列中的任何集合。  如果封鎖一個集合，則該方法會立即嘗試另一個集合，直到找到一個可以執行作業的集合為止。  如需詳細資訊，請參閱[如何：在管線中使用封鎖集合的陣列](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)。  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [集合和資料結構](../../../../docs/standard/collections/index.md)   
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)