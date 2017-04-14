---
title: "如何：使用繪圖繪製區域 | Microsoft Docs"
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
  - "筆刷, 以繪圖繪製"
  - "繪圖, 繪製方式"
  - "繪圖, 使用繪圖"
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用繪圖繪製區域
本範例說明如何繪製具有繪圖的區域。  若要繪製具有繪圖的區域，您可以使用 <xref:System.Windows.Media.DrawingBrush> 和一個或多個 <xref:System.Windows.Media.Drawing> 物件。  下列範例使用 <xref:System.Windows.Media.DrawingBrush> 繪製具有兩個橢圓形繪圖的物件。  
  
## 範例  
 [!code-xml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 下圖顯示範例的輸出。  
  
 ![DrawingBrush 的輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm\_drawingbrush\_simple")  
  
 \(圖案中央為白色的原因描述於 [控制複合圖案的填色](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md)\)  
  
 藉由設定 <xref:System.Windows.Media.DrawingBrush> 物件的 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性，您可以建立重複的圖樣。  下列範例繪製的物件具有以兩個橢圓形繪圖建立的圖樣。  
  
 [!code-xml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 下圖顯示並排顯示的 <xref:System.Windows.Media.DrawingBrush> 輸出。  
  
 ![DrawingBrush 的並排顯示輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm\_drawingbrush\_tiled")  
  
 如需繪圖筆刷的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  如需 <xref:System.Windows.Media.Drawing> 物件的詳細資訊，請參閱[繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)。