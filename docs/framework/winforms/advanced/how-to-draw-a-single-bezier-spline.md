---
title: "如何：繪製單一貝茲曲線 | Microsoft Docs"
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
  - "貝茲曲線, 繪製"
  - "繪製, 貝茲曲線"
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：繪製單一貝茲曲線
貝茲曲線 \(Bézier Spline\) 是由四個點定義而成：起始點、兩個控制點和結束點。  
  
## 範例  
 下列範例繪製一個起始點位於 \(10, 100\)、結束點位於 \(200, 100\) 的貝茲曲線。  兩個控制點位於 \(100, 10\) 和 \(150, 150\)。  
  
 下圖顯示產生的貝茲曲線以及它的起始點、控制點和結束點。  圖中也會顯示曲線的凸面 \(Convex Hull\)，也就是以直線連接四點所形成的多邊形。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 <xref:System.Drawing.Graphics.DrawBezier%2A>   
 [GDI\+ 中的貝茲曲線](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [如何：繪製一連串的貝茲曲線](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)