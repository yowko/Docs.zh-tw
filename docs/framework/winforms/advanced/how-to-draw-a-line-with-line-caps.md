---
title: "如何：繪製包含線條帽緣的線條 | Microsoft Docs"
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
  - "繪製線條, 線條頭尾圖案"
  - "繪製, 線條"
  - "線條, 繪製"
  - "畫筆, 繪製線條"
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：繪製包含線條帽緣的線條
您可以使用稱為「線條端點」的其中一種形狀來繪製線條的開頭和結尾。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支援多種線條帽緣，例如圓形、方形、菱形和箭頭。  
  
## 範例  
 您可以指定線條開頭的線條帽緣 \(開頭帽緣\)、線條結尾的線條帽緣 \(結尾帽緣\) 或短折線中虛線的線條帽緣 \(虛線帽緣\)。  
  
 下列範例繪製一端為箭頭，另一端為圓形帽緣的線條。  圖例中顯示的是產生的線條：  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens4.png "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## 編譯程式碼  
  
-   建立 Windows Form 並處理該表單的 <xref:System.Windows.Forms.Control.Paint> 事件。  將範例中的程式碼貼至 <xref:System.Windows.Forms.Control.Paint> 事件處理常式，該處理常式傳遞 `e` 做為 <xref:System.Windows.Forms.PaintEventArgs>。  
  
## 請參閱  
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=fullName>   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)