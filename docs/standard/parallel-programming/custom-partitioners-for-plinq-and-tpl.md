---
title: "PLINQ 和 TPL 的自訂 Partitioner"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12d234b86b0067178d54d2fdcb5d37ceaee6109d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ 和 TPL 的自訂 Partitioner
若要平行處理資料來源上的作業，其中一個重要步驟是*分割*成可由多個執行緒並行存取的多個區段的來源。 PLINQ 和工作平行程式庫 (TPL) 提供當您撰寫平行查詢，以透明的方式運作的預設 partitioner 或<xref:System.Threading.Tasks.Parallel.ForEach%2A>迴圈。 更進階的情況下，您可以插入您自己的 partitioner。  
  
## <a name="kinds-of-partitioning"></a>類型的資料分割  
 有許多方式來分割資料來源。 最有效率的方法，在多個執行緒會合作以原始來源序列中，程序，而不是實際將來源分割成多個子。 陣列和其他索引來源例如<xref:System.Collections.IList>集合長度會事先知道*定界資料分割*是簡單類型的資料分割。 每個執行緒接收唯一的開始和結束索引，如此可以處理其來源範圍但不覆寫或遭到覆寫其他任何執行緒。 參與定界資料分割的的額外負荷會建立範圍; 的初始工作沒有額外的同步處理之後需要的。 因此，它可以提供良好的效能，只要工作負載會平均分配。 定界資料分割的缺點是，如果一個執行緒提早完成，它無法協助其他執行緒完成其工作。  
  
 針對連結的清單或其長度不知道其他集合，您可以使用*區塊分割*。 在資料分割的區塊，每一個執行緒或工作平行迴圈或查詢中的取用一個區塊中的來源項目的某些數目、 處理，然後恢復擷取其他項目。 發佈的所有項目，並確認沒有重複項目，可確保 partitioner。 區塊 (chunk) 可能是任何規模。 比方說中, 示範的 partitioner [How to： 實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)建立區塊包含只有一個項目。 區塊不會太大，因為此類型的資料分割是原本就負載平衡因為不預先決定的項目至執行緒指派。 不過，partitioner 沒有執行緒取得另一個區塊會需要每次造成同步處理的負荷。 在這些情況下所產生的同步處理的數量是區塊的大小成反比。  
  
 一般情況下，定界資料分割更快時才委派的執行時間很小的仲裁，而且來源具有大量項目，及每個資料分割的總工作大致上相當。 區塊資料分割的是，因此通常在大部分情況下會較快。 在較少的項目或較長的委派的執行時間來源，然後區塊和 range 資料分割的效能是關於等。  
  
 TPL partitioner 也支援動態分割區數目。 這表示它們可以建立資料分割上作業，例如，當<xref:System.Threading.Tasks.Parallel.ForEach%2A>迴圈會產生新的工作。 此功能可讓您調整以及迴圈本身的 partitioner。 動態 partitioner 也是原本就負載平衡。 當您建立的自訂 partitioner 時，您必須支援動態磁碟分割，可供在使用<xref:System.Threading.Tasks.Parallel.ForEach%2A>迴圈。  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>設定負載平衡的 PLINQ Partitioner  
 一些多載<xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType>方法可讓您建立陣列 partitioner 或<xref:System.Collections.IList>來源，並指定是否應嘗試在執行緒之間的工作負載平均分配。 當 partitioner 設定負載平衡時，使用區塊資料分割時，與項目會遞交給小區塊中的每個資料分割要求。 這種方式有助於確保所有資料分割，直到整個迴圈處理的項目或查詢已完成。 其他多載可用來提供負載平衡的任何分割<xref:System.Collections.IEnumerable>來源。  
  
 一般情況下，負載平衡所需要的資料分割來要求元素相對經常從 partitioner。 相反地，沒有靜態分割 partitioner 可以指派項目給每個 partitioner 一次使用範圍或區塊資料分割。 這需要較少的額外負荷比負載平衡，但是可能需要較長的時間執行一個執行緒最後會有比其他更多工作。 預設為 IList 或陣列，傳遞時 PLINQ 一律使用 range 資料分割沒有負載平衡。 若要啟用 PLINQ 的負載平衡，請使用`Partitioner.Create`方法，如下列範例所示。  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 若要判斷是否要使用負載平衡在任何給定的情況下進行實驗而測量作業下代表性的載入和電腦設定完成所需的時間，最好。 例如，靜態資料分割可能會有幾個核心、 多核心電腦上提供顯著的加速效果，但可能會導致速度變慢，有相當多核心電腦上。  
  
 下表列出可用的多載的<xref:System.Collections.Concurrent.Partitioner.Create%2A>方法。 這些 partitioner 不限於只適用於 PLINQ 或<xref:System.Threading.Tasks.Task>。 它們也可以使用與任何自訂的平行建構。  
  
