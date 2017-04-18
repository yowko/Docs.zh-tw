---
title: "GDI+ 中的橢圓形和弧形 | Microsoft Docs"
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
  - "弧形"
  - "繪製, 弧形"
  - "繪製, 橢圓形"
  - "橢圓形"
  - "GDI+, 弧形"
  - "GDI+, 橢圓形"
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# GDI+ 中的橢圓形和弧形
您可以使用 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawEllipse%2A> 和 <xref:System.Drawing.Graphics.DrawArc%2A> 方法輕鬆地繪製橢圓形和弧形。  
  
## 繪製橢圓形  
 若要繪製橢圓形，您需要 <xref:System.Drawing.Graphics> 物件和 <xref:System.Drawing.Pen> 物件。  <xref:System.Drawing.Graphics> 物件提供 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法，而 <xref:System.Drawing.Pen> 物件則是儲存用來產生橢圓形的線條屬性，例如寬度和色彩。  <xref:System.Drawing.Pen> 物件會當成其中一個引數傳遞給 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法。  其他傳遞給 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法的引數會指定橢圓形的週框。  下圖顯示橢圓形及其週框。  
  
 ![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.png "Aboutgdip02\_art05")  
  
 下列範例會繪製一個橢圓形；其週框寬度為 80、高度為 40，而左上角為 \(100, 50\)：  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> 是 <xref:System.Drawing.Graphics> 類別的多載方法，因此可使用許多種方法提供引數給它。  例如，您可以建構 <xref:System.Drawing.Rectangle> 並將 <xref:System.Drawing.Rectangle> 當做引數傳遞給 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法：  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## 繪製弧形  
 弧形是橢圓形的一部分。  若要繪製弧形，您可呼叫 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawArc%2A> 方法。  <xref:System.Drawing.Graphics.DrawArc%2A> 方法的參數和 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法的參數相同，但 <xref:System.Drawing.Graphics.DrawArc%2A> 必須有起始的角度和泛用角度。  下列範例繪製起始角度為 30 度、泛用角度為 180 度的弧形：  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 下圖顯示弧形、橢圓形和週框。  
  
 ![橢圓形和弧形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.png "Aboutgdip02\_art06")  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [如何：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [如何：繪製外框形狀](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)