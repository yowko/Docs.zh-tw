---
title: 在 .NET Framework 4 工作流程中使用 Interop 活動
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466721"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a><span data-ttu-id="d9d35-102">在 .NET Framework 4 工作流程中使用 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-102">Using the Interop Activity in a .NET Framework 4 Workflow</span></span>
<span data-ttu-id="d9d35-103">使用 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 或 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 建立的活動，可以經由使用 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 活動，在 <xref:System.Activities.Statements.Interop> 工作流程中使用。</span><span class="sxs-lookup"><span data-stu-id="d9d35-103">Activities created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] or [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] can be used in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow by using the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="d9d35-104">本主題提供使用 <xref:System.Activities.Statements.Interop> 活動的概觀。</span><span class="sxs-lookup"><span data-stu-id="d9d35-104">This topic provides an overview of using the <xref:System.Activities.Statements.Interop> activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9d35-105"><xref:System.Activities.Statements.Interop>活動不會顯示在工作流程設計工具工具箱除非工作流程的專案具有其**目標 Framework**設定設為 **.Net Framework 4**或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d9d35-105">The <xref:System.Activities.Statements.Interop> activity does not appear in the workflow designer toolbox unless the workflow's project has its **Target Framework** setting set to **.Net Framework 4** or later.</span></span>  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a><span data-ttu-id="d9d35-106">在 .NET Framework 4.5 Workflows 中使用 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-106">Using the Interop Activity in .NET Framework 4.5 Workflows</span></span>  
 <span data-ttu-id="d9d35-107">在本主題中，會建立一個 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動程式庫，其中包含 `DiscountCalculator` 活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-107">In this topic, a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity library is created that contains a `DiscountCalculator` activity.</span></span> <span data-ttu-id="d9d35-108">`DiscountCalculator` 會根據購買金額計算折扣，並且由包含 <xref:System.Workflow.Activities.SequenceActivity> 的 <xref:System.Workflow.Activities.PolicyActivity> 組成。</span><span class="sxs-lookup"><span data-stu-id="d9d35-108">The `DiscountCalculator` calculates a discount based on a purchase amount and consists of a <xref:System.Workflow.Activities.SequenceActivity> that contains a <xref:System.Workflow.Activities.PolicyActivity>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9d35-109">在本主題中建立的 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動會使用 <xref:System.Workflow.Activities.PolicyActivity> 實作活動的邏輯。</span><span class="sxs-lookup"><span data-stu-id="d9d35-109">The [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity created in this topic uses a <xref:System.Workflow.Activities.PolicyActivity> to implement the logic of the activity.</span></span> <span data-ttu-id="d9d35-110">不需使用自訂的 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動或 <xref:System.Activities.Statements.Interop> 活動，即可在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程中使用規則。</span><span class="sxs-lookup"><span data-stu-id="d9d35-110">It is not required to use a custom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] activity or the <xref:System.Activities.Statements.Interop> activity in order to use rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow.</span></span> <span data-ttu-id="d9d35-111">如需範例的使用中的規則[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]而不使用的工作流程<xref:System.Activities.Statements.Interop>活動，請參閱[.NET Framework 4.5 中的原則活動](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d9d35-111">For an example of using rules in a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow without using the <xref:System.Activities.Statements.Interop> activity, see the [Policy Activity in .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) sample.</span></span>  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a><span data-ttu-id="d9d35-112">若要建立 .NET Framework 3.5 活動程式庫專案</span><span class="sxs-lookup"><span data-stu-id="d9d35-112">To create the .NET Framework 3.5 activity library project</span></span>  
  
1.  <span data-ttu-id="d9d35-113">開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，然後選取**新增**，然後**專案...**</span><span class="sxs-lookup"><span data-stu-id="d9d35-113">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New** and then **Project…**</span></span> <span data-ttu-id="d9d35-114">從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d9d35-114">from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="d9d35-115">依序展開**其他專案類型**中的節點**已安裝的範本**窗格，然後選取**Visual Studio 方案**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-115">Expand the **Other Project Types** node in the **Installed Templates** pane and select **Visual Studio Solutions**.</span></span>  
  
3.  <span data-ttu-id="d9d35-116">選取 **空白方案**從**Visual Studio 方案**清單。</span><span class="sxs-lookup"><span data-stu-id="d9d35-116">Select **Blank Solution** from the **Visual Studio Solutions** list.</span></span> <span data-ttu-id="d9d35-117">型別`PolicyInteropDemo`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-117">Type `PolicyInteropDemo` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="d9d35-118">以滑鼠右鍵按一下**PolicyInteropDemo**中**方案總管**，然後選取**新增**，然後**新專案...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-118">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add** and then **New Project…**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d9d35-119">如果**方案總管**視窗未顯示，選取**方案總管**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="d9d35-119">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="d9d35-120">在 **已安裝的範本**清單中，選取**Visual C#** ，然後**流程**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-120">In the **Installed Templates** list, select **Visual C#** and then **Workflow**.</span></span> <span data-ttu-id="d9d35-121">選取  **.NET Framework 3.5**從.NET Framework 版本下拉式清單中，然後選取**Workflow Activity Library**從**範本**清單。</span><span class="sxs-lookup"><span data-stu-id="d9d35-121">Select **.NET Framework 3.5** from the .NET Framework version drop-down list, and then select **Workflow Activity Library** from the **Templates** list.</span></span>  
  
6.  <span data-ttu-id="d9d35-122">型別`PolicyActivityLibrary`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-122">Type `PolicyActivityLibrary` in the **Name** box and click **OK**.</span></span>  
  
7.  <span data-ttu-id="d9d35-123">以滑鼠右鍵按一下**Activity1.cs**中**方案總管**，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-123">Right-click **Activity1.cs** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="d9d35-124">按一下 [ **確定** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="d9d35-124">Click **OK** to confirm.</span></span>  
  
#### <a name="to-create-the-discountcalculator-activity"></a><span data-ttu-id="d9d35-125">若要建立 DiscountCalculator 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-125">To create the DiscountCalculator activity</span></span>  
  
1.  <span data-ttu-id="d9d35-126">以滑鼠右鍵按一下**PolicyActivityLibrary**中**方案總管**，然後選取**新增**，然後**活動...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-126">Right-click **PolicyActivityLibrary** in **Solution Explorer** and select **Add** and then **Activity…**.</span></span>  
  
2.  <span data-ttu-id="d9d35-127">選取 **活動 （程式碼分開置放）** 從**Visual C# 項目**清單。</span><span class="sxs-lookup"><span data-stu-id="d9d35-127">Select **Activity (with code separation)** from the **Visual C# Items** list.</span></span> <span data-ttu-id="d9d35-128">型別`DiscountCalculator`中**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-128">Type `DiscountCalculator` in the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="d9d35-129">以滑鼠右鍵按一下**DiscountCalculator.xoml**中**方案總管**，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-129">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Code**.</span></span>  
  
4.  <span data-ttu-id="d9d35-130">將下列三個屬性加入至 `DiscountCalculator` 類別。</span><span class="sxs-lookup"><span data-stu-id="d9d35-130">Add the following three properties to the `DiscountCalculator` class.</span></span>  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  <span data-ttu-id="d9d35-131">以滑鼠右鍵按一下**DiscountCalculator.xoml**中**方案總管**，然後選取**檢視表設計工具**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-131">Right-click **DiscountCalculator.xoml** in **Solution Explorer** and select **View Designer**.</span></span>  
  
6.  <span data-ttu-id="d9d35-132">拖曳**原則**活動，從**Windows Workflow v3.0**一節**工具箱**並將它放**DiscountCalculator**活動.</span><span class="sxs-lookup"><span data-stu-id="d9d35-132">Drag a **Policy** activity from the **Windows Workflow v3.0** section of the **Toolbox** and drop it in the **DiscountCalculator** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d9d35-133">如果**工具箱**視窗未顯示，選取**工具箱**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="d9d35-133">If the **Toolbox** window is not visible, select **Toolbox** from the **View** menu.</span></span>  
  
#### <a name="to-configure-the-rules"></a><span data-ttu-id="d9d35-134">若要設定規則</span><span class="sxs-lookup"><span data-stu-id="d9d35-134">To configure the rules</span></span>  
  
1.  <span data-ttu-id="d9d35-135">按一下 新增**原則**來選取它，如果尚未選取的活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-135">Click the newly added **Policy** activity to select it, if it is not already selected.</span></span>  
  
2.  <span data-ttu-id="d9d35-136">按一下  **RuleSetReference**中的屬性**屬性**視窗來加以選取，然後按一下屬性右邊的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="d9d35-136">Click the **RuleSetReference** property in the **Properties** window to select it, and click the ellipsis button to the right of the property.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d9d35-137">如果**屬性**看不到視窗中，選擇**屬性視窗**從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="d9d35-137">If the **Properties** window is not visible, choose **Properties Window** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="d9d35-138">選取**按一下 [新增]...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-138">Select **Click New…**.</span></span>  
  
4.  <span data-ttu-id="d9d35-139">按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-139">Click **Add Rule**.</span></span>  
  
5.  <span data-ttu-id="d9d35-140">輸入下列運算式**條件** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-140">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  <span data-ttu-id="d9d35-141">輸入下列運算式**Then 動作** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-141">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  <span data-ttu-id="d9d35-142">按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-142">Click **Add Rule**.</span></span>  
  
8.  <span data-ttu-id="d9d35-143">輸入下列運算式**條件** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-143">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. <span data-ttu-id="d9d35-144">輸入下列運算式**Then 動作** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-144">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. <span data-ttu-id="d9d35-145">按一下 **新增規則**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-145">Click **Add Rule**.</span></span>  
  
11. <span data-ttu-id="d9d35-146">輸入下列運算式**條件** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-146">Type the following expression into the **Condition** box.</span></span>  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. <span data-ttu-id="d9d35-147">輸入下列運算式**Then 動作** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-147">Type the following expression into the **Then Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. <span data-ttu-id="d9d35-148">輸入下列運算式**Else 動作** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="d9d35-148">Type the following expression into the **Else Actions** box.</span></span>  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. <span data-ttu-id="d9d35-149">按一下 [ **[確定]** 以關閉**規則集編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9d35-149">Click **OK** to close the **Rule Set Editor** dialog box.</span></span>  
  
15. <span data-ttu-id="d9d35-150">請確認新建立<xref:System.Workflow.Activities.Rules.RuleSet>中選取**名稱**清單，然後按**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-150">Ensure that the newly-created <xref:System.Workflow.Activities.Rules.RuleSet> is selected in the **Name** list, and click **OK**.</span></span>  
  
16. <span data-ttu-id="d9d35-151">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="d9d35-151">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
 <span data-ttu-id="d9d35-152">下列程式碼範例顯示在本程序中加入至 `DiscountCalculator` 活動的規則。</span><span class="sxs-lookup"><span data-stu-id="d9d35-152">The rules added to the `DiscountCalculator` activity in this procedure are shown in the following code example.</span></span>  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 <span data-ttu-id="d9d35-153">執行 <xref:System.Workflow.Activities.PolicyActivity> 時，這三個規則會評估並修改 `Subtotal` 活動的 `DiscountPercent`、`Total` 及 `DiscountCalculator` 屬性值，以計算所需的折扣。</span><span class="sxs-lookup"><span data-stu-id="d9d35-153">When the <xref:System.Workflow.Activities.PolicyActivity> executes, these three rules evaluate and modify the `Subtotal`, `DiscountPercent`, and `Total` property values of the `DiscountCalculator` activity to calculate the desired discount.</span></span>  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a><span data-ttu-id="d9d35-154">搭配使用 DiscountCalculator 活動與 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-154">Using the DiscountCalculator Activity with the Interop Activity</span></span>  
 <span data-ttu-id="d9d35-155">若要在 `DiscountCalculator` 工作流程內使用 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 活動，需使用 <xref:System.Activities.Statements.Interop> 活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-155">To use the `DiscountCalculator` activity inside a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow, the <xref:System.Activities.Statements.Interop> activity is used.</span></span> <span data-ttu-id="d9d35-156">本節中會建立兩個工作流程 (其中一個使用程式碼，另一個使用工作流程設計工具)，示範如何搭配使用 <xref:System.Activities.Statements.Interop> 活動與 `DiscountCalculator` 活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-156">In this section two workflows are created, one using code and one using the workflow designer, which show how to use the <xref:System.Activities.Statements.Interop> activity with the `DiscountCalculator` activity.</span></span> <span data-ttu-id="d9d35-157">兩個工作流程會使用同樣的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9d35-157">The same host application is used for both workflows.</span></span>  
  
#### <a name="to-create-the-host-application"></a><span data-ttu-id="d9d35-158">若要建立主應用程式</span><span class="sxs-lookup"><span data-stu-id="d9d35-158">To create the host application</span></span>  
  
1.  <span data-ttu-id="d9d35-159">以滑鼠右鍵按一下**PolicyInteropDemo**中**方案總管**，然後選取**新增**，然後**新專案...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-159">Right-click **PolicyInteropDemo** in **Solution Explorer** and select **Add**, and then **New Project…**.</span></span>  
  
2.  <span data-ttu-id="d9d35-160">請確認 **.NET Framework 4.5**已在.NET Framework 版本下拉式清單中，選取，然後選取**工作流程主控台應用程式**從**Visual C# 項目**清單。</span><span class="sxs-lookup"><span data-stu-id="d9d35-160">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list, and select  **Workflow Console Application** from the **Visual C# Items** list.</span></span>  
  
3.  <span data-ttu-id="d9d35-161">型別`PolicyInteropHost`成**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-161">Type `PolicyInteropHost` into the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="d9d35-162">以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-162">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="d9d35-163">在 **目標 framework**下拉式清單中，變更選取範圍 **.NET Framework 4 Client Profile**來 **.NET Framework 4.5**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-163">In the **Target framework** drop-down list, change the selection from **.NET Framework 4 Client Profile** to **.NET Framework 4.5**.</span></span> <span data-ttu-id="d9d35-164">按一下 **是**確認。</span><span class="sxs-lookup"><span data-stu-id="d9d35-164">Click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="d9d35-165">以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**加入參考...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-165">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
7.  <span data-ttu-id="d9d35-166">選取  **PolicyActivityLibrary**從**專案**索引標籤，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-166">Select **PolicyActivityLibrary** from the **Projects** tab and click **OK**.</span></span>  
  
8.  <span data-ttu-id="d9d35-167">以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**加入參考...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-167">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add Reference…**.</span></span>  
  
9. <span data-ttu-id="d9d35-168">選取  **System.Workflow.Activities**， **System.Workflow.ComponentModel**，然後**System.workflow.componentmodel**從 **.NET**索引標籤，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-168">Select **System.Workflow.Activities**, **System.Workflow.ComponentModel**, and then **System.Workflow.Runtime** from the **.NET** tab and click **OK**.</span></span>  
  
10. <span data-ttu-id="d9d35-169">以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-169">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
11. <span data-ttu-id="d9d35-170">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="d9d35-170">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="using-the-interop-activity-in-code"></a><span data-ttu-id="d9d35-171">在程式碼中使用 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-171">Using the Interop Activity in Code</span></span>  
 <span data-ttu-id="d9d35-172">在此範例中，會使用包含 <xref:System.Activities.Statements.Interop> 活動和 `DiscountCalculator` 活動的程式碼建立工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d9d35-172">In this example, a workflow definition is created using code that contains the <xref:System.Activities.Statements.Interop> activity and the `DiscountCalculator` activity.</span></span> <span data-ttu-id="d9d35-173">使用 <xref:System.Activities.WorkflowInvoker> 叫用這個工作流程，使用 <xref:System.Activities.Statements.WriteLine> 活動則會將規則評估的結果寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="d9d35-173">This workflow is invoked using <xref:System.Activities.WorkflowInvoker> and the results of the rule evaluation are written to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
##### <a name="to-use-the-interop-activity-in-code"></a><span data-ttu-id="d9d35-174">若要在程式碼中使用 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-174">To use the Interop activity in code</span></span>  
  
1.  <span data-ttu-id="d9d35-175">以滑鼠右鍵按一下**Program.cs**中**方案總管**，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-175">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="d9d35-176">將下列 `using` 陳述式加入至檔案最上方。</span><span class="sxs-lookup"><span data-stu-id="d9d35-176">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  <span data-ttu-id="d9d35-177">移除 `Main` 方法的內容，並以下列程式碼取代。</span><span class="sxs-lookup"><span data-stu-id="d9d35-177">Remove the contents of the `Main` method and replace with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  <span data-ttu-id="d9d35-178">在名為 `Program` 的 `CalculateDiscountUsingCodeWorkflow` 類別中建立新方法，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9d35-178">Create a new method in the `Program` class called `CalculateDiscountUsingCodeWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d9d35-179">`Subtotal` 活動的 `DiscountPercent`、`Total` 和 `DiscountCalculator` 屬性會以 <xref:System.Activities.Statements.Interop> 活動的引數形式出現，並且繫結至 <xref:System.Activities.Statements.Interop> 活動之 <xref:System.Activities.Statements.Interop.ActivityProperties%2A> 集合的本機工作流程變數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-179">The `Subtotal`, `DiscountPercent`, and `Total` properties of the `DiscountCalculator` activity are surfaced as arguments of the <xref:System.Activities.Statements.Interop> activity, and bound to local workflow variables in the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityProperties%2A> collection.</span></span> <span data-ttu-id="d9d35-180">`Subtotal` 會加入成為 <xref:System.Activities.ArgumentDirection.In> 引數，因為 `Subtotal` 資料會流入 <xref:System.Activities.Statements.Interop> 活動中，此外會加入 `DiscountPercent` 和 `Total` 做為 <xref:System.Activities.ArgumentDirection.Out> 引數，因為它們的資料會流出 <xref:System.Activities.Statements.Interop> 活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-180">`Subtotal` is added as an <xref:System.Activities.ArgumentDirection.In> argument because the `Subtotal` data flows into the <xref:System.Activities.Statements.Interop> activity, and `DiscountPercent` and `Total` are added as <xref:System.Activities.ArgumentDirection.Out> arguments because their data flows out of the <xref:System.Activities.Statements.Interop> activity.</span></span> <span data-ttu-id="d9d35-181">請注意，兩個 <xref:System.Activities.ArgumentDirection.Out> 引數是以 `DiscountPercentOut` 和 `TotalOut` 這兩個名稱加入，表示它們代表 <xref:System.Activities.ArgumentDirection.Out> 引數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-181">Note that the two <xref:System.Activities.ArgumentDirection.Out> arguments are added with the names `DiscountPercentOut` and `TotalOut` to indicate that they represent <xref:System.Activities.ArgumentDirection.Out> arguments.</span></span> <span data-ttu-id="d9d35-182">`DiscountCalculator` 型別會指定為 <xref:System.Activities.Statements.Interop> 活動的 <xref:System.Activities.Statements.Interop.ActivityType%2A>。</span><span class="sxs-lookup"><span data-stu-id="d9d35-182">The `DiscountCalculator` type is specified as the <xref:System.Activities.Statements.Interop> activity’s <xref:System.Activities.Statements.Interop.ActivityType%2A>.</span></span>  
  
5.  <span data-ttu-id="d9d35-183">按 CTRL+F5 建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9d35-183">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="d9d35-184">將 `Subtotal` 的值替換成不同的值，測試出 `DiscountCalculator` 活動所提供的不同折扣層級。</span><span class="sxs-lookup"><span data-stu-id="d9d35-184">Substitute different values for the `Subtotal` value to test out the different discount levels provided by the `DiscountCalculator` activity.</span></span>  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a><span data-ttu-id="d9d35-185">在工作流程設計工具中使用 Interop 活動</span><span class="sxs-lookup"><span data-stu-id="d9d35-185">Using the Interop Activity in the Workflow Designer</span></span>  
 <span data-ttu-id="d9d35-186">在這個範例中，會使用工作流程設計工具建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="d9d35-186">In this example, a workflow is created using the workflow designer.</span></span> <span data-ttu-id="d9d35-187">這個工作流程與上一個範例中的工作流程具有相同的功能，但不會使用 <xref:System.Activities.Statements.WriteLine> 活動顯示折扣，而是由主應用程式在工作流程完成時擷取並顯示折扣資訊。</span><span class="sxs-lookup"><span data-stu-id="d9d35-187">This workflow has the same functionality as the previous example, except than instead of using a <xref:System.Activities.Statements.WriteLine> activity to display the discount, the host application retrieves and displays the discount information when the workflow completes.</span></span> <span data-ttu-id="d9d35-188">同時，這個工作流程不使用區域工作流程變數來包含資料，而是在工作流程設計工具中建立引數，並在叫用工作流程時從主機傳入值。</span><span class="sxs-lookup"><span data-stu-id="d9d35-188">Also, instead of using local workflow variables to contain the data, arguments are created in the workflow designer and the values are passed in from the host when the workflow is invoked.</span></span>  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a><span data-ttu-id="d9d35-189">若要使用工作流程設計工具建立的工作流程裝載 PolicyActivity</span><span class="sxs-lookup"><span data-stu-id="d9d35-189">To host the PolicyActivity using a Workflow Designer-created workflow</span></span>  
  
1.  <span data-ttu-id="d9d35-190">以滑鼠右鍵按一下**Workflow1.xaml**中**方案總管**，然後選取**刪除**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-190">Right-click **Workflow1.xaml** in **Solution Explorer** and select **Delete**.</span></span> <span data-ttu-id="d9d35-191">按一下 [ **確定** ] 以確認。</span><span class="sxs-lookup"><span data-stu-id="d9d35-191">Click **OK** to confirm.</span></span>  
  
2.  <span data-ttu-id="d9d35-192">以滑鼠右鍵按一下**PolicyInteropHost**中**方案總管**，然後選取**新增**，**新項目...**.</span><span class="sxs-lookup"><span data-stu-id="d9d35-192">Right-click **PolicyInteropHost** in **Solution Explorer** and select **Add**, **New Item…**.</span></span>  
  
3.  <span data-ttu-id="d9d35-193">依序展開**Visual C# 項目**節點，然後選取**工作流程**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-193">Expand the **Visual C# Items** node and select **Workflow**.</span></span> <span data-ttu-id="d9d35-194">選取 **活動**從**Visual C# 項目**清單。</span><span class="sxs-lookup"><span data-stu-id="d9d35-194">Select **Activity** from the **Visual C# Items** list.</span></span>  
  
4.  <span data-ttu-id="d9d35-195">型別`DiscountWorkflow`成**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-195">Type `DiscountWorkflow` into the **Name** box and click **Add**.</span></span>  
  
5.  <span data-ttu-id="d9d35-196">按一下 **引數**按鈕以顯示工作流程設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="d9d35-196">Click the **Arguments** button on the lower left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
6.  <span data-ttu-id="d9d35-197">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-197">Click **Create Argument**.</span></span>  
  
7.  <span data-ttu-id="d9d35-198">型別`Subtotal`成**名稱**方塊中，選取**中**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-198">Type `Subtotal` into the **Name** box, select **In** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9d35-199">如果**雙**不是處於**引數型別**下拉式清單中，選取**Vyhledat Typy...**，輸入`System.Double`中**型別名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-199">If **Double** is not in the **Argument type** drop-down list, select **Browse for Types …**, type `System.Double` in the **Type Name** box, and click **OK**.</span></span>  
  
8.  <span data-ttu-id="d9d35-200">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-200">Click **Create Argument**.</span></span>  
  
9. <span data-ttu-id="d9d35-201">型別`DiscountPercent`成**名稱**方塊中，選取**出**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-201">Type `DiscountPercent` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
10. <span data-ttu-id="d9d35-202">按一下  **Vytvořit Argument**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-202">Click **Create Argument**.</span></span>  
  
11. <span data-ttu-id="d9d35-203">型別`Total`成**名稱**方塊中，選取**出**從**方向**下拉式清單中，選取**Double**從**引數型別**下拉式清單中，然後按下 ENTER 儲存引數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-203">Type `Total` into the **Name** box, select **Out** from the **Direction** drop-down, select **Double** from the **Argument type** drop-down, and then press ENTER to save the argument.</span></span>  
  
12. <span data-ttu-id="d9d35-204">按一下 **引數**按鈕以關閉工作流程設計工具左下角**引數**窗格。</span><span class="sxs-lookup"><span data-stu-id="d9d35-204">Click the **Arguments** button on the lower left side of the workflow designer to close the **Arguments** pane.</span></span>  
  
13. <span data-ttu-id="d9d35-205">拖曳**順序**活動，從**控制流程**一節**工具箱**拖放到工作流程設計工具介面。</span><span class="sxs-lookup"><span data-stu-id="d9d35-205">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the workflow designer surface.</span></span>  
  
14. <span data-ttu-id="d9d35-206">拖曳**Interop**活動，從**移轉**一節**工具箱**並將它放**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="d9d35-206">Drag an **Interop** activity from the **Migration** section of the **Toolbox** and drop it in the **Sequence** activity.</span></span>  
  
15. <span data-ttu-id="d9d35-207">按一下  **Interop**活動上的**按一下即可瀏覽...**</span><span class="sxs-lookup"><span data-stu-id="d9d35-207">Click the **Interop** activity on the **Click to browse…**</span></span> <span data-ttu-id="d9d35-208">標籤中，輸入**DiscountCalculator**中**型別名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-208">label, type **DiscountCalculator** in the **Type Name** box, and click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9d35-209">將 <xref:System.Activities.Statements.Interop> 活動加入至工作流程中，並將 `DiscountCalculator` 型別指定為其 <xref:System.Activities.Statements.Interop.ActivityType%2A> 時，<xref:System.Activities.Statements.Interop> 活動會公開三個 <xref:System.Activities.ArgumentDirection.In> 引數和三個 <xref:System.Activities.ArgumentDirection.Out> 引數 (代表 `DiscountCalculator` 活動的三個公用屬性)。</span><span class="sxs-lookup"><span data-stu-id="d9d35-209">When the <xref:System.Activities.Statements.Interop> activity is added to the workflow and the `DiscountCalculator` type is specified as its <xref:System.Activities.Statements.Interop.ActivityType%2A>, the <xref:System.Activities.Statements.Interop> activity exposes three <xref:System.Activities.ArgumentDirection.In> arguments and three <xref:System.Activities.ArgumentDirection.Out> arguments that represent the three public properties of the `DiscountCalculator` activity.</span></span> <span data-ttu-id="d9d35-210"><xref:System.Activities.ArgumentDirection.In>引數具有相同名稱的三個公用屬性和三個<xref:System.Activities.ArgumentDirection.Out>引數具有相同名稱時**出**附加至屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d35-210">The <xref:System.Activities.ArgumentDirection.In> arguments have the same name as the three public properties, and the three <xref:System.Activities.ArgumentDirection.Out> arguments have the same names with **Out** appended to the property name.</span></span> <span data-ttu-id="d9d35-211">在下列步驟中，在前述步驟中建立的工作流程引數會繫結至 <xref:System.Activities.Statements.Interop> 活動的引數。</span><span class="sxs-lookup"><span data-stu-id="d9d35-211">In the following steps, the workflow arguments created in the previous steps are bound to the <xref:System.Activities.Statements.Interop> activity’s arguments.</span></span>  
  
16. <span data-ttu-id="d9d35-212">型別`DiscountPercent`成**輸入 VB 運算式**右邊的方塊**Discountpercent**屬性並按下 TAB 鍵。</span><span class="sxs-lookup"><span data-stu-id="d9d35-212">Type `DiscountPercent` into the **Enter a VB expression** box to the right of the **DiscountPercentOut** property and press TAB.</span></span>  
  
17. <span data-ttu-id="d9d35-213">型別`Subtotal`成**輸入 VB 運算式**右邊的方塊**Subtotal**屬性並按下 TAB 鍵。</span><span class="sxs-lookup"><span data-stu-id="d9d35-213">Type `Subtotal` into the **Enter a VB expression** box to the right of the **Subtotal** property and press TAB.</span></span>  
  
18. <span data-ttu-id="d9d35-214">型別`Total`成**輸入 VB 運算式**右邊的方塊**TotalOut**屬性並按下 TAB 鍵。</span><span class="sxs-lookup"><span data-stu-id="d9d35-214">Type `Total` into the **Enter a VB expression** box to the right of the **TotalOut** property and press TAB.</span></span>  
  
19. <span data-ttu-id="d9d35-215">以滑鼠右鍵按一下**Program.cs**中**方案總管**，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d9d35-215">Right-click **Program.cs** in **Solution Explorer** and select **View Code**.</span></span>  
  
20. <span data-ttu-id="d9d35-216">將下列 `using` 陳述式加入至檔案最上方。</span><span class="sxs-lookup"><span data-stu-id="d9d35-216">Add the following `using` statement at the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. <span data-ttu-id="d9d35-217">註解 `CalculateDiscountInCode` 方法中對 `Main` 方法的呼叫，然後加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9d35-217">Comment out the call to the `CalculateDiscountInCode` method in the `Main` method and add the following code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9d35-218">如果您未遵循前述程序，而出現預設的 `Main` 程式碼，請以下列程式碼取代 `Main` 的內容。</span><span class="sxs-lookup"><span data-stu-id="d9d35-218">If you did not follow the previous procedure and the default `Main` code is present, replace the contents of `Main` with the following code.</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. <span data-ttu-id="d9d35-219">在名為 `Program` 的 `CalculateDiscountUsingDesignerWorkflow` 類別中建立新方法，其中包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d9d35-219">Create a new method in the `Program` class called `CalculateDiscountUsingDesignerWorkflow` that contains the following code.</span></span>  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. <span data-ttu-id="d9d35-220">按 CTRL+F5 建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9d35-220">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="d9d35-221">若要指定不同的 `Subtotal` 金額，請變更下列程式碼中 `SubtotalValue` 的值。</span><span class="sxs-lookup"><span data-stu-id="d9d35-221">To specify a different `Subtotal` amount, change the value of `SubtotalValue` in the following code.</span></span>  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a><span data-ttu-id="d9d35-222">規則功能概觀</span><span class="sxs-lookup"><span data-stu-id="d9d35-222">Rules Features Overview</span></span>  
 <span data-ttu-id="d9d35-223">[!INCLUDE[wf1](../../../includes/wf1-md.md)] 規則引擎可支援以優先順序為主的方式處理規則，並且支援向前鏈結。</span><span class="sxs-lookup"><span data-stu-id="d9d35-223">The [!INCLUDE[wf1](../../../includes/wf1-md.md)] rules engine provides support for processing rules in a priority-based manner with support for forward chaining.</span></span> <span data-ttu-id="d9d35-224">規則可針對單一項目或集合中之項目進行評估。</span><span class="sxs-lookup"><span data-stu-id="d9d35-224">Rules can be evaluated for a single item or for items in a collection.</span></span> <span data-ttu-id="d9d35-225">如需規則概觀與特定規則功能的詳細資訊，請參閱下表。</span><span class="sxs-lookup"><span data-stu-id="d9d35-225">For an overview of rules and information on specific rules functionality, please refer to the following table.</span></span>  
  
|<span data-ttu-id="d9d35-226">規則功能</span><span class="sxs-lookup"><span data-stu-id="d9d35-226">Rules Feature</span></span>|<span data-ttu-id="d9d35-227">文件</span><span class="sxs-lookup"><span data-stu-id="d9d35-227">Documentation</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="d9d35-228">規則概觀</span><span class="sxs-lookup"><span data-stu-id="d9d35-228">Rules Overview</span></span>|[<span data-ttu-id="d9d35-229">Windows Workflow Foundation Rules Engine 簡介</span><span class="sxs-lookup"><span data-stu-id="d9d35-229">Introduction to the Windows Workflow Foundation Rules Engine</span></span>](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|<span data-ttu-id="d9d35-230">RuleSet</span><span class="sxs-lookup"><span data-stu-id="d9d35-230">RuleSet</span></span>|<span data-ttu-id="d9d35-231">[在工作流程中使用 Ruleset](https://go.microsoft.com/fwlink/?LinkId=178516)和 <xref:System.Workflow.Activities.Rules.RuleSet></span><span class="sxs-lookup"><span data-stu-id="d9d35-231">[Using RuleSets in Workflows](https://go.microsoft.com/fwlink/?LinkId=178516) and <xref:System.Workflow.Activities.Rules.RuleSet></span></span>|  
|<span data-ttu-id="d9d35-232">規則評估</span><span class="sxs-lookup"><span data-stu-id="d9d35-232">Evaluation of Rules</span></span>|[<span data-ttu-id="d9d35-233">Ruleset 中的規則評估</span><span class="sxs-lookup"><span data-stu-id="d9d35-233">Rules Evaluation in RuleSets</span></span>](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|<span data-ttu-id="d9d35-234">規則鏈結</span><span class="sxs-lookup"><span data-stu-id="d9d35-234">Rules Chaining</span></span>|<span data-ttu-id="d9d35-235">[向前鏈結控制項](https://go.microsoft.com/fwlink/?LinkId=178518)和[規則的向前鏈結](https://go.microsoft.com/fwlink/?LinkId=178519)</span><span class="sxs-lookup"><span data-stu-id="d9d35-235">[Forward Chaining Control](https://go.microsoft.com/fwlink/?LinkId=178518) and [Forward Chaining of Rules](https://go.microsoft.com/fwlink/?LinkId=178519)</span></span>|  
|<span data-ttu-id="d9d35-236">處理規則中的集合</span><span class="sxs-lookup"><span data-stu-id="d9d35-236">Processing Collections in Rules</span></span>|[<span data-ttu-id="d9d35-237">處理規則中的集合</span><span class="sxs-lookup"><span data-stu-id="d9d35-237">Processing Collections in Rules</span></span>](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|<span data-ttu-id="d9d35-238">使用 PolicyActivity</span><span class="sxs-lookup"><span data-stu-id="d9d35-238">Using the PolicyActivity</span></span>|<span data-ttu-id="d9d35-239">[使用 PolicyActivity 活動](https://go.microsoft.com/fwlink/?LinkId=178521)和 <xref:System.Workflow.Activities.PolicyActivity></span><span class="sxs-lookup"><span data-stu-id="d9d35-239">[Using the PolicyActivity Activity](https://go.microsoft.com/fwlink/?LinkId=178521) and <xref:System.Workflow.Activities.PolicyActivity></span></span>|  
  
 <span data-ttu-id="d9d35-240">在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中建立的工作流程不會使用 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 提供的所有規則功能，例如宣告式活動條件及條件式活動 (例如 <xref:System.Workflow.Activities.ConditionedActivityGroup> 和 <xref:System.Workflow.Activities.ReplicatorActivity>)。</span><span class="sxs-lookup"><span data-stu-id="d9d35-240">Workflows created in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] do not use all of the rules features provided by [!INCLUDE[wf1](../../../includes/wf1-md.md)], such as declarative activity conditions and conditional activities such as the <xref:System.Workflow.Activities.ConditionedActivityGroup> and <xref:System.Workflow.Activities.ReplicatorActivity>.</span></span> <span data-ttu-id="d9d35-241">如有必要，這個功能可供以 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 和 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 建立的工作流程使用。</span><span class="sxs-lookup"><span data-stu-id="d9d35-241">If required, this functionality is available for workflows created using [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="d9d35-242">如需詳細資訊，請參閱 <<c0> [ 移轉指引](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="d9d35-242">For more information, see [Migration Guidance](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>
