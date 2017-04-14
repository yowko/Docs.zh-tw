---
title: "如何：繪製矩形 | Microsoft Docs"
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
  - "繪製, 矩形"
  - "圖形 [WPF], 矩形"
  - "矩形, 繪製"
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：繪製矩形
本範例說明如何使用 <xref:System.Windows.Shapes.Rectangle> 項目繪製矩形。  
  
 若要繪製矩形，請建立 <xref:System.Windows.Shapes.Rectangle> 項目並指定它的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。  若要繪製矩形內部，請設定其 <xref:System.Windows.Shapes.Shape.Fill%2A>。  若要繪製矩形外框，請使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性。  
  
 若要將矩形的邊角繪製成圓角，請指定選擇性的 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性。  <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性會設定用來繪製矩形圓角的 X 軸和 Y 軸半徑。  
  
 下列範例會將兩個 <xref:System.Windows.Shapes.Rectangle> 項目繪製在 <xref:System.Windows.Controls.Canvas> 中。  第一個矩形的內部為 <xref:System.Windows.Media.Brushes.Blue%2A>。  第二個矩形有 <xref:System.Windows.Media.Brushes.Blue%2A> 內部、<xref:System.Windows.Media.Brushes.Black%2A> 外框和圓角。  
  
## 範例  
 [!code-xml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 雖然本範例使用 <xref:System.Windows.Controls.Canvas> 包含矩形，不過您可以將矩形項目 \(以及所有其他圖案項目\) 用於任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。  事實上，矩形特別適合用來提供 <xref:System.Windows.Controls.Grid> 面板部分的背景。  如需範例，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Rectangle>   
 [圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)