---
title: "如何：使用 Polyline 項目繪製聚合線 | Microsoft Docs"
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
  - "連接的線條"
  - "繪製, 聚合線 (Polyline)"
  - "圖形 [WPF], 聚合線 (Polyline)"
  - "線條, 連接 (請參閱聚合線 (Polyline))"
  - "聚合線 (Polyline), 繪製"
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 Polyline 項目繪製聚合線
本範例說明如何使用 <xref:System.Windows.Shapes.Polyline> 項目繪製聚合線 \(Polyline\)，聚合線是一連串連接在一起的線條。  
  
 若要繪製聚合線，請建立 <xref:System.Windows.Shapes.Polyline> 項目，並使用其 <xref:System.Windows.Shapes.Polyline.Points%2A> 屬性指定形狀頂點。  最後，使用 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性描述聚合線外框，因為如果線條沒有筆劃，就無法顯示出來。  
  
> [!NOTE]
>  由於 <xref:System.Windows.Shapes.Polyline> 項目不是封閉形狀，因此即使刻意封閉形狀外框，<xref:System.Windows.Shapes.Shape.Fill%2A> 屬性也沒有作用。  若要使用 <xref:System.Windows.Shapes.Shape.Fill%2A> 建立封閉形狀，請使用 <xref:System.Windows.Shapes.Polygon> 項目。  
  
 下列範例會在 <xref:System.Windows.Controls.Canvas> 中繪製兩個 <xref:System.Windows.Shapes.Polyline> 項目。  
  
## 範例  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，有效的點語法是以空格分隔的 X 和 Y 座標配對 \(中間以逗號分隔\) 清單。  
  
 [!code-xml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 雖然本範例使用 <xref:System.Windows.Controls.Canvas> 包含聚合線，不過您可以將聚合線項目 \(以及所有其他圖案項目\) 用於任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Shapes.Polygon>   
 <xref:System.Windows.Shapes.Shape>   
 [圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)