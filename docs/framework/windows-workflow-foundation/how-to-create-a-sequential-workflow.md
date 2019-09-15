---
title: 作法：建立循序工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989696"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="1234b-102">作法：建立循序工作流程</span><span class="sxs-lookup"><span data-stu-id="1234b-102">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="1234b-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="1234b-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="1234b-104">本主題將逐步說明如何建立使用內建活動（例如<xref:System.Activities.Statements.Sequence>活動）的工作流程，以及先前[如何執行的自訂活動：建立活動](how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1234b-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="1234b-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="1234b-105">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="1234b-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="1234b-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="1234b-107">若要完成本主題，您必須先[完成如何：建立活動](how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="1234b-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1234b-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="1234b-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="1234b-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="1234b-109">To create the workflow</span></span>

1. <span data-ttu-id="1234b-110">以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowactivities]** ，然後選取 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="1234b-111">在 [**已安裝**的**通用專案**] 節點中，選取 [**工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="1234b-112">從 [**工作流程**] 清單中選取 [**活動**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="1234b-113">在`SequentialNumberGuessWorkflow` [**名稱**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="1234b-114">從 [**工具箱**] 的 [**控制流程**] 區段，將 [**序列**] 活動拖放到工作流程設計介面上的 [在**此放置活動**] 標籤上。</span><span class="sxs-lookup"><span data-stu-id="1234b-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="1234b-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="1234b-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="1234b-116">按兩下**方案總管**中的 [ **SequentialNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。</span><span class="sxs-lookup"><span data-stu-id="1234b-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="1234b-117">在工作流程設計工具的左下方按一下 [**引數**]，以顯示 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1234b-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="1234b-118">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="1234b-119">在`MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [In]，選取 [自**變數型**別] 下拉式清單**中**的 [ **Int32** ]，然後按下 enter 以儲存引數。</span><span class="sxs-lookup"><span data-stu-id="1234b-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="1234b-120">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="1234b-121">在`Turns`新加入的引數下方輸入 [名稱] 方塊，從 [方向] 下拉式清單中選取 [Out]，選取 [引數型別] 下拉式清單中的 [Int32]，然後按 enter。 `MaxNumber`</span><span class="sxs-lookup"><span data-stu-id="1234b-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="1234b-122">在活動設計工具的左下方按一下 [**引數**]，以關閉 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1234b-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="1234b-123">按一下工作流程設計工具左下方的 [**變數**]，以顯示 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1234b-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="1234b-124">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="1234b-125">如果沒有顯示 [**建立變數**] 方塊，請按一下工作流程設計工具介面上的 [**序列**] 活動加以選取。</span><span class="sxs-lookup"><span data-stu-id="1234b-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="1234b-126">在`Guess` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="1234b-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="1234b-127">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="1234b-128">在`Target` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="1234b-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="1234b-129">在活動設計工具的左下方按一下 [**變數**]，以關閉 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1234b-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="1234b-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="1234b-130">To add the workflow activities</span></span>

1. <span data-ttu-id="1234b-131">將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **Sequence** ] 活動上。</span><span class="sxs-lookup"><span data-stu-id="1234b-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="1234b-132">在`Target` [**到**] 方塊中輸入，並在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="1234b-133">如果沒有顯示 [**工具箱**] 視窗，請從 [**視圖**] 功能表中選取 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="1234b-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="1234b-134">從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **DoWhile** ] 活動拖放到工作流程上，使其位於 [**指派**] 活動下方。</span><span class="sxs-lookup"><span data-stu-id="1234b-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="1234b-135">在 [ **DoWhile** ] 活動的 [ **Condition** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="1234b-136"><xref:System.Activities.Statements.DoWhile> 活動會執行其子活動，然後評估其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。</span><span class="sxs-lookup"><span data-stu-id="1234b-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="1234b-137">如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 判斷值為 `True`，則會再次執行 <xref:System.Activities.Statements.DoWhile> 中的活動。</span><span class="sxs-lookup"><span data-stu-id="1234b-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="1234b-138">此範例中會評估使用者的猜測，而 <xref:System.Activities.Statements.DoWhile> 會繼續，直到猜測正確為止。</span><span class="sxs-lookup"><span data-stu-id="1234b-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="1234b-139">從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，並將它放在上一個步驟的 [ **DoWhile** ] 活動中。</span><span class="sxs-lookup"><span data-stu-id="1234b-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="1234b-140">在 [**屬性] 視窗**中`"EnterGuess"` ，于 [**提示**] 活動的 [ **BookmarkName** ] 屬性值方塊中輸入包含引號。</span><span class="sxs-lookup"><span data-stu-id="1234b-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="1234b-141">在`Guess` [**結果**] 屬性值方塊中輸入，然後在 [ **Text** ] 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="1234b-142">如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="1234b-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="1234b-143">將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **DoWhile** ] 活動中，使其遵循 [**提示**] 活動。</span><span class="sxs-lookup"><span data-stu-id="1234b-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1234b-144">當您卸載 [**指派**] 活動時，請注意工作流程設計工具如何自動加入 [ **Sequence** ] 活動，以同時包含 [**提示**] 活動和新加入的 [**指派**] 活動。</span><span class="sxs-lookup"><span data-stu-id="1234b-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="1234b-145">在`Turns` [**到**] 方塊中`Turns + 1`輸入，然後在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中鍵入。</span><span class="sxs-lookup"><span data-stu-id="1234b-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="1234b-146">從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **If** ] 活動拖放到 [ **Sequence** ] 活動中，使其遵循新加入的 [**指派**] 活動。</span><span class="sxs-lookup"><span data-stu-id="1234b-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="1234b-147">在 [ **If** ] 活動的 [ **Condition** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="1234b-148">從 [**工具箱**] 的 [**控制流程**] 區段中，將另一個 [ **if** ] 活動拖放到第一個 [ **if** ] 活動的 [ **Then** ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="1234b-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="1234b-149">在新加入的 [ **If** ] 活動的 [ **Condition** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="1234b-150">從 [**工具箱**] 的 [**基本**] 區段拖放兩個 [ **WriteLine** ] 活動，使其成為新加入之 [ **If** ] 活動的 [ **Then** ] 區段，另一個則位於 [ **Else** ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="1234b-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="1234b-151">按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="1234b-152">按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="1234b-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="1234b-153">下列範例說明完成的工作流程：</span><span class="sxs-lookup"><span data-stu-id="1234b-153">The following example illustrates the completed workflow:</span></span>

     ![顯示已完成之順序工作流程的螢幕擷取畫面。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="1234b-155">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="1234b-155">To build the workflow</span></span>

1. <span data-ttu-id="1234b-156">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="1234b-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="1234b-157">如需有關如何執行工作流程的指示，請參閱下一個主題[：如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="1234b-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="1234b-158">如果您已經完成[如何：以不同的](how-to-run-a-workflow.md)工作流程樣式執行工作流程步驟，並想要使用此步驟中的順序工作流程執行它，請直接跳[[至如何：](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="1234b-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1234b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1234b-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="1234b-160">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="1234b-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="1234b-161">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="1234b-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="1234b-162">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="1234b-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="1234b-163">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="1234b-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="1234b-164">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="1234b-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
