---
title: 工作流程中的模型化取消行為
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e455bf4d74f77c6cd87301dc9a21f56117777ecf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>工作流程中的模型化取消行為
活動可以在工作流程內部取消，例如，由 <xref:System.Activities.Statements.Parallel> 活動在它的 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 評估為 `true` 時來取消不完整的分支，或是從工作流程外部取消 (如果主機呼叫 <xref:System.Activities.WorkflowApplication.Cancel%2A>)。 若要提供取消處理，工作流程作者可以使用 <xref:System.Activities.Statements.CancellationScope> 活動、<xref:System.Activities.Statements.CompensableActivity> 活動或是建立可提供取消邏輯的自訂活動。 本主題提供工作流程取消的概觀。  
  
## <a name="cancellation-compensation-and-transactions"></a>取消、補償和交易  
 如果交易程序的任何部分發生錯誤，交易可讓應用程式中止 (回復) 在交易內部執行的所有變更。 但是，並非所有可能需要取消或復原的工作都適合交易使用，例如長時間執行的工作或是未牽涉到交易資源的工作。 補償會提供一個模型，可在工作流程發生後續失敗時，復原之前完成的非交易式工作。 取消會提供一個模型給工作流程和活動的作者使用，以便處理尚未完成的非交易式工作。 如果活動尚未完成執行而且遭到取消，則會叫用它的取消邏輯 (如果有的話)。  
  
> [!NOTE]
>  如需交易與補償的詳細資訊，請參閱[交易](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)和[補償](../../../docs/framework/windows-workflow-foundation/compensation.md)。  
  
## <a name="using-cancellationscope"></a>使用 CancellationScope  
 <xref:System.Activities.Statements.CancellationScope> 活動有兩個可以包含子活動的區段：<xref:System.Activities.Statements.CancellationScope.Body%2A> 和 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>。 <xref:System.Activities.Statements.CancellationScope.Body%2A> (組成活動邏輯的活動所在的地方) 以及 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> (可提供活動取消邏輯之活動所在的地方)。 只有當活動尚未完成時才可以將它取消。 如果是 <xref:System.Activities.Statements.CancellationScope> 活動，完成指的是 <xref:System.Activities.Statements.CancellationScope.Body%2A> 中的活動完成。 如果排定了取消要求而且尚未完成 <xref:System.Activities.Statements.CancellationScope.Body%2A> 中的活動，則 <xref:System.Activities.Statements.CancellationScope> 將會標示為 <xref:System.Activities.ActivityInstanceState.Canceled> 而且將會執行 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動。  
  
### <a name="canceling-a-workflow-from-the-host"></a>從主機取消工作流程  
 主機可以取消工作流程，其方式是呼叫正在裝載工作流程之 <xref:System.Activities.WorkflowApplication.Cancel%2A> 執行個體的 <xref:System.Activities.WorkflowApplication> 方法。 在下列範例中，將會建立一個具有 <xref:System.Activities.Statements.CancellationScope> 的工作流程。 將會叫用此工作流程，然後主機會呼叫 <xref:System.Activities.WorkflowApplication.Cancel%2A>。 工作流程的主要執行工作會停止，並叫用 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 的 <xref:System.Activities.Statements.CancellationScope>，然後工作流程會完成而且狀態為 <xref:System.Activities.ActivityInstanceState.Canceled>。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 當叫用這個工作流程時，主控台就會顯示下列輸出。  
  
 **正在啟動工作流程。**  
**已叫用 CancellationHandler。**   
**取消工作流程 b30ebb30-df46-4d90-a211-e31c38d8db3c。**    
> [!NOTE]
>  當取消 <xref:System.Activities.Statements.CancellationScope> 活動並叫用 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 時，工作流程作者必須判斷此活動取消之前所完成的進度，才能提供適當的取消邏輯。 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 不會提供有關取消之活動進度的任何資訊。  
  
 如果未處理的例外狀況反昇而超過工作流程的根，而且 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 處理常式傳回 <xref:System.Activities.UnhandledExceptionAction.Cancel>，也可以取消工作流程。 在這個範例中，工作流程會啟動然後擲回 <xref:System.ApplicationException>。 工作流程未處理這個例外狀況，所以叫用了 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 處理常式。 此處理常式會指示執行階段取消工作流程，而且會叫用目前執行之 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 活動的 <xref:System.Activities.Statements.CancellationScope>。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 當叫用這個工作流程時，主控台就會顯示下列輸出。  
  
 **正在啟動工作流程。**  
