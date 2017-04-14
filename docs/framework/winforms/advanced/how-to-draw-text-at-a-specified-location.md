---
title: "如何：在指定的位置繪製文字 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繪製文字"
  - "繪製文字, 指定的位置 [Windows Form]"
  - "文字, 在指定的位置描繪 [Windows Form]"
  - "Windows Form, 在指定的位置描繪文字"
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：在指定的位置繪製文字
當您執行自訂繪製時，可以從指定點開始繪製一行水平文字。  您可以使用取得 <xref:System.Drawing.Point> 或 <xref:System.Drawing.PointF> 參數之 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 多載方法，以此方式繪製文字。  <xref:System.Drawing.Graphics.DrawString%2A> 方法也需要 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Font>  
  
 您也可以使用取得 <xref:System.Drawing.Point> 之 <xref:System.Windows.Forms.TextRenderer> 的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 多載方法。  <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 也需要 <xref:System.Drawing.Color> 和 <xref:System.Drawing.Font>。  
  
 下列圖例示範在使用 <xref:System.Drawing.Graphics.DrawString%2A> 多載方法時，於指定點繪製文字的輸出。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")  
  
### 若要使用 GDI\+ 繪製一行文字  
  
1.  使用 <xref:System.Drawing.Graphics.DrawString%2A> 方法、傳遞想要的文字、<xref:System.Drawing.Point> 或 <xref:System.Drawing.PointF>、<xref:System.Drawing.Font> 然後 <xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### 若要使用 GDI 繪製一行文字  
  
1.  使用 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法、傳遞想要的文字、<xref:System.Drawing.Point>、<xref:System.Drawing.Font> 然後 <xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## 編譯程式碼  
 前一個範例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## 請參閱  
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [如何：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [如何：在矩形中繪製被包圍的文字](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)