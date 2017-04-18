---
title: "GDI+ 中的貝茲曲線 | Microsoft Docs"
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
  - "貝茲曲線"
  - "GDI+, 貝茲曲線"
  - "曲線, 貝茲"
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# GDI+ 中的貝茲曲線
貝茲曲線 \(Bézier Spline\) 是由四個點所指定的曲線：兩個端點 \(p1 和 p2\) 和兩個控制點 \(c1 和 c2\)。  該曲線以 p1 做為起始，並以 p2 做為結束。  該曲線並不會通過控制點，但控制點作用類似磁鐵，將曲線拉往某些方向並且影響曲線彎曲的方式。  下圖顯示貝茲曲線及其端點和控制點。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.png "Aboutgdip02\_art11a")  
  
 曲線以 p1 做為起始點，並朝控制點 c1 的方向移動。  p1 曲線的切線是從 p1 到 c1 繪製而成。  而端點 p2 的切線則是從 c2 繪製到 p2。  
  
## 繪製貝茲曲線  
 若要繪製貝茲曲線，您需要 <xref:System.Drawing.Graphics> 類別執行個體和 <xref:System.Drawing.Pen>。  <xref:System.Drawing.Graphics> 類別執行個體提供 <xref:System.Drawing.Graphics.DrawBezier%2A> 方法，而 <xref:System.Drawing.Pen> 則是儲存屬性，例如用來呈現曲線的線條寬度和色彩。  <xref:System.Drawing.Pen> 會當成其中一個引數傳遞給 <xref:System.Drawing.Graphics.DrawBezier%2A> 方法。  傳遞給 <xref:System.Drawing.Graphics.DrawBezier%2A> 方法的其餘引數是端點和控制點。  下列範例以起始點 \(0, 0\)、控制點 \(40, 20\) 和 \(80, 150\)，以及結束點 \(100, 10\) 來繪製貝茲曲線：  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 下圖將顯示曲線、控制點和兩條切線。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.png "Aboutgdip02\_art12")  
  
 貝茲曲線最初是由 Pierre Bézier 開發，用於汽車工業設計上。  經過長久的使用與測試後，證實了貝茲曲線在許多電腦輔助設計類型的應用上非常有用，而且也可以用來定義字型的外框。  貝茲曲線可以產生各種不同的形狀，下列圖例顯示其中幾種。  
  
 ![路徑](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.png "Aboutgdip02\_art13")  
  
## 請參閱  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [如何：建立畫筆](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)