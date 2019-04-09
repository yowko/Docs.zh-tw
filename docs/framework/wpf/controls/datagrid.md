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
ms.openlocfilehash: dda712d58a4ff956de074ecd416402ba0aece5f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197148"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>控制項可讓您顯示和編輯資料從許多不同的來源，例如，從 SQL database、 LINQ 查詢或任何其他可繫結的資料來源。 如需詳細資訊，請參閱[繫結來源概觀](../data/binding-sources-overview.md)。  
  
 資料行可以顯示文字的控制項，例如<xref:System.Windows.Controls.ComboBox>，或任何其他 WPF 內容，例如影像、 按鈕或在範本中所包含的任何內容。 您可以使用<xref:System.Windows.Controls.DataGridTemplateColumn>顯示範本中所定義的資料。 下表列出預設提供的資料行類型。  
  
|產生的資料行類型|資料類型|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> 您可以自訂外觀，例如資料格的字型、 色彩和大小。 <xref:System.Windows.Controls.DataGrid> 支援所有其他的 WPF 控制項的樣式和範本化功能。 <xref:System.Windows.Controls.DataGrid> 也包含預設和可自訂的行為，進行編輯、 排序和驗證。  
  
 下表列出一些常見工作的<xref:System.Windows.Controls.DataGrid>，以及如何完成這些工作。 藉由檢視相關的 API，您可以找到詳細資訊和範例程式碼。  
  
|情節|方法|  
|--------------|--------------|  
|更改背景色彩|設定<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>屬性為 2 或更多，然後指派<xref:System.Windows.Media.Brush>要<xref:System.Windows.Controls.DataGrid.RowBackground%2A>和<xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>屬性。|  
|定義資料格和資料列的選取行為|設定 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性。|  
|自訂標頭、 資料格，以及資料列的視覺外觀|適用於新<xref:System.Windows.Style>要<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>， <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>， <xref:System.Windows.Controls.DataGrid.CellStyle%2A>，或<xref:System.Windows.Controls.DataGrid.RowStyle%2A>屬性。|  
|設定調整大小選項|設定<xref:System.Windows.FrameworkElement.Height%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>， <xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.MaxWidth%2A>，或<xref:System.Windows.FrameworkElement.MinWidth%2A>屬性。 如需詳細資訊，請參閱 < [DataGrid 控制項中的調整大小選項](sizing-options-in-the-datagrid-control.md)。|  
|存取選取的項目|請檢查<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>屬性來取得所選儲存格和<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A>屬性，以取得選取的資料列。 如需詳細資訊，請參閱<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>。|  
|自訂使用者互動|設定<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>， <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>， <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>， <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>， <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>，和<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>屬性。|  
|取消或變更自動產生的資料行|處理<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>事件。|  
|凍結資料行|設定<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A>屬性設為 1，並移動資料行的最左邊的位置來設定<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A>屬性設為 0。|  
|使用 XML 資料做為資料來源|繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>上<xref:System.Windows.Controls.DataGrid>XPath 查詢，其代表的項目集合。 建立每個資料行<xref:System.Windows.Controls.DataGrid>。 每個資料行繫結所設定之查詢的項目來源取得的屬性繫結上的 XPath。 如需範例，請參閱 <xref:System.Windows.Controls.DataGridTextColumn>。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|說明如何設定新的 WPF 專案中，新增 Entity Framework 項目、 設定來源，並顯示資料的<xref:System.Windows.Controls.DataGrid>。|  
|[HOW TO：將資料列詳細資料新增至 DataGrid 控制項](how-to-add-row-details-to-a-datagrid-control.md)|描述如何建立資料列詳細資料，如<xref:System.Windows.Controls.DataGrid>。|  
|[HOW TO：使用 DataGrid 控制項實作驗證](how-to-implement-validation-with-the-datagrid-control.md)|描述如何驗證中的值<xref:System.Windows.Controls.DataGrid>儲存格和資料列，並顯示驗證回應。|  
|[DataGrid 控制項中的預設鍵盤和滑鼠行為](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|描述如何互動<xref:System.Windows.Controls.DataGrid>使用鍵盤和滑鼠的控制項。|  
|[HOW TO：在 DataGrid 控制項中分組、排序和篩選資料](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|描述如何檢視中的資料<xref:System.Windows.Controls.DataGrid>以不同的方式，藉由將分組、 排序和篩選資料。|  
|[DataGrid 控制項中的調整大小選項](sizing-options-in-the-datagrid-control.md)|描述如何控制中的絕對和自動調整大小<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- [樣式設定和範本化](styling-and-templating.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [控制項](index.md)
- [WPF 內容模型](wpf-content-model.md)
