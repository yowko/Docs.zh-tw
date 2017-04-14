---
title: "GDI+ 中的圖形路徑 | Microsoft Docs"
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
  - "繪製, 路徑"
  - "GDI+, 描繪路徑"
  - "圖形, 路徑"
  - "路徑, 繪製"
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# GDI+ 中的圖形路徑
路徑是由組合的線條、矩形和簡單曲線形成。  回顧[向量圖形概觀](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)一節的說明，下列基本的建置區塊已被證明為最有效的繪製圖片方法：  
  
-   程式行  
  
-   矩形  
  
-   橢圓形  
  
-   弧形  
  
-   多邊形  
  
-   基本曲線  
  
-   貝茲曲線  
  
 在 GDI\+ 中，<xref:System.Drawing.Drawing2D.GraphicsPath> 物件可將這些建置區塊序列收集成為一個單位。  您只需呼叫一次 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawPath%2A> 方法，便可繪製線條、矩形、多邊形和曲線之完整序列。  下列圖例顯示組合線條、弧形、貝茲曲線和基本曲線而建立的路徑。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.png "Aboutgdip02\_art14")  
  
## 使用路徑  
 <xref:System.Drawing.Drawing2D.GraphicsPath> 類別提供下列方法，可用來建立一連串要繪製的項目：<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> \(用於基本曲線\) 和 <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>。  這些方法都為多載；也就是說，所有方法都支援數個不同的參數清單。  例如，<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> 方法的其中一個變異可接收四個整數，而 <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> 方法的另一個變異則可接收兩個 <xref:System.Drawing.Point> 物件。  
  
 將線條、矩形和貝茲曲線加入至路徑的方法，包含許多可在單一呼叫中將數個項目加入至路徑的搭配方法：<xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A> 和 <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>。  此外，<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> 和 <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> 方法具有 <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> 以及 <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A> 兩個搭配方法，它們可將封閉曲線或派形圖加入至路徑。  
  
 若要繪製路徑，您需要 <xref:System.Drawing.Graphics> 物件、<xref:System.Drawing.Pen> 物件和 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawPath%2A> 方法，而 <xref:System.Drawing.Pen> 物件則是儲存用來產生路徑的線條屬性，例如寬度和色彩。  <xref:System.Drawing.Drawing2D.GraphicsPath> 物件可儲存組成路徑的線條和曲線序列。  <xref:System.Drawing.Pen> 物件和 <xref:System.Drawing.Drawing2D.GraphicsPath> 物件會當成引數傳遞至 <xref:System.Drawing.Graphics.DrawPath%2A> 方法。  下列範例繪製由線條、橢圓形和貝茲曲線組成的路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 下圖將顯示該路徑。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.png "Aboutgdip02\_art15")  
  
 除了將線條、矩形和曲線加入到路徑，您也可以將其他路徑新增到路徑中。  您可以將現有的路徑結合成為大型的複雜路徑。  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 另外還有兩個項目可加入至路徑中：字串和派形圖。  扇形圖是指橢圓形的內景部分。  下列範例從弧形、基本曲線、字串和圓形圖建立路徑：  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 下圖將顯示該路徑。  請注意，路徑並不一定要連接起來；弧形、基本曲線、字串和圓形圖是個別分開的。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.png "Aboutgdip02\_Art16")  
  
## 請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)