---
title: 資料和工作平行處理原則中可能出現的錯誤
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da87531ff7f20181e1e5499acb8152d0fbadc8af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>資料和工作平行處理原則中可能出現的錯誤
在許多情況下，相較於一般循序迴圈，<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 更能提供顯著的效能改良。 不過，平行處理迴圈的工作所帶來的複雜性可能會造成問題，而在循序程式碼中，這些問題不是不常見，就是完全不會發生。 本主題列出一些您在撰寫平行迴圈時應該避免的作法。  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>不要認為平行一定比較快  
 在某些情況下，平行迴圈的執行速度可能比循序迴圈更慢。 基本的經驗法則是，反覆項目不多且使用者委派速度很快的平行迴圈不太可能加快多少速度。 不過，因為效能牽涉到許多因素，我們建議您一律要測量實際的結果。  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>避免寫入共用的記憶體位置  
 循序程式碼經常會讀取或寫入靜態變數或類別欄位。 不過，每當有多個執行緒同時存取這類變數時，就很可能產生競爭情形。 即便您可以使用鎖定來同步處理變數的存取，同步處理的成本也會減損效能。 因此，我們建議您盡可能避免在平行迴圈中存取共用狀態，或至少做出限制。 執行這項操作的最佳方式是使用 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 的多載，其在迴圈執行時會使用 <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 變數來儲存執行緒區域狀態。 如需詳細資訊，請參閱[如何：撰寫含有執行緒區域變數的 Parallel.For 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)和[如何：撰寫含有執行緒區域變數的 Parallel.ForEach 迴圈](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)。  
  
## <a name="avoid-over-parallelization"></a>避免過度平行處理  
 在使用平行迴圈時，您會因為分割來源集合和同步處理背景工作執行緒而產生額外成本。 電腦上的處理器數目則會進一步限制平行處理的好處。 多個計算繫結執行緒若只在一個處理器上執行，系統並不會獲得任何加速效果。 因此，您必須注意不要過度平行處理迴圈。  
  
 最常發生過度平行處理的情況是巢狀迴圈。 在大部分情況下，除非您適用下列一或多個條件，否則最好只平行處理外部迴圈︰  
  
-   已知內部迴圈太長。  
  
-   您正在對每個順序執行昂貴的計算  (範例所示作業並不昂貴)。  
  
-   已知目標系統有足夠的處理器，可處理因為在 `cust.Orders` 上平行處理查詢而會產生的執行緒數目。  
  
 在上述所有情況下，若要判斷最佳的查詢形狀，最好的方式是測試和測量。  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>避免呼叫非安全執行緒的方法  
 從平行迴圈寫入到非安全執行緒執行個體方法的作業，可能會導致資料損毀，而您的程式不一定會偵測到。 這樣的作業也可能會導致例外狀況。 在下列範例中，多個執行緒會嘗試同時呼叫 <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> 方法，但該類別並不支援這麼做。  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>限制安全執行緒方法的呼叫  
 .NET Framework 中的大部分靜態方法都是安全執行緒，並可從多個執行緒同時呼叫。 不過，即使在這些情況下，所牽涉到的同步處理作業也可能會導致查詢速度顯著變慢。  
  
> [!NOTE]
>  您可以自行測試這一點，方法是在您的查詢中插入一些 <xref:System.Console.WriteLine%2A> 呼叫。 雖然本文件的範例使用這個方法來做示範，但除非必要，請勿將它用在平行迴圈中。  
  
