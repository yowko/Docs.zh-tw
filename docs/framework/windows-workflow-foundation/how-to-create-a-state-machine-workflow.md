---
title: 作法：建立狀態機器工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 84d2355a78c7d33bf712baf158f28861e59e75d1
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881950"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="9e05a-102">作法：建立狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="9e05a-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="9e05a-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="9e05a-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="9e05a-104">本主題將逐步解說如何建立這類使用內建活動的工作流程<xref:System.Activities.Statements.StateMachine>活動，並從先前的自訂活動[How to:建立活動](how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="9e05a-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="9e05a-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="9e05a-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e05a-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="9e05a-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="9e05a-107">若要完成本主題，您必須先完成[How to:建立活動](how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="9e05a-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e05a-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="9e05a-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="9e05a-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="9e05a-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="9e05a-110">以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管**，然後選取**新增**，**新項目**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="9e05a-111">在 **已安裝**，**通用的項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="9e05a-112">選取 **活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="9e05a-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="9e05a-113">型別`StateMachineNumberGuessWorkflow`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="9e05a-114">拖曳**StateMachine**活動，從**狀態機器**一節**工具箱**拖曳至**活動拖曳到這裏**上加上標籤工作流程設計介面中。</span><span class="sxs-lookup"><span data-stu-id="9e05a-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="9e05a-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="9e05a-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="9e05a-116">按兩下**StateMachineNumberGuessWorkflow.xaml**中**方案總管 中**時所要顯示工作流程設計工具中，在不顯示。</span><span class="sxs-lookup"><span data-stu-id="9e05a-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="9e05a-117">按一下 **引數**以顯示工作流程設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="9e05a-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="9e05a-118">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="9e05a-119">型別`MaxNumber`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="9e05a-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="9e05a-120">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="9e05a-121">型別`Turns`成**名稱**下方新增`MaxNumber`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9e05a-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="9e05a-122">按一下 **引數**關閉的活動設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="9e05a-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="9e05a-123">按一下 **變數**以顯示工作流程設計工具左下角**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="9e05a-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="9e05a-124">按一下 **建立的變數**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9e05a-125">如果沒有**建立變數**] 方塊中，請按一下 [<xref:System.Activities.Statements.StateMachine>活動在工作流程設計工具介面，以選取它。</span><span class="sxs-lookup"><span data-stu-id="9e05a-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="9e05a-126">型別`Guess`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="9e05a-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="9e05a-127">按一下 **建立的變數**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="9e05a-128">型別`Target`成**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="9e05a-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="9e05a-129">按一下 **變數**關閉的活動設計工具左下角**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="9e05a-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="9e05a-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="9e05a-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="9e05a-131">按一下  **State1**來選取它。</span><span class="sxs-lookup"><span data-stu-id="9e05a-131">Click **State1** to select it.</span></span> <span data-ttu-id="9e05a-132">在 [**屬性] 視窗**，變更**DisplayName**到`Initialize Target`。</span><span class="sxs-lookup"><span data-stu-id="9e05a-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9e05a-133">如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="9e05a-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="9e05a-134">按兩下剛剛重新命名**初始化目標**狀態中的工作流程設計工具，將它展開。</span><span class="sxs-lookup"><span data-stu-id="9e05a-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="9e05a-135">拖曳**指派**活動，從**基本型別**一節**工具箱**拖曳至**項目**狀態一節。</span><span class="sxs-lookup"><span data-stu-id="9e05a-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="9e05a-136">型別`Target`成**要** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="9e05a-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="9e05a-137">如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="9e05a-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="9e05a-138">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="9e05a-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="9e05a-139">拖曳**狀態**活動，從**狀態機器**一節**工具箱**拖曳至工作流程設計工具，將滑鼠移至**初始化目標**狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="9e05a-140">請注意周圍會出現四個三角形**初始化目標**上方有新的狀態時的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="9e05a-141">新狀態放置在正下方的三角形**初始化目標**狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="9e05a-142">這會將新的狀態，到工作流程，並建立從轉換**初始化目標**狀態到新的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="9e05a-143">按一下  **State1**來選取它，變更**DisplayName**到`Enter Guess`，然後按兩下以展開工作流程設計工具中的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="9e05a-144">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖曳至**項目**狀態一節。</span><span class="sxs-lookup"><span data-stu-id="9e05a-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="9e05a-145">輸入下列運算式**文字** 屬性方塊**WriteLine**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="9e05a-146">拖曳**指派**活動，從**基本型別**一節**工具箱**並放入**結束**狀態一節。</span><span class="sxs-lookup"><span data-stu-id="9e05a-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="9e05a-147">型別`Turns`成**要**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="9e05a-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="9e05a-148">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="9e05a-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="9e05a-149">拖曳**FinalState**活動，從**狀態機器**一節**工具箱**，將滑鼠移至**Enter Guess**狀態，並將它放拖曳至右邊的三角形**輸入猜測**狀態，讓之間建立轉換**Enter Guess**並**FinalState**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="9e05a-150">轉換的預設名稱是**T2**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="9e05a-151">按一下以選取它，並設定工作流程設計工具中的轉換其**DisplayName**要**猜測正確**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="9e05a-152">然後按一下並選取**FinalState**，並將它拖曳到右邊，使其沒有完整的轉換名稱，而不會重疊的兩個狀態的其中一個要顯示的空間。</span><span class="sxs-lookup"><span data-stu-id="9e05a-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="9e05a-153">這將可以更容易完成教學課程中的其他步驟。</span><span class="sxs-lookup"><span data-stu-id="9e05a-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="9e05a-154">按兩下剛剛重新命名**猜測正確**中工作流程設計工具，將其展開的轉換。</span><span class="sxs-lookup"><span data-stu-id="9e05a-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="9e05a-155">拖曳**ReadInt**活動，從**NumberGuessWorkflowActivities**一節**工具箱**並將它放**觸發程序**區段轉換。</span><span class="sxs-lookup"><span data-stu-id="9e05a-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="9e05a-156">在 [**屬性] 視窗**的**ReadInt**活動中，輸入`"EnterGuess"`包括到引號**BookmarkName**屬性值方塊，然後輸入`Guess`成**結果**屬性值方塊</span><span class="sxs-lookup"><span data-stu-id="9e05a-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="9e05a-157">輸入下列運算式**猜測正確**轉換**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="9e05a-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="9e05a-158">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="9e05a-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e05a-159">收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="9e05a-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="9e05a-160">針對此轉換，如果使用者的`Guess`符合隨機產生`Target`，則控制權會傳遞給**FinalState**和工作流程完成。</span><span class="sxs-lookup"><span data-stu-id="9e05a-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="9e05a-161">根據先前的猜測是否正確，工作流程應轉換到**FinalState**或回到**輸入猜測**狀態，再試一次。</span><span class="sxs-lookup"><span data-stu-id="9e05a-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="9e05a-162">兩種轉換共用相同觸發程序等待接收透過使用者的猜測**ReadInt**活動。</span><span class="sxs-lookup"><span data-stu-id="9e05a-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="9e05a-163">這稱為共用轉換。</span><span class="sxs-lookup"><span data-stu-id="9e05a-163">This is called a shared transition.</span></span> <span data-ttu-id="9e05a-164">若要建立共用的轉換，請按一下 的圓形，表示開始**猜測正確**轉換，並將它拖曳至所需的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="9e05a-165">在此情況下轉換是自行轉換，因此將拖曳的起點**猜測正確**轉換拖放回到底部**Enter Guess**狀態。</span><span class="sxs-lookup"><span data-stu-id="9e05a-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="9e05a-166">建立轉換之後, 在工作流程設計工具中選取它，並設定其**DisplayName**屬性設**猜測不正確**。</span><span class="sxs-lookup"><span data-stu-id="9e05a-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e05a-167">共用的轉換也可以建立從轉換設計工具內依序按一下**新增共用的觸發程序轉換**底部的轉換設計工具，然後選取 所需的目標狀態從**可用的狀態，來連接**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="9e05a-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9e05a-168">請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。</span><span class="sxs-lookup"><span data-stu-id="9e05a-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="9e05a-169">由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。</span><span class="sxs-lookup"><span data-stu-id="9e05a-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="9e05a-170">按兩下**猜測不正確**中工作流程設計工具，將其展開的轉換。</span><span class="sxs-lookup"><span data-stu-id="9e05a-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="9e05a-171">請注意，**觸發程序**已設為相同**ReadInt**所使用的活動**猜測正確**轉換。</span><span class="sxs-lookup"><span data-stu-id="9e05a-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="9e05a-172">輸入下列運算式**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="9e05a-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="9e05a-173">拖曳**如果**活動，從**控制流程**一節**工具箱**並將它放**動作**轉換的區段。</span><span class="sxs-lookup"><span data-stu-id="9e05a-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="9e05a-174">輸入下列運算式**如果**活動的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="9e05a-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="9e05a-175">將兩個**WriteLine**活動，從**基本型別**一節**工具箱**和卸除它們，因此，另一個**然後**區段**如果**活動，另一個處於**Else**一節。</span><span class="sxs-lookup"><span data-stu-id="9e05a-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="9e05a-176">按一下  **WriteLine**中的活動**然後**區段以選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="9e05a-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="9e05a-177">按一下  **WriteLine**中的活動**Else**區段以選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="9e05a-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="9e05a-178">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層連結顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="9e05a-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="9e05a-179">下列範例示範完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9e05a-179">The following example illustrates the completed workflow.</span></span>  
  
     ![顯示已完成的狀態機器工作流程的圖例。](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="9e05a-181">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="9e05a-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="9e05a-182">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="9e05a-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="9e05a-183">如需有關如何執行工作流程，指示，請參閱下一個主題中， [How to:執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="9e05a-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="9e05a-184">如果您已經完成[How to:執行工作流程](how-to-run-a-workflow.md)步驟來搭配另一個樣式的工作流程並想要使用此步驟的狀態機器工作流程執行，請直接跳到[以建置並執行應用程式](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)一節[How to:執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="9e05a-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e05a-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e05a-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="9e05a-186">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="9e05a-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="9e05a-187">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="9e05a-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="9e05a-188">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="9e05a-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="9e05a-189">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="9e05a-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="9e05a-190">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="9e05a-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
