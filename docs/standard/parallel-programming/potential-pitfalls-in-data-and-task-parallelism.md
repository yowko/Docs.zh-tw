---
title: "Potential Pitfalls in Data and Task Parallelism | Microsoft Docs"
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
  - "parallel programming, pitfalls"
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Potential Pitfalls in Data and Task Parallelism
在許多情況下，<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 均可為一般循序迴圈帶來更大幅的效能提升。  然而，將迴圈平行化的工作所伴隨的複雜性，卻可能導致在循序程式碼中鮮少甚或完全不會發生的問題。  本主題列出您在撰寫平行迴圈時所應避免的動作。  
  
## 不要假設平行的速度一定比較快  
 在某些情況下，平行迴圈的執行速度可能會比循序迴圈還要慢。  基本原則是，如果平行迴圈中的反覆項目和快速使用者委派的數量不多，就不見得能大幅提高速度。  但由於效能牽涉到許多因素，因此建議您一定要測量實際的結果。  
  
## 避免寫入共用記憶體位置  
 在循序程式碼中，讀取或寫入靜態變數或類別欄位都很常見。  但每當有多個執行緒同時存取此類變數時，就很可能出現競爭情形。  即便您可以使用鎖定來同步處理變數的存取，但卻可能因同步處理而犧牲了效能。  因此，建議您避免或至少盡可能限制平行迴圈中的共用狀態存取。  這麼做的最佳方法就是使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 的多載，這些多載會在迴圈執行期間使用 <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 變數來儲存執行緒區域狀態。  如需詳細資訊，請參閱[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)與[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)。  
  
## 避免過度平行處理  
 使用平行迴圈時，會因為要分割來源集合和將背景工作執行緒同步處理而產生額外負荷成本。  再者，平行處理的優勢也會受到電腦處理器數目的限制。  以單一處理器執行多個一般電腦處理執行緒，將不會有任何提高速度的效果。  因此，您必須謹慎避免將迴圈過度平行化。  
  
 最常發生過度平行化情形的就是巢狀迴圈。  在大多數情況下，除非下列一項或多項條件成立，否則最好只將外部迴圈平行化：  
  
-   已得知內部迴圈很長。  
  
-   您正在對每筆訂單執行高度耗費資源的計算。\(範例中所示的作業並不會耗費高度資源。\)  
  
-   已得知目標系統有足夠的處理器，可處理對 `cust.Orders` 平行處理查詢時將產生的執行緒數目。  
  
 在任何情況下，測試並評估都是決定最佳查詢型態最理想的途徑。  
  
## 避免呼叫非安全執行緒方法  
 從平行迴圈寫入非安全執行緒執行個體方法，可能會導致您的程式無法偵測到的資料損毀。  這也可能會導致例外狀況。  下列範例中將嘗試同時以多個執行緒呼叫 <xref:System.IO.FileStream.WriteByte%2A?displayProperty=fullName> 方法，而類別並不支援此作業。  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## 限制安全執行緒方法的呼叫  
 在 .NET Framework 中，大部分的靜態方法都屬於安全執行緒方法，可同時從多個執行緒加以呼叫。  但即使在這些情況下，相關的同步處理仍可能導致查詢效能明顯降低。  
  
> [!NOTE]
>  您可以在查詢中插入某些 <xref:System.Console.WriteLine%2A> 呼叫，以自行測試效能的變化。  雖然我們在文件範例中使用此方法做為說明之用，但是如非必要，請勿在平行迴圈中使用此方法。  
  
## 留意執行緒相似性問題  
 有些技術 \(例如單一執行緒 Apartment \(STA\) 元件的 COM 互通性、Windows Form 和 Windows Presentation Foundation \(WPF\)\) 具有必須以特定執行緒執行程式碼的執行緒相似性限制。  例如在 Windows Form 和 WPF 中，都只能在建立控制項的執行緒上存取該控制項。  也就是說，這表示除非您將執行緒排程器設為只在 UI 執行緒上排定工作，否則您無法從平行迴圈中更新清單控制項。  如需詳細資訊，請參閱[How to: Schedule Work on the User Interface \(UI\) Thread](../Topic/How%20to:%20Schedule%20Work%20on%20the%20User%20Interface%20\(UI\)%20Thread.md)。  
  
