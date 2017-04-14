---
title: "如何：建立 GeometryDrawing | Microsoft Docs"
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
  - "類別, GeometryDrawing"
  - "GeometryDrawing 類別"
  - "圖形, GeometryDrawing 類別"
  - "可呈現的圖案"
  - "圖案, 可呈現的"
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立 GeometryDrawing
本範例顯示如何建立和顯示 <xref:System.Windows.Media.GeometryDrawing>。  <xref:System.Windows.Media.GeometryDrawing> 可讓您將 <xref:System.Windows.Media.Pen> 和 <xref:System.Windows.Media.Brush> 與 <xref:System.Windows.Media.Geometry> 產生關聯，以建立有外框的實心形狀。  <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> 描述形狀的結構、<xref:System.Windows.Media.GeometryDrawing.Brush%2A> 描述形狀的實心，而 <xref:System.Windows.Media.GeometryDrawing.Pen%2A> 則描述形狀的外框。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.GeometryDrawing> 來呈現形狀。  此圖案是由一個 <xref:System.Windows.Media.GeometryGroup> 和兩個 <xref:System.Windows.Media.EllipseGeometry> 物件描述。  此圖案的內部是用 <xref:System.Windows.Media.LinearGradientBrush> 繪製，而其外框則是用 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> 繪製。  <xref:System.Windows.Media.GeometryDrawing> 是使用 <xref:System.Windows.Media.ImageDrawing> 和 <xref:System.Windows.Controls.Image> 項目來顯示。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 下圖顯示產生的 <xref:System.Windows.Media.GeometryDrawing>。  
  
 ![兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
  
 若要建立更複雜的繪圖，可以使用 <xref:System.Windows.Media.DrawingGroup> 將多個繪圖物件合併到單一複合繪圖。  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingGroup>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [建立複合圖形](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)