---
title: "如何：在矩形中繪製被包圍的文字 | Microsoft Docs"
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
  - "字串 [Windows Form], 在矩形中描繪"
  - "文字 [Windows Form], 在矩形中描繪"
  - "Windows Form, 在矩形中描繪文字"
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：在矩形中繪製被包圍的文字
您可以使用取得 <xref:System.Drawing.Rectangle> 或 <xref:System.Drawing.RectangleF> 參數之 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 多載方法，在矩形中繪製被包圍的文字。  您也會使用 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Font>。  
  
 您也可以使用取得 <xref:System.Drawing.Rectangle> 和 <xref:System.Windows.Forms.TextFormatFlags> 參數之 <xref:System.Windows.Forms.TextRenderer> 的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 多載方法，在矩形中繪製被包圍的文字。  您也會使用 <xref:System.Drawing.Color> 和 <xref:System.Drawing.Font>。  
  
 下列圖例示範了在使用 <xref:System.Drawing.Graphics.DrawString%2A> 方法時，於矩形中繪製文字的輸出。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")  
  
### 若要使用 GDI\+ 在矩形中繪製被包圍的文字  
  
1.  使用 <xref:System.Drawing.Graphics.DrawString%2A> 多載方法、傳遞想要的文字、<xref:System.Drawing.Rectangle> 或 <xref:System.Drawing.RectangleF>、<xref:System.Drawing.Font> 然後 <xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### 若要使用 GDI 在矩形中繪製被包圍的文字  
  
1.  使用 <xref:System.Windows.Forms.TextFormatFlags> 列舉值指定應該被 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 多載方法包圍的文字、傳遞想要的文字、<xref:System.Drawing.Rectangle>、<xref:System.Drawing.Font> 然後 <xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## 編譯程式碼  
 前一個範例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## 請參閱  
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [如何：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)   
 [如何：在指定的位置繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)