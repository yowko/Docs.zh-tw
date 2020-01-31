---
title: 自訂 DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744019"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>自訂 Windows Form DataGridView 控制項
`DataGridView` 控制項提供數個屬性，可讓您用來調整其資料格、資料列和資料行的外觀和基本行為（外觀與風格）。 不過，如果您有超出 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別功能的特殊需求，您也可以透過建立自訂資料格、資料行和資料列的方式，為控制項執行主控描繪或擴充其功能。  
  
 若要自行繪製儲存格和資料列，您可以處理各種 `DataGridView` 繪製事件。 若要修改現有的功能或提供新的功能，您可以建立衍生自現有 `DataGridViewCell`、`DataGridViewColumn`和 `DataGridViewRow` 類型的專屬類型。 您也可以藉由建立衍生型別來提供新的編輯功能，以在儲存格處於編輯模式時，顯示您所選擇的控制項。  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)  
 描述如何處理 <xref:System.Windows.Forms.DataGridView.CellPainting> 事件，以便手動繪製儲存格。  
  
 [操作說明：在 Windows Forms DataGridView 控制項中自訂資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)  
 描述如何處理 <xref:System.Windows.Forms.DataGridView.RowPrePaint> 和 <xref:System.Windows.Forms.DataGridView.RowPostPaint> 事件，以便使用自訂的漸層背景和跨越多個資料行的內容繪製資料列。  
  
 [操作說明：擴充儲存格和資料行的行為和外觀以自訂 Windows Forms DataGridView 控制項中的儲存格和資料行](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 描述如何建立從 `DataGridViewCell` 和 `DataGridViewColumn` 衍生的自訂類型，以便在滑鼠指標停留在資料格上時反白顯示。  
  
 [操作說明：停用 Windows Forms DataGridView 控制項按鈕資料行中的按鈕](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 描述如何建立從 <xref:System.Windows.Forms.DataGridViewButtonCell> 和 <xref:System.Windows.Forms.DataGridViewButtonColumn> 衍生的自訂類型，以便在按鈕資料行中顯示已停用的按鈕。  
  
 [操作說明：Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 描述如何執行 `IDataGridViewEditingControl` 介面，並建立從 `DataGridViewCell` 和 `DataGridViewColumn` 衍生的自訂類型，以便在儲存格處於編輯模式時顯示 <xref:System.Windows.Forms.DateTimePicker> 控制項。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 提供 <xref:System.Windows.Forms.DataGridViewCell> 類別的參考檔。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 提供 <xref:System.Windows.Forms.DataGridViewRow> 類別的參考檔。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 提供 <xref:System.Windows.Forms.DataGridViewColumn> 類別的參考檔。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 提供 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面的參考檔。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。  
  
## <a name="see-also"></a>請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
