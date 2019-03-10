---
title: 使用 WorkflowInvoker 與 WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 29d152cd6011fb3b55aae60726d095dc44dd23a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707686"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>使用 WorkflowInvoker 與 WorkflowApplication
Windows Workflow Foundation (WF) 提供幾個方法來裝載工作流程。 <xref:System.Activities.WorkflowInvoker> 提供一種簡單方法來叫用工作流程，如同方法呼叫一般，但只能用於不使用持續性的工作流程。 <xref:System.Activities.WorkflowApplication> 提供更豐富的模型，可執行包含生命週期事件通知、執行控制、書籤繼續以及持續性的工作流程。 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 支援傳訊活動，主要搭配工作流程服務使用。 本主題會向您介紹如何使用 <xref:System.Activities.WorkflowInvoker> 和 <xref:System.Activities.WorkflowApplication> 進行工作流程裝載。 如需有關裝載的工作流程<xref:System.ServiceModel.Activities.WorkflowServiceHost>，請參閱 <<c2> [ 工作流程服務](../wcf/feature-details/workflow-services.md)並[裝載工作流程服務概觀](../wcf/feature-details/hosting-workflow-services-overview.md)。  
  
## <a name="using-workflowinvoker"></a>使用 WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker>如同方法叫用般，提供執行工作流程的模型。 若要使用 <xref:System.Activities.WorkflowInvoker> 叫用工作流程，請呼叫 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 方法，並傳入要叫用之工作流程的工作流程定義。 在此範例中，會使用 <xref:System.Activities.Statements.WriteLine> 叫用 <xref:System.Activities.WorkflowInvoker> 活動。  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 使用 <xref:System.Activities.WorkflowInvoker> 叫用工作流程時，工作流程會在呼叫執行緒上執行，且 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 方法會封鎖至工作流程完成為止，並包含任何閒置時間。 若要設定工作流程必須完成的逾時間隔，請使用接受 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 的其中一個 <xref:System.TimeSpan> 多載。 在此範例中，會以兩個不同的逾時間隔叫用工作流程兩次。 第一個工作流程會完成，但是第二個則不會。  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  只有在超過逾時間隔及工作流程在執行期間變成閒置狀態時，才會擲回 <xref:System.TimeoutException>。 需要比指定的逾時間隔還長的時間才能完成的工作流程，會在工作流程沒有變成閒置狀態時成功完成。  
  
 <xref:System.Activities.WorkflowInvoker> 也提供叫用方法的非同步版本。 如需詳細資訊，請參閱 <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> 與 <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>。  
  
