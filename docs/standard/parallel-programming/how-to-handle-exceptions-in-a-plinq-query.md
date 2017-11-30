---
title: "如何：處理 PLINQ 查詢中的例外狀況"
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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>如何：處理 PLINQ 查詢中的例外狀況
此主題中的第一個範例顯示如何處理<xref:System.AggregateException?displayProperty=nameWithType>，可能會擲回從 PLINQ 查詢時，它會執行。 第二個範例顯示如何將 try-catch 區塊內的委派，會擲回例外狀況盡量靠近。 如此一來，您可以攔截這些一旦發生，且會繼續執行查詢。 當系統允許例外狀況反昇至聯結的執行緒時，查詢可能就可以在引發例外狀況之後，繼續處理某些項目。  
  
 在某些情況下時 PLINQ 退而循序執行，且發生例外狀況，例外狀況可能會直接傳播，並不包裝在<xref:System.AggregateException>。 此外， <xref:System.Threading.ThreadAbortException>s 一律會直接傳播。  
  
> [!NOTE]
>  Visual Studio 啟用 [Just My Code] 時，會擲回例外狀況的行上中斷，並顯示錯誤訊息，指出 「 例外狀況未處理的使用者程式碼 」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。  
>   
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 此範例示範如何將執行的查詢，來攔截任何程式碼周圍的 try catch 區塊<xref:System.AggregateException?displayProperty=nameWithType>，它就會擲回。  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 在此範例中，查詢無法繼續之後擲回例外狀況。 應用程式程式碼攔截例外狀況時，PLINQ 已在所有執行緒上停止查詢。  
  
## <a name="example"></a>範例  
 下列範例會示範如何將 try-catch 區塊放在委派以使其可攔截例外狀況並繼續執行查詢。  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   若要編譯及執行這些範例中，將其複製到 PLINQ 資料範例範例並從 Main 呼叫方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 除非您知道如何處理它，讓您執行不會損毀您的程式狀態，請不要攔截例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.ParallelEnumerable>  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
