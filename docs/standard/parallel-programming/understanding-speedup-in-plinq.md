---
title: "認識 PLINQ 中的加速"
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
helpviewer_keywords: PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3373cb6a2c535bd7d42eb062e1f9727952f7cfb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-speedup-in-plinq"></a>認識 PLINQ 中的加速
PLINQ 的主要目的是加速執行 LINQ 查詢物件藉由在多核心電腦上平行執行查詢委派。 每個項目的來源集合中的處理序無關，各自有涉及在個別的委派之間共用的狀態時，PLINQ 的執行效果最好。 這類作業在 LINQ to Objects 和 PLINQ 中很常見，和通常稱為 「*delightfully 平行*"因為它們出借本身輕鬆地與多個執行緒上排程。 不過，並非所有的查詢包含完全個 delightfully 平行作業。在大部分情況下，查詢牽涉到某些運算子是無法平行處理，或降低平行執行的速度。 即使是完全 delightfully 平行查詢，使用 PLINQ 必須並仍資料分割的資料來源和上排程工作的執行緒，通常是在查詢完成時的結果合併。 所有這些作業新增計算成本的平行化作業;這些將加入的平行處理的成本會呼叫*負擔*。 若要達到最佳效能 PLINQ 查詢中的，目標是最大化 delightfully 平行的組件的組件，需要額外負荷降到最低。 本文章提供可協助您撰寫時仍會產生正確的結果會盡可能有效率的 PLINQ 查詢的資訊。  
  
## <a name="factors-that-impact-plinq-query-performance"></a>影響 PLINQ 查詢效能的因素  
 下列各節列出一些最重要的因素影響平行查詢效能。 這些是一般陳述式本身並不足夠預測查詢效能，在所有情況下。 如往常，請務必測量利用某個範圍的代表性的組態和負載在電腦上的特定查詢的效能。  
  
1.  計算整體工作的成本。  
  
     若要達到加速，PLINQ 查詢必須足夠 delightfully 平行的工作，來彌補額外負荷。 工作可以表示為乘以來源集合中的項目數的每個委派的運算成本。 假設作業可平行處理，更多計算它的昂貴，大於加速的機會。 例如，如果函式執行的一毫秒，循序查詢超過 1000年項目將會接受一個第二個執行這項操作，而平行查詢具有四個核心的電腦上可能只 250 毫秒。 這會產生 750 毫秒的加速效果。 如果函式需要每個項目執行一秒，通常會是 750 秒。 如果委派是很昂貴，PLINQ 可能會提供顯著的加速效果，與來源集合中只有幾個項目。 相反地，小型的來源集合具有 trivial 委派通常不是 PLINQ 的理想候選項。  
  
     在下列範例中，queryA 可能是工作的適合做為 PLINQ，假設其選取的函式牽涉到大量。 queryB 可能就不適合的候選項，因此沒有足夠的工作，在 Select 陳述式中，平行化作業帶來的額外負荷將位移大部分或所有的加速效果。  
  
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
  
2.  系統 （平行處理原則的程度） 上的邏輯核心數目。  
  
     這點明顯推論上一節，delightfully 平行查詢執行速度在電腦上具有多個核心因為工作可以分配給更多並行執行緒。 整體的加速效果量取決於整體的查詢工作的百分比是可並行。 不過，不會假設所有查詢都會都執行兩次以快速在八個核心的電腦上做為四個核心的電腦。 微調查詢，以獲得最佳效能時, 務必測量在具有不同的數字的核心電腦上的實際結果。 這點與點 #1： 較大的資料集，才能利用大於運算資源。  
  
3.  數目和類型的作業。  
  
     PLINQ 提供 AsOrdered 運算子的情況下，它是為了維持來源序列中項目的順序。 與順序相關聯的成本，但此成本是通常太大。 同樣地，GroupBy 和聯結作業會產生負擔。 當處理以任何順序，來源集合中的項目，並將其傳遞至下一個運算子，他們就可以為允許時，PLINQ 的執行效果最好。 如需詳細資訊，請參閱 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。  
  
4.  查詢執行的表單。  
  
     如果您透過呼叫 ToArray 或 ToList 儲存查詢的結果，所有平行執行緒的結果必須合併成單一的資料結構。 這牽涉到無可避免的運算成本。 同樣地，如果您來使用 （針對每個 Visual Basic 中） 的 「 foreach 迴圈，逐一查看結果，背景工作執行緒的結果必須序列化到列舉程式執行緒。 但是，如果您只想執行某些動作，根據每個執行緒的結果，您可以在多個執行緒上執行這項工作使用 ForAll 方法。  
  
5.  合併選項類型。  
  
     PLINQ 可以緩衝的輸出，並產生區塊 （chunk） 或一次之後整個結果集產生，或資料流的個別結果時，會產生這些設定。 先前的結果是減少整體的執行時間並降低延遲，產生的項目之間的第二個結果。  雖然的合併選項執行不一定都有重大影響整體查詢效能，它們就會影響認知的效能，因為它們可以控制使用者必須等候以查看結果。 如需詳細資訊，請參閱 [PLINQ 中的合併選項](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。  
  
6.  類型的資料分割。  
  
     在某些情況下，透過索引的來源集合 PLINQ 查詢可能會導致不平衡的工作負載。 當發生這種情況時，您可以藉由建立自訂 partitioner 增加查詢效能。 如需詳細資訊，請參閱 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)。  
  
## <a name="when-plinq-chooses-sequential-mode"></a>當 PLINQ 選擇循序模式  
 PLINQ 將一律嘗試執行至少以最快速度會以循序方式執行查詢的查詢。 雖然 PLINQ 看起來如何計算高度耗費資源的使用者委派，或有多大的輸入的來源是，它看起來特定的查詢 「 圖形 」。 具體來說，它會尋找查詢運算子或通常會導致查詢執行速度變慢，在平行模式中的運算子的組合。 發現這類圖形，根據預設 PLINQ 會回復為循序模式。  
  
 不過之後測量特定的查詢效能，您可能決定實際執行速度在平行模式。 在此情況下，您可以使用<xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType>加上旗標透過<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>指示 PLINQ 來平行處理查詢的方法。 如需詳細資訊，請參閱[如何：在 PLINQ 中指定執行模式](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)。  
  
 下列清單描述 PLINQ 依預設會在循序模式中執行的查詢圖形：  
  
-   查詢包含 Select、 編製索引，索引的 SelectMany 或 ElementAt 子句之後已經移除或重新排列原始索引的排序或篩選運算子。  
  
-   查詢中包含 Take、 TakeWhile，略過 SkipWhile 運算子，且來源序列中的索引不在原始的訂單。  
  
-   包含 Zip 或 SequenceEquals 的查詢，除非其中一個資料來源具有原始排序的索引，而且另一個資料來源也可以索引 (也就是陣列或 IList(T))。  
  
-   包含 Concat，除非它套用到索引的資料來源的查詢。  
  
-   包含相反地，除非套用至索引的資料來源的查詢。  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
