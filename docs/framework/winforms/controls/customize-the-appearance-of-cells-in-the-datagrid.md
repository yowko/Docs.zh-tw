---
title: 如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 73f93fb2ccbcbe55f2c3a8fa78f509b012956515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528677"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>如何：在 Windows Form DataGridView 控制項中自訂儲存格的外觀
您可以自訂處理的任何資料格的外觀<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.CellPainting>事件。 您可以擷取<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Drawing.Graphics>從<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>。 與這個<xref:System.Drawing.Graphics>，您可能會影響整個外觀<xref:System.Windows.Forms.DataGridView>控制項，但是您通常會想要影響目前所繪製的儲存格的外觀。 <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A>屬性<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>可讓您限制您到目前所繪製的儲存格的繪製作業。  
  
 在下列程式碼範例中，您會繪製中的所有資料格`ContactName`資料行使用<xref:System.Windows.Forms.DataGridView>控制項的色彩配置。 每個資料格文字內容中繪製<xref:System.Drawing.Color.Crimson%2A>，而且在相同的色彩繪製內凹矩形<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.GridColor%2A>屬性。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`與`ContactName`例如 Northwind 範例資料庫中的 Customers 資料表中的一個資料行。  
  
-   System、System.Windows.Forms 和 System.Drawing 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CellPainting>  
 [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
