---
title: PLINQ 和 TPL 的自訂 Partitioner
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42df511857d367859fc68e2d881dd5b5e2e0bfbc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662569"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>PLINQ 和 TPL 的自訂 Partitioner

若要將資料來源上的作業平行化，其中一個必要步驟就是將來源「分割」  成多個可供多個執行緒同時存取的區段。 PLINQ 和「工作平行程式庫」(TPL) 提供預設的 Partitioner，可在您撰寫平行查詢或 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈時在背景中運作。 針對較進階的案例，您可以插入自己的 Partitioner。

## <a name="kinds-of-partitioning"></a>資料分割的種類

有許多可分割資料來源的方法。 在最有效率的方法中，多個執行緒會合作處理原始來源序列，而不會實際將來源分割成多個子序列。 針對陣列及其他已編製索引的來源 (例如已事先知道長度的 <xref:System.Collections.IList> 集合)，「定界分割」  是最簡單的資料分割種類。 每個執行緒都會收到唯一的開始和結束索引，因此可處理自己的來源範圍，而不會覆寫任何其他執行緒或被任何其他執行緒覆寫。 定界分割唯一涉及的額外負荷就是一開始的範圍建立工作；之後則不需要任何額外的同步處理。 因此，只要平均分配工作負載，便能夠提供良好的效能。 定界分割有個缺點，就是如果一個執行緒提早完成，它並無法協助其他執行緒完成它們的工作。

針對連結清單或其他長度不明的集合，您可以使用「區塊分割」  。 在區塊分割中，平行迴圈或查詢中的每個執行緒或工作都會取用一個區塊中的一些來源元素、處理它們，然後再返回來擷取額外的元素。 Partitioner 可確保散發所有元素且沒有任何重複項目。 區塊可以是任何大小。 例如，[如何：實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)所示範之 Partitioner 會建立只包含一個項目的區塊。 只要區塊不是太大，這類資料分割本質上可提供負載平衡，因為不是以預先決定的方式將元素指派給執行緒。 不過，每次執行緒需要取得另一個區塊時，Partitioner 的確會造成同步處理額外負荷。 在這些情況下所導致的同步處理量多寡與區塊的大小成反比。

一般而言，只有在委派的執行時間為少到適中，且來源有大量元素，以及每個資料分割的總工作量大致相等時，定界分割才會比較快。 因此，通常區塊分割在大多數情況下會比較快。 當來源只有少量元素或委派的執行時間較長時，則區塊分割和定界分割的效能大致相等。

TPL Partitioner 也支援動態數量的資料分割。 這意謂著它們可以機動地建立資料分割，例如當 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈產生新工作時。 此功能可讓 Partitioner 搭配迴圈本身一起進行調整。 動態 Partitioner 也具有負載平衡的本質。 當您建立自訂 Partitioner 時，必須支援從 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈取用動態分割。

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>為 PLINQ 設定負載平衡 Partitioner

<xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> 方法的某些多載可讓您針對陣列或 <xref:System.Collections.IList> 來源建立 Partitioner，並指定它是否應該嘗試平衡執行緒之間的工作負載。 設定讓 Partitioner 進行負載平衡時，會使用區塊分割，在收到元素要求時，會將元素以小區塊交給每個資料分割。 此方法有助於確保所有資料分割都有元素可處理，直到整個迴圈或查詢完成為止。 您可以使用額外的多載來提供任何 <xref:System.Collections.IEnumerable> 來源的負載平衡分割。

一般而言，負載平衡需要資料分割較頻繁地向 Partitioner 要求元素。 相較之下，執行靜態分割的 Partitioner 則可藉由使用定界分割或區塊分割，將元素一次全部指派給每個 Partitioner。 此做法所需的額外負荷比負載平衡少，但如果一個執行緒最後的工作量明顯多於其他執行緒，執行時間就可能較長。 根據預設，當所傳遞的是 IList 或陣列時，PLINQ 一律會使用沒有負載平衡的定界分割。 若要為 PLINQ 啟用負載平衡，請使用 `Partitioner.Create` 方法，如以下範例所示。

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

