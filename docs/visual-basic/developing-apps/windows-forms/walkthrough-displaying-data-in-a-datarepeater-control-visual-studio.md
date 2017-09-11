---
title: "逐步解說︰ 在 DataRepeater 控制項 (Visual Studio) 中顯示資料 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b795b8f3bb42aecdbdfade62f4943239fec6eac4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="17790-102">逐步解說：在 DataRepeater 控制項中顯示資料 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="17790-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="17790-103">本逐步解說顯示繫結中的資料提供基本的開始-完成案例<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="17790-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="17790-104">Prerequisite</span></span>  
 <span data-ttu-id="17790-105">這個逐步解說需要使用 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="17790-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="17790-106">如果您的開發電腦上沒有這個資料庫，則可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)下載。</span><span class="sxs-lookup"><span data-stu-id="17790-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="17790-107">如需指示，請參閱[下載範例資料庫](https://msdn.microsoft.com/library/bb399411)。</span><span class="sxs-lookup"><span data-stu-id="17790-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="17790-108">概觀</span><span class="sxs-lookup"><span data-stu-id="17790-108">Overview</span></span>  
 <span data-ttu-id="17790-109">本逐步解說的第一個部分包含四項主要工作：</span><span class="sxs-lookup"><span data-stu-id="17790-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="17790-110">建立方案。</span><span class="sxs-lookup"><span data-stu-id="17790-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="17790-111">新增<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="17790-112">加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="17790-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="17790-113">加入資料繫結控制項。</span><span class="sxs-lookup"><span data-stu-id="17790-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="17790-114">建立 DataRepeater 方案</span><span class="sxs-lookup"><span data-stu-id="17790-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="17790-115">在第一個步驟中，您會建立專案和方案。</span><span class="sxs-lookup"><span data-stu-id="17790-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="17790-116">建立 DataRepeater 方案</span><span class="sxs-lookup"><span data-stu-id="17790-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="17790-117">在 Visual Studio 的 [檔案] **** 功能表上，按一下 [新增專案] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="17790-118">在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 窗格中，展開 [ **Visual Basic**]，然後按一下 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="17790-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="17790-119">在 [範本] **** 窗格中，按一下 [Windows Form 應用程式] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="17790-120">在 [名稱] **** 方塊中，輸入 `DataRepeaterApp`。</span><span class="sxs-lookup"><span data-stu-id="17790-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="17790-121">按一下 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="17790-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="17790-122">Windows Forms 設計工具隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="17790-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="17790-123">從 [Windows Form 設計工具] 中選取表單。</span><span class="sxs-lookup"><span data-stu-id="17790-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="17790-124">在 [屬性] **** 視窗中，將 **Size** 屬性設定為 `800, 700`。</span><span class="sxs-lookup"><span data-stu-id="17790-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="17790-125">加入 DataRepeater 控制項</span><span class="sxs-lookup"><span data-stu-id="17790-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="17790-126">在此步驟中，您將加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項加入表單。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="17790-127">加入 DataRepeater 控制項</span><span class="sxs-lookup"><span data-stu-id="17790-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="17790-128">在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="17790-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="17790-129">[ **工具箱** ] 會開啟。</span><span class="sxs-lookup"><span data-stu-id="17790-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="17790-130">選取 [Visual Basic PowerPacks] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="17790-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="17790-131">拖放到<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項拖曳至**Form1**。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="17790-132">在 [屬性] 視窗中，將 **Location** 屬性設定為 `0, 25`。</span><span class="sxs-lookup"><span data-stu-id="17790-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="17790-133">將 **Size** 屬性設定為 `460, 600`。</span><span class="sxs-lookup"><span data-stu-id="17790-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="17790-134">加入資料來源</span><span class="sxs-lookup"><span data-stu-id="17790-134">Adding a Data Source</span></span>  
 <span data-ttu-id="17790-135">在此步驟中，您加入的資料來源<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="17790-136">加入資料來源</span><span class="sxs-lookup"><span data-stu-id="17790-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="17790-137">按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="17790-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="17790-138">在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="17790-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="17790-139">請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="17790-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="17790-140">在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="17790-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="17790-141">如果下拉式清單中提供 Northwind 範例資料庫的資料連接，請按一下這個資料連接。</span><span class="sxs-lookup"><span data-stu-id="17790-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="17790-142">-或-</span><span class="sxs-lookup"><span data-stu-id="17790-142">-or-</span></span>  
  
    -   <span data-ttu-id="17790-143">按一下 [新增連接] **** ，設定新的資料連接。</span><span class="sxs-lookup"><span data-stu-id="17790-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="17790-144">如需詳細資訊，請參閱[How to︰ 建立連接至 SQL Server 資料庫](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d)。</span><span class="sxs-lookup"><span data-stu-id="17790-144">For more information, see [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span></span>  
  
5.  <span data-ttu-id="17790-145">如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按 [下一步] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17790-146">如果對話方塊隨即出現，請按一下 [是] **** ，將檔案儲存到專案。</span><span class="sxs-lookup"><span data-stu-id="17790-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="17790-147">在 [Save Connection String to the Application Configuration file] **** (將連接字串儲存到應用程式組態檔)頁面上，按一下 [下一步] **** 。</span><span class="sxs-lookup"><span data-stu-id="17790-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="17790-148">在 [選擇您的資料庫物件] **** 頁面上，展開 [資料表] **** 節點。</span><span class="sxs-lookup"><span data-stu-id="17790-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="17790-149">選取 [Customers] **** 和 [Orders] **** 資料表旁邊的核取方塊，然後按一下 [完成] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="17790-150">會將 []**** 加入專案中，且 [] **** 和 [] **** 資料表會出現在 [資料來源] **** 視窗中。</span><span class="sxs-lookup"><span data-stu-id="17790-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="17790-151">加入資料繫結控制項</span><span class="sxs-lookup"><span data-stu-id="17790-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="17790-152">您可以在此步驟中，將資料繫結控制項來加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="17790-153">若要加入資料繫結控制項</span><span class="sxs-lookup"><span data-stu-id="17790-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="17790-154">在 [資料來源] **** 視窗中，選取 [Customers] **** 資料表的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="17790-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="17790-155">在資料表節點上，按一下下拉式清單中的 [詳細資料] **** ，將資料表的卸除類型變更為 **[詳細資料]** 。</span><span class="sxs-lookup"><span data-stu-id="17790-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="17790-156">選取**客戶**資料表節點，並將其拖曳到項目樣板區域 （左上區域） 的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="17790-157">A<xref:System.Windows.Forms.BindingNavigator>控制項加入至表單，而**NorthwindDataSet**， **CustomersBindingSource**， **CustomersTableAdapter**， **TableAdapterManager**，和**CustomersBindingNavigator**元件新增至元件匣。</xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="17790-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="17790-158">選取所有的欄位及其關聯的標籤，然後放置在靠近項目範本區域左邊緣的地方。</span><span class="sxs-lookup"><span data-stu-id="17790-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="17790-159">選取後五個欄位 ([Region]****、[Postal Code] ****、[Country] ****、[Phone] ****和 [Fax] ****) 及其關聯的標籤，然後向上移至前六個欄位的右方。</span><span class="sxs-lookup"><span data-stu-id="17790-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="17790-160">選取項目範本 (控制項的上方區域)。</span><span class="sxs-lookup"><span data-stu-id="17790-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="17790-161">在 [屬性] 視窗中，將 **Size** 屬性設定為 `427, 170`。</span><span class="sxs-lookup"><span data-stu-id="17790-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="17790-162">此時，您有一個將會顯示客戶重複清單的工作應用程式。</span><span class="sxs-lookup"><span data-stu-id="17790-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="17790-163">您可以按 F5 鍵執行應用程式、變更資料，以及加入或刪除客戶資料錄。</span><span class="sxs-lookup"><span data-stu-id="17790-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="17790-164">在下一步的選擇性步驟中，您將學習如何自訂<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="17790-165">後續步驟 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="17790-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="17790-166">此逐步解說部分包含四項選擇性工作：</span><span class="sxs-lookup"><span data-stu-id="17790-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="17790-167">變更外觀的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="17790-168">防止使用者加入或刪除資料錄。</span><span class="sxs-lookup"><span data-stu-id="17790-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="17790-169">加入搜尋功能，可<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="17790-170">將主要和詳細的資料表來<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="17790-171">變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="17790-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="17790-172">這個選擇性的步驟，在您變更`BackColor`的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在設計階段。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="17790-173">您也會加入程式碼，以替代色彩的方式顯示資料列，並根據條件變更標籤的 `ForeColor` 。</span><span class="sxs-lookup"><span data-stu-id="17790-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="17790-174">變更控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="17790-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="17790-175">在 Windows Form 設計工具中，選取 主要 （下方） 區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="17790-176">在 [屬性] 視窗中，將 `BackColor` 屬性設定為白色。</span><span class="sxs-lookup"><span data-stu-id="17790-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="17790-177">按兩下<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>開啟程式碼編輯器。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="17790-178">在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="17790-179">在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，將下列程式碼加入至替代`BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="17790-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     <span data-ttu-id="17790-180">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="17790-180">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]</span></span>  
  
