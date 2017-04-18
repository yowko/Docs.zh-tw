---
title: "如何：修改線條或線段結尾的端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "圖形, 圖案端點"
  - "圖案項目, 端點"
  - "圖案項目, 結尾"
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：修改線條或線段結尾的端點
本範例說明如何修改開放式 <xref:System.Windows.Shapes.Shape> 項目開頭或結尾的圖案。  若要變更開放式 <xref:System.Windows.Shapes.Shape> 開頭的端點，請使用其 <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> 屬性。  若要變更開放式 <xref:System.Windows.Shapes.Shape> 結尾的端點，請使用其 <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> 屬性。  若要檢視可用的線條端點，請查看 <xref:System.Windows.Media.PenLineCap> 列舉。  
  
> [!NOTE]
>  這個屬性只會影響開放式形狀，例如 <xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Polyline> 或開放式 <xref:System.Windows.Shapes.Path> 項目。  
  
 下列範例會繪製四個 <xref:System.Windows.Shapes.Polyline> 項目，並在每個項目的端點使用不同一組的形狀。  
  
## 範例  
 [!code-xml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[圖案項目範例](http://go.microsoft.com/fwlink/?LinkID=160037) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Media.PenLineCap>