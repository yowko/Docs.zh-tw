---
title: "GDI+ 中的開放型和封閉型曲線 | Microsoft Docs"
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
  - "曲線"
  - "曲線, 繪製"
  - "曲線, 填滿"
  - "GDI+, 曲線"
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ 中的開放型和封閉型曲線
下圖顯示兩個曲線：一個是開放型，一個是封閉型。  
  
 ![開放型 & 封閉型曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.png "Aboutgdip02\_art24")  
  
## 曲線的 Managed 介面  
 封閉型曲線具有內景，因此可使用筆刷填入色彩。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 中的 <xref:System.Drawing.Graphics> 類別提供以下方法，可用來填滿封閉的形狀和曲線：<xref:System.Drawing.Graphics.FillRectangle%2A>、<xref:System.Drawing.Graphics.FillEllipse%2A>、<xref:System.Drawing.Graphics.FillPie%2A>、<xref:System.Drawing.Graphics.FillPolygon%2A>、<xref:System.Drawing.Graphics.FillClosedCurve%2A>、<xref:System.Drawing.Graphics.FillPath%2A> 和 <xref:System.Drawing.Graphics.FillRegion%2A>。  當您呼叫其中一種方法時，您必須將其中一個指定的筆刷類型當做引數傳遞 \(<xref:System.Drawing.SolidBrush>、<xref:System.Drawing.Drawing2D.HatchBrush>、<xref:System.Drawing.TextureBrush>、<xref:System.Drawing.Drawing2D.LinearGradientBrush> 或 <xref:System.Drawing.Drawing2D.PathGradientBrush>\)。  
  
 <xref:System.Drawing.Graphics.FillPie%2A> 方法是 <xref:System.Drawing.Graphics.DrawArc%2A> 方法的搭配方法。  <xref:System.Drawing.Graphics.DrawArc%2A> 方法繪製橢圓形外框，而 <xref:System.Drawing.Graphics.FillPie%2A> 方法則是填滿橢圓形的內景部分。  下列範例會繪製弧形並將橢圓形內景的對應區域填入色彩：  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 下圖將顯示弧形和已填滿的扇形圖。  
  
 ![開放型 & 封閉型曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.png "Aboutgdip02\_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> 方法是 <xref:System.Drawing.Graphics.DrawClosedCurve%2A> 方法的搭配方法。  上述兩種方法都可透過將結束點連接到起始點來自動封閉曲線。  下列範例會繪製一條通過 \(0, 0\)、\(60, 20\) 和 \(40, 50\) 的曲線。  然後該曲線將透過連接 \(40, 50\) 和起始點 \(0, 0\) 自動封閉起來，而且內景將填入純色。  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> 方法可填入路徑個別部分的內景。  如果路徑的某個部分未能形成封閉型曲線或形狀，<xref:System.Drawing.Graphics.FillPath%2A> 方法會在填入色彩之前，自動將路徑的該部分封閉起來。  下列範例繪製並填滿由弧形、基本曲線、字串和圓形圖所組成的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 下圖將顯示純色填滿或未以純色填滿的路徑。  請注意，<xref:System.Drawing.Graphics.DrawPath%2A> 方法可為字串中的文字繪製出外框，但不會填入色彩。  <xref:System.Drawing.Graphics.FillPath%2A> 方法將會為字串中的字元內景上色。  
  
 ![路徑中的字串](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.png "Aboutgdip02\_art26")  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)