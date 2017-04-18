---
title: "How to: Handle Exceptions in a PLINQ Query | Microsoft Docs"
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
  - "PLINQ queries, how to handle exceptions"
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Handle Exceptions in a PLINQ Query
本主題的第一個範例說明如何處理 PLINQ 查詢執行時可能擲回的 <xref:System.AggregateException?displayProperty=fullName>。  第二個範例說明如何盡可能在即將擲回例外狀況之前，在委派內放置 try\-catch 區塊。  透過這種方式，您可以在例外狀況發生時立即攔截例外狀況，並甚至繼續執行查詢。  如果可以將每個例外狀況個別擲回給聯結的執行緒，則引發例外狀況之後，查詢仍可能會繼續處理某些項目。  
  
 有時候，PLINQ 在回到循序執行方式後發生了例外狀況，這時可能會直接傳播例外狀況，而不是將例外狀況包在 <xref:System.AggregateException> 中再傳播。  另外，系統一定會直接傳播 <xref:System.Threading.ThreadAbortException>。  
  
> [!NOTE]
>  啟用 "Just My Code" 時，Visual Studio 會在擲回例外狀況的程式碼行處中斷，並顯示「使用者程式碼未處理的例外狀況」之類的錯誤訊息。 這是良性的錯誤。  您可以按 F5 從中斷的地方繼續，並看到下面範例所示的例外狀況處理行為。  若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消選取 \[工具\]、\[選項\]、\[偵錯\]、\[一般\] 下的 \[Just My Code\] 核取方塊即可。  
>   
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。  如需加速的詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 範例  
 此範例說明如何在執行查詢的程式碼周圍放置 try\-catch 區塊，以攔截擲回的 <xref:System.AggregateException?displayProperty=fullName>。  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 在此範例中，查詢在例外狀況擲回後將無法繼續執行。  在您的應用程式程式碼攔截到例外狀況前，PLINQ 即已停止所有執行緒上的查詢。  
  
## 範例  
 下列範例說明如何在委派中放置 try\-catch 區塊，以攔截例外狀況並繼續執行查詢。  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## 編譯程式碼  
  
-   若要編譯和執行這些範例，請將其複製到「PLINQ Data 範例」範例中，然後從 Main 呼叫方法。  
  
## 穩固程式設計  
 如果您不知道如何處理例外狀況，請勿加以攔截，以免破壞程式的狀態。  
  
## 請參閱  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)