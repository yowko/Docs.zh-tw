---
title: HOW TO：在 Windows Forms DataGridView 控制項的儲存格中顯示影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e3a4c395e86e4091d8344bebcf99ee04474f3295
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609936"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>HOW TO：在 Windows Forms DataGridView 控制項的儲存格中顯示影像
圖片或圖形是其中一個值，您可以將資料列中顯示。 通常，這些圖形的形式是員工的照片或公司標誌。  
  
 將圖片很簡單，當您顯示內的資料時<xref:System.Windows.Forms.DataGridView>控制項。 <xref:System.Windows.Forms.DataGridView>控制項以原生方式處理支援之任何映像格式<xref:System.Drawing.Image>類別，如 OLE 圖片某些資料庫所使用的格式。  
  
 如果<xref:System.Windows.Forms.DataGridView>控制項的資料來源的資料行的映像，則會自動顯示<xref:System.Windows.Forms.DataGridView>控制項。  
  
 下列程式碼範例示範如何從內嵌資源擷取圖示，並將它轉換成 image 資料行的每個資料格中顯示的點陣圖。 如需文字的資料格的值取代成對應的映像的其他範例，請參閱[How to:自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- 名為內嵌的圖示資源`tree.ico`。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [如何：自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
