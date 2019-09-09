---
title: 作法：建立狀態機器工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 451f9581ae997ad86fee968fa978713db2049455
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044392"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="28140-102">作法：建立狀態機器工作流程</span><span class="sxs-lookup"><span data-stu-id="28140-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="28140-103">工作流程可以從內建活動建構，也可以從自訂活動建構。</span><span class="sxs-lookup"><span data-stu-id="28140-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="28140-104">本主題將逐步說明如何建立使用內建活動（例如<xref:System.Activities.Statements.StateMachine>活動）的工作流程，以及先前[如何執行的自訂活動：建立活動](how-to-create-an-activity.md)主題。</span><span class="sxs-lookup"><span data-stu-id="28140-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="28140-105">此工作流程會以數字猜測遊戲為模型。</span><span class="sxs-lookup"><span data-stu-id="28140-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28140-106">「快速入門」教學課程中的每個主題都與之前的主題息息相關。</span><span class="sxs-lookup"><span data-stu-id="28140-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="28140-107">若要完成本主題，您必須先[完成如何：建立活動](how-to-create-an-activity.md)。</span><span class="sxs-lookup"><span data-stu-id="28140-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28140-108">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="28140-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="28140-109">建立工作流程</span><span class="sxs-lookup"><span data-stu-id="28140-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="28140-110">以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowactivities]** ，然後選取 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="28140-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="28140-111">在 [**已安裝**的**通用專案**] 節點中，選取 [**工作流程**]。</span><span class="sxs-lookup"><span data-stu-id="28140-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="28140-112">從 [**工作流程**] 清單中選取 [**活動**]。</span><span class="sxs-lookup"><span data-stu-id="28140-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="28140-113">在`StateMachineNumberGuessWorkflow` [**名稱**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="28140-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="28140-114">從 [**工具箱**] 的 [**狀態機器**] 區段中，將 [ **StateMachine** ] 活動拖放到工作流程設計介面上的 [在**此放置活動**] 標籤上。</span><span class="sxs-lookup"><span data-stu-id="28140-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="28140-115">若要建立工作流程變數和引數</span><span class="sxs-lookup"><span data-stu-id="28140-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="28140-116">按兩下**方案總管**中的 [ **StateMachineNumberGuessWorkflow** ]，在設計工具中顯示工作流程（如果尚未顯示）。</span><span class="sxs-lookup"><span data-stu-id="28140-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="28140-117">在工作流程設計工具的左下方按一下 [**引數**]，以顯示 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="28140-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="28140-118">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="28140-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="28140-119">在`MaxNumber` [**名稱**] 方塊中輸入，從 [**方向**] 下拉式清單中選取 [In]，選取 [自**變數型**別] 下拉式清單**中**的 [ **Int32** ]，然後按下 enter 以儲存引數。</span><span class="sxs-lookup"><span data-stu-id="28140-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="28140-120">按一下 [**建立引數**]。</span><span class="sxs-lookup"><span data-stu-id="28140-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="28140-121">在`Turns`新加入的引數下方輸入 [名稱] 方塊，從 [方向] 下拉式清單中選取 [Out]，選取 [引數型別] 下拉式清單中的 [Int32]，然後按 enter。 `MaxNumber`</span><span class="sxs-lookup"><span data-stu-id="28140-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="28140-122">在活動設計工具的左下方按一下 [**引數**]，以關閉 [**引數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="28140-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="28140-123">按一下工作流程設計工具左下方的 [**變數**]，以顯示 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="28140-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="28140-124">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="28140-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="28140-125">如果沒有顯示 [**建立變數**] 方塊，請<xref:System.Activities.Statements.StateMachine>按一下工作流程設計工具介面上的活動加以選取。</span><span class="sxs-lookup"><span data-stu-id="28140-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="28140-126">在`Guess` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="28140-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="28140-127">按一下 [**建立變數**]。</span><span class="sxs-lookup"><span data-stu-id="28140-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="28140-128">在`Target` [**名稱**] 方塊中輸入，從 [**變數類型**] 下拉式清單中選取 [ **Int32** ]，然後按 enter 儲存變數。</span><span class="sxs-lookup"><span data-stu-id="28140-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="28140-129">在活動設計工具的左下方按一下 [**變數**]，以關閉 [**變數**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="28140-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="28140-130">若要加入工作流程活動</span><span class="sxs-lookup"><span data-stu-id="28140-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="28140-131">按一下 [ **State1** ] 加以選取。</span><span class="sxs-lookup"><span data-stu-id="28140-131">Click **State1** to select it.</span></span> <span data-ttu-id="28140-132">在 [**屬性] 視窗**中，將 [ `Initialize Target`DisplayName] 變更為。</span><span class="sxs-lookup"><span data-stu-id="28140-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="28140-133">如果沒有顯示 [**屬性] 視窗**，請從 [**視圖**] 功能表中選取 [**屬性視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="28140-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="28140-134">在工作流程設計工具中，按兩下新重新命名的 [**初始化目標**] 狀態，將它展開。</span><span class="sxs-lookup"><span data-stu-id="28140-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="28140-135">將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [**專案**] 區段上。</span><span class="sxs-lookup"><span data-stu-id="28140-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="28140-136">在`Target` [**到**] 方塊中輸入，並在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="28140-137">如果沒有顯示 [**工具箱**] 視窗，請從 [**視圖**] 功能表中選取 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="28140-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="28140-138">在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。</span><span class="sxs-lookup"><span data-stu-id="28140-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="28140-139">將 [ **state** ] 活動從 [工具箱] 的 [**狀態機器**] 區段拖曳至工作流程設計**工具**，並將它放在 [**初始化目標**] 狀態上。</span><span class="sxs-lookup"><span data-stu-id="28140-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="28140-140">請注意，當新狀態超過時，會在**初始化目標**狀態周圍出現四個三角形。</span><span class="sxs-lookup"><span data-stu-id="28140-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="28140-141">將新狀態放置在 [**初始化目標**] 狀態正下方的三角形上。</span><span class="sxs-lookup"><span data-stu-id="28140-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="28140-142">這會將新的狀態放到工作流程上，並建立從**初始化目標**狀態到新狀態的轉換。</span><span class="sxs-lookup"><span data-stu-id="28140-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="28140-143">按一下 [ **State1** ] 加以選取，將 [ **DisplayName** ] 變更為`Enter Guess`，然後在工作流程設計工具中按兩下該狀態加以展開。</span><span class="sxs-lookup"><span data-stu-id="28140-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="28140-144">將 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [**專案**] 區段上。</span><span class="sxs-lookup"><span data-stu-id="28140-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="28140-145">在 [ **WriteLine**] 的 [ **Text** ] 屬性方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="28140-146">將 [ **Assign** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到狀態的 [結束 **] 區段。**</span><span class="sxs-lookup"><span data-stu-id="28140-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="28140-147">在`Turns` [**到**] 方塊中`Turns + 1`輸入，然後在 [**輸入C#運算式**] 或 [**輸入 VB 運算式**] 方塊中鍵入。</span><span class="sxs-lookup"><span data-stu-id="28140-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="28140-148">在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。</span><span class="sxs-lookup"><span data-stu-id="28140-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="28140-149">從 [**工具箱**] 的 [**狀態機器**] 區段中，將 [ **FinalState** ] 活動拖曳到 [**輸入猜測**] 狀態，然後將它放置到出現在 [**輸入猜測**] 狀態右邊的三角形上，如此一來，轉換就會是在**Enter 猜測**和**FinalState**之間建立。</span><span class="sxs-lookup"><span data-stu-id="28140-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="28140-150">轉換的預設名稱為**T2**。</span><span class="sxs-lookup"><span data-stu-id="28140-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="28140-151">按一下工作流程設計工具中的轉換來選取它，並將其**DisplayName**設定為 [**猜測正確**]。</span><span class="sxs-lookup"><span data-stu-id="28140-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="28140-152">然後，按一下並選取**FinalState**，並將其拖曳至右側，讓完整轉換名稱顯示空間，而不會覆迭兩個狀態的其中一個。</span><span class="sxs-lookup"><span data-stu-id="28140-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="28140-153">這將可以更容易完成教學課程中的其他步驟。</span><span class="sxs-lookup"><span data-stu-id="28140-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="28140-154">在工作流程設計工具中，按兩下新重新命名的 [**猜測正確**] 轉換，將其展開。</span><span class="sxs-lookup"><span data-stu-id="28140-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="28140-155">從 [**工具箱**] 的 [ **[numberguessworkflowactivities]** ] 區段中，將 [ **ReadInt** ] 活動拖放到轉換的 [**觸發**程式] 區段中。</span><span class="sxs-lookup"><span data-stu-id="28140-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="28140-156">在 [ **ReadInt** ] 活動的 [ `"EnterGuess"` **屬性] 視窗**中，在 [ **BookmarkName**屬性值] 方塊中輸入包含`Guess`引號，然後在 [**結果**] 屬性值方塊中輸入</span><span class="sxs-lookup"><span data-stu-id="28140-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="28140-157">在 [**猜測正確**轉換的**條件**] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="28140-158">在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。</span><span class="sxs-lookup"><span data-stu-id="28140-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="28140-159">收到觸發事件時會發生轉換，若有 <xref:System.Activities.Statements.Transition.Condition%2A> 存在，則會評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="28140-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="28140-160">在此轉換中，如果使用者`Guess`與隨機產生`Target`的相符，則控制權會傳遞至**FinalState** ，而且工作流程會完成。</span><span class="sxs-lookup"><span data-stu-id="28140-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="28140-161">視猜測是否正確而定，工作流程應該轉換成**FinalState** ，或回到另一個 Try 的**Enter 猜測**狀態。</span><span class="sxs-lookup"><span data-stu-id="28140-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="28140-162">這兩個轉換共用的觸發程式，會等待使用者透過**ReadInt**活動收到猜測。</span><span class="sxs-lookup"><span data-stu-id="28140-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="28140-163">這稱為共用轉換。</span><span class="sxs-lookup"><span data-stu-id="28140-163">This is called a shared transition.</span></span> <span data-ttu-id="28140-164">若要建立共用轉換，請按一下表示 [**猜測正確**] 轉換開始的圓形，然後將它拖曳至想要的狀態。</span><span class="sxs-lookup"><span data-stu-id="28140-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="28140-165">在此情況下，轉換是一種自我轉換，因此請將**猜測正確**轉換的起點拖放回 [**進入猜測**] 狀態的底部。</span><span class="sxs-lookup"><span data-stu-id="28140-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="28140-166">建立轉換之後，請在工作流程設計工具中選取它，並將其**DisplayName**屬性設定為 [**猜測不正確**]。</span><span class="sxs-lookup"><span data-stu-id="28140-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="28140-167">您也可以從轉換設計工具內建立共用轉換，方法是按一下轉換設計工具底部的 [**新增共用觸發程式轉換**]，然後從可用的狀態選取所需的目標狀態**以進行**連線下拉式。</span><span class="sxs-lookup"><span data-stu-id="28140-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="28140-168">請注意，如果轉換的 <xref:System.Activities.Statements.Transition.Condition%2A> 值評估為 `false` (或所有共用觸發轉換的條件皆評估為 `false`)，則不會發生轉換，且會重新排程該狀態之所有轉換的所有觸發。</span><span class="sxs-lookup"><span data-stu-id="28140-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="28140-169">由於設定條件的方式，在本教學課程中不會發生這種情況 (我們對於猜測是否正確有具體的動作)。</span><span class="sxs-lookup"><span data-stu-id="28140-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="28140-170">在工作流程設計工具中按兩下 [**猜測不正確**] 轉換，將其展開。</span><span class="sxs-lookup"><span data-stu-id="28140-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="28140-171">請注意，此**觸發**程式已設定為「**猜測正確**」轉換所使用的相同**ReadInt**活動。</span><span class="sxs-lookup"><span data-stu-id="28140-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="28140-172">在 [**條件**] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="28140-173">從 [**工具箱**] 的 [**控制流程**] 區段，將 [ **If** ] 活動拖放到轉換的 [**動作**] 區段中。</span><span class="sxs-lookup"><span data-stu-id="28140-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="28140-174">在 [ **If** ] 活動的 [ **Condition** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="28140-175">將兩個 [ **WriteLine** ] 活動從 [**工具箱**] 的 [**基本**] 區段拖放到 [ **if** ] 活動的 [ **Then** ] 區段，其中一個是在 [ **Else** ] 區段中。</span><span class="sxs-lookup"><span data-stu-id="28140-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="28140-176">按一下 [ **Then** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="28140-177">按一下 [ **Else** ] 區段中的 [ **WriteLine** ] 活動加以選取，然後在 [ **Text** ] 屬性值方塊中輸入下列運算式。</span><span class="sxs-lookup"><span data-stu-id="28140-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="28140-178">在工作流程設計工具頂端的階層連結顯示中，按一下 [ **StateMachine** ]，返回 [整體狀態機器] 視圖。</span><span class="sxs-lookup"><span data-stu-id="28140-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="28140-179">下列範例示範完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="28140-179">The following example illustrates the completed workflow.</span></span>  
  
     ![顯示已完成狀態機器工作流程的圖例。](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="28140-181">若要建置工作流程</span><span class="sxs-lookup"><span data-stu-id="28140-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="28140-182">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="28140-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="28140-183">如需有關如何執行工作流程的指示，請參閱下一個主題[：如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="28140-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="28140-184">如果您已經完成[如何：使用不同的](how-to-run-a-workflow.md)工作流程樣式執行工作流程步驟，並想要從這個步驟使用狀態機器工作流程執行它，然後直接跳[到](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [如何：執行工作流程](how-to-run-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="28140-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28140-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28140-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="28140-186">Windows Workflow Foundation 程式設計</span><span class="sxs-lookup"><span data-stu-id="28140-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="28140-187">設計工作流程</span><span class="sxs-lookup"><span data-stu-id="28140-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="28140-188">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="28140-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="28140-189">如何：建立活動</span><span class="sxs-lookup"><span data-stu-id="28140-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="28140-190">如何：執行工作流程</span><span class="sxs-lookup"><span data-stu-id="28140-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
