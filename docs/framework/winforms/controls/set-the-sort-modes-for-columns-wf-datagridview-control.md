---
title: 如何：設定 Windows Form DataGridView 控制項中的資料行排序模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>如何：設定 Windows Form DataGridView 控制項中的資料行排序模式
在<xref:System.Windows.Forms.DataGridView>控制項中，文字方塊資料行使用自動排序依預設，而其他資料行類型不會自動排序。 有時候您會想要覆寫這些預設值。 例如，您可以顯示影像取代文字、 數字或列舉型別資料格的值。 雖然無法排序映像，可以進行排序它們代表的基礎值。  
  
 在<xref:System.Windows.Forms.DataGridView>控制項，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行的屬性值會決定其排序行為。  
  
 下列程序示範`Priority`資料行從[如何： 在 Windows Form DataGridView 控制項中自訂格式化資料](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。 這個資料行的影像資料行，但不是預設排序。 它包含實際的資料格的值字串，不過，因此會自動排序。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>若要設定資料行的排序模式  
  
-   設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項 ，包含名為 `Priority` 的資料行。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [在 Windows Forms DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [操作說明：自訂 Windows Forms DataGridView 控制項中的排序](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
