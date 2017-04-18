---
title: "GDI+ 中的畫筆、線條和矩形 | Microsoft Docs"
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
  - "繪製, 線條"
  - "繪製, 矩形"
  - "範例 [Windows Form], 描繪線條和圖案"
  - "範例 [Windows Form], GDI+"
  - "範例 [Windows Form], 畫筆"
  - "GDI+, 線條"
  - "GDI+, 畫筆"
  - "GDI+, 矩形"
  - "線條"
  - "線條, 虛線"
  - "矩形"
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# GDI+ 中的畫筆、線條和矩形
若要使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製線條，您必須建立 <xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics> 物件提供實際進行繪製的方法，而 <xref:System.Drawing.Pen> 物件則是儲存屬性，例如線條色彩、寬度和樣式。  
  
## 繪製線條  
 若要繪製線條，請呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawLine%2A> 方法。  <xref:System.Drawing.Pen> 物件會當成其中一個引數傳遞給 <xref:System.Drawing.Graphics.DrawLine%2A> 方法。  下列範例從點 \(4, 2\) 至點 \(12, 6\) 繪製一條線：  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> 是 <xref:System.Drawing.Graphics> 類別的多載方法，因此可使用許多種方法提供引數給它。  例如，您可以建構兩個 <xref:System.Drawing.Point> 物件，並將 <xref:System.Drawing.Point> 物件當做引數傳遞給 <xref:System.Drawing.Graphics.DrawLine%2A> 方法：  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## 建構畫筆  
 您可以在建構 <xref:System.Drawing.Pen> 物件時指定某些屬性。  例如，`Pen` 建構函式 \(Constructor\) 可用來指定色彩和寬度。  下列範例從 \(0, 0\) 到 \(60, 30\) 繪製一條寬度為 2 的藍線：  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## 虛線和線條端點  
 <xref:System.Drawing.Pen> 物件也提供屬性，例如 <xref:System.Drawing.Pen.DashStyle%2A>，可用來指定線條的特性。  下列範例從 \(100, 50\) 到 \(300, 80\) 繪製一條虛線：  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 您可以使用 <xref:System.Drawing.Pen> 物件的屬性來設定其他更多線條屬性。  <xref:System.Drawing.Pen.StartCap%2A> 和 <xref:System.Drawing.Pen.EndCap%2A> 屬性可指定線條端點的外觀；結束的端點可以是平面、方的、圓角的、三角形或是自訂的形狀。  <xref:System.Drawing.Pen.LineJoin%2A> 屬性可指定連接的線條是否為斜接 \(使用突出的點來聯結\)、斜切 \(Bevel\)、圓角或裁剪。  下圖顯示具有不同端點和聯結樣式的線條。  
  
 ![線條](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.png "Aboutgdip02\_art04")  
  
## 繪製矩形  
 使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製矩形和繪製線條相似。  若要繪製矩形，您需要 <xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法，而 <xref:System.Drawing.Pen> 物件則是儲存屬性，例如線條寬度和色彩。  <xref:System.Drawing.Pen> 物件會當成其中一個引數傳遞給 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法。  下列範例從左上角 \(100, 50\) 繪製一個寬度為 80、高度為 40 的矩形：  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> 是 <xref:System.Drawing.Graphics> 類別的多載方法，因此可使用許多種方法提供引數給它。  例如，您可以建構 <xref:System.Drawing.Rectangle> 物件並將 <xref:System.Drawing.Rectangle> 物件當做引數傳遞給 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法：  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <xref:System.Drawing.Rectangle> 物件具有用來管理和收集矩形相關資訊的方法和屬性。  例如，<xref:System.Drawing.Rectangle.Inflate%2A> 和 <xref:System.Drawing.Rectangle.Offset%2A> 方法可改變矩形的大小和位置。  <xref:System.Drawing.Rectangle.IntersectsWith%2A> 方法可告訴您該矩形是否與另一個指定的矩形交集，而 <xref:System.Drawing.Rectangle.Contains%2A> 方法則是會通知您指定的點是否位於矩形中。  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Rectangle?displayProperty=fullName>   
 [如何：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [如何：在 Windows Form 上繪製線條](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)   
 [如何：繪製外框形狀](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)