---
title: 作法：處理 PLINQ 查詢中的例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 416ed968d9fe2b7149c90fb6d1fa37547db735dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962502"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>作法：處理 PLINQ 查詢中的例外狀況
此主題中的第一個範例顯示如何處理當執行 PLINQ 查詢時可從它擲回的 <xref:System.AggregateException?displayProperty=nameWithType>。 第二個範例顯示如何將 try-catch 區塊放在委派內，且盡可能地接近將擲回例外狀況的位置。 如此一來，您可以在發生例外狀況時立即攔截它們，並可能繼續執行查詢。 當系統允許例外狀況反昇至聯結的執行緒時，查詢可能就可以在引發例外狀況之後，繼續處理某些項目。  
  
 在某些 PLINQ 回復為循序執行且發生例外狀況的情況中，例外狀況可能會直接傳播，而不會包裝在 <xref:System.AggregateException> 中。 此外，<xref:System.Threading.ThreadAbortException> 一律會直接傳播。  
  
> [!NOTE]
> 啟用 [Just My Code] 時，Visual Studio 會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般]  下的 [Just My Code] 核取方塊即可。  
>   
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 如需加速的詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 此範例會示範如何在執行查詢的程式碼周圍放置 try-catch 區塊，以攔截任何擲回的 <xref:System.AggregateException?displayProperty=nameWithType>。  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 在此範例中，擲回例外狀況之後查詢無法繼續。 應用程式程式碼攔截到例外狀況時，PLINQ 已經停止所有執行緒上的查詢。  
  
## <a name="example"></a>範例  
 下列範例會示範如何將 try-catch 區塊放在委派中，以使其可攔截例外狀況並繼續執行查詢。  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 若要編譯並執行這些範例，請將它們複製到 [PLINQ 資料範] 範例中，並從 Main 呼叫方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 除非您知道如何處理，否則請勿攔截例外狀況，這樣您才不會損毀您的程式狀態。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq.ParallelEnumerable>
- [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
