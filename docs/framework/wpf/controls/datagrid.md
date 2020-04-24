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
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646123"
---
# <a name="datagrid"></a>DataGrid
該<xref:System.Windows.Controls.DataGrid>控制項使您能夠顯示和編輯來自許多不同的源的資料,例如來自 SQL 資料庫、LINQ 查詢或任何其他可綁定資料來源的資料。 如需詳細資訊，請參閱[繫結來源概觀](../data/binding-sources-overview.md)。  
  
 列可以顯示文本、控件(如<xref:System.Windows.Controls.ComboBox>) 或任何其他 WPF 內容,如圖像、按鈕或範本中包含的任何內容。 可以使用<xref:System.Windows.Controls.DataGridTemplateColumn>顯示 樣本中定義的數據。 下表列出了默認情況下提供的列類型。  
  
|產生的欄型態|資料類型|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>可以在外觀(如單元格字體、顏色和大小)中自定義。 <xref:System.Windows.Controls.DataGrid>支援其他 WPF 控件的所有樣式和範本化功能。 <xref:System.Windows.Controls.DataGrid>還包括用於編輯、排序和驗證的預設和可自定義行為。  
  
 下表列出了一<xref:System.Windows.Controls.DataGrid>些常見任務以及如何完成這些任務。 以查看相關的 API,您可以找到更多資訊和範例碼。  
  
|狀況|方法|  
|--------------|--------------|  
|替代背景顏色|將<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>屬性設置為 2 或更多,<xref:System.Windows.Media.Brush>然後<xref:System.Windows.Controls.DataGrid.RowBackground%2A>將<xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>分配到和 屬性。|  
|定義儲存格與行選擇行為|請設定 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性。|  
|自訂標題、儲存格和行的視覺外觀|<xref:System.Windows.Style>將新應用於<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>、或<xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A><xref:System.Windows.Controls.DataGrid.CellStyle%2A><xref:System.Windows.Controls.DataGrid.RowStyle%2A>屬性。|  
|設定大小調整選項|設定<xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A>、 <xref:System.Windows.FrameworkElement.MinWidth%2A> 、 、 、 、 、 關於詳細資訊,請參考[資料格線控制的大小調整選項](sizing-options-in-the-datagrid-control.md)。|  
|存取選取的項目|檢查屬性<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>以取得所選單元格<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A>和 屬性以獲取所選行。 如需詳細資訊，請參閱 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>。|  
|自訂最終使用者互動|設置<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> 、 、 屬性。|  
|取消或變更自動產生的欄位|處理事件<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>。|  
|凍結欄|將<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A>屬性設置為 1,並將列移動到最左側的位置<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A>,將 屬性設置為 0。|  
|使用 XML 資料作為資料來源|將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>上綁<xref:System.Windows.Controls.DataGrid>定 到表示項集合的 XPath 查詢。 在 中創建<xref:System.Windows.Controls.DataGrid>每 一列。 通過在綁定上設置 XPath 綁定到獲取項源上的屬性的查詢來綁定每個列。 如需範例，請參閱 <xref:System.Windows.Controls.DataGridTextColumn>。|  
  
## <a name="related-topics"></a>相關主題  
  
|Title|描述|  
|-----------|-----------------|  
|[逐步解說：在 DataGrid 控制項中顯示來自 SQL Server 資料庫的資料](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|描述如何設置新的 WPF 專案、添加實體框架元素、設置源<xref:System.Windows.Controls.DataGrid>並在 中 顯示數據。|  
|[如何：將資料列詳細資料加入至 DataGrid 控制項](how-to-add-row-details-to-a-datagrid-control.md)|描述如何為 創建<xref:System.Windows.Controls.DataGrid>行詳細資訊。|  
|[操作說明：使用 DataGrid 控制項實作驗證](how-to-implement-validation-with-the-datagrid-control.md)|描述如何驗證單元格和行<xref:System.Windows.Controls.DataGrid>中的值,並顯示驗證反饋。|  
|[DataGrid 控制項中的預設鍵盤和滑鼠行為](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|描述如何使用鍵盤和滑鼠與<xref:System.Windows.Controls.DataGrid>控制項進行互動。|  
|[操作說明：在 DataGrid 控制項中分組、排序和篩選資料](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|描述如何通過分組、排序和篩選<xref:System.Windows.Controls.DataGrid>數據以不同的方式查看數據。|  
|[DataGrid 控制項中的調整大小選項](sizing-options-in-the-datagrid-control.md)|描述如何在 中控制絕對與自動調整<xref:System.Windows.Controls.DataGrid>大小調整 。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DataGrid>
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [控制項](index.md)
- [WPF 內容模型](wpf-content-model.md)
