---
title: 逐步解說：在 DataRepeater 控制項中顯示資料 (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: d02668303f61f6a22f99bd7c86c41c9c139a716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>逐步解說：在 DataRepeater 控制項中顯示資料 (Visual Studio)
本逐步解說提供在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中顯示繫結資料的基本完整情節。  
  
## <a name="prerequisite"></a>必要條件  
 這個逐步解說需要使用 Northwind 範例資料庫。  
  
 如果您的開發電腦上沒有這個資料庫，則可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)下載。 如需指示，請參閱[下載範例資料庫](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
## <a name="overview"></a>總覽  
 本逐步解說的第一個部分包含四項主要工作：  
  
-   建立方案。  
  
-   加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  
  
-   加入資料來源。  
  
-   加入資料繫結控制項。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>建立 DataRepeater 方案  
 在第一個步驟中，您會建立專案和方案。  
  
#### <a name="to-create-a-datarepeater-solution"></a>建立 DataRepeater 方案  
  
1.  在 Visual Studio 的 [檔案]  功能表上，按一下 [新增專案] 。  
  
2.  在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 窗格中，展開 [ **Visual Basic**]，然後按一下 [ **Windows**]。  
  
3.  在 [範本]  窗格中，按一下 [Windows Form 應用程式] 。  
  
4.  在 [名稱]  方塊中，輸入 `DataRepeaterApp`。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
     Windows Forms 設計工具隨即開啟。  
  
6.  從 [Windows Form 設計工具] 中選取表單。 在 [屬性]  視窗中，將 **Size** 屬性設定為 `800, 700`。  
  
## <a name="adding-a-datarepeater-control"></a>加入 DataRepeater 控制項  
 在此步驟中，您會將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項加入表單中。  
  
#### <a name="to-add-a-datarepeater-control"></a>加入 DataRepeater 控制項  
  
1.  在 [ **檢視** ] 功能表上，按一下 [ **工具箱**]。  
  
     [ **工具箱** ] 會開啟。  
  
2.  選取 [Visual Basic PowerPacks]  索引標籤。  
  
3.  將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項拖曳到 **Form1**上。  
  
4.  在 [屬性] 視窗中，將 **Location** 屬性設定為 `0, 25`。  
  
5.  將 **Size** 屬性設定為 `460, 600`。  
  
## <a name="adding-a-data-source"></a>加入資料來源  
 在此步驟中，您會加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的資料來源。  
  
#### <a name="to-add-a-data-source"></a>加入資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 [ **資料來源** ] 視窗中，按一下 [ **加入新資料來源**]。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：  
  
    -   如果下拉式清單中提供 Northwind 範例資料庫的資料連接，請按一下這個資料連接。  
  
         -或-  
  
    -   按一下 [新增連接]  ，設定新的資料連接。 如需詳細資訊，請參閱[加入新連接](/visualstudio/data-tools/add-new-connections)。  
  
5.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後按 [下一步] 。  
  
    > [!NOTE]
    >  如果對話方塊隨即出現，請按一下 [是]  ，將檔案儲存到專案。  
  
6.  在 [Save Connection String to the Application Configuration file]  (將連接字串儲存到應用程式組態檔)頁面上，按一下 [下一步]  。  
  
7.  在 [選擇您的資料庫物件]  頁面上，展開 [資料表]  節點。  
  
8.  選取 [Customers]  和 [Orders]  資料表旁邊的核取方塊，然後按一下 [完成] 。  
  
     會將 [] 加入專案中，且 []  和 []  資料表會出現在 [資料來源]  視窗中。  
  
## <a name="adding-data-bound-controls"></a>加入資料繫結控制項  
 在此步驟中，您會將資料繫結控制項加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
#### <a name="to-add-data-bound-controls"></a>若要加入資料繫結控制項  
  
1.  在 [資料來源]  視窗中，選取 [Customers]  資料表的最上層節點。  
  
2.  在資料表節點上，按一下下拉式清單中的 [詳細資料]  ，將資料表的卸除類型變更為 **[詳細資料]** 。  
  
3.  選取 [Customers]  資料表節點並將它拖曳到 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目範本區域 (上方區域) 上。  
  
     <xref:System.Windows.Forms.BindingNavigator> 控制項隨即加入表單中，而且 **NorthwindDataSet**、CustomersBindingSource 、 **CustomersTableAdapter**、 **TableAdapterManager**和 **CustomersBindingNavigator** 元件也會加入 [元件匣] 中。  
  
4.  選取所有的欄位及其關聯的標籤，然後放置在靠近項目範本區域左邊緣的地方。  
  
5.  選取後五個欄位 ([Region]、[Postal Code] 、[Country] 、[Phone] 和 [Fax] ) 及其關聯的標籤，然後向上移至前六個欄位的右方。  
  
6.  選取項目範本 (控制項的上方區域)。  
  
7.  在 [屬性] 視窗中，將 **Size** 屬性設定為 `427, 170`。  
  
 此時，您有一個將會顯示客戶重複清單的工作應用程式。 您可以按 F5 鍵執行應用程式、變更資料，以及加入或刪除客戶資料錄。  
  
 在接下來的選擇性步驟中，您將學習如何自訂 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  
  
## <a name="next-steps-optional"></a>後續步驟 (選擇性)  
 此逐步解說部分包含四項選擇性工作：  
  
-   變更 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的外觀。  
  
-   防止使用者加入或刪除資料錄。  
  
-   將搜尋功能加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。  
  
-   將主控制項和詳細資料控制項資料表加入 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>變更 DataRepeater 控制項的外觀  
 在這個選擇性步驟中，您會在設計階段變更 `BackColor` 控制項的 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 。 您也會加入程式碼，以替代色彩的方式顯示資料列，並根據條件變更標籤的 `ForeColor` 。  
  
#### <a name="to-change-the-appearance-of-the-control"></a>變更控制項的外觀  
  
1.  在 [Windows Form 設計工具] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的主要 (下方) 區域。  
  
2.  在 [屬性] 視窗中，將 `BackColor` 屬性設定為白色。  
  
3.  按兩下 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 開啟 [程式碼編輯器]。  
  
4.  在 [程式碼編輯器] 中，按一下 [事件] 下拉式清單中的 [DrawItem] 。  
  
5.  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，加入下列程式碼，以替代 `BackColor`。  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 事件處理常式中，加入下列程式碼，以根據條件變更標籤的 `ForeColor` ︰  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  按 F5 鍵執行應用程式並查看自訂。  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>防止使用者加入或刪除資料錄  
 在此選擇性步驟中，您會加入程式碼，以防止使用者在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中加入或刪除資料錄。  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>防止使用者加入及刪除資料錄  
  
1.  在 [Windows Form 設計工具] 中，按兩下表單開啟 [程式碼編輯器]。  
  
2.  將下列程式碼加入 `Form_Load` 事件：  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  在 [類別名稱] 下拉式清單中，按一下 [BindingNavigatorDeleteItem] 。 在 [方法名稱] 下拉式清單中，按一下 [EnabledChanged] 。  
  
4.  將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  這是必要步驟，因為每次目前資料錄變更時， <xref:System.Windows.Forms.BindingSource> 都會啟用 [DeleteItem]  按鈕。  
  
5.  按 F5 執行應用程式。 請注意，[DeleteItem]  按鈕處於停用狀態，而且您無法按 DELETE 鍵刪除項目。  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>將搜尋功能加入 DataRepeater 控制項中  
 在此選擇性步驟中，您會實作在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中搜尋值的功能。 如果找到搜尋字串，控制項就會選取含有此值的項目，並捲動以檢視項目。  
  
#### <a name="to-add-search-capability"></a>加入搜尋功能  
  
1.  將 <xref:System.Windows.Forms.TextBox> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。  
  
     將其放置在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方。  
  
2.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。 將其放置在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的下方。  
  
4.  在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。 將 **Text** 屬性變更為 **Search**。  
  
5.  按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 [程式碼編輯器]，然後將下列程式碼加入 `SearchButton_Click` 事件處理常式。  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  按 F5 執行應用程式。 在 [SearchTextBox]  中輸入客戶 ID，然後按一下 [搜尋]  按鈕。  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>將主控制項和詳細資料控制項資料表加入 DataRepeater  
 在此選擇性步驟中，您會加入第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項，以顯示每個客戶的相關訂單。  
  
#### <a name="to-add-a-master-and-detail-table"></a>加入主控制項和詳細資料控制項資料表  
  
1.  將第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項從 [工具箱]  中的 [Visual Basic PowerPacks]  索引標籤拖曳到表單上。  
  
2.  在 [屬性] 視窗中，將 **Location** 屬性設定為 `465, 25`。  
  
3.  將 **Size** 屬性設定為 `315, 600`。  
  
4.  在 [資料來源]  視窗中，展開 [Customers]  資料表節點，並選取 [Orders]  資料表的詳細資料節點。  
  
5.  在資料表節點上，按一下下拉式清單中的 [詳細資料]  ，將此 [Orders]  資料表的卸除類型變更為 [詳細資料]。  
  
6.  將此 [Orders]  資料表節點拖曳到第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的項目範本區域 (上方區域) 上。  
  
     **OrdersBindingSource** 元件和 **OrdersTableAdapter** 元件隨即加入 [元件匣]。  
  
7.  按 F5 執行應用程式。 當您在第一個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中選取各個客戶時，該客戶的訂單便會顯示在第二個 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中。  
  
## <a name="see-also"></a>另請參閱  
 [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示未繫結的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：變更 DataRepeater 控制項的配置](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [操作說明：在 DataRepeater 控制項中顯示項目標題](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [操作說明：搜尋 DataRepeater 控制項中的資料](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [操作說明：變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [操作說明：停用加入和刪除 DataRepeater 項目](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
