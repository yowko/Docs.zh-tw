---
title: HOW TO：在指定的位置繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: f7834ea45db8dd6e971defd9c3b2b152ffddf512
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336404"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>HOW TO：在指定的位置繪製文字
當您執行自訂繪圖時，您可以在單一的水平列，從指定的點開始來繪製文字。 您也可以使用這個方式繪製文字<xref:System.Drawing.Graphics.DrawString%2A>方法的多載化<xref:System.Drawing.Graphics>類別<xref:System.Drawing.Point>或<xref:System.Drawing.PointF>參數。 <xref:System.Drawing.Graphics.DrawString%2A>方法也需要<xref:System.Drawing.Brush>和 <xref:System.Drawing.Font>  
  
 您也可以使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法的多載化<xref:System.Windows.Forms.TextRenderer>採用<xref:System.Drawing.Point>。 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 也需要<xref:System.Drawing.Color>和<xref:System.Drawing.Font>。  
  
 下圖顯示當您使用時，在指定的點繪製的文字輸出<xref:System.Drawing.Graphics.DrawString%2A>多載的方法。  
  
 ![如果螢幕擷取畫面顯示在指定的時間點的文字輸出。](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>若要繪製一行文字使用 GDI +  
  
1. 使用<xref:System.Drawing.Graphics.DrawString%2A>方法，傳遞您想要的文字<xref:System.Drawing.Point>或是<xref:System.Drawing.PointF>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>若要繪製一行文字使用 GDI  
  
1. 使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法，傳遞您想要的文字<xref:System.Drawing.Point>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)
- [使用字型和文字](using-fonts-and-text.md)
- [HOW TO：建構字型家族和字型](how-to-construct-font-families-and-fonts.md)
- [HOW TO：在矩形中繪製換行文字](how-to-draw-wrapped-text-in-a-rectangle.md)
