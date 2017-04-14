---
title: "如何：使用影像繪製區域 | Microsoft Docs"
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
  - "筆刷, 以影像繪製"
  - "影像, 繪製方式"
  - "繪圖, 使用影像"
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用影像繪製區域
本範例示範如何使用 <xref:System.Windows.Media.ImageBrush> 類別以影像繪製區域。  <xref:System.Windows.Media.ImageBrush> 會顯示以其 <xref:System.Windows.Media.ImageBrush.ImageSource%2A> 屬性所指定的單一影像。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.ImageBrush> 繪製按鈕的 <xref:System.Windows.Controls.Control.Background%2A>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 根據預設，<xref:System.Windows.Media.ImageBrush> 會延伸其影像，填滿您正在繪製的區域。  在上面的範例中，影像會延伸填滿按鈕，這可能會使影像扭曲。  您可以透過將 <xref:System.Windows.Media.TileBrush> 的 <xref:System.Windows.Media.TileBrush.Stretch%2A> 屬性設為 <xref:System.Windows.Media.Stretch> 或 <xref:System.Windows.Media.Stretch> 以控制此行為，這些設定會使得筆刷保留影像的[外觀比例](GTMT) \(Aspect Ratio\)。  
  
 如果您設定了 <xref:System.Windows.Media.ImageBrush> 的 <xref:System.Windows.Media.TileBrush.Viewport%2A> 和 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性，則可以建立重複的圖樣。  下列範例會使用從影像建立的圖樣繪製按鈕。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 如需 <xref:System.Windows.Media.ImageBrush> 類別的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
 這個程式碼範例是 <xref:System.Windows.Media.ImageBrush> 類別完整範例的一部分。  如需完整範例，請參閱 [ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005) \(英文\)。  
  
## 請參閱  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)