---
title: 設定 DataGridView 控制項中的資料行排序模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742992"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>如何：設定 Windows Form DataGridView 控制項中的資料行排序模式
在 <xref:System.Windows.Forms.DataGridView> 控制項中，文字方塊資料行預設會使用自動排序，而其他資料行類型則不會自動排序。 有時候您會想要覆寫這些預設值。 例如，您可以顯示影像來取代文字、數位或列舉資料格值。 雖然無法排序影像，但它們所代表的基礎值可以進行排序。  
  
 在 <xref:System.Windows.Forms.DataGridView> 控制項中，資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性值會決定其排序行為。  
  
 下列程式顯示[如何：在 Windows Forms DataGridView 控制項中自訂資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)的 `Priority` 欄。 此資料行是影像資料行，預設為不可排序。 不過，它包含實際的資料格值，這些都是字串，所以可以自動排序。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>若要設定資料行的排序模式  
  
- 設定 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項 ，包含名為 `Priority` 的資料行。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中排序資料](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [操作說明：自訂 Windows Forms DataGridView 控制項中的排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
