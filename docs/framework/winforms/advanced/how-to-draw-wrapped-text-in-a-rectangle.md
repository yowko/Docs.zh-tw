---
title: HOW TO：在矩形中繪製換行文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: ae6ceb2ca3e541be1d7dd3e5a61a6e52b27e93c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152785"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>HOW TO：在矩形中繪製換行文字
您也可以使用在矩形中繪製換行的文字<xref:System.Drawing.Graphics.DrawString%2A>方法的多載化<xref:System.Drawing.Graphics>類別<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>參數。 您也會使用<xref:System.Drawing.Brush>和<xref:System.Drawing.Font>。  
  
 您也可以繪製的矩形中換行的文字，使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法的多載化<xref:System.Windows.Forms.TextRenderer>採用<xref:System.Drawing.Rectangle>和<xref:System.Windows.Forms.TextFormatFlags>參數。 您也會使用<xref:System.Drawing.Color>和<xref:System.Drawing.Font>。  
  
 下圖顯示當您使用的矩形中繪製的文字輸出<xref:System.Drawing.Graphics.DrawString%2A>方法：
  
 ![如果螢幕擷取畫面顯示時使用 DrawString 方法的輸出。](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>若要繪製被包圍的文字中使用 GDI + 的矩形  
  
1.  使用<xref:System.Drawing.Graphics.DrawString%2A>多載方法，傳遞您想要的文字<xref:System.Drawing.Rectangle>或是<xref:System.Drawing.RectangleF>，<xref:System.Drawing.Font>和<xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>若要繪製被包圍的文字中使用 GDI 矩形  
  
1.  使用<xref:System.Windows.Forms.TextFormatFlags>列舉值，以指定的文字應該以包裝<xref:System.Windows.Forms.TextRenderer.DrawText%2A>多載方法，傳遞您想要的文字<xref:System.Drawing.Rectangle>，<xref:System.Drawing.Font>和<xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)
- [使用字型和文字](using-fonts-and-text.md)
- [HOW TO：建構字型家族和字型](how-to-construct-font-families-and-fonts.md)
- [HOW TO：在指定的位置繪製文字](how-to-draw-text-at-a-specified-location.md)
