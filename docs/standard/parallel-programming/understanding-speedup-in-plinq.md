---
title: "Understanding Speedup in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, performance tuning"
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Understanding Speedup in PLINQ
PLINQ 的主要目的是透過在多核心電腦上以平行的方式執行查詢委派，加快 LINQ to Objects 查詢的執行速度。  當來源集合中的每個項目都會受到獨立處理，讓個別委派間不會共用狀態時，PLINQ 的執行效果最佳。  這種作業在 LINQ to Objects 和 PLINQ 中很常見，因為它們可以讓人輕鬆在多個執行緒上排定查詢，所以通常被形容為「*令人愉快的平行*」\(Delightfully Parallel\)。  但是，並非所有的查詢都完全採用令人愉快的平行作業。大多時候，查詢中會有一些無法平行化或是會讓平行執行變慢的運算子。  即使查詢全然採用令人愉快的平行型態，PLINQ 仍必須分割資料來源並將工作排定至各執行緒上，而且通常必須在查詢完成時合併結果。  這些作業全都算在平行化作業的計算成本內，這些因平行化作業而多出的成本即稱為「*額外負荷*」\(Overhead\)。  若要讓 PLINQ 查詢達到最佳效能，我們的目標就是要盡量讓具有令人愉快的平行型態的組件數提至最高，並且將需要產生額外負荷的組件數降至最低。  本文提供的資訊可協助您撰寫盡可能有效的 PLINQ 查詢，同時仍維持讓查詢產生正確的結果。  
  
## 影響 PLINQ 查詢效能的因素  
 下列幾點列出了影響平行查詢效能的一些最重要因素。  這些都只是一般陳述，光靠這些陳述並不足以預測所有情況下的查詢效能。  再次提醒，請務必在具有各種代表性組態和負載的電腦上測量特定查詢的實際效能。  
  
1.  整體工作的計算成本。  
  
     若要達到加速目的，PLINQ 查詢必須有足夠令人愉快的平行工作來超越額外負荷。  這些工作可用每個委派的計算成本乘以來源集合中的項目數來表示。  假設某項作業可以平行化，則該作業的計算成本愈高，加速的機會就愈大。  例如，如果某個函式需要 1 毫秒來執行，則對超過 1000 個項目執行循序查詢將需花費 1 秒來執行該作業，但是在四核心電腦上執行平行查詢只需花費 250 毫秒。  這樣即產生 750 毫秒的加速效果。  如果函式對每個項目都需要花費 1 秒來執行，這樣即產生 750 秒的加速效果。  如果委派的成本非常高，則來源集合中只要有少數項目，PLINQ 就能提供極高的加速效果。  相反地，如果來源集合不大而且委派的執行時間不長，即不適合使用 PLINQ。  
  
     在下列範例中， queryA 可能是 PLINQ 的候選，選取函式包含許多工作的假設為 thatits。queryB 可能不是候選，因為在 SELECT 陳述式的足夠的工作，因此額外負荷平行處理會抵銷大部分或所有加速。  
  
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
  
2.  系統上的邏輯核心數 \(平行處理原則程度\)。  
  
     這一點顯然是上一點的延伸，令人愉快的平行查詢在具有更多核心的機器上執行速度比較快，因為工作可以分配至更多的並行執行緒上。  整體的加速效果取決於整體查詢工作中可平行化的百分比。  但是，請不要認為所有查詢在八核心電腦上的執行速度都會是在四核心電腦上執行的兩倍。  微調查詢以達到最佳效能時，請務必要在具有各種核心數量的電腦上測量實際結果。  這一點與第一點相關：資料集要比較大，才能真正發揮較多計算資源所帶來的優勢。  
  
3.  作業的數目和種類。  
  
     PLINQ 提供的 AsOrdered 運算子適合用於必須保持來源序列中項目順序的情況。  排序作業會造成相關的成本，但是這個成本通常不高。  GroupBy 和 Join 作業同樣會造成額外負荷。  當 PLINQ 能夠以任何順序處理來源集合中的項目，並將這些準備好的項目立即傳遞給下一個運算子時，PLINQ 的執行效果最佳。  如需詳細資訊，請參閱[Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。  
  
4.  查詢執行形式。  
  
     如果您是透過呼叫 ToArray 或 ToList 來儲存查詢的結果，則必須將所有平行執行緒的結果合併至單一資料結構中。  這會造成無可避免的計算成本。  同理，如果您使用 foreach \(在 Visual Basic 中為 For Each\) 迴圈來逐一查看結果，則必須將背景工作執行緒的結果序列化至列舉程式執行緒上。  但是，如果只想根據每個執行緒的結果來執行某個動作，您可以使用 ForAll 方法在多個執行緒上執行此工作。  
  
5.  合併選項類型。  
  
     PLINQ 可以設定為先緩衝其輸出，然後以區塊方式產生輸出或者是等整個結果集產生之後一次產生全部輸出，也可以設定為在產生個別結果時立即產生輸出。  前者可以減少整體執行時間，而後者可以減少等候個別項目產生的時間。雖然合併選項不一定會對整體查詢效能造成顯著影響，但是可以影響使用者認為的效能，因為這些選項可控制使用者必須等候多久才能看到結果。  如需詳細資訊，請參閱[Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。  
  
6.  分割種類。  
  
     有時候，對可索引的來源集合執行 PLINQ 查詢可能會產生不平衡的工作負載。  若發生這種情形，您可以建立自訂 Partitioner 來提高查詢效能。  如需詳細資訊，請參閱[Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)。  
  
## 當 PLINQ 選擇循序模式時  
 PLINQ 一直會嘗試以至少和循序查詢一樣快的速度執行查詢。  雖然 PLINQ 不會看使用者委派的成本有多高，或是輸入來源有多大，但是它會看特定查詢「型態」。更明確地說，它會尋找通常會導致查詢在平行模式中執行得更緩慢的查詢運算子或運算子組合。  當 PLINQ 發現這類型態時，它預設就會回到循序模式。  
  
 不過，在測量特定查詢的效能之後，您可能會發現查詢在平行模式中實際上執行得更快。  在這類情況中，您可以透過 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A?displayProperty=fullName> 方法使用 <xref:System.Linq.ParallelExecutionMode> 旗標來指示 PLINQ 將查詢平行化。  如需詳細資訊，請參閱[How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)。  
  
 下列清單說明 PLINQ 預設會以循序模式執行的查詢型態：  
  
-   在已將原始索引移除或重新排列的排序運算子或篩選運算子之後，包含 Select、索引 Where、索引 SelectMany 或 ElementAt 子句的查詢。  
  
-   包含 Take、TakeWhile、Skip、SkipWhile 運算子，而且其來源序列中的索引未依原始順序排列的查詢。  
  
-   包含 Zip 或 SequenceEquals 的查詢，除非其中一個資料來源具有原始排序的索引，而且剩餘的另一個資料來源是可索引的資料來源 \(例如 一個矩陣或是IList\(T\)\)。  
  
-   包含 Concat 的查詢，除非是套用至可索引的資料來源。  
  
-   包含 Reverse 的查詢，除非是套用至可索引的資料來源。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)