---
title: "如何：使用 RectangleGeometry 定義矩形 | Microsoft Docs"
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
  - "類別, RectangleGeometry"
  - "圖形 [WPF], 矩形"
  - "RectangleGeometry 類別"
  - "矩形, 使用 RectangleGeometry 類別建立"
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用 RectangleGeometry 定義矩形
這個範例說明如何使用 <xref:System.Windows.Media.RectangleGeometry> 類別來描述矩形。  
  
## 範例  
 下列範例顯示如何建立和轉譯 <xref:System.Windows.Media.RectangleGeometry>。  矩形的相對位置和尺寸是由 <xref:System.Windows.Rect> 結構所定義的。  相對位置是 `50,50`，而高度和寬度都是 `25`，建立出正方形。  矩形的內部是使用 <xref:System.Windows.Media.Brushes.LemonChiffon%2A> 筆刷繪製的，而其外框是使用厚度為 `1` 的 <xref:System.Windows.Media.Brushes.Black%2A> 筆劃繪製的。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.png "graphicsmm\_rectangle")  
RectangleGeometry  
  
 雖然本範例使用 <xref:System.Windows.Shapes.Path> 項目轉譯 <xref:System.Windows.Media.RectangleGeometry>，但還有許多其他方式可以使用 <xref:System.Windows.Media.RectangleGeometry> 物件。  舉例來說，<xref:System.Windows.Media.RectangleGeometry> 可以用來指定 <xref:System.Windows.UIElement> 的 <xref:System.Windows.UIElement.Clip%2A>，或是 <xref:System.Windows.Media.GeometryDrawing> 的 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A>。  
  
 其他簡單的幾何類別包括 <xref:System.Windows.Media.LineGeometry> 和 <xref:System.Windows.Media.EllipseGeometry>。  這些幾何，以及更為複雜的幾何，也都可以使用 <xref:System.Windows.Media.PathGeometry> 或 <xref:System.Windows.Media.StreamGeometry> 建立。  
  
## 請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)