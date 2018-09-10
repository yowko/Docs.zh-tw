---
title: 如何：撰寫簡單的 Parallel.For 迴圈
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29da081784c06d8cd467f0566f9d4db92a130b53
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087270"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>如何：撰寫簡單的 Parallel.For 迴圈
本主題包含兩個範例，示範 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 方法。 第一個範例使用 <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> 方法多載，而第二個會使用 <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType> 多載，這是 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 方法的兩個最簡單的多載。 當您不需要取消迴圈、中斷迴圈的反覆項目，或維護任何執行緒區域狀態時，可以使用這兩個 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 方法的多載。  
  
> [!NOTE]
>  本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
 第一個範例會計算單一目錄中的檔案大小。 第二個會計算兩個矩陣的乘積。  
  
## <a name="example"></a>範例  
 這個範例是簡單的命令列公用程式，它會計算目錄中的檔案大小總計。 它預期會有單一目錄路徑做為引數，並報告該目錄中的檔案大小總計與數量。 在確認目錄存在之後，它會使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 方法來列舉目錄中的檔案，並判斷其檔案大小。 每個檔案大小會加到 `totalSize` 變數。 請注意，加法是透過呼叫 <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> 來執行，因此加法在執行時是不可部分完成的作業。 否則，多個工作可能會嘗試同時更新 `totalSize` 變數。  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 方法來計算兩個矩陣的乘積。 它也顯示如何使用 <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> 類別比較平行迴圈與非平行迴圈的效能。 請注意，由於它可能會產生大量的輸出，因此範例允許輸出重新導向至檔案。  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 平行處理任何程式碼，包括迴圈時，一個重要的目標是要盡可能利用處理器，而不過度平行處理，導致平行處理的負荷否定任何效能優勢。 在這個特定範例中，只有外部迴圈會進行平行處理，因為內部迴圈中沒有執行太多工作。 少量的工作和非預期的快取效果的組合可能導致巢狀平行迴圈中的效能降低。 因此，只平行處理外部迴圈是讓大多數系統上的並行處理好處最大化的最佳方式。  
  
## <a name="the-delegate"></a>委派  
 這個 <xref:System.Threading.Tasks.Parallel.For%2A> 多載的第三個參數是 C# 中類型`Action<int>` 或 Visual Basic 中類型 `Action(Of Integer)` 委派。 `Action` 委派不論有零個、一個或 16 個類型參數，都一律會傳回 void。 在 Visual Basic 中，`Action` 的行為使用 `Sub` 來定義。 這個範例會使用 Lambda 運算式來建立委派，但您也可以用其他方式建立委派。 如需詳細資訊，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
## <a name="the-iteration-value"></a>反覆項目值  
 委派會採用單一輸入參數，其值是目前反覆項目。 此反覆項目值由執行階段所提供，且其起始值為目前執行緒上正在處理之來源區段 (分割區) 上的第一個項目的索引。  
  
 如果您需要對並行處理等級有更多控制，請使用採用 <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType> 輸入參數的其中一個多載，例如：<xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>。  
  
## <a name="return-value-and-exception-handling"></a>傳回值和例外狀況處理  
 當所有執行緒都完成時，<xref:System.Threading.Tasks.Parallel.For%2A> 會傳回 <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> 物件。 這個傳回值適用於您以手動方式停止或中斷迴圈的反覆項目時，因為 <xref:System.Threading.Tasks.ParallelLoopResult>會儲存資訊，以便最後一個反覆項目執行至完成。 如果其中一個執行緒上發生一個或多個例外狀況，將會擲回 <xref:System.AggregateException?displayProperty=nameWithType>。  
  
 在這個範例的程式碼中，不會使用 <xref:System.Threading.Tasks.Parallel.For%2A> 的傳回值。  
  
## <a name="analysis-and-performance"></a>分析和效能  
 您可以使用 [效能精靈] 來檢視電腦上的 CPU 使用量。 做一個試驗，請增加矩陣中的資料行和資料列數目。 矩陣愈大，計算的平行和循序版本之間的效能差異也愈大。 當矩陣是小型矩陣時，循序版本會因為設定平行迴圈的負荷而執行較快。  
  
 對於共用資源的同步呼叫，像是主控台或檔案系統，將會大幅降低平行迴圈的效能。 測量效能時，請試著避免在迴圈內使用例如 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 的呼叫。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   將這段程式碼複製並貼到 Visual Studio 2010 專案。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Parallel.For%2A>  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
- [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [平行程式設計](../../../docs/standard/parallel-programming/index.md)
