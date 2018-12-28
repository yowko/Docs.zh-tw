---
title: HOW TO：建立自訂追蹤參與者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 74c0e8ac025d69f0fd1ee7d451033165a1c8e615
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611851"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="6cacb-102">HOW TO：建立自訂追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="6cacb-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="6cacb-103">工作流程追蹤會提供工作流程執行狀態的可見性。</span><span class="sxs-lookup"><span data-stu-id="6cacb-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="6cacb-104">工作流程執行階段會發出追蹤記錄，其中描述工作流程開發週期事件、活動開發週期事件、書籤繼續及錯誤。</span><span class="sxs-lookup"><span data-stu-id="6cacb-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="6cacb-105">這些追蹤記錄由追蹤參與者使用。</span><span class="sxs-lookup"><span data-stu-id="6cacb-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="6cacb-106">Windows Workflow Foundation (WF) 包含寫入追蹤記錄當做事件追蹤的 Windows (ETW) 事件的標準追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="6cacb-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="6cacb-107">如果不符合需求，您也可以寫入自訂的追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="6cacb-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="6cacb-108">本教學課程步驟描述如何建立擷取 `WriteLine` 活動輸出的自訂追蹤參與者和追蹤設定檔，以便向使用者顯示這些項目。</span><span class="sxs-lookup"><span data-stu-id="6cacb-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cacb-109">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="6cacb-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6cacb-110">若要完成此主題，您必須先完成之前的主題。</span><span class="sxs-lookup"><span data-stu-id="6cacb-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="6cacb-111">若要下載完整的版或觀看視訊逐步解說教學課程，請參閱[Windows Workflow Foundation (WF45)-入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="6cacb-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="6cacb-112">建立自訂追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="6cacb-112">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="6cacb-113">以滑鼠右鍵按一下**NumberGuessWorkflowHost**中**方案總管**，然後選擇 **新增**，**類別**。</span><span class="sxs-lookup"><span data-stu-id="6cacb-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="6cacb-114">型別`StatusTrackingParticipant`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="6cacb-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="6cacb-115">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6cacb-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="6cacb-116">修改 `StatusTrackingParticipant` 類別，使其繼承 `TrackingParticipant`。</span><span class="sxs-lookup"><span data-stu-id="6cacb-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  <span data-ttu-id="6cacb-117">加入下列 `Track` 方法覆寫。</span><span class="sxs-lookup"><span data-stu-id="6cacb-117">Add the following `Track` method override.</span></span> <span data-ttu-id="6cacb-118">追蹤記錄有多種不同型別。</span><span class="sxs-lookup"><span data-stu-id="6cacb-118">There are several different types of tracking records.</span></span> <span data-ttu-id="6cacb-119">我們對於 `WriteLine` 活動的輸出感興趣，該輸出包含在活動追蹤記錄中。</span><span class="sxs-lookup"><span data-stu-id="6cacb-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="6cacb-120">如果 `TrackingRecord` 是 `ActivityTrackingRecord` 活動的 `WriteLine`，則 `Text` 的 `WriteLine` 會附加在工作流程中以 `InstanceId` 命名的檔案裡。</span><span class="sxs-lookup"><span data-stu-id="6cacb-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="6cacb-121">在本教學課程中，該檔案儲存在主應用程式目前的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6cacb-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="6cacb-122">未指定任何追蹤設定檔時，會使用預設的追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="6cacb-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="6cacb-123">使用預設追蹤設定檔時，會發出所有 `ActivityStates` 的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="6cacb-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="6cacb-124">因為我們只需要擷取 `WriteLine` 活動開發週期當中某個時間的文字，我們只能從 `ActivityStates.Executing` 狀態擷取該文字。</span><span class="sxs-lookup"><span data-stu-id="6cacb-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="6cacb-125">在 [建立追蹤設定檔並註冊追蹤參與者](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)，會建立追蹤設定檔，只指定`WriteLine``ActivityStates.Executing`時會發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="6cacb-125">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="6cacb-126">建立追蹤設定檔並註冊追蹤參與者</span><span class="sxs-lookup"><span data-stu-id="6cacb-126">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="6cacb-127">以滑鼠右鍵按一下**WorkflowHostForm**中**方案總管**，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="6cacb-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="6cacb-128">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6cacb-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="6cacb-129">將下列程式碼加入至 `ConfigureWorkflowApplication`，就在將 `StringWriter` 加入至工作流程擴充的程式碼之後、工作流程開發週期處理常式之前。</span><span class="sxs-lookup"><span data-stu-id="6cacb-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="6cacb-130">此追蹤設定檔指定將 `WriteLine` 狀態之 `Executing` 活動的唯一活動狀態記錄發出給自訂追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="6cacb-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="6cacb-131">加入程式碼後，`ConfigureWorkflowApplication` 的最上方看起來如下所示。</span><span class="sxs-lookup"><span data-stu-id="6cacb-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="6cacb-132">顯示追蹤資訊</span><span class="sxs-lookup"><span data-stu-id="6cacb-132">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="6cacb-133">以滑鼠右鍵按一下**WorkflowHostForm**中**方案總管**，然後選擇 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="6cacb-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="6cacb-134">在 `InstanceId_SelectedIndexChanged` 處理常式中，將下列程式碼加入至清除狀態視窗的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="6cacb-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="6cacb-135">在工作流程清單中選取新的工作流程時，會載入該工作流程的追蹤記錄並顯示在狀態視窗中。</span><span class="sxs-lookup"><span data-stu-id="6cacb-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="6cacb-136">下列範例是已完成的 `InstanceId_SelectedIndexChanged` 處理常式。</span><span class="sxs-lookup"><span data-stu-id="6cacb-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="6cacb-137">若要建置及執行應用程式</span><span class="sxs-lookup"><span data-stu-id="6cacb-137">To build and run the application</span></span>  
  
1.  <span data-ttu-id="6cacb-138">按 Ctrl+Shift+B 建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="6cacb-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="6cacb-139">按 Ctrl + F5 啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="6cacb-139">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="6cacb-140">選取的範圍猜測遊戲和要開始，然後按一下 工作流程的型別**新遊戲**。</span><span class="sxs-lookup"><span data-stu-id="6cacb-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="6cacb-141">輸入在猜測**猜測**方塊，然後按一下**移**提交猜測。</span><span class="sxs-lookup"><span data-stu-id="6cacb-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="6cacb-142">請注意，工作流程的狀態會顯示在狀態視窗中。</span><span class="sxs-lookup"><span data-stu-id="6cacb-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="6cacb-143">此輸出是從 `WriteLine` 活動擷取的。</span><span class="sxs-lookup"><span data-stu-id="6cacb-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="6cacb-144">切換至不同的工作流程中，選取其中一項從**工作流程執行個體識別碼**下拉式方塊，並請注意，也會移除目前的工作流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="6cacb-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="6cacb-145">切換回上一個工作流程，注意其狀態已還原，類似下列範例。</span><span class="sxs-lookup"><span data-stu-id="6cacb-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6cacb-146">如果您切換的工作流程在啟用追蹤之前就已經啟動，就不會顯示任何狀態。</span><span class="sxs-lookup"><span data-stu-id="6cacb-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="6cacb-147">但是，如果您做其他猜測，會儲存這些猜測的狀態，因為現在已啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="6cacb-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="6cacb-148">此資訊可用於判斷隨機數字的範圍，但不包含任何先前猜測的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6cacb-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="6cacb-149">這項資訊會在下一個步驟中， [How to:裝載的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="6cacb-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="6cacb-150">請記下工作流程執行個體識別碼，並玩遊戲直到結束。</span><span class="sxs-lookup"><span data-stu-id="6cacb-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4.  <span data-ttu-id="6cacb-151">開啟 Windows 檔案總管並瀏覽至**NumberGuessWorkflowHost\bin\debug**資料夾 (或**bin\release**取決於您的專案設定)。</span><span class="sxs-lookup"><span data-stu-id="6cacb-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="6cacb-152">請注意，除了專案可執行檔外，還有些檔案具有 guid 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6cacb-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="6cacb-153">在上一步驟完成的工作流程中，找出對應工作流程執行個體識別碼的檔案，並在 [記事本] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="6cacb-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="6cacb-154">追蹤資訊包含如下的類似資訊。</span><span class="sxs-lookup"><span data-stu-id="6cacb-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="6cacb-155">除了使用者沒有猜測的情況外，此追蹤資料也不包含工作流程最後猜測的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6cacb-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="6cacb-156">這是因為追蹤資訊僅包含工作流程的 `WriteLine` 輸出，在工作流程完成後顯示的最後一個訊息，是由 `Completed` 處理常式完成的。</span><span class="sxs-lookup"><span data-stu-id="6cacb-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="6cacb-157">在下一個步驟的教學課程中， [How to:裝載多個版本的工作流程-並存](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)，現有`WriteLine`活動會修改成顯示該使用者的猜測和額外`WriteLine`活動加入顯示最終的結果。</span><span class="sxs-lookup"><span data-stu-id="6cacb-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="6cacb-158">整合這些變更之後， [How to:裝載的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)示範如何同時裝載工作流程的多個版本。</span><span class="sxs-lookup"><span data-stu-id="6cacb-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
