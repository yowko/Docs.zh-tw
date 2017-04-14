---
title: "如何：使用 LineGeometry 建立線條 | Microsoft Docs"
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
  - "類別, LineGeometry"
  - "圖形 [WPF], 線條"
  - "LineGeometry 類別"
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 LineGeometry 建立線條
本範例示範如何使用 <xref:System.Windows.Media.LineGeometry> 類別來描述線條。  <xref:System.Windows.Media.LineGeometry> 的定義必須包含一個起始點以及一個結束點。  
  
## 範例  
 下列範例顯示如何建立和呈現 <xref:System.Windows.Media.LineGeometry>。  <xref:System.Windows.Shapes.Path> 項目可用來呈現線條。  因為線條沒有面積，所以沒有指定 <xref:System.Windows.Shapes.Path> 物件的 <xref:System.Windows.Shapes.Shape.Fill%2A>；而改用 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
從 \(10,20\) 繪製至 \(100,130\) 的 LineGeometry  
  
 其他簡單的幾何類別包括 <xref:System.Windows.Media.LineGeometry> 和 <xref:System.Windows.Media.EllipseGeometry>。  這些幾何，以及更為複雜的幾何，也都可以使用 <xref:System.Windows.Media.PathGeometry> 或 <xref:System.Windows.Media.StreamGeometry> 建立。  如需詳細資訊，請參閱 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。  
  
## 請參閱  
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [建立複合圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)