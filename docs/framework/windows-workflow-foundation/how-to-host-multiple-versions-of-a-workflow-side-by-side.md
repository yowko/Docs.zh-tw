---
title: HOW TO：裝載工作流程並存的多個版本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
ms.openlocfilehash: 525aeab7ff08da95735e9c9df7f6f040e8b9e215
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558422"
---
# <a name="how-to-host-multiple-versions-of-a-workflow-side-by-side"></a><span data-ttu-id="e97a2-102">HOW TO：裝載工作流程並存的多個版本</span><span class="sxs-lookup"><span data-stu-id="e97a2-102">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>
<span data-ttu-id="e97a2-103">`WorkflowIdentity` 提供一種方法，讓工作流程應用程式開發人員能夠將名稱和版本與工作流程定義產生關聯性，並為這項資訊與持續性工作流程執行個體建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="e97a2-103">`WorkflowIdentity` provides a way for workflow application developers to associate a name and a version with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="e97a2-104">此身分識別資訊可由工作流程應用程式開發人員使用以啟用案例 (例如並存執行多個版本的工作流程定義)，以及提供動態更新等其他功能的基礎。</span><span class="sxs-lookup"><span data-stu-id="e97a2-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="e97a2-105">教學課程中的此步驟示範如何使用 `WorkflowIdentity` 同時裝載工作流程的多個版本。</span><span class="sxs-lookup"><span data-stu-id="e97a2-105">This step in the tutorial demonstrates how to use `WorkflowIdentity` to host multiple versions of a workflow at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e97a2-106">若要下載完整的版或觀看視訊逐步解說教學課程，請參閱[Windows Workflow Foundation (WF45)-入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="e97a2-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="e97a2-107">本主題內容</span><span class="sxs-lookup"><span data-stu-id="e97a2-107">In this topic</span></span>  
 <span data-ttu-id="e97a2-108">在教學課程的這個步驟中，會修改工作流程的 `WriteLine` 活動以提供其他資訊，並新增 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="e97a2-108">In this step of the tutorial, the `WriteLine` activities in the workflow are modified to provide additional information, and a new `WriteLine` activity is added.</span></span> <span data-ttu-id="e97a2-109">我們會儲存原始工作流程組件的複本，並更新主應用程式，以便同時執行原始和更新的工作流程。</span><span class="sxs-lookup"><span data-stu-id="e97a2-109">A copy of the original workflow assembly is stored, and the host application is updated so that it can run both the original and the updated workflows at the same time.</span></span>  
  
-   [<span data-ttu-id="e97a2-110">製作 NumberGuessWorkflowActivities 專案的複本</span><span class="sxs-lookup"><span data-stu-id="e97a2-110">To make a copy of the NumberGuessWorkflowActivities project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [<span data-ttu-id="e97a2-111">更新工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-111">To update the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [<span data-ttu-id="e97a2-112">若要更新的狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-112">To update the StateMachine workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [<span data-ttu-id="e97a2-113">更新流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-113">To update the Flowchart workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [<span data-ttu-id="e97a2-114">若要更新循序工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-114">To update the Sequential workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [<span data-ttu-id="e97a2-115">若要更新 WorkflowVersionMap 以包含舊版的工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-115">To update WorkflowVersionMap to include the previous workflow versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="e97a2-116">若要建置並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="e97a2-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  <span data-ttu-id="e97a2-117">依照本主題中的步驟進行之前，請執行應用程式、啟動每種型別的數個工作流程，然後針對每個工作流程進行一或兩次猜測。</span><span class="sxs-lookup"><span data-stu-id="e97a2-117">Before following the steps in this topic, run the application, start several workflows of each type, and making one or two guesses for each one.</span></span> <span data-ttu-id="e97a2-118">在此步驟和下一個步驟，使用這些保存的工作流程[如何： 更新執行的工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a2-118">These persisted workflows are used in this step and the following step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e97a2-119">「快速入門教學課程」中的每個步驟都與之前的步驟息息相關。</span><span class="sxs-lookup"><span data-stu-id="e97a2-119">Each step in the Getting Started tutorial depends on the previous steps.</span></span> <span data-ttu-id="e97a2-120">如果您未完成上述步驟，您就可以下載完整的版的教學課程[Windows Workflow Foundation (WF45)-入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="e97a2-120">If you did not complete the previous steps you can download a completed version of the tutorial from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
###  <a name="BKMK_BackupCopy"></a> <span data-ttu-id="e97a2-121">製作 NumberGuessWorkflowActivities 專案的複本</span><span class="sxs-lookup"><span data-stu-id="e97a2-121">To make a copy of the NumberGuessWorkflowActivities project</span></span>  
  
1.  <span data-ttu-id="e97a2-122">開啟**WF45GettingStartedTutorial**中的解決方案[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]如果尚未開啟。</span><span class="sxs-lookup"><span data-stu-id="e97a2-122">Open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] if it is not open.</span></span>  
  
2.  <span data-ttu-id="e97a2-123">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="e97a2-123">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="e97a2-124">關閉**WF45GettingStartedTutorial**解決方案。</span><span class="sxs-lookup"><span data-stu-id="e97a2-124">Close the **WF45GettingStartedTutorial** solution.</span></span>  
  
4.  <span data-ttu-id="e97a2-125">開啟 [Windows 檔案總管]，並巡覽至教學課程方案檔和專案資料夾所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e97a2-125">Open Windows Explorer and navigate to the folder where the tutorial solution file and the project folders are located.</span></span>  
  
5.  <span data-ttu-id="e97a2-126">建立新的資料夾，名為**PreviousVersions**相同的資料夾中**NumberGuessWorkflowHost**並**NumberGuessWorkflowActivities**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-126">Create a new folder named **PreviousVersions** in the same folder as **NumberGuessWorkflowHost** and **NumberGuessWorkflowActivities**.</span></span> <span data-ttu-id="e97a2-127">此資料夾用來儲存組件，這些組件包含在後續教學課程步驟中使用的不同工作流程版本。</span><span class="sxs-lookup"><span data-stu-id="e97a2-127">This folder is used to contain the assemblies that contain the different versions of the workflows used in the subsequent tutorial steps.</span></span>  
  
6.  <span data-ttu-id="e97a2-128">瀏覽至**NumberGuessWorkflowActivities\bin\debug**資料夾 (或**bin\release**取決於您的專案設定)。</span><span class="sxs-lookup"><span data-stu-id="e97a2-128">Navigate to the **NumberGuessWorkflowActivities\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="e97a2-129">複製**NumberGuessWorkflowActivities.dll**將它貼到**PreviousVersions**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e97a2-129">Copy **NumberGuessWorkflowActivities.dll** and paste it into the **PreviousVersions** folder.</span></span>  
  
7.  <span data-ttu-id="e97a2-130">重新命名**NumberGuessWorkflowActivities.dll**中**PreviousVersions**資料夾**NumberGuessWorkflowActivities_v1.dll**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-130">Rename **NumberGuessWorkflowActivities.dll** in the **PreviousVersions** folder to **NumberGuessWorkflowActivities_v1.dll**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e97a2-131">本主題中的步驟示範管理組件的方法，這些組件用於包含多個工作流程版本。</span><span class="sxs-lookup"><span data-stu-id="e97a2-131">The steps in this topic demonstrate one way to manage the assemblies used to contain multiple versions of the workflows.</span></span> <span data-ttu-id="e97a2-132">您也可以使用其他方法，例如強式命名組件以及在全域組件快取中登錄這些組件。</span><span class="sxs-lookup"><span data-stu-id="e97a2-132">Other methods such as strong naming the assemblies and registering them in the global assembly cache could also be used.</span></span>  
  
8.  <span data-ttu-id="e97a2-133">建立新的資料夾，名為**NumberGuessWorkflowActivities_du**相同的資料夾中**NumberGuessWorkflowHost**， **NumberGuessWorkflowActivities**，而新新增**PreviousVersions**資料夾，並複製所有檔案和子**NumberGuessWorkflowActivities**到新的資料夾**NumberGuessWorkflowActivities_du**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e97a2-133">Create a new folder named **NumberGuessWorkflowActivities_du** in the same folder as **NumberGuessWorkflowHost**, **NumberGuessWorkflowActivities**, and the newly added **PreviousVersions** folder, and copy all of the files and subfolders from the **NumberGuessWorkflowActivities** folder into the new **NumberGuessWorkflowActivities_du** folder.</span></span> <span data-ttu-id="e97a2-134">此活動的初始版本之專案的備份副本會在[如何： 更新執行的工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a2-134">This backup copy of the project for the initial version of the activities is used in [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).</span></span>  
  
9. <span data-ttu-id="e97a2-135">重新開啟**WF45GettingStartedTutorial**中的解決方案[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e97a2-135">Re-open the **WF45GettingStartedTutorial** solution in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
###  <a name="BKMK_UpdateWorkflows"></a> <span data-ttu-id="e97a2-136">更新工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-136">To update the workflows</span></span>  
 <span data-ttu-id="e97a2-137">本節已更新工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="e97a2-137">In this section, the workflow definitions are updated.</span></span> <span data-ttu-id="e97a2-138">已更新回應使用者猜測的兩個 `WriteLine` 活動，並新增可在猜測數字後提供遊戲其他相關資訊的 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="e97a2-138">The two `WriteLine` activities that give feedback on the user's guess are updated, and a new `WriteLine` activity is added that provides additional information about the game once the number is guessed.</span></span>  
  
####  <a name="BKMK_UpdateStateMachine"></a> <span data-ttu-id="e97a2-139">若要更新的狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-139">To update the StateMachine workflow</span></span>  
  
1.  <span data-ttu-id="e97a2-140">在 **方案總管**下方**NumberGuessWorkflowActivities**專案中，按兩下**StateMachineNumberGuessWorkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-140">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **StateMachineNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e97a2-141">按兩下**猜測不正確**狀態機器上的轉換。</span><span class="sxs-lookup"><span data-stu-id="e97a2-141">Double-click the **Guess Incorrect** transition on the state machine.</span></span>  
  
3.  <span data-ttu-id="e97a2-142">更新 `Text` 活動中最左邊 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-142">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  <span data-ttu-id="e97a2-143">更新 `Text` 活動中最右邊 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-143">Update the `Text` of the right-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  <span data-ttu-id="e97a2-144">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="e97a2-144">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
6.  <span data-ttu-id="e97a2-145">按兩下**猜測正確**狀態機器上的轉換。</span><span class="sxs-lookup"><span data-stu-id="e97a2-145">Double-click the **Guess Correct** transition on the state machine.</span></span>  
  
7.  <span data-ttu-id="e97a2-146">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**並將它放在**置放動作活動**的標籤轉換。</span><span class="sxs-lookup"><span data-stu-id="e97a2-146">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the **Drop Action activity here** label of the transition.</span></span>  
  
8.  <span data-ttu-id="e97a2-147">在 `Text` 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="e97a2-147">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a> <span data-ttu-id="e97a2-148">更新流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-148">To update the Flowchart workflow</span></span>  
  
1.  <span data-ttu-id="e97a2-149">在 **方案總管**下方**NumberGuessWorkflowActivities**專案中，按兩下**FlowchartNumberGuessWorkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-149">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **FlowchartNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e97a2-150">更新最左邊 `Text` 活動的 `WriteLine`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-150">Update the `Text` of the left-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="e97a2-151">更新最右邊 `Text` 活動的 `WriteLine`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-151">Update the `Text` of the right-most `WriteLine` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="e97a2-152">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖放上的置放點`True`動作的最上方`FlowDecision`.</span><span class="sxs-lookup"><span data-stu-id="e97a2-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it on the drop point of the `True` action of the topmost `FlowDecision`.</span></span> <span data-ttu-id="e97a2-153">`WriteLine` 活動會加入到流程圖中，並連結至 `True` 動作的 `FlowDecision`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-153">The `WriteLine` activity is added to the flowchart and linked to the `True` action of the `FlowDecision`.</span></span>  
  
5.  <span data-ttu-id="e97a2-154">在 `Text` 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="e97a2-154">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a> <span data-ttu-id="e97a2-155">若要更新循序工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-155">To update the Sequential workflow</span></span>  
  
1.  <span data-ttu-id="e97a2-156">在 **方案總管**下方**NumberGuessWorkflowActivities**專案中，按兩下**SequentialNumberGuessWorkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-156">In **Solution Explorer**, under the **NumberGuessWorkflowActivities** project, double-click **SequentialNumberGuessWorkflow.xaml**.</span></span>  
  
2.  <span data-ttu-id="e97a2-157">更新 `Text` 活動中最左邊 `WriteLine` 的 `If`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-157">Update the `Text` of the left-most `WriteLine` in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  <span data-ttu-id="e97a2-158">更新 `Text` 活動中最右邊 `WriteLine` 活動的 `If`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-158">Update the `Text` of the right-most `WriteLine` activity in the `If` activity.</span></span>  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  <span data-ttu-id="e97a2-159">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**之後**DoWhile**活動以便**WriteLine**會在根目錄中的最後一個活動`Sequence`活動。</span><span class="sxs-lookup"><span data-stu-id="e97a2-159">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it after the **DoWhile** activity so that the **WriteLine** is the final activity in the root `Sequence` activity.</span></span>  
  
5.  <span data-ttu-id="e97a2-160">在 `Text` 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="e97a2-160">Type the following expression into the `Text` property box.</span></span>  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="e97a2-161">若要更新 WorkflowVersionMap 以包含舊版的工作流程</span><span class="sxs-lookup"><span data-stu-id="e97a2-161">To update WorkflowVersionMap to include the previous workflow versions</span></span>  
  
1.  <span data-ttu-id="e97a2-162">按兩下**Numberguessworkflowhost** (或**Workflowversionmap.cs**) 底下**NumberGuessWorkflowHost**專案加以開啟。</span><span class="sxs-lookup"><span data-stu-id="e97a2-162">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
2.  <span data-ttu-id="e97a2-163">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e97a2-163">Add the following `using` (or `Imports`) statements to the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="e97a2-164">將三個新的工作流程識別加入到三個現有工作流程識別宣告的正下方。</span><span class="sxs-lookup"><span data-stu-id="e97a2-164">Add three new workflow identities just below the three existing workflow identity declarations.</span></span> <span data-ttu-id="e97a2-165">這些新的 `v1` 工作流程識別將用來針對在更新前啟動之工作流程，提供正確的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="e97a2-165">These new `v1` workflow identities will be used provide the correct workflow definition to workflows started before the updates were made.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 Identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
    ```  
  
    ```csharp  
    // Current version identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity;  
    static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
    // v1 identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
    ```  
  
4.  <span data-ttu-id="e97a2-166">在 `WorkflowVersionMap` 建構函式中，將三個目前工作流程識別的 `Version` 屬性更新為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="e97a2-166">In the `WorkflowVersionMap` constructor, update the `Version` property of the three current workflow identities to `2.0.0.0`.</span></span>  
  
    ```vb  
    'Add the current workflow version identities.  
    StateMachineNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(2, 0, 0, 0)  
    }  
  
    map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
    map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
    map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
    ```  
  
    ```csharp  
    // Add the current workflow version identities.  
    StateMachineNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        // Version = new Version(1, 0, 0, 0),  
        Version = new Version(2, 0, 0, 0)  
    };  
  
    map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
    map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
    map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
    ```  
  
     <span data-ttu-id="e97a2-167">將目前工作流程版本加入到字典中的程式碼會使用專案中參考的目前版本，因此您不需要更新初始化工作流程定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e97a2-167">The code in that adds the current versions of the workflows to the dictionary uses the current versions that are referenced in the project, so the code that initializes the workflow definitions does not need to be updated.</span></span>  
  
5.  <span data-ttu-id="e97a2-168">將下列程式碼加入到建構函式中，放在將目前版本加入到字典中的程式碼之後。</span><span class="sxs-lookup"><span data-stu-id="e97a2-168">Add the following code in the constructor just after the code that adds the current versions to the dictionary.</span></span>  
  
    ```vb  
    'Initialize the previous workflow version identities.  
    StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 0, 0, 0)  
    }  
    ```  
  
    ```csharp  
    // Initialize the previous workflow version identities.  
    StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    };  
    ```  
  
     <span data-ttu-id="e97a2-169">這些工作流程識別都與對應工作流程定義的初始版本相關聯。</span><span class="sxs-lookup"><span data-stu-id="e97a2-169">These workflow identities are associated with the initial versions of the corresponding workflow definitions.</span></span>  
  
6.  <span data-ttu-id="e97a2-170">接下來，載入包含工作流程定義初始版本的組件，建立對應的工作流程定義並將其加入到字典中。</span><span class="sxs-lookup"><span data-stu-id="e97a2-170">Next, load the assembly that contains the initial version of the workflow definitions, and create and add the corresponding workflow definitions to the dictionary.</span></span>  
  
    ```vb  
    'Add the previous version workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v1 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
    Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Add the previous version workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v1 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
    v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
    Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v1,  
        v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     <span data-ttu-id="e97a2-171">以下範例是更新之 `WorkflowVersionMap` 類別的完整清單。</span><span class="sxs-lookup"><span data-stu-id="e97a2-171">The following example is the complete listing for the updated `WorkflowVersionMap` class.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 Identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
  
            'Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            'Add the previous version workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v1 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        // v1 identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
  
            // Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            // Add the previous version workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v1 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {  
            return identity.ToString();  
        }  
    }  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="e97a2-172">若要建置並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="e97a2-172">To build and run the application</span></span>  
  
