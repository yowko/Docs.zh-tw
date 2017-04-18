---
title: "如何：使用 PathGeometry 建立圖案 | Microsoft Docs"
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
  - "類別, PathGeometry"
  - "圖形 [WPF], 圖案"
  - "PathGeometry 類別"
  - "圖案, 使用 PathGeometry 類別建立"
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 PathGeometry 建立圖案
這個範例示範如何使用 <xref:System.Windows.Media.PathGeometry> 類別建立圖案。  <xref:System.Windows.Media.PathGeometry> 物件是由一個或多個 <xref:System.Windows.Media.PathFigure> 物件組成，而每個 <xref:System.Windows.Media.PathFigure> 都代表不同的「圖形」或圖案。  每個 <xref:System.Windows.Media.PathFigure> 本身都是由一個或多個 <xref:System.Windows.Media.PathSegment> 物件所組成，其中每個物件各代表圖形或圖案的某個連接部分。  區段類型包括 <xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.ArcSegment> 和 <xref:System.Windows.Media.BezierSegment>。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.PathGeometry> 建立三角形。  <xref:System.Windows.Media.PathGeometry> 會透過 <xref:System.Windows.Shapes.Path> 項目顯示。  
  
 [!code-xml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 下圖顯示在上述範例中建立的圖案。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.png "wcpsdk\_graphicsmm\_pathgeometry\_triangle")  
使用 PathGeometry 建立的三角形  
  
 上述範例顯示了如何建立三角形這類比較簡單的圖案。  <xref:System.Windows.Media.PathGeometry> 也可以用來建立更複雜的圖案，包括弧線和曲線。  如需相關範例，請參閱[建立橢圓弧形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)、[建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)和[建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.GeometryDrawing>   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)