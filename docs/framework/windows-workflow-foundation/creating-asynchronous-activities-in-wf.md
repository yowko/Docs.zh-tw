---
title: "在 WF 中建立非同步活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d06f825b96f66e35bdd30db272b99bb4e2e3e1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-asynchronous-activities-in-wf"></a>在 WF 中建立非同步活動
<xref:System.Activities.AsyncCodeActivity> 會提供活動作者可用的基底類別，此類別可讓衍生活動實作非同步執行邏輯。 若自訂活動必須執行非同步工作而不保存工作流程排程器執行緒，並且封鎖任何能夠平行執行的活動，則此功能非常實用。 本主題提供如何使用 <xref:System.Activities.AsyncCodeActivity> 建立自訂非同步活動的概觀。  
  
## <a name="using-asynccodeactivity"></a>使用 AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType> 會提供自訂活動作者不同的基底類別，用於不同的活動撰寫需求。 每個基底類別具有一種特定的語意，並且提供工作流程作者 (及活動執行階段) 對應的合約。 以 <xref:System.Activities.AsyncCodeActivity> 為主的活動會採用非同步方式來對排程器執行緒執行相對工作，且以 Managed 程式碼表示其執行邏輯的活動。 因為非同步的緣故，<xref:System.Activities.AsyncCodeActivity> 可能會在執行期間造成閒置點。 由於非同步工作的變動特性，<xref:System.Activities.AsyncCodeActivity> 一定會在活動執行期間建立不保存的區塊。 這樣可以避免工作流程執行階段在非同步工作當中保存工作流程執行個體，同時也避免工作流程執行個體在非同步程式碼執行期間卸載。  
  
### <a name="asynccodeactivity-methods"></a>AsyncCodeActivity 方法  
 衍生自 <xref:System.Activities.AsyncCodeActivity> 的活動可以透過以自訂程式碼覆寫 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 和 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 方法來建立非同步執行邏輯。 執行階段呼叫這些方法時，會將這些方法傳遞到 <xref:System.Activities.AsyncCodeActivityContext>。 <xref:System.Activities.AsyncCodeActivityContext>可讓活動作者，以提供跨共用的狀態<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>的內容中<xref:System.Activities.AsyncCodeActivityContext.UserState%2A>屬性。 在下列範例中，`GenerateRandom` 活動會以非同步的方式產生隨機數字。  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 上一個範例活動衍生自 <xref:System.Activities.AsyncCodeActivity%601>，而且具有提升的 `OutArgument<int>`，名為 `Result`。 `GetRandom` 覆寫會擷取並傳回 <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> 方法所傳回的值，而且此值會設定為 `Result` 值。 不會傳回結果的非同步活動應衍生自 <xref:System.Activities.AsyncCodeActivity>。 在下列範例中，會定義衍生自 `DisplayRandom` 的 <xref:System.Activities.AsyncCodeActivity> 活動。 這個活動就像是 `GetRandom` 活動，但會將訊息顯示到主控台，而不傳回結果。  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 請注意，因為沒有傳回值，`DisplayRandom` 使用 <xref:System.Action> 而非 <xref:System.Func%602> 叫用其委派，而委派未傳回值。  
  
 <xref:System.Activities.AsyncCodeActivity> 也提供 <xref:System.Activities.AsyncCodeActivity.Cancel%2A> 覆寫。 當 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 和 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 是必要的覆寫時，<xref:System.Activities.AsyncCodeActivity.Cancel%2A> 是選擇性的，而且可加以覆寫，讓活動能夠在取消或中止時清除未完成的非同步狀態。 如果可以清除，且 `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` 是 `true`，活動應呼叫 <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>。 從這個方法擲回的任何例外狀況對於工作流程執行個體均非常重要。  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>在類別上叫用非同步方法  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的許多類別提供非同步功能，而且可以使用 <xref:System.Activities.AsyncCodeActivity> 基底活動，以非同步的方式叫用此功能。 在下列範例從[使用活動中的 AsyncOperationContext](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)，就會建立活動，以非同步方式建立檔案使用<xref:System.IO.FileStream>類別。  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>共用 BeginExecute 和 EndExecute 方法之間的狀態  
 上一個範例中，是在 <xref:System.IO.FileStream> 中存取於 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 中建立的 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 物件。 這是可能的，因為 `file` 變數會在 <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> 的 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 屬性中傳遞。 這是在 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 和 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 之間共用狀態的正確方法。 在衍生類別 (此範例中為 `FileWriter`) 中使用成員變數來共用 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 和 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 之間的狀態並不正確，因為可能會有多個活動執行個體參考該活動物件。 嘗試使用成員變數來共用狀態，可能會導致其中一個 <xref:System.Activities.ActivityInstance> 的值覆寫或耗用另一個 <xref:System.Activities.ActivityInstance> 的值。  
  
### <a name="accessing-argument-values"></a>存取引數值  
 <xref:System.Activities.AsyncCodeActivity> 的環境包含在活動定義的引數。 可以存取這些引數，從<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>覆寫使用<xref:System.Activities.AsyncCodeActivityContext>參數。 您不可以在委派中存取引數，但可以使用其參數將引數值或任何其他所需的資料傳遞至委派。 在下列範例中，會定義產生隨機數字的活動，此活動會從其 `Max` 引數取得內含的上限。 當叫用委派時，會將引數的值傳遞至非同步程式碼。  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>使用 AsyncCodeActivity 排定動作或子活動  
 <xref:System.Activities.AsyncCodeActivity> 衍生的自訂活動提供根據工作流程執行緒非同步執行工作的方法，但不提供排定子活動或動作的功能。 但是，可以透過撰寫方式將非同步行為納入子活動排程。 您可以建立非同步活動，然後以 <xref:System.Activities.Activity> 或 <xref:System.Activities.NativeActivity> 衍生活動來撰寫該活動，以提供非同步行為，並排定子活動或動作。 例如，您可以建立衍生自 <xref:System.Activities.Activity> 的活動，並且實作包含該非同步活動及其他實作活動邏輯之活動的 <xref:System.Activities.Statements.Sequence>。 如需其他範例，撰寫使用活動的<xref:System.Activities.Activity>和<xref:System.Activities.NativeActivity>，請參閱[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)，[活動撰寫選項](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)，而[複合](../../../docs/framework/windows-workflow-foundation/samples/composite.md)活動範例。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Action>  
 <xref:System.Func%602>  
 [在活動中使用 AsyncOperationContext](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)
