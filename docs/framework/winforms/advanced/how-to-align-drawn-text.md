---
title: "如何：對齊繪製的文字 | Microsoft Docs"
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
  - "文字, 對齊"
  - "Windows Form, 對齊描繪的文字"
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：對齊繪製的文字
當您執行自訂繪製時，通常會想要置中表單或控制項上的已繪製文字。  只要建立正確的格式化物件並設定適當的格式旗標，就可以輕鬆地對齊使用 <xref:System.Drawing.Graphics.DrawString%2A> 或 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法所繪製的文字。  
  
### 若要使用 GDI\+ \(DrawString\) 繪製置中的文字  
  
1.  使用 <xref:System.Drawing.StringFormat> 搭配適當的 <xref:System.Drawing.Graphics.DrawString%2A> 方法指定置中的文字。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### 若要使用 GDI \(DrawText\) 繪製置中的文字  
  
1.  使用 <xref:System.Windows.Forms.TextFormatFlags> 列舉型別搭配適當的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法，包裝以及垂直和水平置中文字。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## 編譯程式碼  
 上述程式碼範例是專為與 Windows Form 搭配使用而設計的，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [如何：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)