在任何指定的情況下，判斷是否該使用負載平衡的最佳方式，就是在代表性的負載和電腦設定下，進行實驗並測量作業需要多長的時間才能完成。 例如，在只有幾個核心的多核心電腦上，靜態分割可能會帶來顯著的加速效果，但在有較多核心的電腦上，則可能拖慢速度。

下表列出 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 方法的可用多載。 這些 Partitioner 不僅限於與 PLINQ 或 <xref:System.Threading.Tasks.Task> 搭配使用。 它們也可以與任何自訂的平行建構搭配使用。

|多載|使用負載平衡|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|永遠|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|將布林值引數指定為 true 時|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|將布林值引數指定為 true 時|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|永不|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|永不|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|永不|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|永不|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>為 Parallel.ForEach 設定靜態定界分割

在 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈中，會將迴圈主體提供給方法作為委派。 叫用該委派的成本與虛擬方法呼叫大致相同。 在某些案例中，平行迴圈的主體可能相當小，而足以讓每個迴圈反覆運算上的委派引動過程成本變得很高。 在這類情況下，您可以使用其中一個 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 多載，在來源元素上建立定界分割的 <xref:System.Collections.Generic.IEnumerable%601>。 接著，您可以將這個範圍集合傳遞給主體由一般 `for` 迴圈組成的 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法。 此方法的優點是，每個範圍只會產生一次委派引動過程成本，而不是每個元素產生一次。 下列範例示範基本模式。

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

迴圈中的每個執行緒都會收到自己的 <xref:System.Tuple%602>，其中包含所指定子範圍中的起始和結束索引值。 內部 `for` 迴圈會使用 `fromInclusive` 和 `toExclusive` 值來循環處理整個陣列，或直接處理 <xref:System.Collections.IList>。

其中一個 <xref:System.Collections.Concurrent.Partitioner.Create%2A> 多載可讓您指定資料分割的大小，以及資料分割的數量。 如果每個元素的工作量都很低，以致於甚至每個元素一個虛擬方法呼叫都會明顯影響效能，在這類案例中，便可以使用此多載。

## <a name="custom-partitioners"></a>自訂 Partitioner

在某些案例中，可能值得或甚至必須實作您自己的 Partitioner。 例如，您可能有一個自訂集合類別，而根據您對該類別內部結構的了解，可以用比預設 Partitioner 更有效率的方式來分割該類別。 或者，您可能想要根據處理來源集合中不同位置之元素所需的時間，建立不同大小的定界分割。

若要建立基本自訂 Partitioner，請從 <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> 衍生類別並覆寫虛擬方法，如下表所述。

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|此方法只會被主執行緒呼叫一次，並且會傳回 IList(IEnumerator(TSource))。 迴圈或查詢中的每個背景工作執行緒都可以呼叫清單上的 `GetEnumerator`，以擷取不同資料分割上的 <xref:System.Collections.Generic.IEnumerator%601>。|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|如果您實作 <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>，就會傳回 `true`，否則會傳回 `false`。|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|如果 <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> 為 `true`，則可視需要呼叫此方法，而不呼叫 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|

如果結果必須是可排序的，或您需要以索引方式存取元素，則請從 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> 衍生並覆寫其虛擬方法，如下表所述。

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|此方法只會被主執行緒呼叫一次，並且會傳回 `IList(IEnumerator(TSource))`。 迴圈或查詢中的每個背景工作執行緒都可以呼叫清單上的 `GetEnumerator`，以擷取不同資料分割上的 <xref:System.Collections.Generic.IEnumerator%601>。|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|如果您實作 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>，就會傳回 `true`，否則會傳回 false。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|通常，這只會呼叫 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|如果 <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> 為 `true`，則可視需要呼叫此方法，而不呼叫 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>。|

