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
ms.openlocfilehash: 1398d8408a0b85d6603d638312e92ba35c5e77d3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591029"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="e815f-102">逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="e815f-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="e815f-103">在此逐步解說中，您會從 SQL Server 資料庫中取出資料，並在控制項中顯示該資料 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="e815f-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="e815f-104">您可以使用 ADO.NET Entity Framework 來建立代表資料的實體類別，並使用 LINQ 來撰寫查詢，以從實體類別抓取指定的資料。</span><span class="sxs-lookup"><span data-stu-id="e815f-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e815f-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="e815f-105">Prerequisites</span></span>

<span data-ttu-id="e815f-106">您需要下列元件才能完成這個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="e815f-106">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="e815f-107">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e815f-107">Visual Studio.</span></span>

- <span data-ttu-id="e815f-108">存取已附加 AdventureWorks 範例資料庫之 SQL Server 或 SQL Server Express 的執行中實例。</span><span class="sxs-lookup"><span data-stu-id="e815f-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="e815f-109">您可以從[GitHub](https://github.com/Microsoft/sql-server-samples/releases)下載 AdventureWorks 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e815f-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="e815f-110">建立實體類別</span><span class="sxs-lookup"><span data-stu-id="e815f-110">Create entity classes</span></span>

1. <span data-ttu-id="e815f-111">在 Visual Basic 或 c # 中建立新的 WPF 應用程式專案，並將其命名為 `DataGridSQLExample` 。</span><span class="sxs-lookup"><span data-stu-id="e815f-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2. <span data-ttu-id="e815f-112">在方案總管中，以滑鼠右鍵按一下您的專案，指向 [**加入**]，然後選取 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="e815f-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="e815f-113">[加入新項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e815f-113">The Add New Item dialog box appears.</span></span>

3. <span data-ttu-id="e815f-114">在 [已安裝的範本] 窗格中，選取 [**資料**]，然後在範本清單中選取 [ **ADO.NET 實體資料模型**]。</span><span class="sxs-lookup"><span data-stu-id="e815f-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![ADO.NET 實體資料模型專案範本](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. <span data-ttu-id="e815f-116">將檔案命名為 `AdventureWorksModel.edmx` ，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="e815f-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="e815f-117">[實體資料模型精靈] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e815f-117">The Entity Data Model Wizard appears.</span></span>

5. <span data-ttu-id="e815f-118">在 [選擇模型內容] 畫面中，從 [資料庫] 選取**EF Designer** ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="e815f-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6. <span data-ttu-id="e815f-119">在 [選擇您的資料連線] 畫面上，提供 AdventureWorksLT2008 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="e815f-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="e815f-120">如需詳細資訊，請參閱[選擇您的資料連線對話方塊](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e815f-120">For more information, see [Choose Your Data Connection Dialog Box](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).</span></span>

    <span data-ttu-id="e815f-121">請確定 [名稱] 是 `AdventureWorksLT2008Entities` ，而且已選取 [**將 app.config 中的實體連接設定儲存為**] 核取方塊，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="e815f-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7. <span data-ttu-id="e815f-122">在 [選擇您的資料庫物件] 畫面中，展開 [資料表] 節點，然後選取 [ **Product** ] 和 [ **ProductCategory** ] 資料表。</span><span class="sxs-lookup"><span data-stu-id="e815f-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="e815f-123">您可以為所有資料表產生實體類別;不過，在此範例中，您只會從這兩個數據表中取出資料。</span><span class="sxs-lookup"><span data-stu-id="e815f-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="e815f-124">![從 [資料表] 選取 [Product] 和 [ProductCategory]](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="e815f-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="e815f-125">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="e815f-125">Click **Finish**.</span></span>

     <span data-ttu-id="e815f-126">[產品] 和 [ProductCategory] 實體會顯示在 Entity Designer 中。</span><span class="sxs-lookup"><span data-stu-id="e815f-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="e815f-127">![Product 和 ProductCategory 實體模型](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="e815f-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="e815f-128">取出和呈現資料</span><span class="sxs-lookup"><span data-stu-id="e815f-128">Retrieve and present the data</span></span>

1. <span data-ttu-id="e815f-129">開啟 Mainwindow.xaml. xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="e815f-129">Open the MainWindow.xaml file.</span></span>

2. <span data-ttu-id="e815f-130">將 <xref:System.Windows.FrameworkElement.Width%2A> 上的屬性設定 <xref:System.Windows.Window> 為450。</span><span class="sxs-lookup"><span data-stu-id="e815f-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3. <span data-ttu-id="e815f-131">在 XAML 編輯器中，于 <xref:System.Windows.Controls.DataGrid> 和標記之間加入下列標記， `<Grid>` `</Grid>` 以新增 <xref:System.Windows.Controls.DataGrid> 名為的 `dataGrid1` 。</span><span class="sxs-lookup"><span data-stu-id="e815f-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="e815f-132">![包含資料格的視窗](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="e815f-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4. <span data-ttu-id="e815f-133">選取 <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="e815f-133">Select the <xref:System.Windows.Window>.</span></span>

5. <span data-ttu-id="e815f-134">使用屬性視窗或 XAML 編輯器，為事件的指定建立事件處理 <xref:System.Windows.Window> 程式 `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> 。</span><span class="sxs-lookup"><span data-stu-id="e815f-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="e815f-135">如需詳細資訊，請參閱[如何：建立簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e815f-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="e815f-136">以下顯示 Mainwindow.xaml 的 XAML。</span><span class="sxs-lookup"><span data-stu-id="e815f-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e815f-137">如果您使用 Visual Basic，請在 Mainwindow.xaml 的第一行中，將取代 `x:Class="DataGridSQLExample.MainWindow"` 為 `x:Class="MainWindow"` 。</span><span class="sxs-lookup"><span data-stu-id="e815f-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. <span data-ttu-id="e815f-138">開啟的程式碼後置檔案（Mainwindow.xaml 或 MainWindow.xaml.cs） <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="e815f-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7. <span data-ttu-id="e815f-139">加入下列程式碼，只從聯結的資料表中取出特定的值，並將的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定 <xref:System.Windows.Controls.DataGrid> 為查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="e815f-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. <span data-ttu-id="e815f-140">執行範例。</span><span class="sxs-lookup"><span data-stu-id="e815f-140">Run the example.</span></span>

     <span data-ttu-id="e815f-141">您應該會看到 <xref:System.Windows.Controls.DataGrid> 顯示資料的。</span><span class="sxs-lookup"><span data-stu-id="e815f-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="e815f-142">![包含 SQL 資料庫之資料的資料格](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="e815f-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="e815f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e815f-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
