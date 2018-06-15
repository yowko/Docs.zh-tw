---
title: 逐步解說：在 DataRepeater 控制項中顯示資料 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231501"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="1dbce-102">逐步解說：在 DataRepeater 控制項中顯示資料 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1dbce-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="1dbce-103">本逐步解說提供在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中顯示繫結資料的基本完整情節。</span><span class="sxs-lookup"><span data-stu-id="1dbce-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="1dbce-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="1dbce-104">Prerequisite</span></span>  
 <span data-ttu-id="1dbce-105">這個逐步解說需要使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="1dbce-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="1dbce-106">如果您在開發電腦上沒有這個資料庫，您可以從 Microsoft 下載中心下載它。</span><span class="sxs-lookup"><span data-stu-id="1dbce-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="1dbce-107">如需指示，請參閱[下載範例資料庫](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="1dbce-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1dbce-108">總覽</span><span class="sxs-lookup"><span data-stu-id="1dbce-108">Overview</span></span>  
 <span data-ttu-id="1dbce-109">本逐步解說的第一個部分包含四項主要工作：</span><span class="sxs-lookup"><span data-stu-id="1dbce-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="1dbce-110">建立方案。</span><span class="sxs-lookup"><span data-stu-id="1dbce-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="1dbce-111">加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1dbce-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1dbce-112">加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="1dbce-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="1dbce-113">加入資料繫結控制項。</span><span class="sxs-lookup"><span data-stu-id="1dbce-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="1dbce-114">建立 DataRepeater 方案</span><span class="sxs-lookup"><span data-stu-id="1dbce-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="1dbce-115">在第一個步驟中，您會建立專案和方案。</span><span class="sxs-lookup"><span data-stu-id="1dbce-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="1dbce-116">建立 DataRepeater 方案</span><span class="sxs-lookup"><span data-stu-id="1dbce-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="1dbce-117">在 Visual Studio 的 [檔案]  功能表上，按一下 [新增專案] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="1dbce-118">在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 窗格中，展開 [ **Visual Basic**]，然後按一下 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="1dbce-119">在 [範本]  窗格中，按一下 [Windows Form 應用程式] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="1dbce-120">在 [名稱]  方塊中，輸入 `DataRepeaterApp`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="1dbce-121">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="1dbce-122">Windows Forms 設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1dbce-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="1dbce-123">從 [Windows Form 設計工具] 中選取表單。</span><span class="sxs-lookup"><span data-stu-id="1dbce-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="1dbce-124">在 [屬性]  視窗中，將 **Size** 屬性設定為 `800, 700`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="1dbce-125">加入 DataRepeater 控制項</span><span class="sxs-lookup"><span data-stu-id="1dbce-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="1dbce-126">在此步驟中，您會將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項加入表單中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="1dbce-127">加入 DataRepeater 控制項</span><span class="sxs-lookup"><span data-stu-id="1dbce-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="1dbce-128">在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="1dbce-129">[ **工具箱** ] 會開啟。</span><span class="sxs-lookup"><span data-stu-id="1dbce-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="1dbce-130">選取 [Visual Basic PowerPacks]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1dbce-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="1dbce-131">將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項拖曳到 **Form1**上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="1dbce-132">在 [屬性] 視窗中，將 **Location** 屬性設定為 `0, 25`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="1dbce-133">將 **Size** 屬性設定為 `460, 600`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="1dbce-134">加入資料來源</span><span class="sxs-lookup"><span data-stu-id="1dbce-134">Adding a Data Source</span></span>  
 <span data-ttu-id="1dbce-135">在此步驟中，您會加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的資料來源。</span><span class="sxs-lookup"><span data-stu-id="1dbce-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="1dbce-136">加入資料來源</span><span class="sxs-lookup"><span data-stu-id="1dbce-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="1dbce-137">按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="1dbce-138">在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="1dbce-139">請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="1dbce-140">在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="1dbce-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="1dbce-141">如果下拉式清單中提供 Northwind 範例資料庫的資料連接，請按一下這個資料連接。</span><span class="sxs-lookup"><span data-stu-id="1dbce-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="1dbce-142">-或-</span><span class="sxs-lookup"><span data-stu-id="1dbce-142">-or-</span></span>  
  
    -   <span data-ttu-id="1dbce-143">按一下 [新增連接]  ，設定新的資料連接。</span><span class="sxs-lookup"><span data-stu-id="1dbce-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="1dbce-144">如需詳細資訊，請參閱[加入新連接](/visualstudio/data-tools/add-new-connections)。</span><span class="sxs-lookup"><span data-stu-id="1dbce-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="1dbce-145">如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1dbce-146">如果對話方塊隨即出現，請按一下 [是]  ，將檔案儲存到專案。</span><span class="sxs-lookup"><span data-stu-id="1dbce-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="1dbce-147">在 [Save Connection String to the Application Configuration file]  (將連接字串儲存到應用程式組態檔)頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="1dbce-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="1dbce-148">在 [選擇您的資料庫物件]  頁面上，展開 [資料表]  節點。</span><span class="sxs-lookup"><span data-stu-id="1dbce-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="1dbce-149">選取 [Customers]  和 [Orders]  資料表旁邊的核取方塊，然後按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="1dbce-150">會將 [] 加入專案中，且 []  和 []  資料表會出現在 [資料來源]  視窗中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="1dbce-151">加入資料繫結控制項</span><span class="sxs-lookup"><span data-stu-id="1dbce-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="1dbce-152">在此步驟中，您會將資料繫結控制項加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="1dbce-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="1dbce-153">若要加入資料繫結控制項</span><span class="sxs-lookup"><span data-stu-id="1dbce-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="1dbce-154">在 [資料來源]  視窗中，選取 [Customers]  資料表的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="1dbce-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="1dbce-155">在資料表節點上，按一下下拉式清單中的 [詳細資料]  ，將資料表的卸除類型變更為 **[詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="1dbce-156">選取 [Customers]  資料表節點並將它拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目範本區域 (上方區域) 上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1dbce-157"><xref:System.Windows.Forms.BindingNavigator> 控制項隨即加入表單中，而且 **NorthwindDataSet**、CustomersBindingSource 、 **CustomersTableAdapter**、 **TableAdapterManager**和 **CustomersBindingNavigator** 元件也會加入 [元件匣] 中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="1dbce-158">選取所有的欄位及其關聯的標籤，然後放置在靠近項目範本區域左邊緣的地方。</span><span class="sxs-lookup"><span data-stu-id="1dbce-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="1dbce-159">選取後五個欄位 ([Region]、[Postal Code] 、[Country] 、[Phone] 和 [Fax] ) 及其關聯的標籤，然後向上移至前六個欄位的右方。</span><span class="sxs-lookup"><span data-stu-id="1dbce-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="1dbce-160">選取項目範本 (控制項的上方區域)。</span><span class="sxs-lookup"><span data-stu-id="1dbce-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="1dbce-161">在 [屬性] 視窗中，將 **Size** 屬性設定為 `427, 170`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="1dbce-162">此時，您有一個將會顯示客戶重複清單的工作應用程式。</span><span class="sxs-lookup"><span data-stu-id="1dbce-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="1dbce-163">您可以按 F5 鍵執行應用程式、變更資料，以及加入或刪除客戶資料錄。</span><span class="sxs-lookup"><span data-stu-id="1dbce-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="1dbce-164">在接下來的選擇性步驟中，您將學習如何自訂 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1dbce-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="1dbce-165">後續步驟 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="1dbce-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="1dbce-166">此逐步解說部分包含四項選擇性工作：</span><span class="sxs-lookup"><span data-stu-id="1dbce-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="1dbce-167">變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="1dbce-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1dbce-168">防止使用者加入或刪除資料錄。</span><span class="sxs-lookup"><span data-stu-id="1dbce-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="1dbce-169">將搜尋功能加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1dbce-170">將主控制項和詳細資料控制項資料表加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="1dbce-171">變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1dbce-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="1dbce-172">在這個選擇性步驟中，您會在設計階段變更 `BackColor` 控制項的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="1dbce-173">您也會加入程式碼，以替代色彩的方式顯示資料列，並根據條件變更標籤的 `ForeColor` 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="1dbce-174">變更控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1dbce-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="1dbce-175">在 [Windows Form 設計工具] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的主要 (下方) 區域。</span><span class="sxs-lookup"><span data-stu-id="1dbce-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="1dbce-176">在 [屬性] 視窗中，將 `BackColor` 屬性設定為白色。</span><span class="sxs-lookup"><span data-stu-id="1dbce-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="1dbce-177">按兩下 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="1dbce-178">在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="1dbce-179">在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，加入下列程式碼，以替代 `BackColor`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="1dbce-180">在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，加入下列程式碼，以根據條件變更標籤的 `ForeColor` ︰</span><span class="sxs-lookup"><span data-stu-id="1dbce-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="1dbce-181">按 F5 鍵執行應用程式並查看自訂。</span><span class="sxs-lookup"><span data-stu-id="1dbce-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="1dbce-182">防止使用者加入或刪除資料錄</span><span class="sxs-lookup"><span data-stu-id="1dbce-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="1dbce-183">在此選擇性步驟中，您會加入程式碼，以防止使用者在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中加入或刪除資料錄。</span><span class="sxs-lookup"><span data-stu-id="1dbce-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="1dbce-184">防止使用者加入及刪除資料錄</span><span class="sxs-lookup"><span data-stu-id="1dbce-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="1dbce-185">在 [Windows Form 設計工具] 中，按兩下表單開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="1dbce-186">將下列程式碼加入 `Form_Load` 事件：</span><span class="sxs-lookup"><span data-stu-id="1dbce-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="1dbce-187">在 [類別名稱] 下拉式清單中，按一下 [BindingNavigatorDeleteItem] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="1dbce-188">在 [方法名稱] 下拉式清單中，按一下 [EnabledChanged] 。</span><span class="sxs-lookup"><span data-stu-id="1dbce-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="1dbce-189">將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="1dbce-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1dbce-190">這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="1dbce-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="1dbce-191">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1dbce-191">Press F5 to run the application.</span></span> <span data-ttu-id="1dbce-192">請注意，[DeleteItem]  按鈕處於停用狀態，而且您無法按 DELETE 鍵刪除項目。</span><span class="sxs-lookup"><span data-stu-id="1dbce-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="1dbce-193">將搜尋功能加入 DataRepeater 控制項中</span><span class="sxs-lookup"><span data-stu-id="1dbce-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="1dbce-194">在此選擇性步驟中，您會實作在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中搜尋值的功能。</span><span class="sxs-lookup"><span data-stu-id="1dbce-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1dbce-195">如果找到搜尋字串，控制項就會選取含有此值的項目，並捲動以檢視項目。</span><span class="sxs-lookup"><span data-stu-id="1dbce-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="1dbce-196">加入搜尋功能</span><span class="sxs-lookup"><span data-stu-id="1dbce-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="1dbce-197">將 <xref:System.Windows.Forms.TextBox> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1dbce-198">將其放置在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方。</span><span class="sxs-lookup"><span data-stu-id="1dbce-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="1dbce-199">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。</span><span class="sxs-lookup"><span data-stu-id="1dbce-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="1dbce-200">將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1dbce-201">將其放置在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方。</span><span class="sxs-lookup"><span data-stu-id="1dbce-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="1dbce-202">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。</span><span class="sxs-lookup"><span data-stu-id="1dbce-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="1dbce-203">將 **Text** 屬性變更為 **Search**。</span><span class="sxs-lookup"><span data-stu-id="1dbce-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="1dbce-204">按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 [程式碼編輯器]，然後將下列程式碼加入 `SearchButton_Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1dbce-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="1dbce-205">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1dbce-205">Press F5 to run the application.</span></span> <span data-ttu-id="1dbce-206">在 [SearchTextBox]  中輸入客戶 ID，然後按一下 [搜尋]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="1dbce-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="1dbce-207">將主控制項和詳細資料控制項資料表加入 DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1dbce-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="1dbce-208">在此選擇性步驟中，您會加入第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項，以顯示每個客戶的相關訂單。</span><span class="sxs-lookup"><span data-stu-id="1dbce-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="1dbce-209">加入主控制項和詳細資料控制項資料表</span><span class="sxs-lookup"><span data-stu-id="1dbce-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="1dbce-210">將第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項從 [工具箱]  中的 [Visual Basic PowerPacks]  索引標籤拖曳到表單上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="1dbce-211">在 [屬性] 視窗中，將 **Location** 屬性設定為 `465, 25`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="1dbce-212">將 **Size** 屬性設定為 `315, 600`。</span><span class="sxs-lookup"><span data-stu-id="1dbce-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="1dbce-213">在 [資料來源]  視窗中，展開 [Customers]  資料表節點，並選取 [Orders]  資料表的詳細資料節點。</span><span class="sxs-lookup"><span data-stu-id="1dbce-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="1dbce-214">在資料表節點上，按一下下拉式清單中的 [詳細資料]  ，將此 [Orders]  資料表的卸除類型變更為 [詳細資料]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="1dbce-215">將此 [Orders]  資料表節點拖曳到第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目範本區域 (上方區域) 上。</span><span class="sxs-lookup"><span data-stu-id="1dbce-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1dbce-216">**OrdersBindingSource** 元件和 **OrdersTableAdapter** 元件隨即加入 [元件匣]。</span><span class="sxs-lookup"><span data-stu-id="1dbce-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="1dbce-217">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="1dbce-217">Press F5 to run the application.</span></span> <span data-ttu-id="1dbce-218">當您在第一個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中選取各個客戶時，該客戶的訂單便會顯示在第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="1dbce-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbce-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dbce-219">See Also</span></span>  
 [<span data-ttu-id="1dbce-220">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="1dbce-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-221">操作說明：在 DataRepeater 控制項中顯示繫結資料</span><span class="sxs-lookup"><span data-stu-id="1dbce-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-222">操作說明：在 DataRepeater 控制項中顯示未繫結的控制項</span><span class="sxs-lookup"><span data-stu-id="1dbce-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-223">操作說明：變更 DataRepeater 控制項的配置</span><span class="sxs-lookup"><span data-stu-id="1dbce-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-224">操作說明：在 DataRepeater 控制項中顯示項目標題</span><span class="sxs-lookup"><span data-stu-id="1dbce-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-225">操作說明：搜尋 DataRepeater 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="1dbce-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-226">如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="1dbce-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="1dbce-227">操作說明：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="1dbce-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1dbce-228">操作說明：停用加入和刪除 DataRepeater 項目</span><span class="sxs-lookup"><span data-stu-id="1dbce-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="1dbce-229"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1dbce-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
