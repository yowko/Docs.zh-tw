---
title: "如何：使用 TileBrush 建立不同的並排顯示模式 | Microsoft Docs"
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
  - "建立, 使用 TileBrush 的並排顯示模式"
  - "並排顯示模式, 建立"
  - "TileBrush, 建立並排顯示模式"
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 TileBrush 建立不同的並排顯示模式
本範例說明如何使用 <xref:System.Windows.Media.TileBrush> 的 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性建立模式。  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性可讓您指定 <xref:System.Windows.Media.TileBrush> 的內容如何重複顯示，也就是並排填滿輸出區域。  若要建立模式，請將 <xref:System.Windows.Media.TileBrush.TileMode%2A> 設為 <xref:System.Windows.Media.TileMode>、<xref:System.Windows.Media.TileMode>、<xref:System.Windows.Media.TileMode> 或 <xref:System.Windows.Media.TileMode>。  您也必須設定 <xref:System.Windows.Media.TileBrush> 的 <xref:System.Windows.Media.TileBrush.Viewport%2A>，讓它小於正在繪製的區域，否則的話，就只會產生單一並排顯示，不論使用的 <xref:System.Windows.Media.TileBrush.TileMode%2A> 設定為何。  
  
## 範例  
 下列範例會建立五個 <xref:System.Windows.Media.DrawingBrush> 物件，每個都有不同的 <xref:System.Windows.Media.TileBrush.TileMode%2A> 設定，然後使用這些物件繪製五個矩形。  雖然本範例使用了 <xref:System.Windows.Media.DrawingBrush> 類別示範 <xref:System.Windows.Media.TileBrush.TileMode%2A> 行為，但 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性對所有 <xref:System.Windows.Media.TileBrush> 物件 \(即 <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.VisualBrush> 和 <xref:System.Windows.Media.DrawingBrush>\) 的作用完全相同。  
  
 下圖顯示的是這個範例產生的輸出。  
  
 ![TileBrush 並排顯示範例輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm\_DrawingBrushTileModeExample")  
使用 TileMode 屬性建立的並排顯示模式  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## 請參閱  
 [設定 TileBrush 的並排顯示大小](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)