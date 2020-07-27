---
title: DataGrid
description: 瞭解 DataGrid 控制項如何讓您顯示和編輯不同來源的資料，例如資料庫、LINQ 查詢或任何其他可系結的資料來源。
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
ms.openlocfilehash: 3db49c12fcb363ef7f99e5c69beae09ab05addcf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168322"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>控制項可讓您顯示和編輯來自許多不同來源的資料，例如從 SQL 資料庫、LINQ 查詢或任何其他可系結的資料來源。 如需詳細資訊，請參閱[繫結來源概觀](../data/binding-sources-overview.md)。  
  
 資料行可以顯示文字、控制項（例如 <xref:System.Windows.Controls.ComboBox> ）或任何其他 WPF 內容，例如影像、按鈕或範本中包含的任何內容。 您可以使用 <xref:System.Windows.Controls.DataGridTemplateColumn> 來顯示範本中定義的資料。 下表列出預設提供的資料行類型。  
  
|產生的資料行類型|資料類型|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>可以在外觀中進行自訂，例如儲存格字型、色彩和大小。 <xref:System.Windows.Controls.DataGrid>支援其他 WPF 控制項的所有樣式設定和範本化功能。 <xref:System.Windows.Controls.DataGrid>也包含用於編輯、排序和驗證的預設和可自訂行為。  
  
 下表列出中的一些常見工作 <xref:System.Windows.Controls.DataGrid> ，以及如何完成這些作業。 藉由查看相關的 API，您可以找到詳細資訊和範例程式碼。  
  
|狀況|方法|  
|--------------|--------------|  
|替換背景色彩|將 <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> 屬性設定為2或以上，然後將指派給 <xref:System.Windows.Media.Brush> <xref:System.Windows.Controls.DataGrid.RowBackground%2A> 和 <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> 屬性。|  
|定義資料格和資料列選取行為|請設定 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性。|  
|自訂標頭、儲存格和資料列的視覺外觀|將新的套用 <xref:System.Windows.Style> 至 <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> 、 <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> 、 <xref:System.Windows.Controls.DataGrid.CellStyle%2A> 或 <xref:System.Windows.Controls.DataGrid.RowStyle%2A> 屬性。|  
|設定調整大小選項|設定 <xref:System.Windows.FrameworkElement.Height%2A> 、、 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 、 <xref:System.Windows.FrameworkElement.MinHeight%2A> 、 <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> 或 <xref:System.Windows.FrameworkElement.MinWidth%2A> 屬性。 如需詳細資訊，請參閱[DataGrid 控制項中的調整大小選項](sizing-options-in-the-datagrid-control.md)。|  
|存取選取的專案|請檢查 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> 屬性以取得選取的資料格和 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> 屬性，以取得選取的資料列。 如需詳細資訊，請參閱 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>。|  
|自訂使用者互動|設定 <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> 、、 <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> 、 <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> 、 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> 和 <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> 屬性。|  
|取消或變更自動產生的資料行|處理 <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> 事件。|  
|凍結資料行|將 <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 屬性設定為1，並將此屬性設定為0，將資料行移至最左邊的位置 <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> 。|  
|使用 XML 資料做為資料來源|將上的系結 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> 至代表專案集合的 XPath 查詢。 在中建立每個資料行 <xref:System.Windows.Controls.DataGrid> 。 藉由將系結上的 XPath 設定為可取得專案來源屬性的查詢，系結每個資料行。 如需範例，請參閱 <xref:System.Windows.Controls.DataGridTextColumn>。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|描述如何設定新的 WPF 專案、加入 Entity Framework 元素、設定來源，以及在中顯示資料 <xref:System.Windows.Controls.DataGrid> 。|  
|[作法：將資料列詳細資料新增至 DataGrid 控制項](how-to-add-row-details-to-a-datagrid-control.md)|描述如何建立的資料列詳細資料 <xref:System.Windows.Controls.DataGrid> 。|  
|[作法：使用 DataGrid 控制項實作驗證](how-to-implement-validation-with-the-datagrid-control.md)|描述如何驗證 <xref:System.Windows.Controls.DataGrid> 儲存格和資料列中的值，以及顯示驗證意見反應。|  
|[DataGrid 控制項中的預設鍵盤和滑鼠行為](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|描述如何 <xref:System.Windows.Controls.DataGrid> 使用鍵盤和滑鼠與控制項互動。|  
|[作法：在 DataGrid 控制項中分組、排序和篩選資料](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|描述如何透過 <xref:System.Windows.Controls.DataGrid> 分組、排序和篩選資料，以不同的方式來查看中的資料。|  
|[DataGrid 控制項中的調整大小選項](sizing-options-in-the-datagrid-control.md)|描述如何在中控制絕對和自動調整大小 <xref:System.Windows.Controls.DataGrid> 。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [控制項](index.md)
- [WPF 內容模型](wpf-content-model.md)
