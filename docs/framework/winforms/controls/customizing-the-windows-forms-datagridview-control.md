---
title: 自訂 Windows Form DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: ab8d1f07c608aca4f14f5e73860f8c3e263a4610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091378"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>自訂 Windows Form DataGridView 控制項
`DataGridView`控制項提供您可用來調整的外觀和其資料格、 資料列和資料行的基本行為 （外觀及操作） 的數個屬性。 如果您有特殊需求的功能之外<xref:System.Windows.Forms.DataGridViewCellStyle>類別中，不過，您也可以實作主控描繪控制項或擴充其功能，藉由建立自訂的資料格、 資料行和資料列。  
  
 若要繪製的儲存格和資料列自行，您可以處理各種`DataGridView`繪製事件。 若要修改現有的功能，或提供新功能，您可以建立自己的型別衍生自現有`DataGridViewCell`， `DataGridViewColumn`，和`DataGridViewRow`型別。 您也可以建立顯示您選擇的儲存格處於編輯模式的控制項的衍生型別，以提供新的編輯功能。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)  
 描述如何處理<xref:System.Windows.Forms.DataGridView.CellPainting>手動事件，以繪製儲存格。  
  
 [如何：自訂 Windows Form DataGridView 控制項中的資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)  
 描述如何處理<xref:System.Windows.Forms.DataGridView.RowPrePaint>和<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件以繪製自訂的漸層背景的資料列和內容，跨越多個資料行。  
  
 [如何：自訂儲存格和 Windows Form DataGridView 控制項中的資料行，藉由擴充其行為和外觀](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 描述如何建立自訂的型別衍生自`DataGridViewCell`和`DataGridViewColumn`才能將滑鼠指標停留在其上時，反白顯示的資料格。  
  
 [如何：停用在 Windows Form DataGridView 控制項按鈕資料行中的按鈕](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 描述如何建立自訂的型別衍生自<xref:System.Windows.Forms.DataGridViewButtonCell>和<xref:System.Windows.Forms.DataGridViewButtonColumn>若要在按鈕資料行中顯示已停用的按鈕。  
  
 [如何：在 Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 描述如何實作`IDataGridViewEditingControl`介面，並建立自訂的型別衍生自`DataGridViewCell`並`DataGridViewColumn`以顯示<xref:System.Windows.Forms.DateTimePicker>控制當儲存格處於編輯模式。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 提供參考文件<xref:System.Windows.Forms.DataGridViewCell>類別。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 提供參考文件<xref:System.Windows.Forms.DataGridViewRow>類別。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 提供參考文件<xref:System.Windows.Forms.DataGridViewColumn>類別。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 提供參考文件<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何修改控制項基本外觀和儲存格資料顯示格式。  
  
## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