下表提供額外的詳細資料，說明三種負載平衡 Partitioner 如何實作 <xref:System.Collections.Concurrent.OrderablePartitioner%601> 類別。

|方法/屬性|沒有負載平衡的 IList/陣列|有負載平衡的 IList/陣列|IEnumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|使用定界分割|使用已針對所指定 partitionCount 之清單進行最佳化的區塊分割|藉由建立靜態數量的資料分割來使用區塊分割。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|擲回不支援例外狀況|使用已針對清單和動態分割進行最佳化的區塊分割|藉由建立動態數量的資料分割來使用區塊分割。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|傳回 `true`。|傳回 `true`。|傳回 `true`。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|傳回 `true`。|傳回 `false`。|傳回 `false`。|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|傳回 `true`。|傳回 `true`。|傳回 `true`。|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|傳回 `false`。|傳回 `true`。|傳回 `true`。|

### <a name="dynamic-partitions"></a>動態分割

如果您想要在 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法中使用 Partitioner，您必須能夠傳回動態數量的資料分割。 這意謂著 Partitioner 可以在迴圈執行期間，隨時視需要為新資料分割提供列舉值。 基本上，每次迴圈新增平行工作時，都會為該工作要求新的資料分割。 如果您要求資料必須可排序，則請從 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> 衍生，如此才能為每個資料分割中的每個項目指派唯一索引。

如需詳細資訊和範例，請參閱[如何：實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)。

### <a name="contract-for-partitioners"></a>Partitioner 的合約

實作自訂 Partitioner 時，請依循下列指導方針來協助確保能夠與 PLINQ 和 TPL 中的 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 正確互動：

- 如果使用等於或小於零的 `partitionsCount` 引數來呼叫 <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>，將會擲回 <xref:System.ArgumentOutOfRangeException>。 雖然 PLINQ 和 TPL 永遠不會傳入等於 0 的 `partitionCount`，但建議您杜絕這個可能性。

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> 和 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> 應該一律傳回 `partitionsCount` 數量的資料分割。 如果 Partitioner 用盡資料而無法建立符合所要求數量的資料分割，則方法應該針對剩餘的每個資料分割傳回空的列舉值。 否則，PLINQ 和 TPL 都會擲回 <xref:System.InvalidOperationException>。

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>、<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>、<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A> 及 <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> 應該一律不傳回 `null` (在 Visual Basic 中為 `Nothing`)。 如果會傳回該值，PLINQ/TPL 將會擲回 <xref:System.InvalidOperationException>。

- 方法如果會傳回資料分割，應該一律傳回能夠以完整且唯一方式列舉資料來源的資料分割。 除非 Partitioner 的設計上所需，否則資料來源中不應該有任何重複項目或是略過的項目。 如果不允許使用此規則，則輸出順序可能會相當凌亂。

- 下列布林值 getter 必須一律精確地傳回下列值，如此輸出順序才不會凌亂：

  - `KeysOrderedInEachPartition`：每個分割都會傳回具有遞增索引鍵索引的項目。

  - `KeysOrderedAcrossPartitions`：在所有傳回的分割中，分割 *i* 中之索引鍵索引會高於分割 *i*-1 中的索引鍵索引。

  - `KeysNormalized`：所有索引鍵索引都會從零開始，以單純方式遞增而沒有間隔。

- 所有索引都必須是唯一的。 不可以有重複的索引。 如果不允許使用此規則，則輸出順序可能會相當凌亂。

- 所有索引都不可為負值。 如果未遵守此規則，則 PLINQ/TPL 可能會擲回例外狀況。

## <a name="see-also"></a>另請參閱

- [平行程式設計](../../../docs/standard/parallel-programming/index.md)
- [如何：實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [如何：為靜態分割實作 Partitioner](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
