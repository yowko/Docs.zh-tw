---
title: HOW TO：自訂 Windows Forms DataGridView 控制項的儲存格外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 9b07c139689a9776f6f901c0f9fbe9d2d0303d56
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648152"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>HOW TO：自訂 Windows Forms DataGridView 控制項的儲存格外觀
您可以藉由處理自訂的任何資料格外觀<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellPainting>事件。 您可以擷取<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Drawing.Graphics>從<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>。 與這個<xref:System.Drawing.Graphics>，您可能會影響的整個外觀<xref:System.Windows.Forms.DataGridView>控制項，但是您通常會想要影響目前所繪製的儲存格的外觀。 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>可讓您限制您到目前所繪製的儲存格的繪製作業。  
  
 在下列程式碼範例中，您將會繪製中的所有儲存格`ContactName`資料行使用<xref:System.Windows.Forms.DataGridView>控制項的色彩配置。 每個資料格文字內容中繪製<xref:System.Drawing.Color.Crimson%2A>，並在相同的色彩繪製內凹矩形<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.GridColor%2A>屬性。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`使用`ContactName`例如 Northwind 範例資料庫中的 Customers 資料表中的資料行。  
  
- System、System.Windows.Forms 和 System.Drawing 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
