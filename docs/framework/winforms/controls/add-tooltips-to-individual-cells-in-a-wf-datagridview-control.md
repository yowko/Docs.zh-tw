---
title: 將工具提示加入至 DataGridView 控制項中的個別儲存格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732188"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>如何：將工具提示加入至 Windows Form DataGridView 控制項中的個別儲存格
根據預設，工具提示是用來顯示太小而無法顯示其全部內容的 <xref:System.Windows.Forms.DataGridView> 資料格的值。 不過，您可以覆寫此行為，以設定個別資料格的工具提示文字值。 這適用于向使用者顯示資料格的其他相關資訊，或為使用者提供資料格內容的替代描述。 例如，如果您有一個顯示狀態圖示的資料列，您可能會想要使用工具提示來提供文字說明。  
  
 您也可以將 [<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>] 屬性設定為 [`false`]，以停用資料格層級工具提示的顯示。  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>若要將工具提示加入至資料格  
  
- 設定 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含名為 `Rating` 的資料行，可顯示一到四個星號（"*"）符號的字串值。 控制項的 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件必須與範例中所示的事件處理常式方法相關聯。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 當您將 <xref:System.Windows.Forms.DataGridView> 控制項系結到外部資料源，或藉由執行虛擬模式來提供自己的資料來源時，可能會遇到效能問題。 若要避免使用大量資料時的效能損失，請處理 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> 事件，而不是設定多個儲存格的 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性。 當您處理這個事件時，取得資料格的值 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 屬性會引發事件，並傳回事件處理常式中所指定 <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> 屬性的值。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計](programming-with-cells-rows-and-columns-in-the-datagrid.md)