|多載|使用負載平衡|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|永遠|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|布林值的引數指定為 true 時|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|布林值的引數指定為 true 時|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|永不|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|永不|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>設定 Parallel.ForEach 的靜態範圍的 Partitioner  
 在<xref:System.Threading.Tasks.Parallel.For%2A>迴圈，迴圈的主體提供給方法的委派。 叫用該委派的成本是關於相同的虛擬方法呼叫。 在某些情況下，平行迴圈的主體可能小的每個迴圈反覆項目上的委派引動過程成本變得重要。 在這種情況下，您可以使用其中一個<xref:System.Collections.Concurrent.Partitioner.Create%2A>多載來建立<xref:System.Collections.Generic.IEnumerable%601>界定資料分割，在來源項目。 然後，您可以傳遞給此集合的範圍到<xref:System.Threading.Tasks.Parallel.ForEach%2A>其主體包含一般方法`for`迴圈。 這個方法的好處是每個範圍，而不是一次每個項目委派引動過程成本一次所造成。 下列範例示範基本模式。  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 在迴圈中的每個執行緒會收到自己<xref:System.Tuple%602>，其中包含的開始和結束的指定子範圍中的索引值。 內部`for`迴圈使用`fromInclusive`和`toExclusive`迴圈陣列值或<xref:System.Collections.IList>直接。  
  
 其中一個<xref:System.Collections.Concurrent.Partitioner.Create%2A>多載可讓您指定的資料分割和資料分割數目的大小。 這個多載可用於案例其中每個項目工作是很低，每個項目甚至一種虛擬方法呼叫對明顯影響效能。  
  
## <a name="custom-partitioners"></a>自訂 Partitioner  
 在某些情況下，它可能是值得或甚至必須實作自己的 partitioner。 例如，您可能比 partitioner 可以以您的內部結構類別的知識為基礎的預設值更有效率，您可以分割的自訂集合類別。 或者，您可能想要建立界定資料分割的基礎知識的花多少時間將來源集合中的不同位置的程序項目不同的大小。  
  
 若要建立基本的自訂 partitioner，衍生自<xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType>並覆寫虛擬方法下, 表中所述。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|這個方法會由主執行緒呼叫一次，並傳回 IList(IEnumerator(TSource))。 迴圈或查詢中的每個工作者執行緒可以呼叫`GetEnumerator`上擷取清單<xref:System.Collections.Generic.IEnumerator%601>透過不同的磁碟分割。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|傳回`true`如果您實作<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>，否則`false`。|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|如果<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>是`true`，而不是可選擇性地呼叫這個方法<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|  
  
 如果結果必須是可排序，或您為項目需要索引的存取，然後衍生自<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>並覆寫其虛擬方法下, 表中所述。  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|這個方法會由主執行緒呼叫一次，並傳回`IList(IEnumerator(TSource))`。 迴圈或查詢中的每個工作者執行緒可以呼叫`GetEnumerator`上擷取清單<xref:System.Collections.Generic.IEnumerator%601>透過不同的磁碟分割。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|傳回`true`如果您實作<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; 否則為 false。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|一般而言，這只會呼叫<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|如果<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>是`true`，而不是可選擇性地呼叫這個方法<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|  
  
 下表提供有關的其他詳細資料的三種負載平衡 partitioner 實作<xref:System.Collections.Concurrent.OrderablePartitioner%601>類別。  
  