1.  <span data-ttu-id="e97a2-173">按下 CTRL+SHIFT+B 建置應用程式，然後按下 CTRL+F5 啟動。</span><span class="sxs-lookup"><span data-stu-id="e97a2-173">Press CTRL+SHIFT+B to build the application, and then CTRL+F5 to start.</span></span>  
  
2.  <span data-ttu-id="e97a2-174">按一下 啟動新的工作流程**新遊戲**。</span><span class="sxs-lookup"><span data-stu-id="e97a2-174">Start a new workflow by clicking **New Game**.</span></span> <span data-ttu-id="e97a2-175">工作流程的版本會顯示在狀態視窗下，反映從相關聯的 `WorkflowIdentity` 更新的版本。</span><span class="sxs-lookup"><span data-stu-id="e97a2-175">The version of the workflow is displayed under the status window and reflects the updated version from the associated `WorkflowIdentity`.</span></span> <span data-ttu-id="e97a2-176">記下 `InstanceId`，當工作流程完成時，您就可以檢視該工作流程的追蹤檔案，然後輸入猜測直到遊戲完成為止。</span><span class="sxs-lookup"><span data-stu-id="e97a2-176">Make a note of the `InstanceId` so you can view the tracking file for the workflow when it completes, and then enter guesses until the game is complete.</span></span> <span data-ttu-id="e97a2-177">請注意，狀態視窗中所顯示的使用者猜測資訊，會以 `WriteLine` 活動的更新為根據。</span><span class="sxs-lookup"><span data-stu-id="e97a2-177">Note how the user's guess is displayed in the information displayed in the status window based on the updates to the `WriteLine` activities.</span></span>  
  
 <span data-ttu-id="e97a2-178">**請輸入介於 1 到 10 之間的數字**</span><span class="sxs-lookup"><span data-stu-id="e97a2-178">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e97a2-179">**5 是太高。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-179">**5 is too high.** </span></span>  
