---
title: HOW TO：建立活動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402503"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="318a5-102">HOW TO：建立活動</span><span class="sxs-lookup"><span data-stu-id="318a5-102">How to: Create an Activity</span></span>
<span data-ttu-id="318a5-103">活動是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的行為核心單位。</span><span class="sxs-lookup"><span data-stu-id="318a5-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="318a5-104">活動的執行邏輯可以實作在 Managed 程式碼中，或是使用其他活動來實作。</span><span class="sxs-lookup"><span data-stu-id="318a5-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="318a5-105">本主題示範如何建立兩個活動。</span><span class="sxs-lookup"><span data-stu-id="318a5-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="318a5-106">第一個活動是簡單的活動，使用程式碼來實作其執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="318a5-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="318a5-107">第二個活動的實作則是使用其他活動來定義。</span><span class="sxs-lookup"><span data-stu-id="318a5-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="318a5-108">教學課程中的下列步驟將會使用這些活動。</span><span class="sxs-lookup"><span data-stu-id="318a5-108">These activities are used in following steps in the tutorial.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="318a5-109">若要下載教學課程的完整的版本，請參閱[Windows Workflow Foundation (WF45)-入門教學課程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="318a5-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-activity-library-project"></a><span data-ttu-id="318a5-110">建立活動程式庫專案</span><span class="sxs-lookup"><span data-stu-id="318a5-110">To create the activity library project</span></span>  
  
