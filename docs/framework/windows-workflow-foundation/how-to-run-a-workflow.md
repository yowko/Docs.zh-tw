---
title: 作法：執行工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 3badda7afeb25b44b0de574f97452d05efe75bfc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962292"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="76e40-102">作法：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="76e40-102">How to: Run a Workflow</span></span>
<span data-ttu-id="76e40-103">本主題是 Windows Workflow Foundation 消費者入門教學課程的接續, 並討論如何建立工作流程主機, 並執行先前[的 how to:建立工作流程](how-to-create-a-workflow.md)主題。</span><span class="sxs-lookup"><span data-stu-id="76e40-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="76e40-104">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="76e40-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="76e40-105">若要完成本主題, 您必須[先完成如何:建立活動](how-to-create-an-activity.md)和[如何:建立工作流程](how-to-create-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="76e40-105">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

> [!NOTE]
> <span data-ttu-id="76e40-106">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="76e40-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="76e40-107">建立工作流程主機專案</span><span class="sxs-lookup"><span data-stu-id="76e40-107">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="76e40-108">開啟先前[的 how to:使用 Visual Studio 2012](how-to-create-an-activity.md)建立活動主題。</span><span class="sxs-lookup"><span data-stu-id="76e40-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="76e40-109">在 [ **方案總管** ] 中，以滑鼠右鍵按一下 [ **WF45GettingStartedTutorial** ] 方案，並依序選取 [ **加入**]、[ **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="76e40-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="76e40-110">如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。</span><span class="sxs-lookup"><span data-stu-id="76e40-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="76e40-111">在 [ **已安裝** ] 節點中，選取 [ **Visual C#** ]、[ **工作流程** ] (或 [ **Visual Basic**]、[ **工作流程**])。</span><span class="sxs-lookup"><span data-stu-id="76e40-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="76e40-112">依據設定哪個程式語言為 Visual Studio 主要語言而異，[ **Visual C#** ] 或 [ **Visual Basic** ] 節點可能會顯示在 [ **已安裝** ] 節點中的 [ **其他語言** ] 節點下。</span><span class="sxs-lookup"><span data-stu-id="76e40-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="76e40-113">確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。</span><span class="sxs-lookup"><span data-stu-id="76e40-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="76e40-114">選取 [ **工作流程** ] 清單中的 [ **工作流程主控台應用程式** ]。</span><span class="sxs-lookup"><span data-stu-id="76e40-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="76e40-115">在 [名稱] `NumberGuessWorkflowHost`**方塊中輸入** ，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="76e40-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="76e40-116">這樣會建立一個具有基本工作流程裝載支援的入門工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="76e40-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="76e40-117">此基本裝載程式碼會修改，並用來執行工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="76e40-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="76e40-118">在 [ **方案總管** ] 中，以滑鼠右鍵按一下新加入的 [ **NumberGuessWorkflowHost** ] 專案，然後選取 [ **加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="76e40-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="76e40-119">選取 [ **加入參考** ] 清單中的 [ **解決方案** ]、勾選 [ **NumberGuessWorkflowActivities**] 旁的核取方塊，然後按一下 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="76e40-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="76e40-120">在 [ **方案總管** ] 中，以滑鼠右鍵按一下 **Workflow1.xaml** ，再選擇 [ **刪除**]。</span><span class="sxs-lookup"><span data-stu-id="76e40-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="76e40-121">按一下 [ **確定** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="76e40-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="76e40-122">修改工作流程裝載程式碼</span><span class="sxs-lookup"><span data-stu-id="76e40-122">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="76e40-123">按兩下 [ **方案總管** ] 中的 [ **Program.cs** ] 或 [ **Module1.vb** ]，顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="76e40-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    >  <span data-ttu-id="76e40-124">如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。</span><span class="sxs-lookup"><span data-stu-id="76e40-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="76e40-125">因為這個專案是使用 [ **工作流程主控台應用程式** ] 範本所建立，所以 [ **Program.cs** ] 或 [ **Module1.vb** ] 會包含下列基本工作流程裝載程式碼。</span><span class="sxs-lookup"><span data-stu-id="76e40-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

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

     <span data-ttu-id="76e40-126">這個所產生的裝載程式碼使用 <xref:System.Activities.WorkflowInvoker>。</span><span class="sxs-lookup"><span data-stu-id="76e40-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="76e40-127"><xref:System.Activities.WorkflowInvoker> 提供一種簡單方法來叫用工作流程，如同方法呼叫一般，但只能用於不使用持續性的工作流程。</span><span class="sxs-lookup"><span data-stu-id="76e40-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="76e40-128"><xref:System.Activities.WorkflowApplication> 提供更豐富的模型，可執行包含生命週期事件通知、執行控制、書籤繼續以及持續性的工作流程。</span><span class="sxs-lookup"><span data-stu-id="76e40-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="76e40-129">此範例會使用書籤且將 <xref:System.Activities.WorkflowApplication> 用於裝載工作流程。</span><span class="sxs-lookup"><span data-stu-id="76e40-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="76e40-130">將下列 `using` 或 **Imports** 陳述式加入至 **Program.cs** 或 **Module1.vb** 上層的現有 **using** 或 **Imports** 陳述式下方。</span><span class="sxs-lookup"><span data-stu-id="76e40-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="76e40-131">使用下列基本 <xref:System.Activities.WorkflowInvoker> 裝載程式碼來取代使用 <xref:System.Activities.WorkflowApplication> 的程式碼字行。</span><span class="sxs-lookup"><span data-stu-id="76e40-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="76e40-132">這個範例裝載程式碼會示範裝載及叫用工作流程的基本步驟，但是尚未包含從這個主題成功執行工作流程的功能。</span><span class="sxs-lookup"><span data-stu-id="76e40-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="76e40-133">在下列步驟中，會修改此基本程式碼，並加入其他功能，直到應用程式完成為止。</span><span class="sxs-lookup"><span data-stu-id="76e40-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="76e40-134">請將`Workflow1`這些範例中的`FlowchartNumberGuessWorkflow`取代`SequentialNumberGuessWorkflow`為、 `StateMachineNumberGuessWorkflow`或, 視您在先前[的 how to:建立工作流程](how-to-create-a-workflow.md)步驟。</span><span class="sxs-lookup"><span data-stu-id="76e40-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="76e40-135">如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="76e40-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="76e40-136">此程式碼會建立 <xref:System.Activities.WorkflowApplication>、訂閱三個工作流程開發週期事件、使用 <xref:System.Activities.WorkflowApplication.Run%2A>的呼叫來啟動工作流程，然後等候工作流程完成。</span><span class="sxs-lookup"><span data-stu-id="76e40-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="76e40-137">當工作流程完成時，會設定 <xref:System.Threading.AutoResetEvent> 且主機應用程式會完成。</span><span class="sxs-lookup"><span data-stu-id="76e40-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="76e40-138">若要設定工作流程的輸入引數</span><span class="sxs-lookup"><span data-stu-id="76e40-138">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="76e40-139">將下列陳述式加入至 **Program.cs** 或 **Module1.vb** 上層的現有 `using` 或 `Imports` 陳述式下方。</span><span class="sxs-lookup"><span data-stu-id="76e40-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="76e40-140">以下列用來建立及傳遞參數字典至所建立之工作流程的程式碼，取代建立新 <xref:System.Activities.WorkflowApplication> 的程式碼字行。</span><span class="sxs-lookup"><span data-stu-id="76e40-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="76e40-141">請將`Workflow1`這些範例中的`FlowchartNumberGuessWorkflow`取代`SequentialNumberGuessWorkflow`為、 `StateMachineNumberGuessWorkflow`或, 視您在先前[的 how to:建立工作流程](how-to-create-a-workflow.md)步驟。</span><span class="sxs-lookup"><span data-stu-id="76e40-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="76e40-142">如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="76e40-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="76e40-143">此字典包含具有 `MaxNumber`索引鍵的一個項目。</span><span class="sxs-lookup"><span data-stu-id="76e40-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="76e40-144">輸入字典中的索引鍵對應至工作流程根活動上的輸入引數。</span><span class="sxs-lookup"><span data-stu-id="76e40-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="76e40-145">工作流程會使用`MaxNumber` 來決定隨機產生的號碼上限。</span><span class="sxs-lookup"><span data-stu-id="76e40-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="76e40-146">若要擷取工作流程的輸出引數</span><span class="sxs-lookup"><span data-stu-id="76e40-146">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="76e40-147">修改 <xref:System.Activities.WorkflowApplication.Completed%2A> 處理常式來擷取與顯示工作流程使用的轉換次數。</span><span class="sxs-lookup"><span data-stu-id="76e40-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="76e40-148">若要繼續書籤</span><span class="sxs-lookup"><span data-stu-id="76e40-148">To resume a bookmark</span></span>

1. <span data-ttu-id="76e40-149">將下列程式碼加入至目前 `Main` 宣告正後方的 <xref:System.Threading.AutoResetEvent> 方法上方。</span><span class="sxs-lookup"><span data-stu-id="76e40-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="76e40-150">將以下的 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式加入至 `Main`中現有三個工作流程開發週期處理常式的正下方。</span><span class="sxs-lookup"><span data-stu-id="76e40-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="76e40-151">每當工作流程變成閒置狀態，等候下一項猜測值時，就會呼叫此處理常式並設定 `idleAction` <xref:System.Threading.AutoResetEvent> 。</span><span class="sxs-lookup"><span data-stu-id="76e40-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="76e40-152">下列步驟中的程式碼會使用 `idleEvent` 和 `syncEvent` 來判斷工作流程是否要等候下一項猜測值或已完成。</span><span class="sxs-lookup"><span data-stu-id="76e40-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="76e40-153">在此範例中，主機應用程式會使用 <xref:System.Activities.WorkflowApplication.Completed%2A> 和 <xref:System.Activities.WorkflowApplication.Idle%2A> 處理常式中的自動重設事件，以同步化主機應用程式與工作流程的進度。</span><span class="sxs-lookup"><span data-stu-id="76e40-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="76e40-154">繼續書籤前，封鎖與等候工作流程變成閒置狀態並非必要的操作，但是在此範例中，必須同步化事件，如此主機才會知道工作流程是否已完成，或是否正在等候更多使用 <xref:System.Activities.Bookmark>的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="76e40-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="76e40-155">如需詳細資訊, 請參閱[書簽](bookmarks.md)。</span><span class="sxs-lookup"><span data-stu-id="76e40-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="76e40-156">移除對 `WaitOne`的呼叫，並以程式碼取代它來收集來自使用者的輸入，並繼續 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="76e40-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="76e40-157">移除下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="76e40-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="76e40-158">以下列範例取代它。</span><span class="sxs-lookup"><span data-stu-id="76e40-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="76e40-159">若要建置及執行應用程式</span><span class="sxs-lookup"><span data-stu-id="76e40-159">To build and run the application</span></span>

1. <span data-ttu-id="76e40-160">在 [ **方案總管** ] 中，以滑鼠右鍵按一下 [ **NumberGuessWorkflowHost** ]，並選取 [ **設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="76e40-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="76e40-161">按 CTRL+F5 建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="76e40-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="76e40-162">盡量以最少的次數嘗試猜測數字。</span><span class="sxs-lookup"><span data-stu-id="76e40-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="76e40-163">若要以工作流程的其他樣式之一來嘗試使用應用程式，請在用來建立 `Workflow1` 的程式碼中，將 <xref:System.Activities.WorkflowApplication> 替換成 `FlowchartNumberGuessWorkflow`、 `SequentialNumberGuessWorkflow`或 `StateMachineNumberGuessWorkflow`，視您想使用的工作流程樣式而定。</span><span class="sxs-lookup"><span data-stu-id="76e40-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="76e40-164">如需如何將持續性加入工作流應用程式的相關指示, 請參閱[下一個主題: 如何:建立並執行長時間執行的](how-to-create-and-run-a-long-running-workflow.md)工作流程。</span><span class="sxs-lookup"><span data-stu-id="76e40-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="76e40-165">範例</span><span class="sxs-lookup"><span data-stu-id="76e40-165">Example</span></span>
 <span data-ttu-id="76e40-166">以下範例是 `Main` 方法的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="76e40-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="76e40-167">請將`Workflow1`這些範例中的`FlowchartNumberGuessWorkflow`取代`SequentialNumberGuessWorkflow`為、 `StateMachineNumberGuessWorkflow`或, 視您在先前[的 how to:建立工作流程](how-to-create-a-workflow.md)步驟。</span><span class="sxs-lookup"><span data-stu-id="76e40-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="76e40-168">如果您不替換 `Workflow1` ，那麼在您嘗試建置或執行工作流程時，會發生建置錯誤。</span><span class="sxs-lookup"><span data-stu-id="76e40-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="76e40-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76e40-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="76e40-170">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="76e40-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="76e40-171">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="76e40-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="76e40-172">如何：建立工作流程</span><span class="sxs-lookup"><span data-stu-id="76e40-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="76e40-173">如何：建立並執行長時間執行的工作流程</span><span class="sxs-lookup"><span data-stu-id="76e40-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="76e40-174">等待工作流程中的輸入</span><span class="sxs-lookup"><span data-stu-id="76e40-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="76e40-175">裝載工作流程</span><span class="sxs-lookup"><span data-stu-id="76e40-175">Hosting Workflows</span></span>](hosting-workflows.md)
