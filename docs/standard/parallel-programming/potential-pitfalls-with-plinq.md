---
title: "Potential Pitfalls with PLINQ | Microsoft Docs"
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
  - "PLINQ queries, pitfalls"
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Potential Pitfalls with PLINQ
在許多情況下，PLINQ 均可比循序 LINQ to Objects 查詢帶來更大幅的效能提升。  但平行處理查詢執行的工作所伴隨的複雜性，卻可能導致在循序程式碼中鮮少甚或完全不會發生的問題。  本主題列出您在撰寫 PLINQ 查詢時所應避免的動作。  
  
## 不要假設平行的速度一定比較快  
 平行處理有時會致使 PLINQ 查詢的執行速度低於 LINQ to Objects 查詢。  基本原則是，來源項目不多和使用者委派快速的查詢，不見得能大幅提高速度。  但由於效能牽涉到許多因素，因此建議您先評估實際的結果，再決定是否要使用 PLINQ。  如需詳細資訊，請參閱[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## 避免寫入共用記憶體位置  
 在循序程式碼中，讀取或寫入靜態變數或類別欄位都很常見。  但每當有多個執行緒同時存取此類變數時，就很可能出現競爭情形。  即便您可以使用鎖定來同步處理變數的存取，但卻可能因同步處理而犧牲了效能。  因此，建議您避免或至少盡可能限制 PLINQ 查詢中的共用狀態存取。  
  
## 避免過度平行處理  
 使用 `AsParallel` 運算子時，您將因為分割來源集合和同步處理背景工作執行緒而造成額外負荷成本。  再者，平行處理的優勢也會受到電腦處理器數目的限制。  以單一處理器執行多個一般電腦處理執行緒，將不會有任何提高速度的效果。  因此，您必須謹慎避免過度平行處理查詢。  
  
 在巢狀查詢中最常發生過度平行處理的情形，如下列程式碼片段所示。  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 在這種情況下，最好僅平行處理外部資料來源 \(客戶\)，除非下列一項或多項條件成立：  
  
-   已得知內部資料來源 \(cust.Orders\) 很長。  
  
-   您正在對每筆訂單執行高度耗費資源的計算。\(範例中所示的作業並不會耗費高度資源。\)  
  
-   已得知目標系統有足夠的處理器，可處理對 `cust.Orders` 平行處理查詢時將產生的執行緒數目。  
  
 在任何情況下，測試並評估都是決定最佳查詢型態最理想的途徑。  如需詳細資訊，請參閱[How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)。  
  
## 避免呼叫非安全執行緒方法  
 從 PLINQ 查詢寫入非安全執行緒執行個體方法，可能會導致您的程式無法偵測到的資料損毀。  這也可能會導致例外狀況。  下列範例中將嘗試同時以多個執行緒呼叫 `Filestream.Write` 方法，而類別並不支援此作業。  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## 限制安全執行緒方法的呼叫  
 在 .NET Framework 中，大部分的靜態方法都屬於安全執行緒方法，可同時從多個執行緒加以呼叫。  但即使在這些情況下，相關的同步處理仍可能導致查詢效能明顯降低。  
  
> [!NOTE]
>  您可以在查詢中插入某些 <xref:System.Console.WriteLine%2A> 呼叫，以自行測試效能的變化。  雖然我們在文件範例中使用此方法做為說明之用，但請勿在 PLINQ 查詢中使用此方法。  
  
## 避免不必要的排序作業  
 PLINQ 以平行方式執行查詢時，會將來源序列分成可在多個執行緒上並行操作的資料分割。  根據預設，資料分割的處理順序以及結果的傳遞順序，都是無法預測的 \(`OrderBy` 之類的運算子除外\)。  您可以指示 PLINQ 保留任何來源序列的順序，但這會對效能產生負面影響。  最佳作法是盡可能將查詢結構化，使其無須依賴順序保留。  如需詳細資訊，請參閱[Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)。  
  
## ForAll 的優先順序應高於 ForEach  
 雖然 PLINQ 可在多個執行緒上執行查詢，但如果您在 `foreach` 迴圈 \(在 Visual Basic 中為 `For Each`\) 中使用查詢結果，您就必須將這些結果重新合併到一個執行緒中，並且以列舉程式依序存取結果。  在某些情況下這是無法避免的，但只要情況允許，即應使用 `ForAll` 方法讓每個執行緒輸出其本身的結果，例如寫入 <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> 之類的安全執行緒集合。  
  
 換句話說，相同問題適用於 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> `source.AsParallel().Where().ForAll(...)` 應該認真慣用  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## 留意執行緒相似性問題  
 有些技術 \(例如單一執行緒 Apartment \(STA\) 元件的 COM 互通性、Windows Form 和 Windows Presentation Foundation \(WPF\)\) 具有必須以特定執行緒執行程式碼的執行緒相似性限制。  例如在 Windows Form 和 WPF 中，都只能在建立控制項的執行緒上存取該控制項。  如果您嘗試在 PLINQ 查詢中存取共用狀態的 Windows Form 控制項，您在執行偵錯工具時將會引發例外狀況。\(您可以關閉此設定。\)但如果是在 UI 執行緒上使用您的查詢，則您可以從列舉查詢結果的 `foreach` 迴圈存取控制項，因為該程式碼僅在一個執行緒上執行。  
  
## 不要假設 ForEach、For 和 ForAll 的反覆項目一定會平行執行  
 請務必記住，<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 或 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 迴圈中的個別反覆項目可以平行執行，但不一定要平行執行。  因此，您應避免撰寫下列程式碼：任何取決於平行執行反覆項目或以任何特定順序執行反覆項目之正確性的程式碼。  
  
 例如，這個程式碼就很容易造成死結：  
  
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
  
 在這個範例中，有一個反覆項目會設定事件，而其他所有反覆項目會等候該事件。  在設定事件的那個反覆項目完成之前，這些等候事件的反覆項目都無法完成。  但是，這些等候事件的反覆項目可能會讓所有用於執行平行迴圈的執行緒無法繼續，而造成設定事件的反覆項目沒有機會執行。  這會導致死結：也就是設定事件的反覆項目永遠不會執行，而等待事件的反覆項目也永遠不會啟動。  
  
 更明確地說，平行迴圈中絕不應該有反覆項目等候迴圈中的另一個反覆項目完成。  如果平行迴圈決定以循序方式執行反覆項目，但是順序相反，即會發生死結。  
  
## 請參閱  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)