---
title: "Walkthrough: Creating a Dataflow Pipeline | Microsoft Docs"
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
  - "dataflow pipelines, creating with TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, creating dataflow pipeline"
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Walkthrough: Creating a Dataflow Pipeline
雖然您可以使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=fullName> 方法從來源區塊接收訊息，但是也可以將訊息區連接起來，形成「*資料流程管線*」\(Dataflow Pipeline\)。  資料流程管線是一系列的元件，或稱為「*資料流程區塊*」\(Dataflow Block\)，各個元件分別執行一項特定工作，以便共同完成整體目標。  資料流程管線中的每個資料流程區塊會在收到來自其他資料流程區塊的訊息時，開始執行工作。  以汽車製造的裝配線做比喻。  當每輛汽車通過裝配線時，某一站會組裝車架，下一站會安裝引擎，以此類推。  由於裝配線能夠同時組裝多輛車，因此裝配線的生產量會優於一次將一輛車從頭到尾組裝完成的生產量。  
  
> [!TIP]
>  TPL 資料流程程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[管理 NuGet 封裝\]，然後在線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
 本文示範資料流程管線，該管線會從網站下載《The Iliad of Homer》  一書，並將個別字與第一個字的字元反向的字做比對，來搜尋文字。  本文件中資料流程管線是由下列步驟形成：  
  
1.  建立參與管線的資料流程區塊。  
  
2.  將每個資料流程區塊連接到管線中的下一個區塊。  每個區塊都會收到管線中前一個區塊的輸出做為輸入。  
  
3.  對每個資料流程區塊建立接續工作，在前一個區塊完成之後將下一個區塊設定為已完成狀態。  
  
4.  將資料公佈至管線的開頭。  
  
5.  將管線的開頭標示為已完成。  
  
6.  等候管線完成所有工作。  
  
## 必要條件  
 在開始這個逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。  
  
## 建立主控台應用程式  
 在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，建立 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 或 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 主控台應用程式專案。  加入 System.Threading.Tasks.Dataflow.dll 的參考。  
  
 或者，也可以建立檔案並將它命名為 `ReverseWords.cs` \(在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中為 `ReverseWords.vb`\)，然後在 Visual Studio 命令提示字元視窗中執行下列命令來編譯專案。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 將下列程式碼加入至您的專案，建立基本的應用程式。  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## 建立資料流程區塊  
 將下列程式碼加入至 `Main` 方法，建立參與管線的資料流程區塊。  下表摘要說明管線中每個成員的角色。  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|成員|類型|描述|  
|--------|--------|--------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|從網站下載書籍的文字。|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|將書籍的文字分成文字陣列。|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|移除文字陣列中簡短的字，依字母順序排序產生的字，並且移除重複項目。|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|在篩選過的文字陣列集合中，尋找反向排列項目同樣出現在文字陣列中的所有文字。|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|將文字和對應的反向文字顯示到主控台。|  
  
 雖然您可以將這個範例中資料流程管線的多個步驟合併成單一步驟，但是範例的目的在於說明撰寫多個獨立的資料流程工作來執行整體工作的概念。  這個範例會使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 讓管線的每個成員對其輸入資料執行作業，並且將結果傳送到管線中的下一個步驟。  管線的 `findReversedWords` 成員是 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件，因為它會針對每個輸入產生多個獨立的輸出。  管線的尾端 `printReversedWords` 是 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，因為它會對其輸入執行動作，但不會產生結果。  
  
## 構成管線  
 加入下列程式碼，將管線中的每個區塊連接到下一個區塊。  
  
 當您呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法將來源資料流程區塊連接到目標資料流程區塊時，來源資料流程區塊會在有可用資料時，將資料傳播至目標區塊。  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## 建立完成工作  
 加入下列程式碼，讓每個資料流程區塊在處理所有資料之後執行最後一個動作。  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 若要在管線中傳播完成，每一項完成工作都要將下一個資料流程區塊設定為已完成狀態。  例如，當管線的開頭設定為已完成狀態時，它會處理所有剩餘的緩衝訊息，然後執行其完成工作，將管線中的第二個成員設定為已完成狀態。  管線中的第二個成員接著就會處理所有剩餘的緩衝訊息，並執行其完成工作，將管線中的第三個成員設定為已完成狀態。  這個流程會繼續進行，直到管線中的所有成員完成為止。  這個範例會使用 `delegate` 關鍵字 \(在 `Function` 中為 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) 定義接續工作。  
  
## 將資料公佈至管線  
 加入下列程式碼，將《The Iliad of Homer》這本書的 URL 公佈至資料流程管線的開頭。  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 這個範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=fullName> 以同步方式將資料傳送至管線的開頭。  如果您必須以非同步方式將資料傳送至資料流程節點，則使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=fullName> 方法。  
  
## 完成管線活動  
 加入下列程式碼，將管線的開頭標示為已完成。  管線的開頭會在處理所有緩衝的訊息後，執行其接續工作。  這個接續工作會透過管線傳播已完成狀態。  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 這個範例會藉由資料流程管線傳送要處理的 URL。  如果您透過管線傳送多個輸入，請在送出所有輸入之後呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=fullName> 方法。  如果您的應用程式並未明確定義資料何時失效，或是應用程式不需要等候管線完成，則可以省略這個步驟。  
  
## 等候管線完成  
 加入下列程式碼等候管線完成。  由於這個範例使用接續工作透過管線傳播完成，因此整個作業會在管線的尾端完成時完成。  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 您可以從任何一個執行緒或同時從多個執行緒等候資料流程完成。  
  
## 完整範例  
 下列範例將示範本逐步解說的完整程式碼。  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## 後續步驟  
 這個範例會藉由資料流程管線傳送要處理的 URL。  如果您透過管線傳送多個輸入值，則可以在應用程式中引入某種形式的平行處理原則，這種形式類似組件汽車工廠內零件移動的流程。  當管線中的第一個成員將其結果傳送給第二個成員時，可以在第二個成員處理第一個結果時平行處理另一個項目。  
  
 使用資料流程管線達成的平行處理原則稱為「*粗略平行處理原則*」\(Coarse\-grained Parallelism\)，因為它通常包含數量較少的大型工作。  您也可以在資料流程管線中使用「*精細平行處理原則*」\(Fine\-grained Parallelism\) 處理一些較小且執行時間較短的工作。  在這個範例中，管線的 `findReversedWords` 成員會使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 方法平行處理工作清單中的多個項目。  在粗略管線中使用精細平行處理原則可以改善整體生產量。  
  
 您也可以將來源資料流程區塊連接到目標區塊，藉此建立「*資料流程網路*」\(Dataflow Network\)。  <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法的多載版本採用 <xref:System.Predicate%601> 物件定義目標區塊是否依據其值接受每個訊息。  大部分做為來源的資料流程區塊類型都會依照連接的順序，對所有連接的目標區塊提供訊息，直到其中一個區塊接受該訊息為止。  使用這個篩選機制就可以建立連接資料流程區塊的系統，透過不同的路徑導引不同的資料。  如需使用篩選建立資料流程網路的範例，請參閱[Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)