---
title: 作法：建立循序工作流程
description: 本文所建立的工作流程會使用這兩個內建活動，例如 Sequence 活動和自訂活動。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 0c47290d11770a094fb09bcb4dc34aee1e4371a9
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190516"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="01efe-103">作法：建立循序工作流程</span><span class="sxs-lookup"><span data-stu-id="01efe-103">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="01efe-104">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="01efe-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="01efe-105">本主題逐步解說如何建立工作流程，此工作流程會使用活動等內建活動 <xref:System.Activities.Statements.Sequence> ，以及先前的 how [To：建立活動](how-to-create-an-activity.md) 主題的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="01efe-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="01efe-106">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="01efe-106">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="01efe-107">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="01efe-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="01efe-108">若要完成本主題，您必須先完成 [如何：建立活動](how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="01efe-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="01efe-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="01efe-109">To create the workflow</span></span>

1. <span data-ttu-id="01efe-110">以滑鼠右鍵按一下 **方案總管** 中的 **[numberguessworkflowactivities]** **，然後選取 [** 新增]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="01efe-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="01efe-111">在 [ **已安裝** 的 **一般專案** ] 節點中，選取 [ **工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="01efe-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="01efe-112">從 **[工作流程]** 清單中選取 **[活動]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="01efe-113">`SequentialNumberGuessWorkflow`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="01efe-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="01efe-114">從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **Sequence** ] 活動拖放到工作流程設計介面上的 [在 **此放置活動**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="01efe-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="01efe-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="01efe-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="01efe-116">按兩下 **方案總管** 中的 [ **SequentialNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。</span><span class="sxs-lookup"><span data-stu-id="01efe-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="01efe-117">在工作流程設計工具的左下方按一下 [ **引數** ]，以顯示 [ **引數** ] 窗格。</span><span class="sxs-lookup"><span data-stu-id="01efe-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="01efe-118">按一下 **[建立引數]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="01efe-119">在 `MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [加入]，從 [**引數類型**] 下拉式清單 **中** 選取 [ **Int32** ]，然後按 enter 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="01efe-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="01efe-120">按一下 **[建立引數]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="01efe-121">在 `Turns` 新加入之引數底下的 [**名稱**] 方塊中輸入 `MaxNumber` ，從 [**方向**] 下拉式清單 **中** 選取 [從自 **變數類型**] 下拉式清單選取 [ **Int32** ]，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="01efe-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="01efe-122">在活動設計工具的左下方按一下 **[引數]**，以關閉 **[引數]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="01efe-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="01efe-123">在工作流程設計工具的左下方按一下 [ **變數** ]，以顯示 [ **變數** ] 窗格。</span><span class="sxs-lookup"><span data-stu-id="01efe-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="01efe-124">按一下 **[建立變數]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="01efe-125">如果沒有顯示 [ **建立變數** ] 方塊，請按一下工作流程設計工具介面上的 [ **Sequence** ] 活動加以選取。</span><span class="sxs-lookup"><span data-stu-id="01efe-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="01efe-126">在 `Guess` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="01efe-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="01efe-127">按一下 **[建立變數]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="01efe-128">在 `Target` [**名稱**] 方塊中輸入，並從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="01efe-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="01efe-129">在活動設計工具的左下方按一下 **[變數]**，以關閉 **[變數]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="01efe-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="01efe-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="01efe-130">To add the workflow activities</span></span>

1. <span data-ttu-id="01efe-131">從 [**工具箱**] 的 [**基本**] 區段中，將 [**指派**] 活動拖放到 [**序列**] 活動上。</span><span class="sxs-lookup"><span data-stu-id="01efe-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="01efe-132">在 `Target` [ **到** ] 方塊中輸入，並在 [ **輸入 c # 運算式** ] 或 [ **輸入 VB 運算式** ] 方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="01efe-133">若 **[工具箱]** 視窗並未顯示，請從 **[檢視]** 功能表中選取 **[工具箱]**。</span><span class="sxs-lookup"><span data-stu-id="01efe-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="01efe-134">從 [**工具箱**] 的 [**控制流程**] 區段中，將 [ **DoWhile** ] 活動拖放到工作流程上，使其位於 [**指派**] 活動下方。</span><span class="sxs-lookup"><span data-stu-id="01efe-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="01efe-135">在 [ **DoWhile** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="01efe-136"><xref:System.Activities.Statements.DoWhile> 活動會執行其子活動，然後評估其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。</span><span class="sxs-lookup"><span data-stu-id="01efe-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="01efe-137">如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 判斷值為 `True`，則會再次執行 <xref:System.Activities.Statements.DoWhile> 中的活動。</span><span class="sxs-lookup"><span data-stu-id="01efe-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="01efe-138">此範例中會評估使用者的猜測，而 <xref:System.Activities.Statements.DoWhile> 會繼續，直到猜測正確為止。</span><span class="sxs-lookup"><span data-stu-id="01efe-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="01efe-139">從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，然後將它放在上一個步驟的 [ **DoWhile** ] 活動中。</span><span class="sxs-lookup"><span data-stu-id="01efe-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="01efe-140">在 [**屬性] 視窗** 的 [ `"EnterGuess"` **提示**] 活動的 [ **BookmarkName** ] 屬性值方塊中，輸入包含引號。</span><span class="sxs-lookup"><span data-stu-id="01efe-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="01efe-141">`Guess`在 [**結果**] 屬性值方塊中輸入，並在 [ **Text** ] 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="01efe-142">如果未顯示 [**屬性] 視窗**，請從 [ **View** ] 功能表選取 [**屬性視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="01efe-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="01efe-143">從 [**工具箱**] 的 [**基本**] 區段中，將 [**指派**] 活動拖放到 [ **DoWhile** ] 活動中，讓它遵循 [**提示**] 活動。</span><span class="sxs-lookup"><span data-stu-id="01efe-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="01efe-144">當您卸載 [ **指派** ] 活動時，請注意工作流程設計工具如何自動加入 [ **Sequence** ] 活動，以同時包含 [ **提示** ] 活動和新加入的 [ **指派** ] 活動。</span><span class="sxs-lookup"><span data-stu-id="01efe-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="01efe-145">在 [到] 方塊中輸入 `Turns` ，然後 `Turns + 1` 在 [**輸入 c # 運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="01efe-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="01efe-146">從 [**工具箱**] 的 [**控制流程**] 區段中，將 [ **If** ] 活動拖放到 [**序列**] 活動中，使其在新增的 [**指派**] 活動之後。</span><span class="sxs-lookup"><span data-stu-id="01efe-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="01efe-147">在 [ **If** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="01efe-148">從 [**工具箱**] 的 [**控制流程**] 區段中，將另一個 [ **if** ] 活動拖放到第一個 [ **if** ] 活動的 [ **Then** ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="01efe-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="01efe-149">在新加入的 [ **If** ] 活動的 [ **條件** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="01efe-150">將兩個 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **If** ] 活動的 [ **Then** ] 區段中，另一個則是在 [ **Else** ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="01efe-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="01efe-151">按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="01efe-152">按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="01efe-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="01efe-153">下列範例說明已完成的工作流程：</span><span class="sxs-lookup"><span data-stu-id="01efe-153">The following example illustrates the completed workflow:</span></span>

     ![顯示已完成之連續工作流程的螢幕擷取畫面。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="01efe-155">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="01efe-155">To build the workflow</span></span>

1. <span data-ttu-id="01efe-156">按 CTRL+SHIFT+B 建置解決方案。</span><span class="sxs-lookup"><span data-stu-id="01efe-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="01efe-157">如需如何執行工作流程的指示，請參閱下一個主題 [：如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="01efe-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="01efe-158">如果您已經完成 how to：使用不同的工作流程樣式來[執行工作流程](how-to-run-a-workflow.md)步驟，而且想要使用此步驟中的順序工作流程來執行它，請直接跳至 how [To：執行工作流程](how-to-run-a-workflow.md)的 [[建立並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)] 區段。</span><span class="sxs-lookup"><span data-stu-id="01efe-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01efe-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01efe-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="01efe-160">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="01efe-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="01efe-161">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="01efe-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="01efe-162">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="01efe-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="01efe-163">作法：建立活動</span><span class="sxs-lookup"><span data-stu-id="01efe-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="01efe-164">作法：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="01efe-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
