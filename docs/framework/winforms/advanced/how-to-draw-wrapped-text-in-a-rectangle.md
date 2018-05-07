---
title: 如何：在矩形中繪製被包圍的文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>如何：在矩形中繪製被包圍的文字
您也可以使用矩形中繪製換行的文字<xref:System.Drawing.Graphics.DrawString%2A>多載方法的<xref:System.Drawing.Graphics>類別接受<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>參數。 您也會使用<xref:System.Drawing.Brush>和<xref:System.Drawing.Font>。  
  
 您也可以繪製的矩形中換行的文字，使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>多載方法的<xref:System.Windows.Forms.TextRenderer>採用<xref:System.Drawing.Rectangle>和<xref:System.Windows.Forms.TextFormatFlags>參數。 您也會使用<xref:System.Drawing.Color>和<xref:System.Drawing.Font>。  
  
 下圖顯示當您使用的矩形中繪製的文字輸出<xref:System.Drawing.Graphics.DrawString%2A>方法。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>要繪製被包圍的文字中使用 GDI + 矩形  
  
1.  使用<xref:System.Drawing.Graphics.DrawString%2A>多載方法，傳遞您想要的選項，的文字<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>，<xref:System.Drawing.Font>和<xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>要繪製被包圍的文字中使用 GDI 矩形  
  
1.  使用<xref:System.Windows.Forms.TextFormatFlags>列舉值，以指定的文字應該包裝與<xref:System.Windows.Forms.TextRenderer.DrawText%2A>多載方法，傳遞您想要的選項，的文字<xref:System.Drawing.Rectangle>，<xref:System.Drawing.Font>和<xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [操作說明：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [操作說明：在指定的位置繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
