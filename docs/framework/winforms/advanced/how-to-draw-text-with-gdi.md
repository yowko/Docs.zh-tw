---
title: "如何：使用 GDI 繪製文字 | Microsoft Docs"
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
  - "繪製, 文字"
  - "GDI, 描繪文字 [Windows Form]"
  - "文字, 使用 TextRenderer 描繪"
  - "Windows Form, 使用 GDI 描繪文字"
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 GDI 繪製文字
您可以使用 <xref:System.Windows.Forms.TextRenderer> 類別中的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法存取 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 功能，以便在表單或控制項上繪製文字。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 文字呈現通常會比 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供更高的效能以及更精確的文字測量。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer> 類別的 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法並不支援列印。  當列印時一定要使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawString%2A> 方法。  
  
## 範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 方法在矩形內的多個線條上繪製文字。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 若要使用 <xref:System.Windows.Forms.TextRenderer> 類別呈現文字，您需要 <xref:System.Drawing.IDeviceContext> \(例如 <xref:System.Drawing.Graphics> 和 <xref:System.Drawing.Font>\)、要繪製文字的位置，以及繪製文字的色彩。  您可以選擇性地使用 <xref:System.Windows.Forms.TextFormatFlags> 列舉型別指定文字格式。  
  
 如需取得 <xref:System.Drawing.Graphics> 的詳細資訊，請參閱 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。  如需建構 <xref:System.Drawing.Font> 的詳細資訊，請參閱 [如何：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)。  
  
## 編譯程式碼  
 上述程式碼範例是專為與 Windows Form 搭配使用而設計的，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`\(即 <xref:System.Windows.Forms.PaintEventHandler> 的參數\)。  
  
## 請參閱  
 <xref:System.Windows.Forms.TextRenderer>   
 <xref:System.Drawing.Font>   
 <xref:System.Drawing.Color>   
 <xref:System.Drawing.Color>   
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)