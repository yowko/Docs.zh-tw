---
title: 在 DataGridView 控制項中自訂儲存格的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744049"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀
您可以藉由處理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellPainting> 事件來自訂任何資料格的外觀。 您可以從 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>的 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> 屬性中，將 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Drawing.Graphics> 解壓縮。 在此 <xref:System.Drawing.Graphics>中，您可能會影響整個 <xref:System.Windows.Forms.DataGridView> 控制項的外觀，但通常只會影響目前正在繪製之儲存格的外觀。 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> 的 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> 屬性可讓您將繪製作業限制為目前正在繪製的儲存格。  
  
 在下列程式碼範例中，您將使用 <xref:System.Windows.Forms.DataGridView> 控制項的色彩配置，繪製 `ContactName` 資料行中的所有資料格。 每個儲存格的文字內容都會在 <xref:System.Drawing.Color.Crimson%2A>中繪製，而內凹矩形則繪製成與 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.GridColor%2A> 屬性相同的色彩。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含 `ContactName` 的資料行，例如 Northwind 範例資料庫中的 Customers 資料表之一。  
  
- System、System.Windows.Forms 和 System.Drawing 組件的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
