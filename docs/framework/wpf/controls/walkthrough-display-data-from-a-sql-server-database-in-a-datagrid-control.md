---
title: 逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料
description: 瞭解如何使用此逐步解說，從 SQL Server 資料庫取得資料，並將其顯示在 Windows Presentation Foundation DataGrid 控制項中。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: cc41979c869021c9c363f3f68ce590d4702e068c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167550"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料

在此逐步解說中，您會從 SQL Server 資料庫中取出資料，並在控制項中顯示該資料 <xref:System.Windows.Controls.DataGrid> 。 您可以使用 ADO.NET Entity Framework 來建立代表資料的實體類別，並使用 LINQ 來撰寫查詢，以從實體類別抓取指定的資料。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- Visual Studio。

- 存取已附加 AdventureWorks 範例資料庫之 SQL Server 或 SQL Server Express 的執行中實例。 您可以從[GitHub](https://github.com/Microsoft/sql-server-samples/releases)下載 AdventureWorks 資料庫。

## <a name="create-entity-classes"></a>建立實體類別

1. 在 Visual Basic 或 c # 中建立新的 WPF 應用程式專案，並將其命名為 `DataGridSQLExample` 。

2. 在方案總管中，以滑鼠右鍵按一下您的專案，指向 [**加入**]，然後選取 [**新增專案**]。

     [加入新項目] 對話方塊隨即出現。

3. 在 [已安裝的範本] 窗格中，選取 [**資料**]，然後在範本清單中選取 [ **ADO.NET 實體資料模型**]。

     ![ADO.NET 實體資料模型專案範本](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. 將檔案命名為 `AdventureWorksModel.edmx` ，然後按一下 [**新增**]。

     [實體資料模型精靈] 隨即出現。

5. 在 [選擇模型內容] 畫面中，從 [資料庫] 選取**EF Designer** ，然後按 **[下一步]**。

6. 在 [選擇您的資料連線] 畫面上，提供 AdventureWorksLT2008 資料庫的連接。 如需詳細資訊，請參閱[選擇您的資料連線對話方塊](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100))。

    請確定 [名稱] 是 `AdventureWorksLT2008Entities` ，而且已選取 [**將 App.Config 中的實體連接設定為**] 核取方塊，然後按 **[下一步]**。

7. 在 [選擇您的資料庫物件] 畫面中，展開 [資料表] 節點，然後選取 [ **Product** ] 和 [ **ProductCategory** ] 資料表。

     您可以為所有資料表產生實體類別;不過，在此範例中，您只會從這兩個數據表中取出資料。

     ![從 [資料表] 選取 [Product] 和 [ProductCategory]](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. 按一下 [完成] 。

     [產品] 和 [ProductCategory] 實體會顯示在 Entity Designer 中。

     ![Product 和 ProductCategory 實體模型](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>取出和呈現資料

1. 開啟 Mainwindow.xaml. xaml 檔案。

2. 將 <xref:System.Windows.FrameworkElement.Width%2A> 上的屬性設定 <xref:System.Windows.Window> 為450。

3. 在 XAML 編輯器中，于 <xref:System.Windows.Controls.DataGrid> 和標記之間加入下列標記， `<Grid>` `</Grid>` 以新增 <xref:System.Windows.Controls.DataGrid> 名為的 `dataGrid1` 。

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![包含資料格的視窗](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. 選取 <xref:System.Windows.Window>。

5. 使用屬性視窗或 XAML 編輯器，為事件的指定建立事件處理 <xref:System.Windows.Window> 程式 `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> 。 如需詳細資訊，請參閱[如何：建立簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。

     以下顯示 Mainwindow.xaml 的 XAML。

    > [!NOTE]
    > 如果您使用 Visual Basic，請在 Mainwindow.xaml 的第一行中，將取代 `x:Class="DataGridSQLExample.MainWindow"` 為 `x:Class="MainWindow"` 。

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. 開啟的程式碼後置檔案（Mainwindow.xaml 或 MainWindow.xaml.cs） <xref:System.Windows.Window> 。

7. 加入下列程式碼，只從聯結的資料表中取出特定的值，並將的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性設定 <xref:System.Windows.Controls.DataGrid> 為查詢的結果。

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. 執行範例。

     您應該會看到 <xref:System.Windows.Controls.DataGrid> 顯示資料的。

     ![包含 SQL 資料庫之資料的資料格](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
