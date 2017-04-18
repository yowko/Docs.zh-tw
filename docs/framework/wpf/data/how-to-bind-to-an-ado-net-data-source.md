---
title: "如何：繫結至 ADO.NET 資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ADO.NET 資料來源, 繫結至"
  - "繫結, 至 ADO.NET 資料來源"
  - "資料繫結, 繫結至 ADO.NET 資料來源"
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：繫結至 ADO.NET 資料來源
這個範例顯示如何將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> 控制項繫結至 [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`。  
  
## 範例  
 在這個範例中，`OleDbConnection` 物件會用於連接到資料來源，這個資料來源是連接字串 \(Connection String\) 中指定的 `Access MDB` 檔案。  建立連接之後，會建立 `OleDbDataAdpater` 物件。  `OleDbDataAdpater` 物件會執行一個 select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] 陳述式從資料庫擷取資料錄集 \(Recordset\)。  [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] 命令的結果會透過呼叫 `OleDbDataAdapter` 的 `Fill` 方法，儲存在 `DataSet` 的 `DataTable` 中。  這個範例中的 `DataTable` 名為 `BookTable`。  然後範例會將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性設為 `DataSet` 物件。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 然後我們就可以將 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性繫結至 `DataSet` 的 `BookTable`：  
  
 [!code-xml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate` 是一種定義資料顯示方式的 <xref:System.Windows.DataTemplate>：  
  
 [!code-xml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` 會將 `int` 轉換成色彩。  如果使用這個轉換器時，`NumPages` 的值小於 350，則第三個 <xref:System.Windows.Controls.TextBlock> 的 <xref:System.Windows.Controls.TextBlock.Background%2A> 色彩會顯示綠色，否則會顯示紅色。  這裡不顯示轉換器的實作。  
  
## 請參閱  
 <xref:System.Windows.Data.BindingListCollectionView>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)