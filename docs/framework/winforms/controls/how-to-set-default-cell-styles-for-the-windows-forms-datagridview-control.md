---
title: 如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 072a9ce7e28983683ac1104b70c160cf5eea12b7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207240"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式
您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項為整個控制項，以及為特定資料行和資料列，指定預設儲存格樣式。 這些預設值會從控制項層級往下篩選至資料行層級，接著至資料列層級，然後至儲存格層級。 如果在儲存格層級未設定特定 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性，則會使用資料列層級的預設屬性設定。 如果在資料列層級也未設定這個屬性，則會使用預設資料行設定。 最後，如果在資料行層級還是未設定這個屬性，則會使用預設 <xref:System.Windows.Forms.DataGridView> 設定。 您可以利用這項設定，避免必須在多個層級重複設定屬性。 您只需要在每個層級指定不同於上一層級的樣式。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[如何： 設定預設的儲存格樣式和資料格式的 Windows Form DataGridView 控制項使用設計工具](https://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\))。  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>以程式設計方式設定預設儲存格樣式  
  
1.  設定透過 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性擷取之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  建立並初始化新的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，以供多個資料列和資料行使用。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  設定特定資料列和資料行的 `DefaultCellStyle` 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要在您使用非常大量的資料集時達到最大延展性，您應該共用使用相同樣式的多個資料列、資料行或儲存格之間的 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個項目的樣式屬性。 此外，您應該建立共用資料列，並使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> 屬性來加以存取。 如需詳細資訊，請參閱 <<c0> [ 縮放 Windows Form DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [操作說明：設定 Windows Forms DataGridView 控制項的替代資料列樣式](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
