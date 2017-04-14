---
title: "如何：設定 TileBrush 的並排顯示大小 | Microsoft Docs"
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
  - "TileBrush, 方磚的大小"
  - "TileBrush 的 Viewport 屬性"
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：設定 TileBrush 的並排顯示大小
本範例說明如何設定 <xref:System.Windows.Media.TileBrush> 的並排顯示大小。  根據預設，<xref:System.Windows.Media.TileBrush> 會產生單一並排顯示來完全填滿您正在繪製的區域。  您可以設定 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性覆寫這項行為。  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性會指定 <xref:System.Windows.Media.TileBrush> 的並排顯示大小。  根據預設，<xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性的值是相對於正在繪製的區域大小。  若要設定 <xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性指定並排顯示的絕對大小，請將 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性設為 <xref:System.Windows.Media.BrushMappingMode>。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.ImageBrush> \(<xref:System.Windows.Media.TileBrush> 的一種\)，以並排方式顯示繪製矩形。  這個範例會將每個並排顯示設為輸出區域 \(即矩形\) 的 50 % x 50 %。  因此，矩形是以影像的四個投影所繪製。  
  
 下圖顯示的是範例產生的輸出。  
  
 ![使用影像筆刷來並排顯示的範例](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 下面的範例則會建立 <xref:System.Windows.Media.ImageBrush>，然後將其 <xref:System.Windows.Media.TileBrush.Viewport%2A> 設為 `0,0,25,25`，將 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 設為 <xref:System.Windows.Media.BrushMappingMode>，然後使用它來繪製另一個矩形。  因此，筆刷會產生寬度為 25 個[像素](GTMT)和高度為 25 個[像素](GTMT)的並排顯示。  
  
 下圖顯示的是範例產生的輸出。  
  
 ![檢視區為 0,0,0.25,0.25 的並排顯示 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 上述範例是某個完整範例的一部分。  如需完整範例，請參閱 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005) \(英文\)。  
  
 雖然本範例使用了 <xref:System.Windows.Media.ImageBrush> 類別，但 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> 屬性對其他 <xref:System.Windows.Media.TileBrush> 物件 \(即 <xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush>\) 的作用完全相同。  如需 <xref:System.Windows.Media.ImageBrush> 和其他 <xref:System.Windows.Media.TileBrush> 物件的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.TileBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [使用 TileBrush 建立不同的並排顯示模式](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)