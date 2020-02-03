---
title: 取得 DataGridView 控制項中選取的儲存格、資料列和資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 0079c590ee6e4732523fd50be157bd58ec1bfb1b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743078"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>如何：取得 Windows Form DataGridView 控制項中選取的儲存格、資料列和資料行
您可以使用對應的屬性，從 <xref:System.Windows.Forms.DataGridView> 控制項取得選取的儲存格、資料列或資料行： <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>。 在下列程式中，您會取得選取的儲存格，並在 <xref:System.Windows.Forms.MessageBox>中顯示其資料列和資料行索引。  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的儲存格  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 屬性。  
  
    > [!NOTE]
    > 使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法，以避免顯示可能大量的資料格。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的資料列  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 屬性。 若要讓使用者選取資料列，您必須將 [<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>] 屬性設定為 [<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>] 或 [<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>]。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的資料行  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性。 若要讓使用者能夠選取資料行，您必須將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Windows.Forms.Button> 名為 `selectedCellsButton`、`selectedRowsButton`和 `selectedColumnsButton`的控制項，每個都有附加 <xref:System.Windows.Forms.Control.Click> 事件的處理常式。  
  
- 名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 選取大量的資料格、資料列或資料行時，本主題中所述的集合不會有效率地執行。 如需有關使用這些具有大量資料之集合的詳細資訊，請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
