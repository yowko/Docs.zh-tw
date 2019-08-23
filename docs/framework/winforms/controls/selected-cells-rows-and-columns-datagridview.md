---
title: 作法：取得 Windows Forms DataGridView 控制項中已選取的儲存格、資料列和資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960521"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>作法：取得 Windows Forms DataGridView 控制項中已選取的儲存格、資料列和資料行
您可以使用對應的屬性, 從<xref:System.Windows.Forms.DataGridView>控制項取得選取的儲存格、資料列或資料行: <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、和<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>。 在下列程式中, 您會取得選取的儲存格, 並在中<xref:System.Windows.Forms.MessageBox>顯示其資料列和資料行索引。  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的儲存格  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 屬性。  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>使用方法, 以避免顯示可能大量的資料格。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的資料列  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 屬性。 若要讓使用者選取資料列, 您必須將<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性設定<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>為<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>若要取得 DataGridView 控制項中選取的資料行  
  
- 請使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 屬性。 若要讓使用者能夠選取資料行, 您必須<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>將屬性<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>設定<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>為或。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Windows.Forms.Button>名為`selectedCellsButton`、 `selectedRowsButton`和`selectedColumnsButton`的<xref:System.Windows.Forms.Control.Click>控制項, 每個都有附加事件的處理常式。  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 選取大量的資料格、資料列或資料行時, 本主題中所述的集合不會有效率地執行。 如需有關使用這些具有大量資料之集合的詳細資訊, 請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [選取範圍和剪貼簿與 Windows Forms DataGridView 控制項搭配使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