1.  <span data-ttu-id="318a5-111">開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，然後選擇 **新增**，**專案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="318a5-111">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and choose **New**,  **Project** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="318a5-112">依序展開**其他專案類型**中的節點**已安裝**，**範本**清單，然後選取**Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="318a5-112">Expand the **Other Project Types** node in the **Installed**, **Templates** list and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="318a5-113">選取 **空白方案**從**Visual Studio 方案**清單。</span><span class="sxs-lookup"><span data-stu-id="318a5-113">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="318a5-114">確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。</span><span class="sxs-lookup"><span data-stu-id="318a5-114">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="318a5-115">型別`WF45GettingStartedTutorial`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="318a5-115">Type `WF45GettingStartedTutorial` in the **Name** box and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="318a5-116">以滑鼠右鍵按一下**WF45GettingStartedTutorial**中**方案總管**，然後選擇 **新增**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="318a5-116">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="318a5-117">如果沒有顯示 [ **方案總管** ] 視窗，請選取 [ **檢視** ] 功能表上的 [ **方案總管** ]。</span><span class="sxs-lookup"><span data-stu-id="318a5-117">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="318a5-118">在 [ **已安裝** ] 節點中，選取 [ **Visual C#**]、[ **工作流程** ] (或 [ **Visual Basic**]、[ **工作流程**])。</span><span class="sxs-lookup"><span data-stu-id="318a5-118">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span> <span data-ttu-id="318a5-119">請確認 **.NET Framework 4.5**中選取[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]版本下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="318a5-119">Ensure that **.NET Framework 4.5** is selected in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version drop-down list.</span></span> <span data-ttu-id="318a5-120">選取 **活動程式庫**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="318a5-120">Select **Activity Library** from the **Workflow** list.</span></span> <span data-ttu-id="318a5-121">型別`NumberGuessWorkflowActivities`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="318a5-121">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="318a5-122">依據設定哪個程式語言為 Visual Studio 主要語言而異，[ **Visual C#** ] 或 [ **Visual Basic** ] 節點可能會顯示在 [ **已安裝** ] 節點中的 [ **其他語言** ] 節點下。</span><span class="sxs-lookup"><span data-stu-id="318a5-122">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
6.  <span data-ttu-id="318a5-123">以滑鼠右鍵按一下**Activity1.xaml**中**方案總管**，然後選擇 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="318a5-123">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="318a5-124">按一下 [ **確定** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="318a5-124">Click **OK** to confirm.</span></span>  
  
### <a name="to-create-the-readint-activity"></a><span data-ttu-id="318a5-125">若要建立 ReadInt 活動</span><span class="sxs-lookup"><span data-stu-id="318a5-125">To create the ReadInt activity</span></span>  
  
1.  <span data-ttu-id="318a5-126">選擇**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="318a5-126">Choose **Add New Item** from the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="318a5-127">在 **已安裝**，**通用的項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="318a5-127">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="318a5-128">選取 **程式碼活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="318a5-128">Select **Code Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="318a5-129">型別`ReadInt`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="318a5-129">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="318a5-130">以下列定義取代現有的 `ReadInt` 定義。</span><span class="sxs-lookup"><span data-stu-id="318a5-130">Replace the existing `ReadInt` definition with the following definition.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="318a5-131">`ReadInt` 活動衍生自 <xref:System.Activities.NativeActivity%601>，而不是程式碼活動範本預設的 <xref:System.Activities.CodeActivity>。</span><span class="sxs-lookup"><span data-stu-id="318a5-131">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="318a5-132">如果活動提供單一結果 (透過 <xref:System.Activities.CodeActivity%601> 引數公開)，則可使用 <xref:System.Activities.Activity%601.Result%2A>，但 <xref:System.Activities.CodeActivity%601> 不支援使用書籤，因而會使用 <xref:System.Activities.NativeActivity%601>。</span><span class="sxs-lookup"><span data-stu-id="318a5-132"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>  
  
### <a name="to-create-the-prompt-activity"></a><span data-ttu-id="318a5-133">若要建立提示活動</span><span class="sxs-lookup"><span data-stu-id="318a5-133">To create the Prompt activity</span></span>  
  
1.  <span data-ttu-id="318a5-134">按 CTRL+SHIFT+B 以建置專案。</span><span class="sxs-lookup"><span data-stu-id="318a5-134">Press CTRL+SHIFT+B to build the project.</span></span> <span data-ttu-id="318a5-135">建置專案可將此專案中的 `ReadInt` 活動用來建置此步驟中的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="318a5-135">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>  
  
2.  <span data-ttu-id="318a5-136">選擇**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="318a5-136">Choose **Add New Item** from the **Project** menu.</span></span>  
  
3.  <span data-ttu-id="318a5-137">在 **已安裝**，**通用的項目**節點中，選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="318a5-137">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="318a5-138">選取 **活動**從**工作流程**清單。</span><span class="sxs-lookup"><span data-stu-id="318a5-138">Select **Activity** from the **Workflow** list.</span></span>  
  
4.  <span data-ttu-id="318a5-139">型別`Prompt`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="318a5-139">Type `Prompt` into the **Name** box and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="318a5-140">按兩下**Prompt.xaml**中**方案總管 中**如果未顯示在設計工具中顯示它。</span><span class="sxs-lookup"><span data-stu-id="318a5-140">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>  
  
6.  <span data-ttu-id="318a5-141">按一下 **引數**中要顯示在活動設計工具的左下方**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="318a5-141">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>  
  
7.  <span data-ttu-id="318a5-142">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="318a5-142">Click **Create Argument**.</span></span>  
  
8.  <span data-ttu-id="318a5-143">型別`BookmarkName`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="318a5-143">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
9. <span data-ttu-id="318a5-144">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="318a5-144">Click **Create Argument**.</span></span>  
  
10. <span data-ttu-id="318a5-145">型別`Result`成**名稱**是在新加入的方塊`BookmarkName`引數，選取**Out**從**方向**下拉式清單中，選取**Int32**從**引數型別**下拉式清單，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="318a5-145">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
11. <span data-ttu-id="318a5-146">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="318a5-146">Click **Create Argument**.</span></span>  
  
12. <span data-ttu-id="318a5-147">型別`Text`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**字串**從**引數型別**下拉式清單，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="318a5-147">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
     <span data-ttu-id="318a5-148">這三個引數會繫結至下列步驟中加入至 <xref:System.Activities.Statements.WriteLine> 活動之 `ReadInt` 和 `Prompt` 活動的對應引數。</span><span class="sxs-lookup"><span data-stu-id="318a5-148">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>  
  
13. <span data-ttu-id="318a5-149">按一下 **引數**關閉的活動設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="318a5-149">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
14. <span data-ttu-id="318a5-150">拖曳**順序**活動，從**控制流程**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**提示**活動設計工具。</span><span class="sxs-lookup"><span data-stu-id="318a5-150">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="318a5-151">如果**工具箱**未顯示視窗中，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="318a5-151">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
15. <span data-ttu-id="318a5-152">拖曳**WriteLine**活動，從**基本型別**一節**工具箱**拖曳至**活動拖曳到這裏**的標籤**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="318a5-152">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>  
  
16. <span data-ttu-id="318a5-153">繫結**文字**引數**WriteLine**活動**文字**引數**提示**活動輸入`Text`到**輸入 C# 運算式**或是**輸入 VB 運算式**方塊中**屬性**視窗中，然後再按 TAB 鍵兩次。</span><span class="sxs-lookup"><span data-stu-id="318a5-153">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the TAB key two times.</span></span> <span data-ttu-id="318a5-154">這樣會將選項移出屬性外，以關閉 IntelliSense 清單成員視窗並儲存屬性值。</span><span class="sxs-lookup"><span data-stu-id="318a5-154">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="318a5-155">這個屬性也可以設定輸入`Text`成**輸入 C# 運算式**或是**輸入 VB 運算式**活動本身的方塊。</span><span class="sxs-lookup"><span data-stu-id="318a5-155">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="318a5-156">如果**屬性 視窗**顯示，請選取**屬性視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="318a5-156">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
17. <span data-ttu-id="318a5-157">拖曳**ReadInt**活動，從**NumberGuessWorkflowActivities**一節**工具箱**並將它放**順序**活動中，讓它遵循**WriteLine**活動。</span><span class="sxs-lookup"><span data-stu-id="318a5-157">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>  
  
18. <span data-ttu-id="318a5-158">繫結**BookmarkName**引數**ReadInt**活動**BookmarkName**引數**提示**輸入活動`BookmarkName`成**輸入 VB 運算式**右邊的方塊**BookmarkName**中的引數**屬性 視窗**，然後按下 TAB 鍵兩個次關閉 IntelliSense 清單成員視窗並儲存屬性。</span><span class="sxs-lookup"><span data-stu-id="318a5-158">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the TAB key two times to close the IntelliSense list members window and save the property.</span></span>  
  
19. <span data-ttu-id="318a5-159">繫結**結果**引數**ReadInt**活動**結果**引數**提示**活動輸入`Result`到**輸入 VB 運算式**右邊的方塊**結果**中的引數**屬性 視窗**，然後按兩次 TAB 鍵。</span><span class="sxs-lookup"><span data-stu-id="318a5-159">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the TAB key two times.</span></span>  
  
20. <span data-ttu-id="318a5-160">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="318a5-160">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="318a5-161">如需如何使用這些活動中，建立工作流程的指示，請參閱下一步在教學課程中，[如何： 建立工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="318a5-161">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318a5-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="318a5-162">See Also</span></span>  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [<span data-ttu-id="318a5-163">設計及實作自訂活動</span><span class="sxs-lookup"><span data-stu-id="318a5-163">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [<span data-ttu-id="318a5-164">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="318a5-164">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="318a5-165">如何：建立工作流程</span><span class="sxs-lookup"><span data-stu-id="318a5-165">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="318a5-166">在自訂活動設計工具中使用 ExpressionTextBox</span><span class="sxs-lookup"><span data-stu-id="318a5-166">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
