---
title: 認識 PLINQ 中的加速
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26128e5d707d3f331dc2b691f5a5f798bdf84c25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322988"
---
# <a name="understanding-speedup-in-plinq"></a>認識 PLINQ 中的加速
PLINQ 的主要目的是要藉由在多核心電腦上平行執行查詢委派，來加快 LINQ to Objects 查詢的執行速度。 當來源集合中每個元素的處理各自獨立，個別委派之間沒有涉及任何共用狀態時，PLINQ 能夠發揮最佳執行效能。 這類作業在 LINQ to Objects 和 PLINQ 中相當常見，通常稱為「令人愉快的平行」，因為它們很容易出借本身供多個執行緒上的排程使用。 不過，並非所有查詢都全部由令人愉快的平行作業所組成；在大多數情況下，查詢會涉及一些無法平行處理或是會拖慢平行執行速度的運算子。 而且，即使查詢是完全令人愉快的平行查詢，PLINQ 仍然必須分割資料來源並在執行緒上排定工作，通常還會在查詢完成時合併結果。 所有這些作業都會計入平行處理的計算成本中；這些添加平行處理的成本稱為「額外負荷」。 若要在 PLINQ 查詢中達到最佳效能，目標就是要將令人愉快的平行部分提升到最高，並將需要額外負荷的部分降到最低。 本文提供資訊來協助您撰寫儘可能發揮最高效率又仍然能產生正確結果的 PLINQ 查詢。  
  
## <a name="factors-that-impact-plinq-query-performance"></a>影響 PLINQ 查詢效能的因素  
 下列各節列出一些影響平行查詢效能的最重要因素。 這些是一般陳述，本身並不足以預測所有情況下的查詢效能。 如往常一般，請務必在電腦上使用一系列代表性設定和負載來測量特定查詢的實際效能。  
  
1. 整體工作的計算成本。  
  
     若要達到加速的效果，PLINQ 查詢必須有足夠的令人愉快平行工作來抵銷額外負荷。 此工作可以用每個委派的計算成本乘以來源集合中的元素數目來表示。 假設某個作業可以平行處理，則其計算成本越高，加速的機會也越大。 例如，如果某個函式所需的執行時間為 1 毫秒，則循序查詢 1000 個元素將需要 1 秒的時間來執行該作業，但如果在四核心電腦上執行平行查詢，則可能只需要 250 毫秒。 這樣就會產生 750 毫秒的加速效果。 如果該函式針對每個元素需要 1 秒的執行時間，則加速效果會是 750 秒。 如果委派的成本相當高，則 PLINQ 可能只要利用來源集合中的一些項目，就可以提供明顯的加速效果。 相反地，含有瑣碎委派的小型來源集合通常不是 PLINQ 的理想適用對象。  
  
     在下列範例中，假設 queryA 的 Select 函式涉及很多工作，則 queryA 就可能是 PLINQ 的理想適用對象。 queryB 可能不是理想的適用對象，因為 Select 陳述式中並沒有足夠的工作，而平行處理的額外負荷將會抵銷大部分或全部的加速效果。  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2. 系統上的邏輯核心數目 (平行處理程度)。  
  
     此點是上一節的明顯必然結果，令人愉快的平行查詢在有較多核心的電腦上執行速度較快，因為可以在更多並行執行緒之間分配工作。 整體加速效果的大小取決於整體查詢工作的可平行處理百分比。 不過，請不要認為所有查詢在八核心電腦上的執行速度會是四核心電腦的兩倍。 調整查詢以獲得最佳效能時，請務必在各種不同核心數的電腦上測量實際的結果。 此點與第 1 點相關：必須要有較大型的資料集，才能利用較多的計算資源。  
  
3. 作業的數量和種類。  
  
     PLINQ 針對必須維持來源序列中元素順序的情況，提供 AsOrdered 運算子。 排序有相關的成本，但此成本通常不是太大。 GroupBy 和 Join 作業同樣也會造成額外負荷。 在允許以任何順序處理來源集合中的元素，並在一備妥這些元素就立即傳遞給下一個運算子的情況下，PLINQ 能夠發揮最佳執行效能。 如需詳細資訊，請參閱 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。  
  
4. 查詢執行的形式。  
  
     如果您藉由呼叫 ToArray 或 ToList 來儲存查詢的結果，就必須將來自所有平行執行緒的結果合併成單一資料結構。 這會涉及無法避免的計算成本。 同樣地，如果您藉由使用 foreach (在 Visual Basic 中為 For Each) 迴圈來逐一查看結果，就必須將來自背景工作執行緒的結果序列化至列舉值執行緒。 但如果您只是想要根據來自每個執行緒的結果執行某個動作，則可以使用 ForAll 方法在多個執行緒上執行此工作。  
  
5. 合併作業的類型。  
  
     您可以將 PLINQ 設定成緩衝處理其輸出，然後在產生整個結果集後再以區塊方式產生它或全部一次產生，或是在產生結果時串流處理個別的結果。 前者的結果是縮短整體執行時間，後者的結果則是縮短產生元素之間的延遲時間。  雖然合併選項並不一定對整體查詢效能造成重大影響，但可影響察覺到的效能，因為它們可以控制使用者必須等待多久才能看到結果。 如需詳細資訊，請參閱 [PLINQ 中的合併選項](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。  
  
6. 資料分割的種類。  
  
     在某些情況下，在可編製索引之來源集合上執行的 PLINQ 查詢可能會導致工作負載不平衡。 當發生這種情況時，您或許能夠藉由建立自訂 Partitioner 來提升查詢效能。 如需詳細資訊，請參閱 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)。  
  
## <a name="when-plinq-chooses-sequential-mode"></a>當 PLINQ 選擇循序模式時  
 PLINQ 會一律嘗試至少以和查詢循序執行時一樣快的速度來執行查詢。 雖然 PLINQ 並不會考慮使用者委派的計算成本有多高，或是輸入來源有多大，但確實會尋找特定的查詢「型態」。 具體而言，它會尋找通常造成查詢在平行執行模式下執行速度變慢的查詢運算子或運算子組合。 當 PLINQ 找到該型態時，預設會回復成循序模式。  
  
 不過，在測量特定查詢的效能之後，您可能會判斷出實際上以平行模式執行的速度較快。 在這類情況下，您可以透過 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> 方法使用 <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType>旗標，來指示 PLINQ 平行處理查詢。 如需詳細資訊，請參閱[如何：在 PLINQ 中指定執行模式](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)。  
  
 以下清單描述 PLINQ 預設將以循序模式執行的查詢型態：  
  
-   在已移除或已重新排列原始索引的排序或篩選運算子之後包含 Select、已編製索引的 Where、已編製索引的 SelectMany 或 ElementAt 子句的查詢。  
  
-   包含 Take、TakeWhile、Skip、SkipWhile 運算子且來源序列中的索引不是按原始順序排列的查詢。  
  
-   包含 Zip 或 SequenceEquals 的查詢，除非其中一個資料來源具有原始排序的索引，而且另一個資料來源也可以索引 (也就是陣列或 IList(T))。  
  
-   包含 Concat 的查詢 (但套用至可編製索引的資料來源時除外)  
  
-   包含 Reverse 的查詢 (但套用至可編製索引的資料來源時除外)  
  
## <a name="see-also"></a>另請參閱

- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
