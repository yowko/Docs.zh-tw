---
title: "如何：保留當做背景之影像的外觀比例 | Microsoft Docs"
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
  - "背景影像的外觀比例, 保留"
  - "背景影像, 保留外觀比例"
  - "筆刷, 保留背景影像的外觀比例"
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：保留當做背景之影像的外觀比例
本範例示範如何使用 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性保留影像的[外觀比例](GTMT) \(Aspect Ratio\)。  
  
 根據預設，當您使用 <xref:System.Windows.Media.ImageBrush> 繪製區域時，它的內容會延伸填滿整個輸出區域。  當輸出區域和影像的[外觀比例](GTMT)不同時，影像會因延伸而扭曲。  
  
 若要 <xref:System.Windows.Media.ImageBrush> 保留影像的外觀比例，請將 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設為 <xref:System.Windows.Media.Stretch> 或 <xref:System.Windows.Media.Stretch>。  
  
## 範例  
 下列範例使用兩個 <xref:System.Windows.Media.ImageBrush> 物件繪製兩個矩形。  每個矩形都是 300 x 150 [像素](GTMT)，而且各包含一個 300 x 300 像素的影像。  第一個筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設為 <xref:System.Windows.Media.Stretch>，而第二個筆刷的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設為 <xref:System.Windows.Media.Stretch>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 下圖顯示第一個筆刷的輸出，其中將 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設為 <xref:System.Windows.Media.Stretch>。  
  
 ![Stretch 屬性設定為 Uniform 的 ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.png "graphicsmm\_ImageBrushUniformStretch")  
  
 下圖顯示第二個筆刷的輸出，其中將 <xref:System.Windows.Media.TileBrush.Stretch%2A> 設為 <xref:System.Windows.Media.Stretch>。  
  
 ![Stretch 屬性設定為 UniformToFill 的 ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.png "graphicsmm\_ImageBrushUniformToFillStretch")  
  
 請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性對其他 <xref:System.Windows.Media.TileBrush> 物件 \(即 <xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush>\) 的作用完全相同。  如需 <xref:System.Windows.Media.ImageBrush> 和其他 <xref:System.Windows.Media.TileBrush> 物件的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
 另外請注意，雖然 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性看起來像是指定 <xref:System.Windows.Media.TileBrush> 內容如何延伸填滿其輸出區域，但實際上是指定 <xref:System.Windows.Media.TileBrush> 內容如何延伸填滿其基底並排顯示。  如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush>。  
  
 這個程式碼範例是 <xref:System.Windows.Media.ImageBrush> 類別完整範例的一部分。  如需完整範例，請參閱 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.TileBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)