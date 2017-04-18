---
title: "Custom Partitioners for PLINQ and TPL | Microsoft Docs"
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
  - "tasks, partitioners"
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Custom Partitioners for PLINQ and TPL
若要將對資料來源執行的作業平行化，其中一個必要步驟是將來源「*分割*」\(Partition\) 成多個可供多個執行緒並行存取的區段。  PLINQ 和工作平行程式庫 \(TPL\) 提供預設 Partitioner，這些 Partitioner 會在您寫入平行查詢或 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈時透明執行。  對於更進階的情節，您可以插入自己的 Partitioner。  
  
## 分割的種類  
 分割資料來源的方式有許多種。  最有效的方式是讓多個執行緒合作處理原始來源序列，而不是將來源實際分割成多個子序列。  對於長度已知的陣列和其他索引來源 \(例如 <xref:System.Collections.IList> 集合\)，「*定界分割*」\(Range Partitioning\) 是最簡單的分割方式。  每個執行緒都會收到唯一的起始和結束索引，所以它可以處理自己的來源範圍，而不會覆寫其他執行緒或是遭其他執行緒覆寫。  定界分割唯一的額外負荷，就是一開始的範圍建立工作，不過之後就不需要額外執行同步處理。  因此，只要能平均分割工作負載，這種方式就能夠提供良好的效能。  定界分割的缺點是即使某個執行緒提前完成，也無法協助其他執行緒完成工作。  
  
 對於長度未知的鏈結串列或集合，您可以使用「*區塊分割*」\(Chunk Partitioning\)。  在區塊分割中，平行迴圈或查詢中的每個執行緒或工作都會耗用區塊中的一些來源項目、進行處理，然後再回來擷取其他項目。  Partitioner 會確保所有項目都受到處理而且沒有重複。  區塊可以是任何大小。  例如，[How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)中示範的 Partitioner 會建立只包含一個項目的區塊。  只要區塊不大，這種分割就可以平衡負載，這是因為指派給執行緒的項目不是預先決定的。  但是，每次執行緒需要取得其他區塊時，Partitioner 都需要再花精神執行同步處理。  這些情節中需要的同步處理量與區塊大小成反比。  
  
 一般來說，定界分割只有在委派執行時間不長、來源具有大量項目，且每個分割的總工作量大致相同時較快。  因此，在大多數情節中區塊分割比較快。  在來源具有小量項目或委派執行時間較長時，區塊分割和定界分割的效能幾乎相等。  
  
 TPL Partitioner 也支援動態數量的資料分割。  這表示它們可以動態建立資料分割，例如當 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈繁衍新的工作時。  這個功能可以讓 Partitioner 隨著迴圈本身一起縮放。  動態 Partitioner 也能夠平衡負載。  當您建立自訂 Partitioner 時，必須支援讓 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈可以使用動態分割。  
  
### 針對 PLINQ 設定負載平衡 Partitioner  
 <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=fullName> 方法的某些多載可讓您建立陣列或 <xref:System.Collections.IList> 來源的 Partitioner，並且指定這個 Partitioner 是否應嘗試平衡執行緒之間的工作負載。  當設定 Partitioner 進行平衡負載，就會使用區塊分割，並在要求項目時將項目以小區塊的形式交給每個資料分割。  這個方法可協助確保所有資料分割都有項目可以處理，直到整個迴圈或查詢完成為止。  還有一個多載可以用來將任何 <xref:System.Collections.IEnumerable> 來源進行負載平衡分割。  
  
 一般來說，負載平衡需要資料分割經常向 Partitioner 要求項目。  相較之下，執行靜態分割的 Partitioner 可以使用定界分割或區塊分割一次將項目指派給每個 Partitioner。  這樣需要的工作會比負載平衡少，但是如果某個執行緒最後獲得的工作比其他執行緒多許多，則執行時間可能會較長。  根據預設，當 PLINQ 接受 IList 或陣列時，一律會使用沒有負載平衡的定界分割。  若要針對 PLINQ 啟用負載平衡，請使用 `Partitioner.Create` 方法，如下列範例所示。  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 判斷在任何指定情節中是否使用負載平衡的最佳方法，是以具代表性的負載和電腦組態，實驗並測量完成作業的時間。  例如，靜態分割可能讓只具有少數核心的多核心電腦大幅增加速度，但是可能讓具有眾多核心的電腦速度下降。  
  
 下表列出 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 方法的可用多載。  這些 Partitioner 不只能用於 PLINQ 或 <xref:System.Threading.Tasks.Task>。  它們也能用於任何自訂平行建構。  
  
