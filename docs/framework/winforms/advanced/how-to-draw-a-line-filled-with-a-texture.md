---
title: "如何：繪製填滿材質的線條 | Microsoft Docs"
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
  - "繪製線條, 紋理"
  - "繪製, 線條"
  - "線條, 紋理"
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：繪製填滿材質的線條
除了繪製包含純色的線條之外，也可以繪製包含材質的線條。  若要繪製包含材質的線條和曲線，請建立 <xref:System.Drawing.TextureBrush> 物件，然後將該 <xref:System.Drawing.TextureBrush> 物件傳遞至 <xref:System.Drawing.Pen.%23ctor%2A> 建構函式。  和材質筆刷關聯的點陣圖是用來拼接平面 \(不可見\)，當畫筆繪製線條或曲線時，畫筆的筆觸會露出拼接材質的某些像素。  
  
## 範例  
 下列範例會從 `Texture1.jpg` 檔案建立 <xref:System.Drawing.Bitmap> 物件。  這個點陣圖是用來建構 <xref:System.Drawing.TextureBrush> 物件，而 <xref:System.Drawing.TextureBrush> 物件則是用來建構 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics.DrawImage%2A> 呼叫會繪製左上角位於 \(0, 0\) 的點陣圖。  <xref:System.Drawing.Graphics.DrawEllipse%2A> 呼叫會使用 <xref:System.Drawing.Pen> 物件來繪製紋理橢圓形。  
  
 下圖顯示的是點陣圖和紋理橢圓形。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## 編譯程式碼  
 建立 Windows Form 並處理該表單的 <xref:System.Windows.Forms.Control.Paint> 事件。  將上述程式碼貼至 <xref:System.Windows.Forms.Control.Paint> 事件處理常式中。  請以系統中有效的影像取代 `Texture.jpg`。  
  
## 請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)