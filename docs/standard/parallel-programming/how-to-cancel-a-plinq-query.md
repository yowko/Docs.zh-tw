---
title: "如何：取消 PLINQ 查詢"
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
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>如何：取消 PLINQ 查詢
下列範例顯示兩種方式可取消 PLINQ 查詢。 第一個範例示範如何取消資料周遊大部分所組成的查詢。 第二個範例示範如何取消包含是高度耗費計算能力的使用者函式的查詢。  
  
> [!NOTE]
>  Visual Studio 啟用 [Just My Code] 時，會擲回例外狀況的行上中斷，並顯示錯誤訊息，指出 「 例外狀況未處理的使用者程式碼 」。 這個錯誤是良性的。 您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。  
>   
>  這個範例是為了示範用法，執行速度可能比不上對應的循序 LINQ to Objects 查詢。 提升速度的詳細資訊，請參閱[PLINQ 中的了解加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ 架構不會回復單一<xref:System.OperationCanceledException>到<xref:System.AggregateException?displayProperty=nameWithType>;<xref:System.OperationCanceledException>必須個別在 catch 區塊中處理。 如果一或多個使用者委派擲回 OperationCanceledException(externalCT) (使用外部<xref:System.Threading.CancellationToken?displayProperty=nameWithType>)，但沒有其他例外狀況，而查詢定義為`AsParallel().WithCancellation(externalCT)`，然後 PLINQ 將會發出單一<xref:System.OperationCanceledException>(externalCT) 而不是<xref:System.AggregateException?displayProperty=nameWithType>. 不過，如果一位使用者委派擲回<xref:System.OperationCanceledException>，而且另一個委派會擲回其他例外狀況類型，則這兩個例外狀況將會回復成<xref:System.AggregateException>。  
  
 取消作業的一般指引如下所示：  
  
1.  如果您執行的使用者委派取消您應該告知 PLINQ 有關外部<xref:System.Threading.CancellationToken>並擲回<xref:System.OperationCanceledException>(externalCT)。  
  
2.  如果發生取消並擲回任何例外狀況，然後您應該處理<xref:System.OperationCanceledException>而不是<xref:System.AggregateException>。  
  
## <a name="example"></a>範例  
 下列範例會示範如何處理取消作業，當您在使用者程式碼中有高度耗費計算能力的函式。  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 當您處理取消使用者程式碼中的時，您不必使用<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>查詢定義中。 不過，我們建議您採用這種因為<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>不有任何影響查詢效能並啟用由查詢運算子和使用者程式碼來處理取消作業。  
  
 為了確保系統的回應能力，我們建議您檢查有無取消情形周圍每毫秒; 一次不過，任何時段內，最多 10 毫秒會視為可接受的。 對您的程式碼的效能，此頻率應該沒有負面影響。  
  
 處置列舉值時，例如當程式碼中斷超出反覆查看查詢結果 （適用於每一個 Visual Basic 中） 的 「 foreach 迴圈 」 將查詢已取消，但會擲回任何例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq.ParallelEnumerable>  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
