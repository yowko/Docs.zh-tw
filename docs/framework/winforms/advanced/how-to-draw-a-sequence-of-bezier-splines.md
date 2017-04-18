---
title: "如何：繪製一連串的貝茲曲線 | Microsoft Docs"
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
  - "貝茲曲線, 描繪順序"
  - "曲線, 描繪貝茲"
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：繪製一連串的貝茲曲線
您可以使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawBeziers%2A> 方法來繪製一連串連接的貝茲曲線 \(Bézier Spline\)。  
  
## 範例  
 下列範例繪製由兩條連接的貝茲曲線所組成的曲線。  第一條貝茲曲線的結束點即是第二條貝茲曲線的起始點。  
  
 下圖顯示的是連接的曲線和七個點。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## 編譯程式碼  
 上述範例是專為與 Windows Form 搭配使用而設計的，而且它需要 <xref:System.Windows.Forms.PaintEventArgs> `e` \(即 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數\)。  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [GDI\+ 中的貝茲曲線](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)