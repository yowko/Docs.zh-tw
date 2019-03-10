---
title: HOW TO：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: c34807cc1d2a569068ba82479e3a2bf230f4f2c5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704403"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>HOW TO：啟用 Windows Form DataGridView 控制項中的資料行重新調整順序
當您在 <xref:System.Windows.Forms.DataGridView> 控制項中啟用資料行重新調整順序，使用者可以使用滑鼠拖曳資料行標頭，將資料行移至新的位置。 在 <xref:System.Windows.Forms.DataGridView> 控制項中，<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> 屬性值會決定使用者是否能將資料行移至不同位置。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[How to:啟用資料行重新調整順序中的 Windows Form DataGridView 控制項使用設計工具](enable-column-reordering-in-the-datagrid-using-the-designer.md)。  
  
### <a name="to-enable-column-reordering-programmatically"></a>以程式設計方式啟用資料行重新調整順序  
  
-   將 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> 屬性設定為 `true`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   
  <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [如何：凍結 Windows Form DataGridView 控制項中的資料行](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
