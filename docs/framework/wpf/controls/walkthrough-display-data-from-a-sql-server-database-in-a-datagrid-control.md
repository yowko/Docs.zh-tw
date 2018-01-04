---
title: "逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8ed596706c8d656842191262c25301db595ee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料
在本逐步解說中，從 SQL Server 資料庫擷取資料並顯示在該資料<xref:System.Windows.Controls.DataGrid>控制項。 您可以使用 ADO.NET Entity Framework 來建立實體類別，表示資料，並使用 LINQ 來撰寫查詢以擷取指定的資料從實體類別。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   中的 SQL Server 或 SQL Server Express 的 AdventureWorks 範例資料庫，附加至該執行個體的存取。 您可以下載 AdventureWorks 資料庫從[GitHub](https://github.com/Microsoft/sql-server-samples/releases)。  
  
### <a name="to-create-entity-classes"></a>若要建立實體類別  
  
1.  在 Visual Basic 或 C# 中，建立新的 WPF 應用程式專案，並命名`DataGridSQLExample`。  
  
2.  在 [方案總管] 中，以滑鼠右鍵按一下您的專案，指向**新增**，然後選取**新項目**。  
  
     [加入新項目] 對話方塊隨即出現。  
  
3.  在已安裝的範本 窗格中，選取**資料**在範本清單中，選取**ADO.NET 實體資料模式**l。  
  
     ![選取 ADO.NET 實體資料模型](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  將檔案命名`AdventureWorksModel.edmx`，然後按一下 **新增**。  
  
     [實體資料模型精靈] 隨即出現。  
  
5.  在 選擇模型內容 畫面中，選取**從資料庫產生**，然後按一下 **下一步**。  
  
     ![選取 從資料庫選項產生](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  在 [選擇資料連接] 畫面中，提供 AdventureWorksLT2008 資料庫的連接。 如需詳細資訊，請參閱[選擇您的資料連接對話方塊](http://go.microsoft.com/fwlink/?LinkId=160190)。  
  
     ![提供資料庫連接](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  請確定名稱是`AdventureWorksLT2008Entities`而且**將實體連接設定儲存為 App.Config 中**核取方塊已選取，然後按一下 **下一步**。  
  
8.  在 [選擇您的資料庫物件] 畫面中，展開 [資料表] 節點，然後選取**產品**和**ProductCategory**資料表。  
  
     您可以產生實體類別，所有的資料表。不過，在此範例中您只擷取資料從這兩份資料表。  
  
     ![從資料表中選取 Product 和 ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. 按一下 [ **完成**]。  
  
     在 Entity Designer 中，會顯示 Product 和 ProductCategory 實體。  
  
     ![Product 和 ProductCategory 實體模型](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>若要擷取並將資料呈現  
  
1.  開啟 MainWindow.xaml 檔案。  
  
2.  設定<xref:System.Windows.FrameworkElement.Width%2A>屬性<xref:System.Windows.Window>到 450。  
  
3.  在 XAML 編輯器中，加入下列<xref:System.Windows.Controls.DataGrid>標記之間`<Grid>`和`</Grid>`新增標記<xref:System.Windows.Controls.DataGrid>名為`dataGrid1`。  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![包含資料格的視窗](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  選取 <xref:System.Windows.Window>。  
  
5.  使用 [屬性] 視窗或 XAML 編輯器，建立事件處理常式<xref:System.Windows.Window>名為`Window_Loaded`如<xref:System.Windows.FrameworkElement.Loaded>事件。 如需詳細資訊，請參閱[How to： 建立簡單的事件處理常式](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480)。  
  
     下圖顯示 XAML mainwindow.xaml。  
  
    > [!NOTE]
    >  如果您使用 Visual Basic 中，在 MainWindow.xaml 的第一行中，取代`x:Class="DataGridSQLExample.MainWindow"`與`x:Class="MainWindow"`。  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  開啟的程式碼後置檔案 （MainWindow.xaml.vb 或 MainWindow.xaml.cs） <xref:System.Windows.Window>。  
  
7.  加入下列程式碼，來聯結資料表中擷取特定的值及設定<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.DataGrid>查詢的結果。  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  執行範例。  
  
     您應該會看到<xref:System.Windows.Controls.DataGrid>，會顯示資料。  
  
     ![SQL 資料庫中的資料的 DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.DataGrid>  
 [如何 i： 開始使用 WPF 應用程式中的 Entity Framework？](http://go.microsoft.com/fwlink/?LinkId=159868)