|多載|使用負載平衡|  
|--------|------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|永遠|  
|[Create\<TSource\>\(TSource\<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|當布林值引數指定為 true 時|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|當布林值引數指定為 true 時|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|永不|  
  
### 針對 Parallel.ForEach 設定靜態定界 Partitioner  
 在 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈中，迴圈的主體是以委派形式提供給方法。  叫用該委派的成本大致與虛擬方法呼叫相同。  在某些情節中，平行迴圈的主體可能相當小，使得在每個迴圈反覆項目叫用委派的成本變得相當大。  在這種情況下，您可以使用其中一個 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 多載以建立來源項目定界分割的 <xref:System.Collections.Generic.IEnumerable%601>。  然後，您可以將這個定界集合傳遞至 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法，該方法的主體包含一般 `for` 迴圈。  這個方法的優點是叫用委派的成本只會對每個定界產生一次，而不是對每個項目即產生一次。  下列範例會示範基本模式的用法。  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 迴圈中的每個執行緒都會收到自己的 <xref:System.Tuple%602>，其中包含指定之子定界的起始和結束索引值。  內部 `for` 迴圈會使用 `fromInclusive` 和 `toExclusive` 值對陣列或 <xref:System.Collections.IList> 直接進行迴圈。  
  
 其中一個 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 多載可讓您指定資料分割大小和資料分割數量。  這個多載可以用在每個工作的項目少到即使只對每個項目呼叫一個虛擬方法，都會對效能有顯著影響的情節中。  
  
## 自訂 Partitioner  
 在某些情節中，實作自己的 Partitioner 可能有價值或者甚至是必要的。  例如，您可能具有自訂集合類別，根據您對於這個類別的內部結構的知識，您可以比使用預設 Partitioner 更有效率地進行分割。  或者，您可以根據對於處理來源集合中不同位置的項目需時多久的知識，建立各種大小的定界資料分割。  
  
 若要建立基本的自訂 Partitioner，請從 <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=fullName> 衍生類別，並且覆寫虛擬方法，如下表所述。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|這個方法會由主執行緒呼叫一次，並且傳回 IList\(IEnumerator\(TSource\)\)。  迴圈或查詢中的每個背景工作執行緒都可以呼叫清單上的 `GetEnumerator`，以擷取個別資料分割的 <xref:System.Collections.Generic.IEnumerator%601>。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|如果實作 <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> 則傳回 `true`，否則傳回 `false`。|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|如果 <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> 為 `true`，可以選擇性呼叫這個方法，而非 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|  
  
 如果結果必須可以排序，或者您需要以索引方式存取項目，請從 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> 衍生，並且覆寫其虛擬方法，如下表所述。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|這個方法會由主執行緒呼叫一次，並且傳回 `IList(IEnumerator(TSource))`。  迴圈或查詢中的每個背景工作執行緒都可以呼叫清單上的 `GetEnumerator`，以擷取個別資料分割的 <xref:System.Collections.Generic.IEnumerator%601>。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|如果實作 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A> 則傳回 `true`，否則傳回 false。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|通常這只會呼叫 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|如果 <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> 為 `true`，可以選擇性呼叫這個方法，而非 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|  
  
 下表提供關於三種負載平衡 Partitioner 如何實作 <xref:System.Collections.Concurrent.OrderablePartitioner%601> 類別的額外詳細資料。  
  
|方法\/屬性|沒有負載平衡的 IList \/ 陣列|有負載平衡的 IList \/ 陣列|IEnumerable|  
|------------|-------------------------|------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|使用定界分割|使用針對指定之 partitionCount 清單最佳化的區塊分割|建立靜態數量的資料分割來使用區塊分割。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=fullName>|擲回不支援例外狀況|使用針對清單和動態資料分割最佳化的區塊分割|建立動態數量的資料分割來使用區塊分割。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|傳回 `true`|傳回 `true`|傳回 `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|傳回 `true`|傳回 `false`|傳回 `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|傳回 `true`|傳回 `true`|傳回 `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|傳回 `false`|傳回 `true`|傳回 `true`|  
  
### 動態資料分割  
 如果您想要在 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法中使用 Partitioner，您必須能夠傳回動態數量的資料分割。  這表示 Partitioner 可以在迴圈執行時，隨時應需要提供列舉程式來產生新的資料分割。  基本上，迴圈每次加入新的平行工作時，就會要求以新的資料分割執行該工作。  如果您需要資料可以排序，請從 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> 衍生，讓每個資料分割中的每個項目都指派有唯一的索引。  
  
 如需詳細資訊和範例，請參閱 [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)。  
  
### Partitioner 的合約  
 當您實作自訂 Partitioner 時，請遵循下列方針以協助確保在 TPL 中與 PLINQ 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 正確互動：  
  
-   針對使用零或以下的 `partitionsCount` 做為引數來呼叫的 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>，擲回 <xref:System.ArgumentOutOfRangeException>。  雖然 PLINQ 和 TPL 不會傳入等於 0 的 `partitionCount`，我們還是建議您防範這種可能性。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> 和 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> 應該永遠傳回 `partitionsCount` 數量的資料分割。  如果 Partitioner 用盡資料而無法建立如要求的數量那麼多的資料分割，則方法應該針對每個多出的資料分割傳回空白的列舉程式。  否則，PLINQ 和 TPL 都會擲回 <xref:System.InvalidOperationException>。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>、<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>、<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> 和 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> 永遠不應傳回 `null` \(在 Visual Basic 中為 `Nothing` \)。  如果真的傳回該值，則 PLINQ \/ TPL 會擲回 <xref:System.InvalidOperationException>。  
  
-   傳回分割的方法永遠應該傳回可以完整且唯一列舉資料來源的資料分割。  除非 Partitioner 的設計特別要求，否則資料來源中不應該有重複或者略過的項目。  如果未遵循這個規則，則輸出順序可能會受干擾。  
  
-   下列布林值 getter 永遠必須準確傳回下列值，讓輸出順序不受到干擾：  
  
    -   `KeysOrderedInEachPartition`：每個資料分割都會傳回主索引鍵增加的項目。  
  
    -   `KeysOrderedAcrossPartitions`：在所有傳回的資料分割中，資料分割  *i*  中的主索引鍵高於資料分割*i* \-1 中的主索引鍵。  
  
    -   `KeysNormalized`：所有主索引鍵從零開始增加沒有間距。  
  
-   所有的索引都必須是唯一的。  不能有重複的索引。  如果未遵循這個規則，則輸出順序可能會受干擾。  
  
-   所有的索引都不能是負值。  如果未遵循這個規則，則 PLINQ\/TPL 可能會擲回例外狀況。  
  
## 請參閱  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)   
 [How to: Implement a Partitioner for Static Partitioning](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)