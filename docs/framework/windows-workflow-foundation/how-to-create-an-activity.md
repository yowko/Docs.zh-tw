---
title: HOW TO：建立活動
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 48df9b90a92468858bd3ac5498bd83fd0d57fe75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315136"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="c6c05-102">HOW TO：建立活動</span><span class="sxs-lookup"><span data-stu-id="c6c05-102">How to: Create an Activity</span></span>

<span data-ttu-id="c6c05-103">活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。</span><span class="sxs-lookup"><span data-stu-id="c6c05-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="c6c05-104">活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。</span><span class="sxs-lookup"><span data-stu-id="c6c05-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="c6c05-105">本主題示範如何建立兩個活動。</span><span class="sxs-lookup"><span data-stu-id="c6c05-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="c6c05-106">第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="c6c05-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="c6c05-107">第二個活動的實作則是使用其他活動來定義。</span><span class="sxs-lookup"><span data-stu-id="c6c05-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="c6c05-108">教學課程中的下列步驟將會使用這些活動。</span><span class="sxs-lookup"><span data-stu-id="c6c05-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c05-109">若要下載教學課程的完整版本，請參閱 [Windows Workflow Foundation (WF45) - 快速入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="c6c05-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="c6c05-110">建立活動程式庫專案</span><span class="sxs-lookup"><span data-stu-id="c6c05-110">Create the activity library project</span></span>

