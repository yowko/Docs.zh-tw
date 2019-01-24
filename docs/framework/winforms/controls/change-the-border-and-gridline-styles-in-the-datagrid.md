---
title: HOW TO：變更 框線 及 Windows Form DataGridView 控制項中的格線樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 052538f22c1da9836a61f66e3230e5e3e3cc72cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590886"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>HOW TO：變更 框線 及 Windows Form DataGridView 控制項中的格線樣式
使用<xref:System.Windows.Forms.DataGridView>控制項，您可以自訂控制項的框線和格線可改善使用者體驗的外觀。 您可以修改格線的色彩，除了在控制項內的資料格的框線樣式的控制項框線樣式。 您也可以套用不同的儲存格一般的資料格、 資料列標題儲存格和資料行標題儲存格的框線樣式。  
  
> [!NOTE]
>  格線的色彩只適用於<xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>， <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>，並<xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical>的值<xref:System.Windows.Forms.DataGridViewCellBorderStyle>列舉型別和<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single>的值<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>列舉型別。 這些列舉的其他值會使用作業系統所指定的色彩。 此外，當啟用視覺化樣式在 Windows XP 和 Windows Server 2003 系列，透過<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法，<xref:System.Windows.Forms.DataGridView.GridColor%2A>不會使用屬性值。  
  
### <a name="to-change-the-gridline-color-programmatically"></a>若要以程式設計方式變更的格線色彩  
  
-   設定 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>若要以程式設計方式變更整個 DataGridView 控制項的框線樣式  
  
-   將 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.BorderStyle> 列舉值。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>若要以程式設計方式變更 DataGridView 儲存格的框線樣式  
  
-   設定<xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>， <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>，和<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
