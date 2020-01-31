---
title: 在 DataGridView 控制項的儲存格中顯示影像
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
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740282"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>如何：顯示 Windows Form DataGridView 控制項的儲存格影像
圖片或圖形是您可以在資料列中顯示的其中一個值。 這些圖形經常會採用員工相片或公司標誌的形式。  
  
 當您在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示資料時，合併圖片就很簡單。 <xref:System.Windows.Forms.DataGridView> 控制項原本就會處理 <xref:System.Drawing.Image> 類別支援的任何影像格式，以及某些資料庫所使用的 OLE 圖片格式。  
  
 如果 <xref:System.Windows.Forms.DataGridView> 控制項的資料來源有一欄影像，<xref:System.Windows.Forms.DataGridView> 控制項就會自動顯示它們。  
  
 下列程式碼範例示範如何從內嵌資源將圖示解壓縮，並將其轉換成點陣圖，以顯示在影像資料行的每個資料格中。 如需以對應影像取代文字資料格值的另一個範例，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- 名為 `tree.ico`的內嵌圖示資源。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