|方法/屬性|IList / 陣列沒有負載平衡|IList / 陣列負載平衡|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|使用 range 資料分割|使用最佳化，列出指定 partitionCount 分割區塊|會使用區塊資料分割所建立的資料分割的靜態數目。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|不支援會擲回例外狀況|會使用區塊資料分割最佳化清單和動態的資料分割|會使用區塊資料分割建立動態的資料分割數目。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|傳回 `true`。|傳回 `true`。|傳回 `true`。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|傳回 `true`。|傳回 `false`。|傳回 `false`。|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|傳回 `true`。|傳回 `true`。|傳回 `true`。|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|傳回 `false`。|傳回 `true`。|傳回 `true`。|  
  
### <a name="dynamic-partitions"></a>動態分割  
 如果您想要用於 partitioner<xref:System.Threading.Tasks.Parallel.ForEach%2A>方法，您必須能夠傳回的資料分割的動態數目。 這表示，partitioner 迴圈執行期間，隨時可以提供新資料分割指定的列舉值。 基本上，每次迴圈會將新的平行工作，它會要求該工作的新資料分割。 如果您需要為可排序資料，然後衍生自<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>，讓每個資料分割中的每個項目指派唯一的索引。  
  
 如需詳細資訊和範例，請參閱[How to： 實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)。  
  
### <a name="contract-for-partitioners"></a>Partitioner 合約  
 當您實作的自訂 partitioner 時，請遵循下列指導方針來協助確保正確互動 PLINQ 和<xref:System.Threading.Tasks.Parallel.ForEach%2A>TPL 中：  
  
-   如果<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>是呼叫的引數的零或更少的`partitionsCount`，會擲回<xref:System.ArgumentOutOfRangeException>。 雖然 PLINQ 和 TPL 會永遠不會傳入`partitionCount`等於 0，不過建議您防範可能性。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>和<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>應該會一律傳回`partitionsCount`數字的資料分割。 如果 partitioner 用盡資料，而且無法建立要求最多的資料分割，此方法應傳回其餘的分割區的每個空白的列舉值。 PLINQ 和 TPL 否則將會擲回<xref:System.InvalidOperationException>。  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A><xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>， <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>，和<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>永遠不應該傳回`null`(`Nothing`在 Visual Basic 中)。 如果沒有的話，PLINQ / TPL 會擲回<xref:System.InvalidOperationException>。  
  
-   傳回的資料分割的方法應該一律會傳回可完全且唯一列舉資料來源的資料分割。 除非特別需要的 partitioner 設計時，則應該不是重複的資料來源或略過的項目。 如果未遵照這項規則，則可能會變碼的輸出順序。  
  
-   下列布林 getter，讓不變碼的輸出順序，必須一定可以正確地傳回下列值：  
  
    -   `KeysOrderedInEachPartition`： 每個資料分割傳回隨著增加的索引鍵索引的項目。  
  
    -   `KeysOrderedAcrossPartitions`： 對於會傳回索引鍵索引資料分割中的所有資料分割*我*高於索引鍵索引資料分割中*我*-1。  
  
    -   `KeysNormalized`： 沒有間距，從零開始單純增加所有的索引鍵索引。  
  
-   所有索引必須都是唯一的。 不可能重複的索引。 如果未遵照這項規則，則可能會變碼的輸出順序。  
  
-   所有索引不可都為負值。 如果未遵照這項規則，則 PLINQ/TPL 可能擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 [操作說明：實作動態磁碟分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [操作說明：為靜態分割實作 Partitioner](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
