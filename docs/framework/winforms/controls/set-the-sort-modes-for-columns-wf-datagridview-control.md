---
title: HOW TO：設定 Windows Forms DataGridView 控制項的資料行排序模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: fd627e3aaed7330a05c46b9e2ca0a213404e0bfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625732"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>HOW TO：設定 Windows Forms DataGridView 控制項的資料行排序模式
在 <xref:System.Windows.Forms.DataGridView>自動排序依預設，而其他資料行類型不會自動排序控制項中，文字方塊資料行使用。 有時候您會想要覆寫這些預設值。 例如，您可以顯示影像取代文字、 數字或列舉型別資料格的值。 雖然映像無法進行排序，就可以排序它們所代表的基礎值。  
  
 在 <xref:System.Windows.Forms.DataGridView>控制項，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行的屬性值會決定其排序行為。  
  
 下列程序示範`Priority`資料行從[How to:自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。 本專欄是映像的資料行，並不是預設可排序。 它會包含實際的資料格的值的字串，不過，，因此會自動排序。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>若要設定資料行排序模式  
  
- 設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項 ，包含名為 `Priority` 的資料行。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中排序資料](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [如何：自訂 Windows Form DataGridView 控制項中排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
