---
title: 作法：執行工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: a7784f37c9e8009adc3735974a6fb0423f24ea37
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238519"
---
# <a name="how-to-run-a-workflow"></a>HOW TO：執行工作流程
本主題將延續 Windows Workflow Foundation 快速入門教學課程，並討論如何建立工作流程主機和執行在先前定義的工作流程[How to:建立工作流程](how-to-create-a-workflow.md)主題。

> [!NOTE]
>  「快速入門」教學課程中的每個主題都與之前的主題息息相關。 若要完成此主題，您必須先完成[How to:Create an Activity](how-to-create-an-activity.md)和[How to:建立工作流程](how-to-create-a-workflow.md)。

> [!NOTE]
>  若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。  
  
### <a name="to-create-the-workflow-host-project"></a>建立工作流程主機專案  
  
1. 從先前開啟的方案[How to:建立活動](how-to-create-an-activity.md)使用 Visual Studio 2012 的主題。  
  
2. 在 [ **方案總管** ] 中，以滑鼠右鍵按一下 [ **WF45GettingStartedTutorial** ] 方案，並依序選取 [ **加入**]、[ **新增專案**]。  
  
    > [!TIP]
    >  如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。

3. 在 [ **已安裝** ] 節點中，選取 [ **Visual C#** ]、[ **工作流程** ] (或 [ **Visual Basic**]、[ **工作流程**])。

    > [!NOTE]
    >  依據設定哪個程式語言為 Visual Studio 主要語言而異，[ **Visual C#** ] 或 [ **Visual Basic** ] 節點可能會顯示在 [ **已安裝** ] 節點中的 [ **其他語言** ] 節點下。

     確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。 選取 [ **工作流程** ] 清單中的 [ **工作流程主控台應用程式** ]。 在 [名稱] `NumberGuessWorkflowHost`**方塊中輸入** ，然後按一下 [確定]  。 這樣會建立一個具有基本工作流程裝載支援的入門工作流程應用程式。 此基本裝載程式碼會修改，並用來執行工作流程應用程式。

4. 在 [ **方案總管** ] 中，以滑鼠右鍵按一下新加入的 [ **NumberGuessWorkflowHost** ] 專案，然後選取 [ **加入參考**]。 選取 [ **加入參考** ] 清單中的 [ **解決方案** ]、勾選 [ **NumberGuessWorkflowActivities**] 旁的核取方塊，然後按一下 [ **確定**]。

5. 在 [ **方案總管** ] 中，以滑鼠右鍵按一下 **Workflow1.xaml** ，再選擇 [ **刪除**]。 按一下 [ **確定** ] 以確認。

### <a name="to-modify-the-workflow-hosting-code"></a>修改工作流程裝載程式碼

1. 按兩下 [ **方案總管** ] 中的 [ **Program.cs** ] 或 [ **Module1.vb** ]，顯示其程式碼。

    > [!TIP]
    >  如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。

     因為這個專案是使用 [ **工作流程主控台應用程式** ] 範本所建立，所以 [ **Program.cs** ] 或 [ **Module1.vb** ] 會包含下列基本工作流程裝載程式碼。

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     這個所產生的裝載程式碼使用 <xref:System.Activities.WorkflowInvoker>。 <xref:System.Activities.WorkflowInvoker> 提供一種簡單方法來叫用工作流程，如同方法呼叫一般，但只能用於不使用持續性的工作流程。 <xref:System.Activities.WorkflowApplication> 提供更豐富的模型，可執行包含生命週期事件通知、執行控制、書籤繼續以及持續性的工作流程。 此範例會使用書籤且將 <xref:System.Activities.WorkflowApplication> 用於裝載工作流程。 將下列 `using` 或 **Imports** 陳述式加入至 **Program.cs** 或 **Module1.vb** 上層的現有 **using** 或 **Imports** 陳述式下方。

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     使用下列基本 <xref:System.Activities.WorkflowInvoker> 裝載程式碼來取代使用 <xref:System.Activities.WorkflowApplication> 的程式碼字行。 這個範例裝載程式碼會示範裝載及叫用工作流程的基本步驟，但是尚未包含從這個主題成功執行工作流程的功能。 在下列步驟中，會修改此基本程式碼，並加入其他功能，直到應用程式完成為止。

    > [!NOTE]
    >  請取代`Workflow1`在這些範例中使用`FlowchartNumberGuessWorkflow`， `SequentialNumberGuessWorkflow`，或`StateMachineNumberGuessWorkflow`，取決於您在上一個完成的工作流程[How to:建立工作流程](how-to-create-a-workflow.md)步驟。 如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     此程式碼會建立 <xref:System.Activities.WorkflowApplication>、訂閱三個工作流程開發週期事件、使用 <xref:System.Activities.WorkflowApplication.Run%2A>的呼叫來啟動工作流程，然後等候工作流程完成。 當工作流程完成時，會設定 <xref:System.Threading.AutoResetEvent> 且主機應用程式會完成。

### <a name="to-set-input-arguments-of-a-workflow"></a>若要設定工作流程的輸入引數

1. 將下列陳述式加入至 **Program.cs** 或 **Module1.vb** 上層的現有 `using` 或 `Imports` 陳述式下方。

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. 以下列用來建立及傳遞參數字典至所建立之工作流程的程式碼，取代建立新 <xref:System.Activities.WorkflowApplication> 的程式碼字行。

    > [!NOTE]
    >  請取代`Workflow1`在這些範例中使用`FlowchartNumberGuessWorkflow`， `SequentialNumberGuessWorkflow`，或`StateMachineNumberGuessWorkflow`，取決於您在上一個完成的工作流程[How to:建立工作流程](how-to-create-a-workflow.md)步驟。 如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     此字典包含具有 `MaxNumber`索引鍵的一個項目。 輸入字典中的索引鍵對應至工作流程根活動上的輸入引數。 工作流程會使用`MaxNumber` 來決定隨機產生的號碼上限。

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>若要擷取工作流程的輸出引數

1. 修改 <xref:System.Activities.WorkflowApplication.Completed%2A> 處理常式來擷取與顯示工作流程使用的轉換次數。

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>若要繼續書籤

1. 將下列程式碼加入至目前 `Main` 宣告正後方的 <xref:System.Threading.AutoResetEvent> 方法上方。

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. 將以下的 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式加入至 `Main`中現有三個工作流程開發週期處理常式的正下方。

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     每當工作流程變成閒置狀態，等候下一項猜測值時，就會呼叫此處理常式並設定 `idleAction` <xref:System.Threading.AutoResetEvent> 。 下列步驟中的程式碼會使用 `idleEvent` 和 `syncEvent` 來判斷工作流程是否要等候下一項猜測值或已完成。

    > [!NOTE]
    >  在此範例中，主機應用程式會使用 <xref:System.Activities.WorkflowApplication.Completed%2A> 和 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式中的自動重設事件，以同步化主機應用程式與工作流程的進度。 繼續書籤前，封鎖與等候工作流程變成閒置狀態並非必要的操作，但是在此範例中，必須同步化事件，如此主機才會知道工作流程是否已完成，或是否正在等候更多使用 <xref:System.Activities.Bookmark>的使用者輸入。 如需詳細資訊，請參閱 <<c0> [ 書籤](bookmarks.md)。

3. 移除對 `WaitOne`的呼叫，並以程式碼取代它來收集來自使用者的輸入，並繼續 <xref:System.Activities.Bookmark>。

     移除下列程式碼行。

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     以下列範例取代它。

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> 若要建置及執行應用程式

1. 在 [ **方案總管** ] 中，以滑鼠右鍵按一下 [ **NumberGuessWorkflowHost** ]，並選取 [ **設定為啟始專案**]。

2. 按 CTRL+F5 建置並執行應用程式。 盡量以最少的次數嘗試猜測數字。

     若要以工作流程的其他樣式之一來嘗試使用應用程式，請在用來建立 `Workflow1` 的程式碼中，將 <xref:System.Activities.WorkflowApplication> 替換成 `FlowchartNumberGuessWorkflow`、 `SequentialNumberGuessWorkflow`或 `StateMachineNumberGuessWorkflow`，視您想使用的工作流程樣式而定。

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     如需有關如何將持續性工作流程應用程式中，加入指示，請參閱下一個主題中， [How to:建立及執行長時間執行的工作流程](how-to-create-and-run-a-long-running-workflow.md)。

## <a name="example"></a>範例
 以下範例是 `Main` 方法的完整程式碼清單。

> [!NOTE]
>  請取代`Workflow1`在這些範例中使用`FlowchartNumberGuessWorkflow`， `SequentialNumberGuessWorkflow`，或`StateMachineNumberGuessWorkflow`，取決於您在上一個完成的工作流程[How to:建立工作流程](how-to-create-a-workflow.md)步驟。 如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Windows Workflow Foundation 程式設計](programming.md)
- [快速入門教學課程](getting-started-tutorial.md)
- [如何：建立工作流程](how-to-create-a-workflow.md)
- [如何：建立及執行長時間執行的工作流程](how-to-create-and-run-a-long-running-workflow.md)
- [等待工作流程中的輸入](waiting-for-input-in-a-workflow.md)
- [裝載工作流程](hosting-workflows.md)