6.  <span data-ttu-id="17790-181">在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>事件處理常式，加入下列程式碼，變更`ForeColor`根據條件的標籤︰</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></span><span class="sxs-lookup"><span data-stu-id="17790-181">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     <span data-ttu-id="17790-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="17790-182">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]</span></span>  
  
7.  <span data-ttu-id="17790-183">按 F5 鍵執行應用程式並查看自訂。</span><span class="sxs-lookup"><span data-stu-id="17790-183">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="17790-184">防止使用者加入或刪除資料錄</span><span class="sxs-lookup"><span data-stu-id="17790-184">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="17790-185">在這個選擇性的步驟，將加入程式碼會防止使用者新增或刪除資料錄中的<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-185">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="17790-186">防止使用者加入及刪除資料錄</span><span class="sxs-lookup"><span data-stu-id="17790-186">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="17790-187">在 [Windows Form 設計工具] 中，按兩下表單開啟 [程式碼編輯器]。</span><span class="sxs-lookup"><span data-stu-id="17790-187">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="17790-188">將下列程式碼加入 `Form_Load` 事件：</span><span class="sxs-lookup"><span data-stu-id="17790-188">Add the following code to the `Form_Load` event:</span></span>  
  
     <span data-ttu-id="17790-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="17790-189">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]</span></span>  
  
