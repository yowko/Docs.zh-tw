---
title: 如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a89b3f25fb3d6e85c666e57f24e68c297c8c29a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582733"
---
# <a name="how-to-write-a-parallelforeach-loop-with-thread-local-variables"></a>如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈
下列範例說明如何撰寫使用執行緒區域變數的 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 方法。 當 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈執行時，它會將其來源集合分成多個分割。 每個分割會有自己的「執行緒區域」變數複本 (這裡用「執行緒區域」一詞有點不正確，因為有時會有兩個分割在同一個執行緒上執行)。  
  
 這個範例中的程式碼和參數非常類似於對應的 <xref:System.Threading.Tasks.Parallel.For%2A> 方法。 如需詳細資訊，請參閱：[如何：撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)。  
  
 若要在 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 迴圈中使用執行緒區域變數，您必須呼叫使用兩個類型參數的其中一個方法多載。 第一個類型參數 `TSource` 指定來源項目的類型，而第二個類型參數 `TLocal` 則指定執行緒區域變數的類型。  
  
## <a name="example"></a>範例  
 下列範例呼叫 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 多載，以計算一百萬個項目之陣列的總和。 此多載包含四個參數：  
  
-   `source`，這是資料來源。 它必須實作 <xref:System.Collections.Generic.IEnumerable%601>。 在我們的範例中，資料來源是 `IEnumerable<Int32>` 方法傳回的一百萬個成員 <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> 物件。  
  
-   `localInit`，或初始化執行緒區域變數的函式。 此函式會針對 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 作業執行所在的每個分割呼叫一次。 我們的範例會將執行緒區域變數初始化為零。  
  
-   `body`，這是平行迴圈在迴圈的每個反覆項目上叫用的 <xref:System.Func%604>。 其簽章為 `Func\<TSource, ParallelLoopState, TLocal, TLocal>`。 您會提供委派的程式碼，而迴圈會傳入輸入參數，包括：  
  
    -   <xref:System.Collections.Generic.IEnumerable%601> 的目前項目。  
  
    -   可用於委派的程式碼中以檢查迴圈狀態的 <xref:System.Threading.Tasks.ParallelLoopState> 變數。  
  
    -   執行緒區域變數。  
  
     您的委派會傳回執行緒區域變數，該變數接著會傳遞給該特定分割中所執行之迴圈的下一個反覆項目。 每個迴圈分割會保留此變數的個別執行個體。  
  
     在這個範例中，委派會將每個整數的值加入至執行緒區域變數，以維護該分割中整數值項目的累積總計。  
  
-   `localFinally`，這是當每個分割的迴圈作業完成時，`Action<TLocal>` 所叫用的 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 委派。 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 方法會將此執行緒 (或迴圈分割) 之執行緒區域變數的最後一個值傳遞給 `Action<TLocal>` 委派，而您會提供程式碼，以執行為了合併此分割中的結果與其餘分割中的結果所需的動作。 這個委派可由多個工作同時叫用。 因此，此範例使用 <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> 方法來同步處理對 `total` 變數的存取。 由於委派類型是 <xref:System.Action%601>，因此不會有傳回值。  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>請參閱  
 [資料平行處理原則](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [操作說明：撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [PLINQ 和 TPL 中的 Lambda 運算式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