**工作流程 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 中**   
**擲回 ApplicationException。**   
**已叫用 CancellationHandler。**   
**取消工作流程 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9。**    
### <a name="canceling-an-activity-from-inside-a-workflow"></a>從工作流程內部取消活動  
 活動的父系也可以取消該活動。 例如，如果 <xref:System.Activities.Statements.Parallel> 活動有多個執行中的分支，而且它的 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 評估為 `true`，將會取消不完整的分支。 在這個範例中，將會建立具有兩個分支的 <xref:System.Activities.Statements.Parallel> 活動。 它的 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 會設定為 `true`，所以一旦它的任何一個分支完成時，<xref:System.Activities.Statements.Parallel> 就會完成。 在這個範例中，分支 2 完成，所以分支 1 遭到取消。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 當叫用這個工作流程時，主控台就會顯示下列輸出。  
  
 **分支 1 正在啟動。**  
**分支 2 完成。**   
**分支 1 已取消。**   
**工作流程 e0685e24-18ef-4a47-acf3-5c638732f3be 已完成。**  如果例外狀況反昇而超過活動的根，但是在工作流程的更高層處理，也會取消活動。 在這個範例中，工作流程的主要邏輯是由 <xref:System.Activities.Statements.Sequence> 活動所組成。 <xref:System.Activities.Statements.Sequence> 會指定為 <xref:System.Activities.Statements.CancellationScope.Body%2A> 活動的 <xref:System.Activities.Statements.CancellationScope>，該活動包含在 <xref:System.Activities.Statements.TryCatch> 活動中。 從 <xref:System.Activities.Statements.Sequence> 的主體擲回例外狀況，且會由父活動 <xref:System.Activities.Statements.TryCatch> 所處理，並取消 <xref:System.Activities.Statements.Sequence>。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 當叫用這個工作流程時，主控台就會顯示下列輸出。  
  
 **正在啟動序列。**  
**已取消序列。**   
**攔截到例外狀況。**   
**已完成的工作流程 e3c18939-121e-4c43-af1c-ba1ce977ce55。**   
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>從 CancellationHandler 擲回例外狀況。  
 從 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 的 <xref:System.Activities.Statements.CancellationScope> 擲回的任何例外狀況對工作流程都很重要。 如果例外狀況有可能從 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 逸出，請在 <xref:System.Activities.Statements.TryCatch> 中使用 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 來攔截及處理這些例外狀況。  
  
### <a name="cancellation-using-compensableactivity"></a>使用 CompensableActivity 取消  
 就像 <xref:System.Activities.Statements.CancellationScope> 活動一樣，<xref:System.Activities.Statements.CompensableActivity> 具有 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>。 如果取消了 <xref:System.Activities.Statements.CompensableActivity>，將會叫用其 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 中的任何活動。 這對於復原部分完成的可補償工作很有用處。 如需有關如何使用資訊<xref:System.Activities.Statements.CompensableActivity>補償和取消作業，請參閱[補償](../../../docs/framework/windows-workflow-foundation/compensation.md)。  
  
## <a name="cancellation-using-custom-activities"></a>使用自訂活動取消  
 自訂活動作者可以透過幾個方法，將取消邏輯實作到自訂活動中。 從 <xref:System.Activities.Activity> 衍生的自訂活動可以實作取消邏輯，方法是將 <xref:System.Activities.Statements.CancellationScope> 或其他包含取消邏輯的自訂活動放在活動的主體內。 <xref:System.Activities.AsyncCodeActivity> 和 <xref:System.Activities.NativeActivity> 衍生活動可以覆寫其各自的 <xref:System.Activities.NativeActivity.Cancel%2A> 方法，並在這裡提供取消邏輯。 <xref:System.Activities.CodeActivity> 衍生活動不會提供任何取消的規定，因為其所有工作都是在執行階段呼叫 <xref:System.Activities.CodeActivity.Execute%2A> 方法時，於單一執行中執行。 如果尚未呼叫執行方法，而且取消了根據 <xref:System.Activities.CodeActivity> 的活動，此活動會關閉且狀態為 <xref:System.Activities.ActivityInstanceState.Canceled>，而且不會呼叫 <xref:System.Activities.CodeActivity.Execute%2A> 方法。  
  