## <a name="be-aware-of-thread-affinity-issues"></a>注意執行緒相似性問題  
 有些技術 (例如，適用於單一執行緒 Apartment (STA) 元件、Windows Forms 和 Windows Presentation Foundation (WPF) 的 COM 互通性) 會施加執行緒相似性限制，以要求程式碼在特定執行緒上執行。 例如，在 Windows Forms 和 WPF 中，只有用來建立控制項的執行緒能夠存取該控制項。 這表示 (舉例來說) 除非您設定執行緒排程器，讓它排定只利用 UI 執行緒執行工作，否則您無法從平行迴圈更新清單控制項。 如需詳細資訊，請參閱[如何：排定利用使用者介面執行緒 (UI) 執行工作](http://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663)。  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>在等候 Parallel.Invoke 所呼叫的委派時請小心  
 在某些情況下，工作平行程式庫會內嵌工作，這表示它會在目前執行中之執行緒的工作上執行  (如需詳細資訊，請參閱[工作排程器](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65))。在某些案例中，此效能最佳化作業可能會導致死結。 例如，兩項工作可能會執行相同的委派程式碼，此程式碼會在事件發生時發出信號，然後等候另一項工作發出信號。 如果第二項工作在相同的執行緒中內嵌為第一項工作，而原本的第一項工作進入等候狀態，則第二項工作將永遠無法針對其事件發出信號。 若要避免這類情況，您可以對等候作業指定逾時設定，或使用明確的執行緒建構函式以協助確保兩項工作不會互相封鎖對方。  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>不要認為 ForEach、For 和 ForAll 的反覆項目一定要以平行方式執行  
 請記住 <xref:System.Threading.Tasks.Parallel.For%2A>、<xref:System.Threading.Tasks.Parallel.ForEach%2A> 或 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 迴圈中個別的反覆項目可能會以平行方式執行，但不見得需要這麼做。 因此，您所撰寫的程式碼不應依靠系統是否有正確地平行執行反覆項目，也不應依靠系統是否有正確地以特定順序執行反覆項目。 例如，下列程式碼有可能會發生死結︰  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 在此範例中，一個反覆項目會設定事件，而其他所有反覆項目則是等候事件。 在事件設定反覆項目完成之前，沒有任何等候中的反覆項目可以完成。 不過，等待中的反覆項目有可能會在事件設定反覆項目有機會執行之前，就封鎖所有用來執行平行迴圈的執行緒。 這會導致死結，事件設定反覆項目永遠不會執行，而等待中的反覆項目也永遠不會醒來。  
  
 特別是，平行迴圈的反覆項目永遠不應該等候該迴圈的另一個反覆項目才能繼續。 如果平行迴圈決定以循序方式排程反覆項目，但順序相反，系統就會發生死結。  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>應避免在 UI 執行緒上執行平行迴圈  
 請務必保持應用程式之使用者介面 (UI) 的回應性。 如果某項作業的工作足以保證平行處理的運作，則應用程式可能就不應該在 UI 執行緒上執行該項作業。  相反地，應用程式應該卸載該作業，使其在背景執行緒上執行。 例如，如果您想要使用平行迴圈來計算某些資料再轉譯到 UI 控制項中，您應該考慮在工作執行個體內執行迴圈，而不是直接在 UI 的事件處理常式中執行。  只有在核心計算完成後，您才應該將 UI 更新封送處理回 UI 執行緒。  
  
 如果您確實在 UI 執行緒上執行平行迴圈，請注意要避免從迴圈內更新 UI 控制項。 視 UI 更新的叫用方式而定，嘗試從 UI 執行緒上所執行的平行迴圈內更新 UI 控制項，可能會導致狀態損毀、例外狀況、延遲更新和甚至死結。 在下列範例中，平行迴圈會封鎖其執行所在的 UI 執行緒，直到所有反覆項目完成。 不過，如果迴圈的反覆項目是在背景執行緒上執行 (就像 <xref:System.Threading.Tasks.Parallel.For%2A> 的做法)，Invoke 的呼叫會導致訊息提交至 UI 執行緒，並阻止等候要處理的該項訊息。 由於 UI 執行緒會無法執行 <xref:System.Threading.Tasks.Parallel.For%2A>，因此訊息永遠不會進行處理，UI 執行緒則會進入死結。  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 下列範例顯示如何藉由在工作執行個體內執行迴圈來避免死結。 迴圈不會封鎖 UI 執行緒，而且訊息可進行處理。  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>請參閱  
 [平行程式設計](../../../docs/standard/parallel-programming/index.md)  
 [使用 PLINQ 時可能出現的錯誤](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [平行程式設計模式：了解及套用平行模式與 .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
