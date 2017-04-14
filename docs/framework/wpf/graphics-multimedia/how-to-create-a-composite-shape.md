---
title: "如何：建立複合圖案 | Microsoft Docs"
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
  - "複合圖案"
  - "圖形, 複合圖案"
  - "圖案, 複合"
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立複合圖案
本範例示範如何使用 <xref:System.Windows.Media.Geometry> 物件建立複合圖案，並使用 <xref:System.Windows.Shapes.Path> 項目顯示這些圖案。  下列範例將 <xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry> 和 <xref:System.Windows.Media.RectangleGeometry> 搭配使用 <xref:System.Windows.Media.GeometryGroup> 來建立複合圖案。  接著再使用 <xref:System.Windows.Shapes.Path> 項目繪製幾何圖形。  
  
## 範例  
 [!code-xml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 下圖顯示在上述範例中建立的圖案。  
  
 ![使用 GeometryGroup 建立的複合幾何](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.png "wcpsdk\_graphicsmm\_compositegeometryexample1")  
複合幾何  
  
 您可以使用 <xref:System.Windows.Media.PathGeometry> 建立較複雜的圖案 \(例如多邊形和具有弧形片段的圖案\)。  如需如何使用 <xref:System.Windows.Media.PathGeometry> 建立圖案的範例，請參閱 [使用 PathGeometry 建立圖案](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)。  雖然本範例使用 <xref:System.Windows.Shapes.Path> 項目將圖案呈現到螢幕上，但是您也可以使用 <xref:System.Windows.Media.Geometry> 物件描述 <xref:System.Windows.Media.GeometryDrawing> 或 <xref:System.Windows.Media.DrawingContext> 的內容。  這些物件也可用來裁剪 \(Clipping\) 和進行點擊測試。  
  
 這個範例是完整範例的一部分。如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989) \(英文\)。