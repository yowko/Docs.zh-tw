---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: a8f267706c1ace02b091329360779711981d01e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>控制項可讓您顯示和編輯資料從許多不同來源，例如，從 SQL 資料庫、 LINQ 查詢或任何其他可繫結的資料來源。 如需詳細資訊，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
 資料行可以顯示文字的控制項，例如<xref:System.Windows.Controls.ComboBox>，或任何其他 WPF 內容，例如影像、 按鈕或在範本中所包含的任何內容。 您可以使用<xref:System.Windows.Controls.DataGridTemplateColumn>顯示範本中定義的資料。 下表列出預設提供的資料行類型。  
  
|產生的資料行類型|資料類型|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> 您可以自訂的外觀，例如儲存格的字型、 色彩和大小。 <xref:System.Windows.Controls.DataGrid> 支援其他的 WPF 控制項的所有設定樣式和範本功能。 <xref:System.Windows.Controls.DataGrid> 也包含預設值，以及編輯、 排序和驗證自訂行為。  
  
 下表列出一些常見的工<xref:System.Windows.Controls.DataGrid>以及如何完成這些工作。 藉由檢視相關的 API，您可以找到詳細資訊和範例程式碼。  
  
|情節|方法|  
|--------------|--------------|  
|更改背景色彩|設定<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>屬性為 2 或更多，然後指派<xref:System.Windows.Media.Brush>至<xref:System.Windows.Controls.DataGrid.RowBackground%2A>和<xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>屬性。|  
|定義資料格和資料列選取行為|設定 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性。|  
|自訂標頭、 資料格，以及資料列的視覺外觀|套用新的<xref:System.Windows.Style>至<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>， <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>， <xref:System.Windows.Controls.DataGrid.CellStyle%2A>，或<xref:System.Windows.Controls.DataGrid.RowStyle%2A>屬性。|  
|設定調整大小選項|設定<xref:System.Windows.FrameworkElement.Height%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>， <xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.MaxWidth%2A>，或<xref:System.Windows.FrameworkElement.MinWidth%2A>屬性。 如需詳細資訊，請參閱[DataGrid 控制項中的調整大小選項](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)。|  
|存取選取的項目|請檢查<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>屬性來取得選取的資料格和<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A>屬性來取得選取的資料列。 如需詳細資訊，請參閱<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>。|  
|自訂使用者互動|設定<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>， <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>， <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>， <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>， <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>，和<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>屬性。|  
|取消或變更自動產生的資料行|處理<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>事件。|  
|凍結資料行|設定<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A>屬性設為 1，並移動資料行的最左邊的位置設定<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A>屬性設為 0。|  
|使用 XML 資料做為資料來源|繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>上<xref:System.Windows.Controls.DataGrid>XPath 查詢，其代表項目的集合。 建立每個資料行<xref:System.Windows.Controls.DataGrid>。 每個資料行繫結的項目來源取得屬性的查詢將繫結上設定 XPath。 如需範例，請參閱 <xref:System.Windows.Controls.DataGridTextColumn>。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|描述如何設定新的 WPF 專案，加入實體架構項目、 設定來源，以及顯示資料的<xref:System.Windows.Controls.DataGrid>。|  
|[操作說明：將資料列詳細資料加入至 DataGrid 控制項](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|描述如何建立資料列詳細資料，如<xref:System.Windows.Controls.DataGrid>。|  
|[操作說明：使用 DataGrid 控制項實作驗證](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|描述如何驗證中的值<xref:System.Windows.Controls.DataGrid>儲存格和資料列，並顯示驗證回應。|  
|[DataGrid 控制項中的預設鍵盤和滑鼠行為](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|描述如何互動<xref:System.Windows.Controls.DataGrid>使用鍵盤和滑鼠控制。|  
|[操作說明：在 DataGrid 控制項中分組、排序和篩選資料](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|描述如何檢視中的資料<xref:System.Windows.Controls.DataGrid>透過分組、 排序和篩選的資料不同的方式。|  
|[DataGrid 控制項中的調整大小選項](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|描述如何控制中的絕對和自動調整大小<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.DataGrid>  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [控制項](../../../../docs/framework/wpf/controls/index.md)  
 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)