3.  <span data-ttu-id="17790-190">在 [類別名稱] 下拉式清單中，按一下 [BindingNavigatorDeleteItem] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-190">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="17790-191">在 [方法名稱] 下拉式清單中，按一下 [EnabledChanged] ****。</span><span class="sxs-lookup"><span data-stu-id="17790-191">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="17790-192">將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="17790-192">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     <span data-ttu-id="17790-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="17790-193">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17790-194">這是必要步驟因為<xref:System.Windows.Forms.BindingSource>可讓**DeleteItem**按鈕每次變更目前的記錄。</xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="17790-194">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="17790-195">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="17790-195">Press F5 to run the application.</span></span> <span data-ttu-id="17790-196">請注意，[DeleteItem] **** 按鈕處於停用狀態，而且您無法按 DELETE 鍵刪除項目。</span><span class="sxs-lookup"><span data-stu-id="17790-196">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="17790-197">將搜尋功能加入 DataRepeater 控制項中</span><span class="sxs-lookup"><span data-stu-id="17790-197">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="17790-198">在這個選擇性的步驟中，您將實作功能，可搜尋的值<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-198">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="17790-199">如果找到搜尋字串，控制項就會選取含有此值的項目，並捲動以檢視項目。</span><span class="sxs-lookup"><span data-stu-id="17790-199">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="17790-200">加入搜尋功能</span><span class="sxs-lookup"><span data-stu-id="17790-200">To add search capability</span></span>  
  