### <a name="cancellation-using-nativeactivity"></a>使用 NativeActivity 取消  
 <xref:System.Activities.NativeActivity> 衍生活動可以覆寫 <xref:System.Activities.NativeActivity.Cancel%2A> 方法來提供自訂取消邏輯。 如果這個方法未遭到覆寫，則會套用預設工作流程取消邏輯。 預設取消作業，則會發生在處理序<xref:System.Activities.NativeActivity>，不會覆寫<xref:System.Activities.NativeActivity.Cancel%2A>方法或其<xref:System.Activities.NativeActivity.Cancel%2A>方法會呼叫基底<xref:System.Activities.NativeActivity><xref:System.Activities.NativeActivity.Cancel%2A>方法。 當取消某個活動時，執行階段會將此活動標示為將要取消，而且會自動處理某些清除工作。 如果此活動只有待處理的書籤，這些書籤將會被移除，而且此活動將會標示為 <xref:System.Activities.ActivityInstanceState.Canceled>。 接著會取消已取消之活動的任何待處理的子活動。 嘗試排定其他子活動的任何動作都會遭到忽略，而且此活動會標示為 <xref:System.Activities.ActivityInstanceState.Canceled>。 如果有任何待處理的子活動在 <xref:System.Activities.ActivityInstanceState.Canceled> 或 <xref:System.Activities.ActivityInstanceState.Faulted> 狀態下完成，此活動會標示為 <xref:System.Activities.ActivityInstanceState.Canceled>。 請注意，可以忽略取消要求。 如果某個活動沒有任何待處理的書籤或是執行中的子活動，而且被標示為將要取消之後也沒有排定任何其他工作項目，此活動將會順利完成。 在許多案例中，這個預設取消作業就足夠了，但是如果需要其他取消邏輯，則可以使用內建取消活動或自訂活動。  
  
 在下列範例中，將會定義 <xref:System.Activities.NativeActivity.Cancel%2A> 型自訂 <xref:System.Activities.NativeActivity> 活動的 `ParallelForEach` 覆寫。 當取消活動時，這個覆寫會處理該活動的取消邏輯。 這個範例是屬於[非泛型 ParallelForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)範例。  
  
```csharp  
protected override void Cancel(NativeActivityContext context)  
{  
    // If we do not have a completion condition then we can just  
    // use default logic.  
    if (this.CompletionCondition == null)  
    {  
        base.Cancel(context);  
    }  
    else  
    {  
        context.CancelChildren();  
    }  
}  
```  
  
 <xref:System.Activities.NativeActivity> 衍生活動可以檢查 <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A> 屬性來判斷是否已經要求取消，並呼叫 <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> 方法來將其本身標示為已取消。 呼叫 <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> 不會立即完成活動。 通常執行階段會在沒有其他待處理工作時完成此活動，但是如果呼叫 <xref:System.Activities.NativeActivityContext.MarkCanceled%2A>，最終的狀態將會是 <xref:System.Activities.ActivityInstanceState.Canceled> 而不是 <xref:System.Activities.ActivityInstanceState.Closed>。  
  
### <a name="cancellation-using-asynccodeactivity"></a>使用 AsyncCodeActivity 取消  
 <xref:System.Activities.AsyncCodeActivity> 型活動也可以藉由覆寫 <xref:System.Activities.AsyncCodeActivity.Cancel%2A> 方法來提供自訂取消邏輯。 如果這個方法未遭到覆寫，此活動已取消時不會執行任何取消處理動作。 在下列範例中，將會定義 <xref:System.Activities.AsyncCodeActivity.Cancel%2A> 型自訂 <xref:System.Activities.AsyncCodeActivity> 活動的 `ExecutePowerShell` 覆寫。 當取消此活動時，它會執行所要的取消行為。 這個範例是屬於[使用 InvokePowerShell 活動](../../../docs/framework/windows-workflow-foundation/samples/using-the-invokepowershell-activity.md)範例。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 <xref:System.Activities.AsyncCodeActivity> 衍生活動可以檢查 <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A> 屬性來判斷是否已經要求取消，並呼叫 <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> 方法來將其本身標示為已取消。