<span data-ttu-id="e97a2-180">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-180">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-181">**3 是太高。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-181">**3 is too high.** </span></span>  
<span data-ttu-id="e97a2-182">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-182">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-183">**1 是過低。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-183">**1 is too low.** </span></span>  
<span data-ttu-id="e97a2-184">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-184">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-185">**恭喜，您猜數字到 4。**</span><span class="sxs-lookup"><span data-stu-id="e97a2-185">**Congratulations, you guessed the number in 4 turns.**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="e97a2-186">即會顯示從 `WriteLine` 活動更新的文字，但不會顯示本主題中最後加入的 `WriteLine` 活動的輸出。</span><span class="sxs-lookup"><span data-stu-id="e97a2-186">The updated text from the `WriteLine` activities is displayed, but the output of the final `WriteLine` activity that was added in this topic is not.</span></span> <span data-ttu-id="e97a2-187">這是因為狀態視窗是由 `PersistableIdle` 處理常式更新的。</span><span class="sxs-lookup"><span data-stu-id="e97a2-187">That is because the status window is updated by the `PersistableIdle` handler.</span></span> <span data-ttu-id="e97a2-188">由於工作流程已完成且不會在最後一個活動之後閒置，因此不會呼叫 `PersistableIdle` 處理常式。</span><span class="sxs-lookup"><span data-stu-id="e97a2-188">Because the workflow completes and does not go idle after the final activity, the `PersistableIdle` handler is not called.</span></span> <span data-ttu-id="e97a2-189">但是，`Completed` 處理常式會在狀態視窗顯示類似的訊息。</span><span class="sxs-lookup"><span data-stu-id="e97a2-189">However, a similar message is displayed in the status window by the `Completed` handler.</span></span> <span data-ttu-id="e97a2-190">如果需要，可以將程式碼加入到 `Completed` 處理常式，從 `StringWriter` 擷取文字並將其顯示在狀態視窗中。</span><span class="sxs-lookup"><span data-stu-id="e97a2-190">If desired, code could be added to the `Completed` handler to extract the text from the `StringWriter` and display it to the status window.</span></span>  
  