1.  <span data-ttu-id="17790-201">拖放到<xref:System.Windows.Forms.TextBox>控制項從**工具箱**拖曳至表單，其中包含<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="17790-201">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="17790-202">放置在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-202">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="17790-203">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。</span><span class="sxs-lookup"><span data-stu-id="17790-203">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="17790-204">拖放到<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單，其中包含<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="17790-204">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="17790-205">放置在<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-205">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="17790-206">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。</span><span class="sxs-lookup"><span data-stu-id="17790-206">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="17790-207">將 **Text** 屬性變更為 **Search**。</span><span class="sxs-lookup"><span data-stu-id="17790-207">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="17790-208">按兩下<xref:System.Windows.Forms.Button>控制項加入程式碼編輯器中，開啟，並加入下列程式碼以`SearchButton_Click`事件處理常式。</xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="17790-208">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     <span data-ttu-id="17790-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="17790-209">[!code-cs[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
 [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]</span></span>  
  
6.  <span data-ttu-id="17790-210">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="17790-210">Press F5 to run the application.</span></span> <span data-ttu-id="17790-211">在 [SearchTextBox] **** 中輸入客戶 ID，然後按一下 [搜尋] **** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="17790-211">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="17790-212">將主控制項和詳細資料控制項資料表加入 DataRepeater</span><span class="sxs-lookup"><span data-stu-id="17790-212">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="17790-213">在這個選擇性的步驟中，您將新增第二個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項來顯示每位客戶的相關的訂單。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-213">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="17790-214">加入主控制項和詳細資料控制項資料表</span><span class="sxs-lookup"><span data-stu-id="17790-214">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="17790-215">拖曳第二個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**拖曳至表單。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-215">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="17790-216">在 [屬性] 視窗中，將 **Location** 屬性設定為 `465, 25`。</span><span class="sxs-lookup"><span data-stu-id="17790-216">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="17790-217">將 **Size** 屬性設定為 `315, 600`。</span><span class="sxs-lookup"><span data-stu-id="17790-217">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="17790-218">在 [資料來源] **** 視窗中，展開 [Customers] **** 資料表節點，並選取 [Orders] **** 資料表的詳細資料節點。</span><span class="sxs-lookup"><span data-stu-id="17790-218">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="17790-219">在資料表節點上，按一下下拉式清單中的 [詳細資料] **** ，將此 [Orders] **** 資料表的卸除類型變更為 [詳細資料]。</span><span class="sxs-lookup"><span data-stu-id="17790-219">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="17790-220">拖曳這個**訂單**資料表節點拖曳至第二個項目樣板區域 （上方區域）<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-220">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="17790-221">**OrdersBindingSource** 元件和 **OrdersTableAdapter** 元件隨即加入 [元件匣]。</span><span class="sxs-lookup"><span data-stu-id="17790-221">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="17790-222">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="17790-222">Press F5 to run the application.</span></span> <span data-ttu-id="17790-223">當您選取每個客戶在第一個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，訂單 顯示該客戶的第二個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="17790-223">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17790-224">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17790-224">See Also</span></span>  
 <span data-ttu-id="17790-225">[DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-225">[Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-226"> [如何︰ 在 DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-226"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-227"> [如何︰ 顯示未繫結 DataRepeater 控制項中的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-227"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-228"> [如何︰ 變更 DataRepeater 控制項的版面配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-228"> [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-229"> [如何︰ 在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-229"> [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-230"> [如何︰ 搜尋 DataRepeater 控制項中的資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-230"> [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-231"> [如何︰ 使用兩個 DataRepeater 控制項 (Visual Studio) 建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="17790-231"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="17790-232"> [如何︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-232"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="17790-233"> [如何︰ 停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="17790-233"> [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md) </span></span>  
<span data-ttu-id="17790-234"> [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="17790-234"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
