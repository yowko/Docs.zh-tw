---
title: "如何：建立三次方貝茲曲線 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "貝茲曲線, 三次方"
  - "建立, 三次方貝茲曲線"
  - "三次方貝茲曲線"
  - "曲線, 三次方貝茲"
  - "圖形, 三次方貝茲曲線"
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立三次方貝茲曲線
本範例示範如何建立三次方貝茲曲線。  若要建立三次方貝茲曲線，請使用 <xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.PathFigure> 和 <xref:System.Windows.Media.BezierSegment> 等類別。  若要顯示產生的幾何，請使用 <xref:System.Windows.Shapes.Path> 項目，或是與 <xref:System.Windows.Media.GeometryDrawing> 或 <xref:System.Windows.Media.DrawingContext> 一起使用。  在下列範例中，會繪製從 \(10, 100\) 到 \(300, 100\) 的三次方貝茲曲線。  曲線具有控制點 \(100, 0\) 和 \(200, 200\)。  
  
## 範例  
 \[xaml\]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，您可以使用縮寫標記語法來描述路徑。  
  
 [!code-xml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 \[xaml\]  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，您也可以使用物件標記繪製三次方貝茲曲線。  以下內容相當於前一個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。  
  
 [!code-xml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。  
  
## 請參閱  
 [建立橢圓弧形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)   
 [在 PathGeometry 中建立 LineSegment](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)   
 [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)   
 [建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)