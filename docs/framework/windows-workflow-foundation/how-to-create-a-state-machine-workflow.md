---
title: HOW TO：建立狀態機器工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 00f764421d3caf44d853d26d76c6b6d872ab1e3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520025"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="8afba-102">HOW TO：建立狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="8afba-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="8afba-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="8afba-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="8afba-104">本主題逐步說明建立使用這兩個內建的活動，例如工作流程<xref:System.Activities.Statements.StateMachine>活動，並從先前的自訂活動[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="8afba-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="8afba-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="8afba-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afba-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="8afba-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8afba-107">若要完成本主題，您必須先完成[How to： 建立活動](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="8afba-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afba-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="8afba-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="8afba-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="8afba-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="8afba-110">以滑鼠右鍵按一下**NumberGuessWorkflowActivities**中**方案總管 中**選取**新增**，**新項目**。</span><span class="sxs-lookup"><span data-stu-id="8afba-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="8afba-111">在**已安裝**，**一般項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="8afba-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="8afba-112">選取**活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="8afba-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="8afba-113">型別`StateMachineNumberGuessWorkflow`到**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="8afba-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="8afba-114">拖曳**StateMachine**活動從**狀態機器**區段**工具箱**並將其放置**在此置放活動**上加上標籤工作流程設計介面中。</span><span class="sxs-lookup"><span data-stu-id="8afba-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="8afba-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="8afba-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="8afba-116">按兩下**StateMachineNumberGuessWorkflow.xaml**中**方案總管 中**來顯示工作流程設計工具中，如果未顯示。</span><span class="sxs-lookup"><span data-stu-id="8afba-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="8afba-117">按一下**引數**顯示工作流程設計工具的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="8afba-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="8afba-118">按一下**建立引數**。</span><span class="sxs-lookup"><span data-stu-id="8afba-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="8afba-119">型別`MaxNumber`到**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="8afba-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="8afba-120">按一下**建立引數**。</span><span class="sxs-lookup"><span data-stu-id="8afba-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="8afba-121">型別`Turns`到**名稱**下方新增`MaxNumber`引數，選取**出**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="8afba-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="8afba-122">按一下**引數**活動設計工具，以關閉的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="8afba-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="8afba-123">按一下**變數**顯示工作流程設計工具的左下方**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="8afba-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="8afba-124">按一下**建立變數**。</span><span class="sxs-lookup"><span data-stu-id="8afba-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8afba-125">如果沒有**建立變數**顯示方塊中，按一下<xref:System.Activities.Statements.StateMachine>活動在工作流程設計工具介面，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="8afba-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="8afba-126">型別`Guess`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="8afba-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="8afba-127">按一下**建立變數**。</span><span class="sxs-lookup"><span data-stu-id="8afba-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="8afba-128">型別`Target`到**名稱**方塊中，選取**Int32**從**變數型別**下拉式清單，然後按下 ENTER 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="8afba-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="8afba-129">按一下**變數**活動設計工具，以關閉的左下方**變數**窗格。</span><span class="sxs-lookup"><span data-stu-id="8afba-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="8afba-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="8afba-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="8afba-131">按一下**State1**來選取它。</span><span class="sxs-lookup"><span data-stu-id="8afba-131">Click **State1** to select it.</span></span> <span data-ttu-id="8afba-132">在**屬性 視窗**，變更**DisplayName**至`Initialize Target`。</span><span class="sxs-lookup"><span data-stu-id="8afba-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8afba-133">如果**屬性 視窗**顯示，請選取**屬性 視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="8afba-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="8afba-134">按兩下剛剛重新命名**初始化目標**狀態在工作流程設計工具中將它展開。</span><span class="sxs-lookup"><span data-stu-id="8afba-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="8afba-135">拖曳**指派**活動從**基本型別**區段**工具箱**並將其放置**項目**區段的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="8afba-136">型別`Target`到**至** 方塊中，下列運算式**輸入 C# 運算式**或**輸入 VB 運算式**方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="8afba-137">如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="8afba-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="8afba-138">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="8afba-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="8afba-139">拖曳**狀態**活動從**狀態機器**區段**工具箱**拖曳至工作流程設計工具，將滑鼠停留在**初始化目標**狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="8afba-140">請注意周圍會出現四個三角形**初始化目標**時的新狀態是透過它的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="8afba-141">[新增] 狀態正下方的三角形上卸除**初始化目標**狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="8afba-142">這樣會將新狀態放置到工作流程，並且建立從轉換**初始化目標**狀態為新的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="8afba-143">按一下**State1**加以選擇，變更**DisplayName**至`Enter Guess`，然後按兩下以展開工作流程設計工具中的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="8afba-144">拖曳**WriteLine**活動從**基本型別**區段**工具箱**並將其放置**項目**區段的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="8afba-145">將下列運算式輸入到**文字**屬性方塊**WriteLine**。</span><span class="sxs-lookup"><span data-stu-id="8afba-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="8afba-146">拖曳**指派**活動從**基本型別**區段**工具箱**拖曳**結束**區段的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="8afba-147">型別`Turns`到**至**方塊和`Turns + 1`到**輸入 C# 運算式**或**輸入 VB 運算式**方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="8afba-148">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="8afba-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="8afba-149">拖曳**FinalState**活動從**狀態機器**區段**工具箱**，將滑鼠停留在**輸入猜測**狀態，並將它放拖曳至右邊的三角形**輸入猜測**狀態以便之間建立轉換**輸入猜測**和**FinalState**。</span><span class="sxs-lookup"><span data-stu-id="8afba-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="8afba-150">轉換的預設名稱是**T2**。</span><span class="sxs-lookup"><span data-stu-id="8afba-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="8afba-151">按一下以選取它，並設定工作流程設計工具中的轉換其**DisplayName**至**猜測正確**。</span><span class="sxs-lookup"><span data-stu-id="8afba-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="8afba-152">然後按一下並選取**FinalState**，並將它拖曳至右邊，以便挪出空間不重疊的兩個狀態的任何一個顯示完整的轉換名稱。</span><span class="sxs-lookup"><span data-stu-id="8afba-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="8afba-153">這將可以更容易完成教學課程中的其他步驟。</span><span class="sxs-lookup"><span data-stu-id="8afba-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="8afba-154">按兩下剛剛重新命名**猜測正確**將它展開工作流程設計工具中的轉換。</span><span class="sxs-lookup"><span data-stu-id="8afba-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="8afba-155">拖曳**ReadInt**活動從**NumberGuessWorkflowActivities**區段**工具箱**並將它放**觸發程序**區段轉換。</span><span class="sxs-lookup"><span data-stu-id="8afba-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="8afba-156">在**屬性 視窗**如**ReadInt**活動中，輸入`"EnterGuess"`（包含引號） 到**BookmarkName**屬性值方塊中，然後`Guess`到**結果**屬性值方塊</span><span class="sxs-lookup"><span data-stu-id="8afba-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="8afba-157">將下列運算式輸入到**猜測正確**轉換的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="8afba-158">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="8afba-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8afba-159">收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="8afba-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="8afba-160">針對此轉換，如果使用者的`Guess`符合隨機產生`Target`，則控制權會傳遞給**FinalState**和工作流程完成。</span><span class="sxs-lookup"><span data-stu-id="8afba-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="8afba-161">根據先前的猜測是否正確，工作流程應轉換到**FinalState**或返回**輸入猜測**狀態再試一次。</span><span class="sxs-lookup"><span data-stu-id="8afba-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="8afba-162">兩種轉換共用相同觸發程序的等待接收透過使用者的猜測**ReadInt**活動。</span><span class="sxs-lookup"><span data-stu-id="8afba-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="8afba-163">這稱為共用轉換。</span><span class="sxs-lookup"><span data-stu-id="8afba-163">This is called a shared transition.</span></span> <span data-ttu-id="8afba-164">若要建立共用的轉換，請按一下 的圓形，表示開始**猜測正確**轉換，並將它拖曳到所需的狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="8afba-165">在此情況下轉換是自行轉換，因此的起點拖放到**猜測正確**轉換拖放回到底部**輸入猜測**狀態。</span><span class="sxs-lookup"><span data-stu-id="8afba-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="8afba-166">建立轉換之後, 在工作流程設計工具中選取它，並設定其**DisplayName**屬性**猜測不正確**。</span><span class="sxs-lookup"><span data-stu-id="8afba-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8afba-167">共用的轉換也會建立從轉換設計工具內按一下**新增共用的觸發程序轉換**底部的轉換設計工具，然後選取 從想要的目標狀態**要連線的可用狀態**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="8afba-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8afba-168">請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。</span><span class="sxs-lookup"><span data-stu-id="8afba-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="8afba-169">由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。</span><span class="sxs-lookup"><span data-stu-id="8afba-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="8afba-170">按兩下**猜測不正確**將它展開工作流程設計工具中的轉換。</span><span class="sxs-lookup"><span data-stu-id="8afba-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="8afba-171">請注意，**觸發程序**已經設定為相同**ReadInt**所使用的活動**猜測正確**轉換。</span><span class="sxs-lookup"><span data-stu-id="8afba-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="8afba-172">將下列運算式輸入到**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="8afba-173">拖曳**如果**活動從**控制流程**區段**工具箱**並將它放**動作**轉換的區段。</span><span class="sxs-lookup"><span data-stu-id="8afba-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="8afba-174">將下列運算式輸入到**如果**活動的**條件**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="8afba-175">拖放兩**WriteLine**活動從**基本型別**區段**工具箱**，讓其中一項是置於**然後**區段**如果**活動和一個處於**Else** > 一節。</span><span class="sxs-lookup"><span data-stu-id="8afba-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="8afba-176">按一下**WriteLine**中的活動**然後**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="8afba-177">按一下**WriteLine**中的活動**Else**區段來選取它，然後輸入下列運算式**文字**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="8afba-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="8afba-178">傳回的整體狀態機器工作流程設計工具檢視中的，依序按一下**StateMachine**階層顯示在工作流程設計工具的頂端。</span><span class="sxs-lookup"><span data-stu-id="8afba-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="8afba-179">下列範例示範完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="8afba-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="8afba-180">![已完成狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="8afba-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="8afba-181">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="8afba-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="8afba-182">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="8afba-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="8afba-183">如需有關如何執行工作流程，指示，請參閱下一個主題中，[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="8afba-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="8afba-184">如果您已經完成[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)步驟來搭配不同的工作流程的樣式和想要執行此程式碼使用狀態機器工作流程，此步驟中的，跳到[建置並執行應用程式](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)區段[如何： 執行工作流程](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="8afba-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afba-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8afba-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="8afba-186">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="8afba-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="8afba-187">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="8afba-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="8afba-188">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="8afba-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="8afba-189">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="8afba-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="8afba-190">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="8afba-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