1. <span data-ttu-id="c6c05-111">開啟 Visual Studio，然後選擇**的新** > **專案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="c6c05-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="c6c05-112">在 **新的專案**對話方塊底下**已安裝**類別目錄中，選取**Visual C#** > **工作流程**(或**Visual Basic** > **流程**)。</span><span class="sxs-lookup"><span data-stu-id="c6c05-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6c05-113">如果您沒有看到**工作流程**範本類別，您可能需要安裝**Windows Workflow Foundation** Visual Studio 的元件。</span><span class="sxs-lookup"><span data-stu-id="c6c05-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="c6c05-114">選擇**開啟的 Visual Studio 安裝程式**左手邊的連結**新的專案**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c6c05-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="c6c05-115">在 Visual Studio 安裝程式中，選取**個別元件** 索引標籤。然後，在**開發活動**類別目錄中，選取**Windows Workflow Foundation**元件。</span><span class="sxs-lookup"><span data-stu-id="c6c05-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="c6c05-116">選擇**修改**安裝元件。</span><span class="sxs-lookup"><span data-stu-id="c6c05-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="c6c05-117">選取 **活動程式庫**專案範本。</span><span class="sxs-lookup"><span data-stu-id="c6c05-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="c6c05-118">型別`NumberGuessWorkflowActivities`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="c6c05-119">以滑鼠右鍵按一下**Activity1.xaml**中**方案總管**，然後選擇 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="c6c05-120">按一下 [ **確定** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="c6c05-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="c6c05-121">建立 ReadInt 活動</span><span class="sxs-lookup"><span data-stu-id="c6c05-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="c6c05-122">選擇**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="c6c05-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="c6c05-123">在 **已安裝** > **通用的項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="c6c05-124">選取 **程式碼活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="c6c05-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="c6c05-125">型別`ReadInt`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="c6c05-126">以下列定義取代現有的 `ReadInt` 定義。</span><span class="sxs-lookup"><span data-stu-id="c6c05-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="c6c05-127">`ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。</span><span class="sxs-lookup"><span data-stu-id="c6c05-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <xref:System.Activities.CodeActivity%601> <span data-ttu-id="c6c05-128">如果活動提供單一的結果，透過公開可用<xref:System.Activities.Activity%601.Result%2A>引數，但<xref:System.Activities.CodeActivity%601>因此不支援使用書籤，<xref:System.Activities.NativeActivity%601>用。</span><span class="sxs-lookup"><span data-stu-id="c6c05-128">can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="c6c05-129">建立提示活動</span><span class="sxs-lookup"><span data-stu-id="c6c05-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="c6c05-130">按下**Ctrl**+**Shift**+**B**來建置專案。</span><span class="sxs-lookup"><span data-stu-id="c6c05-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="c6c05-131">建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="c6c05-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="c6c05-132">選擇**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="c6c05-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="c6c05-133">在 **已安裝** > **通用的項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="c6c05-134">選取 **活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="c6c05-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="c6c05-135">型別`Prompt`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="c6c05-136">按兩下**Prompt.xaml**中**方案總管 中**如果未顯示在設計工具中顯示它。</span><span class="sxs-lookup"><span data-stu-id="c6c05-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="c6c05-137">按一下 **引數**中要顯示在活動設計工具的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="c6c05-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="c6c05-138">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="c6c05-139">型別`BookmarkName`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下**Enter**儲存引數。</span><span class="sxs-lookup"><span data-stu-id="c6c05-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="c6c05-140">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="c6c05-141">型別`Result`成**名稱**是在新加入的方塊`BookmarkName`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="c6c05-142">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="c6c05-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="c6c05-143">型別`Text`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下**Enter**儲存引數。</span><span class="sxs-lookup"><span data-stu-id="c6c05-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="c6c05-144">這三個引數會繫結至下列步驟中加入至 <xref:System.Activities.Statements.WriteLine> 活動之 `ReadInt` 和 `Prompt` 活動的對應引數。</span><span class="sxs-lookup"><span data-stu-id="c6c05-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="c6c05-145">按一下 **引數**關閉的活動設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="c6c05-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="c6c05-146">拖曳**順序**活動，從**控制流程**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**提示**活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="c6c05-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="c6c05-147">如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="c6c05-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="c6c05-148">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="c6c05-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="c6c05-149">繫結**文字**引數**WriteLine**活動**文字**引數**提示**活動輸入`Text`到**輸入 C# 運算式**或是**輸入 VB 運算式**方塊中**屬性**視窗，然後再按**索引標籤**索引鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="c6c05-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="c6c05-150">這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。</span><span class="sxs-lookup"><span data-stu-id="c6c05-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="c6c05-151">這個屬性也可以設定輸入`Text`成**輸入 C# 運算式**或是**輸入 VB 運算式**活動本身的方塊。</span><span class="sxs-lookup"><span data-stu-id="c6c05-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="c6c05-152">如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="c6c05-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="c6c05-153">拖曳**ReadInt**活動，從**NumberGuessWorkflowActivities**一節**工具箱**並將它放**順序**活動中，讓它遵循**WriteLine**活動。</span><span class="sxs-lookup"><span data-stu-id="c6c05-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="c6c05-154">繫結 **BookmarkName** 引數 **ReadInt** 活動 **BookmarkName** 引數 **提示** 輸入活動 `BookmarkName` 成 **輸入 VB 運算式** 右邊的方塊 **BookmarkName** 中的引數 **屬性 視窗**，然後按 **索引標籤** 鍵關閉 IntelliSense 清單成員視窗並儲存屬性的兩倍。</span><span class="sxs-lookup"><span data-stu-id="c6c05-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="c6c05-155">繫結 **結果** 引數 **ReadInt** 活動 **結果** 引數 **提示** 活動輸入 `Result` 到 **輸入 VB 運算式** 右邊的方塊 **結果** 中的引數 **屬性 視窗** ，然後按下 **索引標籤** 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="c6c05-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="c6c05-156">按下**Ctrl**+**Shift**+**B**建置方案。</span><span class="sxs-lookup"><span data-stu-id="c6c05-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6c05-157">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c6c05-157">Next steps</span></span>

<span data-ttu-id="c6c05-158">如需如何使用這些活動中，建立工作流程的指示，請參閱下一步在教學課程中， [How to:建立工作流程](how-to-create-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c05-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6c05-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6c05-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="c6c05-160">設計和實作自訂活動</span><span class="sxs-lookup"><span data-stu-id="c6c05-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="c6c05-161">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="c6c05-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="c6c05-162">HOW TO：建立工作流程</span><span class="sxs-lookup"><span data-stu-id="c6c05-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="c6c05-163">使用自訂活動設計工具中的 ExpressionTextBox</span><span class="sxs-lookup"><span data-stu-id="c6c05-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)