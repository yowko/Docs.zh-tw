---
title: 逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 1421d076ff202ec87a9d861ab2c7d1c1cdcdc1b7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43798722"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="13451-102">逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="13451-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="13451-103">在本逐步解說中，方法，您可以從 SQL Server 資料庫擷取資料，並顯示該資料<xref:System.Windows.Controls.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="13451-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="13451-104">您可以使用 ADO.NET Entity Framework 建立的實體類別，代表資料，並使用 LINQ 來撰寫查詢來擷取指定的資料從實體類別。</span><span class="sxs-lookup"><span data-stu-id="13451-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13451-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="13451-105">Prerequisites</span></span>  
 <span data-ttu-id="13451-106">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="13451-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="13451-107">.</span><span class="sxs-lookup"><span data-stu-id="13451-107">.</span></span>  
  
-   <span data-ttu-id="13451-108">SQL Server 或 SQL Server Express 具有 AdventureWorks 範例資料庫會附加至它的執行個體的存取。</span><span class="sxs-lookup"><span data-stu-id="13451-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="13451-109">您可以下載的 AdventureWorks 資料庫[GitHub](https://github.com/Microsoft/sql-server-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="13451-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="13451-110">若要建立實體類別</span><span class="sxs-lookup"><span data-stu-id="13451-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="13451-111">在 Visual Basic 或 C# 中，建立新的 WPF 應用程式專案並將它命名`DataGridSQLExample`。</span><span class="sxs-lookup"><span data-stu-id="13451-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="13451-112">在 [方案總管] 中，以滑鼠右鍵按一下您的專案，指向**新增**，然後選取**新項目**。</span><span class="sxs-lookup"><span data-stu-id="13451-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="13451-113">[加入新項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="13451-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="13451-114">在 [已安裝的範本] 窗格中，選取**資料**，然後在範本清單中，選取**ADO.NET 實體資料模式**l。</span><span class="sxs-lookup"><span data-stu-id="13451-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="13451-115">![選取 ADO.NET 實體資料模型](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="13451-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="13451-116">將檔案命名`AdventureWorksModel.edmx`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="13451-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="13451-117">[實體資料模型精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="13451-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="13451-118">在 選擇模型內容 畫面中，選取**從資料庫產生**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13451-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="13451-119">![從資料庫選項中選取 Generate](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="13451-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="13451-120">在 [選擇資料連接] 畫面中，提供您 AdventureWorksLT2008 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="13451-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="13451-121">如需詳細資訊，請參閱 <<c0> [ 選擇您的資料連接對話方塊](https://go.microsoft.com/fwlink/?LinkId=160190)。</span><span class="sxs-lookup"><span data-stu-id="13451-121">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="13451-122">![提供資料庫連接](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="13451-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="13451-123">請確定名稱是`AdventureWorksLT2008Entities`且**將實體連接設定儲存在 App.Config 中為** 核取方塊已選取，然後再按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="13451-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="13451-124">在 [選擇您的資料庫物件] 畫面中，展開 [資料表] 節點，然後選取**產品**並**ProductCategory**資料表。</span><span class="sxs-lookup"><span data-stu-id="13451-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="13451-125">您可以產生實體類別，所有的資料表。不過，在此範例中您只能從擷取資料這兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="13451-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="13451-126">![從資料表中選取 Product 和 ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="13451-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="13451-127">按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="13451-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="13451-128">在 Entity Designer 中，會顯示 Product 和 ProductCategory 實體。</span><span class="sxs-lookup"><span data-stu-id="13451-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="13451-129">![Product 和 ProductCategory 實體模型](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="13451-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="13451-130">擷取及呈現資料</span><span class="sxs-lookup"><span data-stu-id="13451-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="13451-131">開啟 MainWindow.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="13451-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="13451-132">設定<xref:System.Windows.FrameworkElement.Width%2A>屬性上的<xref:System.Windows.Window>設為 450。</span><span class="sxs-lookup"><span data-stu-id="13451-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="13451-133">在 [XAML 編輯器] 中，新增下列<xref:System.Windows.Controls.DataGrid>標記之間`<Grid>`並`</Grid>`要新增的標籤<xref:System.Windows.Controls.DataGrid>名為`dataGrid1`。</span><span class="sxs-lookup"><span data-stu-id="13451-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="13451-134">![視窗與 DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="13451-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="13451-135">選取 <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="13451-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="13451-136">使用 [屬性] 視窗或 [XAML 編輯器] 中，建立事件處理常式<xref:System.Windows.Window>名為`Window_Loaded`如<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="13451-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="13451-137">如需詳細資訊，請參閱 <<c0> [ 如何： 建立簡單的事件處理常式](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480)。</span><span class="sxs-lookup"><span data-stu-id="13451-137">For more information, see [How to: Create a Simple Event Handler](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="13451-138">以下顯示 MainWindow.xaml 的 XAML。</span><span class="sxs-lookup"><span data-stu-id="13451-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13451-139">如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="DataGridSQLExample.MainWindow"`與`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="13451-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="13451-140">開啟的程式碼後置檔案 （MainWindow.xaml.vb 或 MainWindow.xaml.cs） <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="13451-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="13451-141">加入下列程式碼，從聯結的資料表擷取特定的值，並設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.DataGrid>查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="13451-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="13451-142">執行範例。</span><span class="sxs-lookup"><span data-stu-id="13451-142">Run the example.</span></span>  
  
     <span data-ttu-id="13451-143">您應該會看到<xref:System.Windows.Controls.DataGrid>顯示資料。</span><span class="sxs-lookup"><span data-stu-id="13451-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="13451-144">![使用 SQL database 中資料的 DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="13451-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="13451-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="13451-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13451-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13451-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="13451-147">如何 do i： 開始使用 WPF 應用程式中的 Entity Framework？</span><span class="sxs-lookup"><span data-stu-id="13451-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)