### <a name="setting-input-arguments-of-a-workflow"></a>設定工作流程的輸入引數  
 若要將資料傳入工作流程，可以使用以引數名稱做為索引鍵，且對應工作流程輸入引數之輸入參數的字典。 在此範例中，會叫用 <xref:System.Activities.Statements.WriteLine> 並使用輸入參數的字典指定其 <xref:System.Activities.Statements.WriteLine.Text%2A> 引數的值。  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>擷取工作流程的輸出引數  
 工作流程的輸出引數可以使用從 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 呼叫傳回的輸出字典來取得。 下列範例會叫用由具有兩個輸入引數和兩個輸出引數之單一 `Divide` 活動組成的工作流程。 叫用此工作流程時，系統會傳遞包含每個輸入引數之值 (以引數名稱做為索引鍵) 的 `arguments` 字典。 當傳回 `Invoke` 的呼叫時，每個輸出引數都會傳入 `outputs` 字典 (也以引數名稱做為索引鍵)。  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 如果此工作流程衍生自 <xref:System.Activities.ActivityWithResult> (例如 `CodeActivity<TResult>` 或 `Activity<TResult>`)，而且除了定義完善的 <xref:System.Activities.Activity%601.Result%2A> 輸出引數以外，還有其他輸出引數，您就必須使用 `Invoke` 的非泛型多載，才能擷取其他引數。 若要這樣做，傳遞給 `Invoke` 的工作流程定義必須屬於 <xref:System.Activities.Activity> 型別。 在此範例中，`Divide` 活動會衍生自 `CodeActivity<int>` 但宣告為 <xref:System.Activities.Activity>，以便使用 `Invoke` 的非泛型多載 (傳回引數的字典而非單一傳回值)。  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>使用 WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> 提供一組豐富的工作流程執行個體管理功能。 <xref:System.Activities.WorkflowApplication> 可做為實際 <xref:System.Activities.Hosting.WorkflowInstance> 的執行緒安全 Proxy (可封裝執行階段)，並提供建立及載入工作流程執行個體、暫停與繼續、終止，以及生命週期事件通知的方法。 若要使用 <xref:System.Activities.WorkflowApplication> 執行工作流程，您要建立<xref:System.Activities.WorkflowApplication>、訂閱任何想要的開發週期事件、啟動工作流程，然後等候它完成。 在此範例中，會建立由 <xref:System.Activities.Statements.WriteLine> 活動組成的工作流程定義，並使用特定的工作流程定義建立 <xref:System.Activities.WorkflowApplication>。 <xref:System.Activities.WorkflowApplication.Completed%2A> 會進行處理，如此一來，當工作流程完成時即會通知主機應用程式，會呼叫 <xref:System.Activities.WorkflowApplication.Run%2A> 來開始工作流程，然後主機應用程式會等候工作流程完成。 當工作流程完成時，會設定 <xref:System.Threading.AutoResetEvent>，且主機應用程式可繼續執行，如下列範例所示。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>工作流程應用程式開發週期事件  
 除了 <xref:System.Activities.WorkflowApplication.Completed%2A> 以外，當卸載工作流程 (<xref:System.Activities.WorkflowApplication.Unloaded%2A>)、中止 (<xref:System.Activities.WorkflowApplication.Aborted%2A>)、變成閒置 (<xref:System.Activities.WorkflowApplication.Idle%2A> 與 <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>) 或發生未處理的例外狀況 (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>) 時，也可通知主機作者。 工作流程應用程式開發人員可處理這些通知，並採取適當行動，如下列範例所示。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>設定工作流程的輸入引數  
 與使用 <xref:System.Activities.WorkflowInvoker> 傳入資料的方式相似，當開始工作流程時，可使用參數字典將資料傳入工作流程內。 字典中的每一項都對應至指定工作流程的輸入引數。 在此範例中，會叫用由 <xref:System.Activities.Statements.WriteLine> 活動構成的工作流程，且會使用輸入參數的字典指定其 <xref:System.Activities.Statements.WriteLine.Text%2A> 引數。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>擷取工作流程的輸出引數  
 當工作流程完成時，可存取 <xref:System.Activities.WorkflowApplication.Completed%2A> 字典來擷取 <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> 處理常式中的任何輸出引數。 下列範例會使用 <xref:System.Activities.WorkflowApplication> 來裝載工作流程。 A<xref:System.Activities.WorkflowApplication>建構執行個體是使用工作流程定義，其中包含單一`DiceRoll`活動。 
  `DiceRoll` 活動具有兩個輸出引數，這些引數代表擲骰作業的結果。 工作流程完成時，便會在 <xref:System.Activities.WorkflowApplication.Completed%2A> 處理常式中擷取輸出。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> 與 <xref:System.Activities.WorkflowInvoker> 會採用輸入參數的字典，並傳回 `out` 引數的字典。 這些字典參數、屬性與傳回值都屬於型別 `IDictionary<string, object>`。 傳入的字典類別實際執行個體，可以是任何實作 `IDictionary<string, object>` 的類別。 在這些範例中，會使用 `Dictionary<string, object>`。 如需字典的詳細資訊，請參閱<xref:System.Collections.Generic.IDictionary%602>和<xref:System.Collections.Generic.Dictionary%602>。  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>使用書籤將資料傳入執行中的工作流程  
 書籤是一種機制，可讓活動被動等候繼續，也可將資料傳遞至執行中的工作流程執行個體。 如果活動正在等候資料，就可建立 <xref:System.Activities.Bookmark> 並註冊當恢復 <xref:System.Activities.Bookmark> 時要呼叫的回呼方法，如下列範例所示。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 執行時，`ReadLine` 活動就會建立 <xref:System.Activities.Bookmark>、註冊回呼，然後等候繼續 <xref:System.Activities.Bookmark>。 當它繼續時，`ReadLine` 活動會將以 <xref:System.Activities.Bookmark> 傳遞的資料指派至其 <xref:System.Activities.Activity%601.Result%2A> 引數。 在此範例中，使用 `ReadLine` 活動建立的工作流程可蒐集使用者的名稱，並於主控台視窗中顯示。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 當執行 `ReadLine` 活動時，它會建立稱為 <xref:System.Activities.Bookmark> 的 `UserName`，然後等候書籤繼續。 主機會收集想要的資料，然後繼續 <xref:System.Activities.Bookmark>。 工作流程會繼續、顯示名稱，然後完成。  
  
 主應用程式可以檢查工作流程，以判斷是否有任何作用中的書籤。 若要進行這項處理，它可以呼叫 <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> 執行個體的 <xref:System.Activities.WorkflowApplication> 方法，或是在 <xref:System.Activities.WorkflowApplicationIdleEventArgs> 處理常式中檢查 <xref:System.Activities.WorkflowApplication.Idle%2A>。  
  
 下列程式碼範例與上一個範例很相似，例外之處是先列舉作用中的書籤，然後再繼續書籤。 系統會啟動工作流程，而且一旦建立 <xref:System.Activities.Bookmark> 並且工作流程處於閒置狀態之後，就會呼叫 <xref:System.Activities.WorkflowApplication.GetBookmarks%2A>。 當工作流程完成時，主控台就會顯示下列輸出。  
  
 **您的姓名為何？**  
**BookmarkName:使用者名稱-OwnerDisplayName:ReadLine**   
**Steve**   
**Hello Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 下列程式碼範例會檢查傳遞給 <xref:System.Activities.WorkflowApplicationIdleEventArgs> 執行個體之 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式的 <xref:System.Activities.WorkflowApplication>。 在此範例中，處於閒置狀態的工作流程具有一個名為 <xref:System.Activities.Bookmark> 且由名為 `EnterGuess` 之活動所擁有的 `ReadInt`。 此程式碼範例為基礎的[How to:執行工作流程](how-to-run-a-workflow.md)，這屬於[入門教學課程](getting-started-tutorial.md)。 如果該步驟中的 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式修改為包含此範例中的程式碼，就會顯示下列輸出。  
  
 **BookmarkName:EnterGuess-OwnerDisplayName:ReadInt**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>總結  
 <xref:System.Activities.WorkflowInvoker> 提供叫用工作流程的輕鬆方式，雖然它提供在工作流程之初傳入資料，以及從已完成之工作流程擷取資料的方法，但它並不提供可使用 <xref:System.Activities.WorkflowApplication> 的更複雜案例。