3.  <span data-ttu-id="e97a2-191">開啟 Windows 檔案總管並瀏覽至**NumberGuessWorkflowHost\bin\debug**資料夾 (或**bin\release**取決於您的專案設定)，並開啟追蹤檔案使用對應的 [記事本]若要完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="e97a2-191">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="e97a2-192">如果您未進行記`InstanceId`，您可以使用，以識別正確的追蹤檔案**修改日期**Windows 檔案總管中的資訊。</span><span class="sxs-lookup"><span data-stu-id="e97a2-192">If you did not make a note of the `InstanceId`, you can identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span>  
  
 <span data-ttu-id="e97a2-193">**請輸入介於 1 到 10 之間的數字**</span><span class="sxs-lookup"><span data-stu-id="e97a2-193">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="e97a2-194">**5 是太高。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-194">**5 is too high.** </span></span>  
<span data-ttu-id="e97a2-195">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-195">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-196">**3 是太高。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-196">**3 is too high.** </span></span>  
<span data-ttu-id="e97a2-197">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-197">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-198">**1 是過低。** </span><span class="sxs-lookup"><span data-stu-id="e97a2-198">**1 is too low.** </span></span>  
<span data-ttu-id="e97a2-199">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="e97a2-199">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="e97a2-200">**2 是正確的。您猜猜看 4。**</span><span class="sxs-lookup"><span data-stu-id="e97a2-200">**2 is correct. You guessed it in 4 turns.**</span></span>      <span data-ttu-id="e97a2-201">追蹤檔中包含更新的 `WriteLine` 輸出，包括在本主題中加入之 `WriteLine` 的輸出。</span><span class="sxs-lookup"><span data-stu-id="e97a2-201">The updated `WriteLine` output is contained within the tracking file, including the output of the `WriteLine` that was added in this topic.</span></span>  
  
