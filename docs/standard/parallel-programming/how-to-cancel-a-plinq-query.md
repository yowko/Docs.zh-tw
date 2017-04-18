---
title: "How to: Cancel a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to cancel"
  - "cancellation, PLINQ"
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Cancel a PLINQ Query
下列範例說明取消 PLINQ 查詢的兩種方式。  第一個範例說明如何取消大多由資料周遊所組成的查詢。  第二個範例說明如何取消使用者函式在計算時需耗費高度資源的查詢。  
  
> [!NOTE]
>  啟用 "Just My Code" 時，Visual Studio 會在擲回例外狀況的程式碼行處中斷，並顯示「使用者程式碼未處理的例外狀況」之類的錯誤訊息。這是良性的錯誤。  您可以按 F5 從中斷的地方繼續，並看到下面範例所示的例外狀況處理行為。  若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消選取 \[工具\]、\[選項\]、\[偵錯\]、\[一般\] 下的 \[Just My Code\] 核取方塊即可。  
>   
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ 架構不會將單一 <xref:System.OperationCanceledException> 彙總成一個 <xref:System.AggregateException?displayProperty=fullName>；<xref:System.OperationCanceledException> 必須在個別的 catch 區塊中進行處理。  如果有一個或多個使用者委派擲回 OperationCanceledException\(externalCT\) \(使用外部 <xref:System.Threading.CancellationToken?displayProperty=fullName>\)，但沒有其他例外狀況，且查詢定義為 `AsParallel().WithCancellation(externalCT)`，則 PLINQ 會發出單一 <xref:System.OperationCanceledException> \(externalCT\)，而不是 <xref:System.AggregateException?displayProperty=fullName>。  但如果有一個使用者委派擲回 <xref:System.OperationCanceledException>，而另一個委派擲回另一個例外狀況類型，則這兩個例外狀況將會彙總成一個 <xref:System.AggregateException>。  
  
 取消的一般指引如下：  
  
1.  如果您執行使用者委派取消，則應向 PLINQ 通知有關外部 <xref:System.Threading.CancellationToken> 的資訊，並擲回 <xref:System.OperationCanceledException> \(externalCT\)。  
  
2.  如果取消執行，且未擲回其他例外狀況，則您應處理 <xref:System.OperationCanceledException>，而不是 <xref:System.AggregateException>。  
  
## 範例  
 下列範例說明如何在使用者程式碼中的函式會高度耗費運算資源時處理取消。  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 當您處理使用者程式碼中的取消時，您無須在查詢定義中使用 <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>。  但我們建議您使用此項目，因為 <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> 並不會影響查詢效能，並且可讓取消由查詢運算子和您的使用者程式碼來處理。  
  
 為確保系統回應，建議您每隔一毫秒左右檢查一次有無取消；但 10 毫秒以內的期間都是可接受的。  此頻率應不會對程式碼的效能造成負面影響。  
  
 當列舉程式遭到處置，例如程式碼從逐一查看查詢結果的 foreach \(Visual Basic 中為 For Each\) 迴圈中斷時，查詢會被取消，但不會擲回例外狀況。  
  
## 請參閱  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)   
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)