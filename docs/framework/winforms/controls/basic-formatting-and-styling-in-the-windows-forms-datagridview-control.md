---
title: DataGridView 控制項中的基本格式化和樣式設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732005"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的基本格式化和樣式設定
`DataGridView` 控制項可讓您輕鬆地定義資料格的基本外觀，以及儲存格值的顯示格式。 您可以針對特定資料行和資料列中的儲存格，或是針對控制項中的所有資料格，藉由設定透過各種 `DataGridView` 控制項屬性存取之 `DataGridViewCellStyle` 物件的屬性，來定義其外觀和格式設定樣式。 此外，您可以藉由處理 `CellFormatting` 事件，以動態方式根據因素（例如資料格值）來修改這些樣式。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：變更 Windows Forms DataGridView 控制項中的框線和格線樣式](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 描述如何設定 `DataGridView` 屬性，以定義控制項框線的外觀和儲存格之間的邊界線。  
  
 [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)  
 描述 `DataGridViewCellStyle` 類別，以及該類型的屬性如何互動，以定義如何在控制項中顯示儲存格。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 描述如何使用 `DataGridViewCellStyle` 屬性，在特定的資料列和資料行以及整個控制項中，定義儲存格的預設面板。  
  
 [操作說明：格式化 Windows Forms DataGridView 控制項中的資料](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 描述如何使用 `DataGridViewCellStyle` 屬性來格式化儲存格的顯示值。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的字型和色彩樣式](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 描述如何使用 [`DefaultCellStyle`] 屬性，為控制項中的所有儲存格設定基本顯示特性。  
  
 [操作說明：設定 Windows Forms DataGridView 控制項的替代資料列樣式](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 描述如何使用以不同方式顯示的交替資料列，在控制項中建立類似總帳的效果。  
  
 [操作說明：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 描述如何使用 `RowTemplate` 屬性來設定將用於控制項中所有資料列的資料列屬性。  
  
## <a name="reference"></a>參考  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 提供 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的參考檔。  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 提供 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件的參考檔。  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 提供 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性的參考檔。  
  
## <a name="related-sections"></a>相關章節  
 [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)  
 提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。  
  
 [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 提供描述常用資料格、資料列和資料行屬性的主題。  
  
## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