4.  <span data-ttu-id="e97a2-202">切換回猜數字應用程式，並選取其中一個在更新之前啟動的工作流程。</span><span class="sxs-lookup"><span data-stu-id="e97a2-202">Switch back to the number guessing application and select one of the workflows that was started before the updates were made.</span></span> <span data-ttu-id="e97a2-203">您可以查看顯示在狀態視窗下方的版本資訊，找出目前選取之工作流程的版本。</span><span class="sxs-lookup"><span data-stu-id="e97a2-203">You can identify the version of the currently selected workflow by looking at the version information that is displayed below the status window.</span></span> <span data-ttu-id="e97a2-204">輸入一些猜測，請注意，狀態更新會比對 `WriteLine` 活動輸出與舊版的輸出，而且不包含使用者的猜測。</span><span class="sxs-lookup"><span data-stu-id="e97a2-204">Enter some guesses and note that the status updates match the `WriteLine` activity output from the previous version, and do not include the user's guess.</span></span> <span data-ttu-id="e97a2-205">這是因為這些工作流程使用的舊版工作流程定義不含 `WriteLine` 更新。</span><span class="sxs-lookup"><span data-stu-id="e97a2-205">That is because these workflows are using the previous workflow definition that does not have the `WriteLine` updates.</span></span>  
  
     <span data-ttu-id="e97a2-206">在下一個步驟中，[如何： 更新執行的工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)，執行`v1`使其包含與新的功能，會更新工作流程執行個體`v2`執行個體。</span><span class="sxs-lookup"><span data-stu-id="e97a2-206">In the next step, [How to: Update the Definition of a Running Workflow Instance](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md), the running `v1` workflow instances are updated so they contain the new functionality as the `v2` instances.</span></span>
