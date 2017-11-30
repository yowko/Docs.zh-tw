---
title: "使用 PLINQ 時可能出現的錯誤"
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
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a>使用 PLINQ 時可能出現的錯誤
在許多情況下，PLINQ 可透過物件查詢的循序 LINQ 提供顯著的效能改進。 不過，平行查詢執行的工作會帶來可能會造成問題，在循序程式碼，並不常用，或發生的不完全的複雜性。 本主題列出一些作法，以避免當您撰寫 PLINQ 查詢。  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>不要認為平行一定比較快  
 有時平行化作業會導致 PLINQ 查詢執行速度比其 LINQ 物件相等。 基本的經驗法則是，有幾個來源項目和快速的使用者委派的查詢通常不太可能很多。 不過，因為許多因素所相關的效能，建議您在決定是否要使用 PLINQ 之前測量實際結果。 如需詳細資訊，請參閱[認識 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>避免寫入共用的記憶體位置  
 循序程式碼經常會讀取或寫入靜態變數或類別欄位。 不過，每當有多個執行緒同時存取這類變數時，就很可能產生競爭情形。 即便您可以使用鎖定來同步處理變數的存取，同步處理的成本也會減損效能。 因此，我們建議您避免，或至少限制，以盡可能 PLINQ 查詢中的共用狀態存取。  
  
## <a name="avoid-over-parallelization"></a>避免過度平行處理  
 使用`AsParallel`運算子，造成資料分割來源集合和同步處理的背景工作執行緒的額外負荷成本。 電腦上的處理器數目則會進一步限制平行處理的好處。 多個計算繫結執行緒若只在一個處理器上執行，系統並不會獲得任何加速效果。 因此，您必須非常小心不過度平行處理查詢。  
  
 最常見的案例中哪些過度平行處理可以是便會發生中巢狀查詢，如下列程式碼片段所示。  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 在此情況下，最好平行處理僅外部資料來源 （客戶），除非套用一或多個下列條件：  
  
-   內部資料來源 (cust。訂單） 是否已知為很長。  
  
-   您正在對每個順序執行昂貴的計算  (範例所示作業並不昂貴)。  
  
-   已知目標系統有足夠的處理器，可處理因為在 `cust.Orders` 上平行處理查詢而會產生的執行緒數目。  
  
 在上述所有情況下，若要判斷最佳的查詢形狀，最好的方式是測試和測量。 如需詳細資訊，請參閱[如何： 測量 PLINQ 查詢效能](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)。  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>避免呼叫非安全執行緒的方法  
 寫入至非安全執行緒的執行個體方法，從 PLINQ 查詢可能會導致資料損毀可能會或可能不會在程式中未偵測到。 這樣的作業也可能會導致例外狀況。 在下列範例中，將多個執行緒嘗試呼叫`Filestream.Write`方法同時，不支援類別。  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>限制安全執行緒方法的呼叫  
 .NET Framework 中的大部分靜態方法都是安全執行緒，並可從多個執行緒同時呼叫。 不過，即使在這些情況下，所牽涉到的同步處理作業也可能會導致查詢速度顯著變慢。  
  
> [!NOTE]
>  您可以測試這個自行插入某些呼叫<xref:System.Console.WriteLine%2A>在查詢中。 雖然此方法用於文件範例中，供示範之用，請勿使用 PLINQ 查詢中。  
  
## <a name="avoid-unnecessary-ordering-operations"></a>避免不必要的排序作業  
 當 PLINQ 以平行方式執行查詢時，它會將來源序列分割成可在多個執行緒同時運作的資料分割中。 根據預設，資料分割經過處理和傳遞結果的順序不是可預測 (除了運算子，例如`OrderBy`)。 您可以指示要保留的任何來源順序，排序 PLINQ，但這對效能有負面影響。 最佳作法，您應該盡可能是建構查詢，讓它們不會依賴順序保留。 如需詳細資訊，請參閱 [PLINQ 中的順序保留](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>願意 ForAll ForEach 時很可能  
 雖然 PLINQ 查詢上執行多個執行緒，如果您使用中的結果`foreach`迴圈 (`For Each`在 Visual Basic 中)，則查詢結果必須合併回一個執行緒，並循序存取列舉值。 在某些情況下，這是無法避免的。不過，您應該盡可能使用`ForAll`方法，以啟用輸出自己結果，例如，例如寫入安全執行緒集合的每個執行緒<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>。  
  
 相同問題適用於 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>。換句話說，`source.AsParallel().Where().ForAll(...)` 應該比  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>注意執行緒相似性問題  
 有些技術 (例如，適用於單一執行緒 Apartment (STA) 元件、Windows Forms 和 Windows Presentation Foundation (WPF) 的 COM 互通性) 會施加執行緒相似性限制，以要求程式碼在特定執行緒上執行。 例如，在 Windows Forms 和 WPF 中，只有用來建立控制項的執行緒能夠存取該控制項。 如果您嘗試存取的 Windows Form 控制項 PLINQ 查詢中的共用的狀態，如果您正在偵錯工具中，會引發例外狀況。 （這項設定可以關閉。）不過，如果 UI 執行緒上取用您的查詢，然後您可以存取控制項`foreach`迴圈列舉查詢結果，因為只有一個執行緒上執行的程式碼。  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>不要認為 ForEach、For 和 ForAll 的反覆項目一定要以平行方式執行  
 請務必記住該個別的反覆項目中<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>，<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>或<xref:System.Linq.ParallelEnumerable.ForAll%2A>迴圈年，但不是需要以平行方式執行。 因此，您所撰寫的程式碼不應依靠系統是否有正確地平行執行反覆項目，也不應依靠系統是否有正確地以特定順序執行反覆項目。  
  
 例如，下列程式碼有可能會發生死結︰  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 在此範例中，一個反覆項目會設定事件，而其他所有反覆項目則是等候事件。 在事件設定反覆項目完成之前，沒有任何等候中的反覆項目可以完成。 不過，等待中的反覆項目有可能會在事件設定反覆項目有機會執行之前，就封鎖所有用來執行平行迴圈的執行緒。 這會導致死結，事件設定反覆項目永遠不會執行，而等待中的反覆項目也永遠不會醒來。  
  
 特別是，平行迴圈的反覆項目永遠不應該等候該迴圈的另一個反覆項目才能繼續。 如果平行迴圈決定以循序方式排程反覆項目，但順序相反，系統就會發生死結。  
  
## <a name="see-also"></a>另請參閱  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
