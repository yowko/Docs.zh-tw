---
title: "如何：將資料列詳細資料加入至 DataGrid 控制項 | Microsoft Docs"
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
  - "DataGrid [WPF], 資料列詳細資料"
  - "DataTemplate [WPF], DataGrid"
  - "資料列詳細資料 [WPF], DataGrid"
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將資料列詳細資料加入至 DataGrid 控制項
使用 <xref:System.Windows.Controls.DataGrid> 控制項即可透過加入資料列詳細資料區段的方式，自訂資料表示。  加入資料列詳細資料區段可讓您將範本中可以選擇性顯示或摺疊的某些資料組成群組。  例如，您可以將資料列詳細資料加入至 <xref:System.Windows.Controls.DataGrid>，它在 <xref:System.Windows.Controls.DataGrid> 中僅呈現每一個資料列的資料摘要，但是會在使用者選取資料列時呈現更多資料欄位。  您可在 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性中定義資料列詳細資料區段的範本。  下圖顯示資料列詳細資料區段的範例。  
  
 ![包含資料列詳細資料的資料格](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP\_RowDetails")  
  
 您可以將資料列詳細資料範本定義為內嵌 XAML 或是資源。  以下程序會顯示這兩種方式。  做為資源加入的資料範本可以在整個專案中使用，而不需要重新建立範本。  做為內嵌 XAML 加入的資料範本則只能從定義該範本所在的控制項存取。  
  
### 若要使用內嵌 XAML 顯示資料列詳細資料  
  
1.  建立從資料來源顯示資料的 <xref:System.Windows.Controls.DataGrid>。  
  
2.  在 <xref:System.Windows.Controls.DataGrid> 項目中加入 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 項目。  
  
3.  建立定義資料列詳細資料區段外觀的 <xref:System.Windows.DataTemplate>。  
  
     下列 XAML 會顯示 <xref:System.Windows.Controls.DataGrid> 以及如何將 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 定義為內嵌。  <xref:System.Windows.Controls.DataGrid> 會顯示每一個資料列中的三個值，並且在已選取資料列時再多顯示三個值。  
  
     [!code-xml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     下列程式碼顯示用來選取 <xref:System.Windows.Controls.DataGrid> 中所顯示資料的查詢。  在此範例中，查詢會從包含客戶資訊的實體選取資料。  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### 若要使用資源顯示資料列詳細資料  
  
1.  建立從資料來源顯示資料的 <xref:System.Windows.Controls.DataGrid>。  
  
2.  將 <xref:System.Windows.FrameworkElement.Resources%2A> 項目加入至根項目，例如 <xref:System.Windows.Window> 控制項或 <xref:System.Windows.Controls.Page> 控制項，或是將 <xref:System.Windows.Application.Resources%2A> 項目加入至 App.xaml \(或 Application.xaml\) 檔案中的 <xref:System.Windows.Application> 類別。  
  
3.  在資源項目中，建立定義資料列詳細資料區段外觀的 <xref:System.Windows.DataTemplate>。  
  
     下列 XAML 顯示 <xref:System.Windows.Application> 類別中定義的 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>。  
  
     [!code-xml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  在 <xref:System.Windows.DataTemplate> 上，將 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md) 設定為唯一識別資料範本的值。  
  
5.  在 <xref:System.Windows.Controls.DataGrid> 項目中，將 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性設定為之前步驟中定義的資源。  將資源指派為靜態資源。  
  
     下列 XAML 會顯示設定為先前範例中之資源的 <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 屬性。  
  
     [!code-xml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### 若要設定可見性並且避免水平捲動資料列詳細資料  
  
1.  如有需要，將 <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> 屬性設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> 值。  
  
     根據預設，此值會設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>。  您可以將它設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>，以顯示所有資料列的詳細資料，或是設定為 <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>，以隱藏所有資料列的詳細資料。  
  
2.  如有需要，將 <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> 屬性設定為 `true`，以避免水平捲動資料列詳細資料區段。