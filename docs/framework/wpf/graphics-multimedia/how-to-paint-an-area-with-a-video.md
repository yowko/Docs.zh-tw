---
title: "如何：繪製含有視訊的區域 | Microsoft Docs"
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
  - "筆刷, 使用視訊繪製"
  - "使用視訊繪製"
  - "視訊, 繪製方式"
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：繪製含有視訊的區域
本範例說明如何繪製含有媒體的區域。  繪製含有媒體之區域的一個方法，就是一起使用 <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Media.VisualBrush>。  先使用 <xref:System.Windows.Controls.MediaElement> 載入及播放媒體，再使用它來設定 <xref:System.Windows.Media.VisualBrush> 的 <xref:System.Windows.Media.VisualBrush.Visual%2A> 屬性。  接著，您就可以使用 <xref:System.Windows.Media.VisualBrush> 繪製一個載入媒體的區域。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Controls.MediaElement> 和 <xref:System.Windows.Media.VisualBrush>，以繪製含有視訊之 <xref:System.Windows.Controls.TextBlock> 控制項的 <xref:System.Windows.Controls.TextBlock.Foreground%2A>。  這個範例會將 <xref:System.Windows.Controls.MediaElement> 的 <xref:System.Windows.Controls.MediaElement.IsMuted%2A> 屬性設定為 `true`，因此不會產生聲音。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## 範例  
 因為 <xref:System.Windows.Media.VisualBrush> 繼承自 <xref:System.Windows.Media.TileBrush> 類別，所以它會提供數個並排顯示模式。  藉由將 <xref:System.Windows.Media.VisualBrush> 的 <xref:System.Windows.Media.TileBrush.TileMode%2A> 屬性設定為 <xref:System.Windows.Media.TileMode>，並將其 <xref:System.Windows.Media.TileBrush.Viewport%2A> 屬性設定為小於繪製區域的值，就可以建立並排顯示模式。  
  
 下列範例與前一個範例相同，但差別在於 <xref:System.Windows.Media.VisualBrush> 是從視訊產生模式。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 如需如何在應用程式中加入內容檔案 \(例如媒體檔案\) 的詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。  當您加入媒體檔案時，您必須將它加入為內容檔案而非資源檔案。  
  
## 請參閱  
 <xref:System.Windows.Media.VisualBrush>   
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [TileBrush 概觀](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [多媒體概觀](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)