---
title: HOW TO：建立流程圖工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989680"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="d9039-102">作法：建立流程圖工作流程</span><span class="sxs-lookup"><span data-stu-id="d9039-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="d9039-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="d9039-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="d9039-104">本主題將逐步說明如何建立使用內建活動（例如<xref:System.Activities.Statements.Flowchart>活動）的工作流程，以及先前[如何執行的自訂活動：建立活動](how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="d9039-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="d9039-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="d9039-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9039-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="d9039-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="d9039-107">若要完成本主題，您必須先[完成如何：建立活動](how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="d9039-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9039-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="d9039-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="d9039-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="d9039-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="d9039-110">以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowactivities]** ，然後選取 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="d9039-111">在 [**已安裝**的**通用專案**] 節點中，選取 [**工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="d9039-112">從 [**工作流程**] 清單中選取 [**活動**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="d9039-113">在`FlowchartNumberGuessWorkflow` [**名稱**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="d9039-114">從 [**工具箱**] 的 [**流程圖**] 區段，將 [ **flowchart** ] 活動拖放到工作流程設計介面上的 [在**此放置活動**] 標籤上。</span><span class="sxs-lookup"><span data-stu-id="d9039-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="d9039-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="d9039-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="d9039-116">按兩下**方案總管**中的 [ **FlowchartNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。</span><span class="sxs-lookup"><span data-stu-id="d9039-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="d9039-117">在工作流程設計工具的左下方按一下 [**引數**]，以顯示 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d9039-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="d9039-118">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="d9039-119">在`MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [In]，選取 [自**變數型**別] 下拉式清單**中**的 [ **Int32** ]，然後按下 enter 以儲存引數。</span><span class="sxs-lookup"><span data-stu-id="d9039-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="d9039-120">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="d9039-121">在`Turns`新加入的引數下方輸入 [名稱] 方塊，從 [方向] 下拉式清單中選取 [Out]，選取 [引數型別] 下拉式清單中的 [Int32]，然後按 enter。 `MaxNumber`</span><span class="sxs-lookup"><span data-stu-id="d9039-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="d9039-122">在活動設計工具的左下方按一下 [**引數**]，以關閉 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d9039-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="d9039-123">按一下工作流程設計工具左下方的 [**變數**]，以顯示 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d9039-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="d9039-124">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="d9039-125">如果沒有顯示 [**建立變數**] 方塊，請<xref:System.Activities.Statements.Flowchart>按一下工作流程設計工具介面上的活動加以選取。</span><span class="sxs-lookup"><span data-stu-id="d9039-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="d9039-126">在`Guess` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="d9039-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="d9039-127">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="d9039-128">在`Target` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="d9039-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="d9039-129">在活動設計工具的左下方按一下 [**變數**]，以關閉 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d9039-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="d9039-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="d9039-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="d9039-131">從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並將其暫留在 [**開始**] 節點上（位於流程圖頂端）。</span><span class="sxs-lookup"><span data-stu-id="d9039-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="d9039-132">當 [**指派**] 活動超過 [**啟動**] 節點時，[**開始**] 節點周圍會出現三個三角形。</span><span class="sxs-lookup"><span data-stu-id="d9039-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="d9039-133">將 [**指派**] 活動放置在 [**開始**] 節點正下方的三角形上。</span><span class="sxs-lookup"><span data-stu-id="d9039-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="d9039-134">這會將兩個專案連結在一起，並將 [**指派**] 活動指定為流程圖中的第一個活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d9039-135">您也可以手動連結活動與啟動節點，指定活動為工作流程中的啟動活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="d9039-136">若要這麼做，請將滑鼠游標移到 [**開始**] 節點上方，按一下滑鼠停留在 [**啟動**] 節點上方時出現的其中一個矩形，然後將連接線向下拖曳到所需的活動，並放置在出現的其中一個矩形上。</span><span class="sxs-lookup"><span data-stu-id="d9039-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="d9039-137">您也可以在活動上按一下滑鼠右鍵，然後選擇 [**設定為起始節點**]，將它指定為開始活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="d9039-138">在`Target` [**到**] 方塊中輸入，並在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="d9039-139">如果沒有顯示 [**工具箱**] 視窗，請從 [**視圖**] 功能表中選取 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="d9039-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="d9039-140">從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段拖曳 [**提示**] 活動，將它放在上一個步驟的 [**指派**] 活動下方，然後將 [**提示**] 活動連接至 [**指派**] 活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="d9039-141">有三種方式可連接這兩個活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="d9039-142">第一種方式是在您將 [**提示**] 活動放在工作流程上時進行連接。</span><span class="sxs-lookup"><span data-stu-id="d9039-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="d9039-143">當您將 [**提示**] 活動拖曳到工作流程時，請將其暫留在 [**指派**] 活動上方，然後放**到 [** **指派**] 活動上方的四個三角形其中之一。</span><span class="sxs-lookup"><span data-stu-id="d9039-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="d9039-144">第二種方式是將 [**提示**] 活動放置到所需位置的工作流程上。</span><span class="sxs-lookup"><span data-stu-id="d9039-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="d9039-145">然後，將滑鼠停留在 [**指派**] 活動上方，並將出現的其中一個矩形拖曳到 [**提示**] 活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="d9039-146">拖曳滑鼠，使 [**指派**] 活動中的連接線連接至 [**提示**] 活動的其中一個矩形，然後放開滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="d9039-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="d9039-147">第三種方式與第一種方式非常類似，不同之處在于，它不會從 [**工具箱**] 拖曳 [**提示**] 活動，而是從其在工作流程設計介面上的位置拖曳，將其停留在 [**指派**] 活動上方，然後放到其中一個出現的三角形。</span><span class="sxs-lookup"><span data-stu-id="d9039-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="d9039-148">在 [**提示**] 活動的 [ `"EnterGuess"` **屬性] 視窗**中，于 [ **BookmarkName**屬性值] 方塊中輸入包含引號。</span><span class="sxs-lookup"><span data-stu-id="d9039-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="d9039-149">在`Guess` [**結果**] 屬性值方塊中輸入，然後在 [ **Text** ] 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="d9039-150">如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="d9039-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="d9039-151">從 [**工具箱**] 的 [**基本**] 區段中拖曳 [**指派**] 活動，並使用上一個步驟中所述的其中一個方法進行連接，使其位於 [**提示**] 活動下方。</span><span class="sxs-lookup"><span data-stu-id="d9039-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="d9039-152">在`Turns` [**到**] 方塊中`Turns + 1`輸入，然後在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中鍵入。</span><span class="sxs-lookup"><span data-stu-id="d9039-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="d9039-153">從 [**工具箱**] 的 [**流程圖**] 區段中拖曳**FlowDecision** ，並將它連接到 [**指派**] 活動下方。</span><span class="sxs-lookup"><span data-stu-id="d9039-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="d9039-154">在 [**屬性] 視窗**的 [**條件**] 屬性值方塊中，輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="d9039-155">從 [**工具箱**] 將另一個 [ **FlowDecision** ] 活動拖放到第一個活動下方。</span><span class="sxs-lookup"><span data-stu-id="d9039-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="d9039-156">從頂端**FlowDecision**活動上標示**為 False**的矩形拖曳到第二個**FlowDecision**活動頂端的矩形，以連接這兩個活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="d9039-157">如果您在**FlowDecision**上看不到 [ **True** ] 和 [ **False** ] 標籤，請將滑鼠停留在**FlowDecision**上。</span><span class="sxs-lookup"><span data-stu-id="d9039-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="d9039-158">按一下第二個 [ **FlowDecision** ] 活動加以選取。</span><span class="sxs-lookup"><span data-stu-id="d9039-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="d9039-159">在 [**屬性] 視窗**的 [**條件**] 屬性值方塊中，輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="d9039-160">從 [**工具箱**] 的 [**基本**] 區段拖放兩個 [ **WriteLine** ] 活動，使其在兩個**FlowDecision**活動的正下方。</span><span class="sxs-lookup"><span data-stu-id="d9039-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="d9039-161">將底部**FlowDecision**活動的**真正**動作連線到最左邊的 [ **writeline** ] 活動，並將 [ **False** ] 動作連接至最右邊的 [ **writeline** ] 活動。</span><span class="sxs-lookup"><span data-stu-id="d9039-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="d9039-162">按一下最左邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗**的 [**文字**] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="d9039-163">將 [ **WriteLine** ] 連接至其上方的 [**提示**] 活動左邊。</span><span class="sxs-lookup"><span data-stu-id="d9039-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="d9039-164">按一下最右邊的 [ **WriteLine** ] 活動加以選取，然後在 [**屬性] 視窗**的 [**文字**] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="d9039-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="d9039-165">將 [ **WriteLine** ] 活動連接至其上方 [**提示**] 活動的右側。</span><span class="sxs-lookup"><span data-stu-id="d9039-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="d9039-166">下列範例示範完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d9039-166">The following example illustrates the completed workflow.</span></span>  
  
     ![顯示已完成 Windows Workflow Foundation 流程圖的圖表。](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="d9039-168">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="d9039-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="d9039-169">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="d9039-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="d9039-170">如需有關如何執行工作流程的指示，請參閱下一個主題[：如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="d9039-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="d9039-171">如果您已經完成[如何：使用不同的](how-to-run-a-workflow.md)工作流程樣式執行工作流程步驟，並想要使用此步驟中的流程圖工作流程執行，請直接跳[至](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="d9039-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9039-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9039-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="d9039-173">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="d9039-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="d9039-174">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="d9039-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="d9039-175">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="d9039-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="d9039-176">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="d9039-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="d9039-177">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="d9039-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