## 在 Parallel.Invoke 所呼叫的委派中等候時需格外小心  
 在某些情形下，工作平行程式庫會內嵌工作，這表示它會將工作搬到目前正在執行的執行緒上執行 \(如需詳細資訊，請參閱 [Task Schedulers](../Topic/Task%20Schedulers.md)\)。這種效能最佳化作法有時候可能會導致死結。  例如，有兩項工作會執行同一個委派程式碼，這個委派程式碼會在事件發生時發出信號，然後等候另一項工作發出信號。  如果第二項工作內嵌到第一項工作所在的執行緒上，而第一項工作進入等候狀態，則第二項工作會永遠無法發出事件信號。  若要避免發生這種情形，您可以指定等候作業的逾時時間，或者是明確使用執行緒建構函式，協助確保這兩項工作不會阻礙彼此的進行。  
  
## 不要假設 ForEach、For 和 ForAll 的反覆項目一定會平行執行  
 請務必記住，<xref:System.Threading.Tasks.Parallel.For%2A>、<xref:System.Threading.Tasks.Parallel.ForEach%2A> 或 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 迴圈中的個別反覆項目可以平行執行，但不一定要平行執行。  因此，您應避免撰寫下列程式碼：任何取決於平行執行反覆項目或以任何特定順序執行反覆項目之正確性的程式碼。  例如，這個程式碼就很容易造成死結：  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 在這個範例中，有一個反覆項目會設定事件，而其他所有反覆項目會等候該事件。  在設定事件的那個反覆項目完成之前，這些等候事件的反覆項目都無法完成。  但是，這些等候事件的反覆項目可能會讓所有用於執行平行迴圈的執行緒無法繼續，而造成設定事件的反覆項目沒有機會執行。  這會導致死結：也就是設定事件的反覆項目永遠不會執行，而等待事件的反覆項目也永遠不會啟動。  
  
 更明確地說，平行迴圈中絕不應該有反覆項目等候迴圈中的另一個反覆項目完成。  如果平行迴圈決定以循序方式執行反覆項目，但是順序相反，即會發生死結。  
  
## 避免在 UI 執行緒上執行平行迴圈  
 讓應用程式使用者介面 \(UI\) 保持回應非常重要。  如果作業包含足夠的工作來保證平行化作業，則不應該在 UI 執行緒上執行該作業。而是應該要將該作業搬到背景執行緒上執行。  例如，如果您想要使用平行迴圈來計算之後應呈現在 UI 控制項中的某些資料，即應該考慮在工作執行個體中執行迴圈，而非直接在 UI 事件處理常式中執行迴圈。您應等到核心計算完成後，才將 UI 更新封送處理回到 UI 執行緒。  
  
 如果您非得在 UI 執行緒上執行平行迴圈，請小心避免從該迴圈內更新 UI 控制項。  如果嘗試在 UI 執行緒上執行的平行迴圈內更新 UI 控制項，則可能會發生狀態毀損、例外狀況、延遲更新或甚至是死結的情形 \(視您叫用 UI 更新的方法而定\)。  在下列範例中，平行迴圈會讓用來執行的 UI 執行緒無法繼續，直到所有反覆項目都完成為止。  但是，如果迴圈的某個反覆項目在背景執行緒上執行 \(如 <xref:System.Threading.Tasks.Parallel.For%2A> 所為\)，則呼叫 Invoke 會導致提交一則訊息給 UI 執行緒，而導致無法等候該訊息處理完畢。  因為 UI 執行緒無法執行 <xref:System.Threading.Tasks.Parallel.For%2A>，所以訊息永遠不會受到處理，這樣 UI 執行緒就會發生死結。  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 下列範例顯示如何在工作執行個體內執行迴圈，以避免死結。  UI 執行緒不會因為迴圈受阻，而訊息可以受到處理。  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## 請參閱  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Potential Pitfalls with PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)   
 [平行程式設計模式：了解及套用平行模式與 .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=185142)