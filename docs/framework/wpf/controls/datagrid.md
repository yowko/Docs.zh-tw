---
title: "DataGrid | Microsoft Docs"
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
  - "控制項 [WPF], DataGrid"
  - "DataGrid [WPF], 一般工作"
  - "DataGrid [WPF], 自訂外觀"
  - "DataGrid 資料行類型 [WPF]"
  - "DataGrid 資料行 [WPF], 使用"
  - "DataGrid 控制項 [WPF]"
  - "DataGrid 情節 [WPF]"
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DataGrid
<xref:System.Windows.Controls.DataGrid> 控制項可讓您顯示和編輯許多不同來源的資料，例如來自 SQL 資料庫、LINQ 查詢或任何其他可繫結的資料來源。  如需詳細資訊，請參閱 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
 資料行可以顯示文字、控制項 \(例如 <xref:System.Windows.Controls.ComboBox>\) 或任何其他 WPF 內容 \(例如影像、按鈕或樣板中包含的任何內容\)。  您可以使用 <xref:System.Windows.Controls.DataGridTemplateColumn> 來顯示於範本中定義的資料。  下表列出預設提供的資料行型別。  
  
|產生的資料行類型|資料型別|  
|--------------|----------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> 的外觀 \(例如，儲存格字型、色彩和大小\) 可加以自訂。  <xref:System.Windows.Controls.DataGrid> 支援其他 WPF 控制項的所有樣式設定和樣板化功能。  <xref:System.Windows.Controls.DataGrid> 還包括預設及可自訂的編輯、排序與驗證行為。  
  
 下表列出部分 <xref:System.Windows.Controls.DataGrid> 的常見工作以及如何完成這些工作。  您可以藉由檢視相關的 API，找到更多詳細資訊和範例程式碼。  
  
|情節|處理方式|  
|--------|----------|  
|交替使用背景色彩|將 <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> 屬性設定為 2 以上，然後將 <xref:System.Windows.Media.Brush> 指派給 <xref:System.Windows.Controls.DataGrid.RowBackground%2A> 和 <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> 屬性。|  
|定義儲存格和資料列選取行為|設定 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性。|  
|自訂標頭、儲存格和資料列的視覺外觀|將新的 <xref:System.Windows.Style> 套用至 <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.CellStyle%2A> 或 <xref:System.Windows.Controls.DataGrid.RowStyle%2A> 屬性。|  
|設定調整大小選項|設定 <xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>、<xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.MaxWidth%2A> 或 <xref:System.Windows.FrameworkElement.MinWidth%2A> 屬性。  如需詳細資訊，請參閱[DataGrid 控制項中的調整大小選項](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)。|  
|存取選取的項目|核取 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> 屬性可取得選取的儲存格，核取 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> 屬性則可取得選取的資料列。  如需詳細資訊，請參閱 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>。|  
|自訂使用者互動|設定 <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>、<xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>、<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> 和 <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> 屬性。|  
|取消或變更自動產生的資料行|處理 <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> 事件。|  
|凍結資料行|將 <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 屬性設定為 1，並且將資料行移至最左邊的位置 \(將 <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> 屬性設定為 0\)。|  
|將 XML 資料當做資料來源|將 <xref:System.Windows.Controls.DataGrid> 上的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 繫結至代表項目集合的 XPath 查詢。  在 <xref:System.Windows.Controls.DataGrid> 中建立各資料行。  藉由將繫結上的 XPath 設定為可取得項目來源上之屬性的查詢繫結各資料行。  如需範例，請參閱 <xref:System.Windows.Controls.DataGridTextColumn>。|  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|說明如何設定新的 WPF 專案、加入 Entity Framework 項目、設定來源，以及在 <xref:System.Windows.Controls.DataGrid> 中顯示資料。|  
|[如何：將資料列詳細資料加入至 DataGrid 控制項](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|說明如何建立 <xref:System.Windows.Controls.DataGrid> 的資料列詳細資料。|  
|[如何：使用 DataGrid 控制項實作驗證](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|說明如何驗證 <xref:System.Windows.Controls.DataGrid> 儲存格和資料列中的值，並且顯示驗證回應。|  
|[DataGrid 控制項中的預設鍵盤和滑鼠行為](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|說明如何透過鍵盤和滑鼠，與 <xref:System.Windows.Controls.DataGrid> 控制項互動。|  
|[如何：在 DataGrid 控制項中分組、排序和篩選資料](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|說明如何在 <xref:System.Windows.Controls.DataGrid> 中透過分組、排序和篩選資料，以不同的方式檢視資料。|  
|[DataGrid 控制項中的調整大小選項](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|說明如何在 <xref:System.Windows.Controls.DataGrid> 中控制絕對和自動調整大小。|  
  
## 請參閱  
 <xref:System.Windows.Controls.DataGrid>   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [控制項](../../../../docs/framework/wpf/controls/index.md)   
 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)