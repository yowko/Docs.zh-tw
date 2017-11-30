---
title: "HOW TO：建立循序工作流程"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bf6d8b499903522ee09021bb9339ece6a5894eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="da54b-102">HOW TO：建立循序工作流程</span><span class="sxs-lookup"><span data-stu-id="da54b-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="da54b-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="da54b-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="da54b-104">本主題逐步說明建立使用這兩個內建的活動，例如工作流程<xref:System.Activities.Statements.Sequence>活動，並從先前的自訂活動[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="da54b-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="da54b-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="da54b-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da54b-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="da54b-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="da54b-107">若要完成本主題，您必須先完成[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="da54b-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da54b-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="da54b-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="da54b-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="da54b-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="da54b-110">以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管 中**選取**新增**，**新項目**。</span><span class="sxs-lookup"><span data-stu-id="da54b-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="da54b-111">在**已安裝**，**一般項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="da54b-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="da54b-112">選取**活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="da54b-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="da54b-113">型別`SequentialNumberGuessWorkflow`到**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="da54b-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="da54b-114">拖曳**順序**活動從**控制流程**區段**工具箱**並將其放置**在此置放活動**上加上標籤工作流程設計介面。</span><span class="sxs-lookup"><span data-stu-id="da54b-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="da54b-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="da54b-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="da54b-116">按兩下**SequentialNumberGuessWorkflow.xaml**中**方案總管 中**來顯示工作流程設計工具中，如果未顯示。</span><span class="sxs-lookup"><span data-stu-id="da54b-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="da54b-117">按一下**引數**顯示工作流程設計工具的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="da54b-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="da54b-118">按一下**建立引數**。</span><span class="sxs-lookup"><span data-stu-id="da54b-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="da54b-119">型別`MaxNumber`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="da54b-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="da54b-120">按一下**建立引數**。</span><span class="sxs-lookup"><span data-stu-id="da54b-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="da54b-121">型別`Turns`到**名稱**下方新增`MaxNumber`引數，選取**出**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="da54b-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="da54b-122">按一下**引數**活動設計工具，以關閉的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="da54b-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="da54b-123">按一下**變數**顯示工作流程設計工具的左下方**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="da54b-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="da54b-124">按一下**建立變數**。</span><span class="sxs-lookup"><span data-stu-id="da54b-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="da54b-125">如果沒有**建立變數**顯示方塊中，按一下**順序**活動在工作流程設計工具介面，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="da54b-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="da54b-126">型別`Guess`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="da54b-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="da54b-127">按一下**建立變數**。</span><span class="sxs-lookup"><span data-stu-id="da54b-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="da54b-128">型別`Target`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="da54b-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="da54b-129">按一下**變數**活動設計工具，以關閉的左下方**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="da54b-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="da54b-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="da54b-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="da54b-131">拖曳**指派**活動從**基本型別**區段**工具箱**並將其放置**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="da54b-132">型別`Target`到**至** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式**方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="da54b-133">如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="da54b-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="da54b-134">拖曳**DoWhile**活動從**控制流程**區段**工具箱**並將它放在工作流程，使它低於**指派**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3.  <span data-ttu-id="da54b-135">將下列運算式輸入到**DoWhile**活動的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="da54b-136"><xref:System.Activities.Statements.DoWhile> 活動會執行其子活動，然後評估其 <xref:System.Activities.Statements.DoWhile.Condition%2A>。</span><span class="sxs-lookup"><span data-stu-id="da54b-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="da54b-137">如果 <xref:System.Activities.Statements.DoWhile.Condition%2A> 判斷值為 `True`，則會再次執行 <xref:System.Activities.Statements.DoWhile> 中的活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="da54b-138">此範例中會評估使用者的猜測，而 <xref:System.Activities.Statements.DoWhile> 會繼續，直到猜測正確為止。</span><span class="sxs-lookup"><span data-stu-id="da54b-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4.  <span data-ttu-id="da54b-139">拖曳**提示**活動從**NumberGuessWorkflowActivities**區段**工具箱**並將它放**DoWhile**活動從上一個步驟。</span><span class="sxs-lookup"><span data-stu-id="da54b-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5.  <span data-ttu-id="da54b-140">在**屬性 視窗**，型別`"EnterGuess"`（包含引號） 到**BookmarkName**屬性值方塊**提示**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="da54b-141">型別`Guess`到**結果**屬性值方塊中，並輸入下列運算式**文字**屬性方塊中。</span><span class="sxs-lookup"><span data-stu-id="da54b-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="da54b-142">如果**屬性 視窗**顯示，請選取**屬性 視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="da54b-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6.  <span data-ttu-id="da54b-143">拖曳**指派**活動從**基本型別**區段**工具箱**並將它放**DoWhile**活動，接**提示**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da54b-144">當您卸除**指派**活動，請注意工作流程設計工具自動加入**順序**活動，以同時包含**提示**活動和新加入**指派**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7.  <span data-ttu-id="da54b-145">型別`Turns`到**至**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式**方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8.  <span data-ttu-id="da54b-146">拖曳**如果**活動從**控制流程**區段**工具箱**並將它放**順序**活動，接新加入的**指派**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="da54b-147">將下列運算式輸入到**如果**活動的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="da54b-148">拖曳其他**如果**活動從**控制流程**區段**工具箱**並將它放**然後**> 一節的第一個**如果**活動。</span><span class="sxs-lookup"><span data-stu-id="da54b-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="da54b-149">下列運算式輸入至新加入**如果**活動的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="da54b-150">拖放兩**WriteLine**活動從**基本型別**區段**工具箱**，讓其中一項是置於**然後**區段新加入**如果**活動和一個處於**Else** > 一節。</span><span class="sxs-lookup"><span data-stu-id="da54b-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="da54b-151">按一下**WriteLine**中的活動**然後**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="da54b-152">按一下**WriteLine**中的活動**Else**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="da54b-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="da54b-153">下列範例示範完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="da54b-153">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="da54b-154">![已完成循序工作流程](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="da54b-154">![Completed Sequential Workflow](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="da54b-155">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="da54b-155">To build the workflow</span></span>  
  
1.  <span data-ttu-id="da54b-156">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="da54b-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="da54b-157">如需有關如何執行工作流程，指示，請參閱下一個主題中，[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="da54b-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="da54b-158">如果您已經完成[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)步驟與工作流程的不同的樣式和想要使用此步驟中的循序工作流程執行該，跳到[建置並執行應用程式](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)區段[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="da54b-158">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da54b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da54b-159">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="da54b-160">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="da54b-160">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="da54b-161">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="da54b-161">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="da54b-162">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="da54b-162">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="da54b-163">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="da54b-163">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="da54b-164">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="da54b-164">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
