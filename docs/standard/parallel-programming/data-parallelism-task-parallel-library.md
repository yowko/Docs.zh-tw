---
title: 資料平行處理原則 (工作平行程式庫)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bf162a3ef9f66e7c7d74c96f13c055857818a2b
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37070950"
---
# <a name="data-parallelism-task-parallel-library"></a>資料平行處理原則 (工作平行程式庫)
「資料平行處理原則」是指在來源集合或陣列中的元素上，同時 (也就是平行) 執行相同作業的情節。 在資料平行作業中，會將來源集合分割，讓多個執行緒可以同時在不同區段上操作。  
  
 工作平行程式庫 (TPL) 會透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 類別支援資料平行處理原則。 這個類別針對 [for](~/docs/csharp/language-reference/keywords/for.md) 和 [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) 迴圈 (在 Visual Basic 中為 `For` 和 `For Each`)，提供以方法為基礎的平行實作。 針對 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 迴圈撰寫迴圈邏輯的方式，和撰寫循序迴圈很像。 您不必建立執行緒或佇列工作項目。 在基本迴圈中，您不必採用鎖定。 TPL 會為您處理所有低階工作。 如需有關 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 之用途的深入資訊，請下載這份文件：[平行程式設計模式：了解及套用 .NET Framework 4 中的平行模式](http://www.microsoft.com/download/details.aspx?id=19222) \(英文\)。 下列程式碼範例顯示簡單的 `foreach` 迴圈及其平行對等項目。  
  
> [!NOTE]
>  本文件使用 Lambda 運算式來定義 TPL 中的委派。 如果您不熟悉 C# 或 Visual Basic 中的 Lambda 運算式，請參閱 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 當平行迴圈執行時，TPL 會分割資料來源，讓迴圈可以同時在多個部分上操作。 在幕後，工作排程器會依據系統資源和工作負載來分割工作。 如果工作負載變得不平衡，在可能的情況下，排程器會在多個執行緒與處理器之間轉散發工作。  
  
> [!NOTE]
>  您也可以提供您自己的自訂 Partitioner 或排程器。 如需詳細資訊，請參閱 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) 和[工作排程器](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)。  
  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法都有數個多載，可讓您停止或中斷迴圈執行、監視其他執行緒上的迴圈狀態、維護執行緒區域狀態、完成執行緒區域物件、控制並行程度等等。 啟用這個功能的 Helper 類型包括 <xref:System.Threading.Tasks.ParallelLoopState>、<xref:System.Threading.Tasks.ParallelOptions>、<xref:System.Threading.Tasks.ParallelLoopResult>、<xref:System.Threading.CancellationToken> 和 <xref:System.Threading.CancellationTokenSource>。  
  
 如需詳細資訊，請參閱[平行程式設計模式：了解及套用使用 .NET Framework 4 的平行模式](https://www.microsoft.com/download/details.aspx?id=19222)。  
  
 PLINQ 可支援使用宣告式 (或類似查詢) 語法的資料平行處理原則。 如需詳細資訊，請參閱 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[操作說明：撰寫簡單的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|說明如何透過任何陣列或可建立索引的 <xref:System.Collections.Generic.IEnumerable%601> 來源集合，撰寫 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈。|  
|[操作說明：撰寫簡單的 Parallel.ForEach 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|說明如何透過任何 <xref:System.Collections.Generic.IEnumerable%601> 來源集合，撰寫 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈。|  
|[如何：停止或中斷 Parallel.For 迴圈](https://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|描述如何停止或中斷平行迴圈，讓所有執行緒都能收到動作的通知。|  
|[操作說明：撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|說明如何撰寫 <xref:System.Threading.Tasks.Parallel.For%2A> 迴圈 (其中每個執行緒各維護一個任何其他執行緒都看不到的私用變數)，以及當迴圈完成時，如何同步處理所有執行緒的結果。|  
|[如何：撰寫含有 Partition-Local 變數的 Parallel.ForEach 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|說明如何撰寫 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈 (其中每個執行緒各維護一個任何其他執行緒都看不到的私用變數)，以及當迴圈完成時，如何同步處理所有執行緒的結果。|  
|[操作說明：取消 Parallel.For 或 ForEach 迴圈](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|說明如何使用 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 來取消平行迴圈|  
|[操作說明：加速小型迴圈主體](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|說明當迴圈主體非常小時，用來加速執行的一種方法。|  
|[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|提供工作平行程式庫的概觀。|  
|[平行程式設計](../../../docs/standard/parallel-programming/index.md)|介紹如何以 .NET Framework 進行平行程式設計。|  
  
## <a name="see-also"></a>請參閱  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)
