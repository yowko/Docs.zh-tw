---
title: "如何：繪製橢圓形或圓形 | Microsoft Docs"
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
  - "圓形, 繪製"
  - "繪製圓形"
  - "繪製橢圓形"
  - "橢圓形, 繪製"
  - "圖形, 繪製圓形"
  - "圖形, 繪製橢圓形"
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：繪製橢圓形或圓形
本範例說明如何使用 <xref:System.Windows.Shapes.Ellipse> 項目繪製橢圓形和圓形。  若要繪製橢圓形，請建立 <xref:System.Windows.Shapes.Ellipse> 項目並指定它的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。  請使用它的 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性指定要用來繪製橢圓形內部的 <xref:System.Windows.Media.Brush>。  請使用它的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性指定要用來繪製橢圓形外框的 <xref:System.Windows.Media.Brush>。  <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性會指定橢圓形外框的粗細。  
  
 若要繪製圓形，請將 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 設為相等。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas> 中繪製四個 <xref:System.Windows.Shapes.Ellipse>。  
  
## 範例  
 [!code-xml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 雖然本範例使用 <xref:System.Windows.Controls.Canvas> 包含橢圓形，不過您可以將橢圓形項目 \(以及所有其他圖案項目\) 用於任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Ellipse>   
 <xref:System.Windows.Shapes.Shape>   
 [圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)