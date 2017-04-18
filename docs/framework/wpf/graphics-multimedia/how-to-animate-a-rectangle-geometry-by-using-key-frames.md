---
title: "如何：使用主要畫面格建立矩形幾何的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的 RectangleGeometry 物件"
  - "主要畫面格, 建立 RectangleGeometry 物件動畫"
  - "RectangleGeometry 物件, 使用主要畫面格建立動畫"
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用主要畫面格建立矩形幾何的動畫
本範例說明如何使用主要畫面格，將 <xref:System.Windows.Media.RectangleGeometry> 的 <xref:System.Windows.Media.RectangleGeometry.Rect%2A> 屬性顯示為動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Media.RectangleGeometry> 的 <xref:System.Windows.Media.RectangleGeometry.Rect%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格。  
  
1.  在前兩秒，使用 <xref:System.Windows.Media.Animation.LinearRectKeyFrame> 類別的執行個體，將矩形的位置、寬度和高度逐漸變化顯示為動畫。  線性的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.LinearRectKeyFrame>\) 會在兩個值之間建立平滑的線性轉換。  
  
2.  在後半秒結尾，使用 <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> 類別的執行個體，突然縮短矩形的高度。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame>\) 會在值之間建立突然的變化，也就是說，高度會快速縮短而且很明顯。  
  
3.  在最後兩秒，使用 <xref:System.Windows.Media.Animation.SplineRectKeyFrame> 類別的執行個體，將矩形變回原始大小和位置。  [曲線](GTMT)主要畫面格 \(例如 <xref:System.Windows.Media.Animation.SplineRectKeyFrame>\) 會根據 <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個範例中，一開始會緩慢變更，當接近時間區段結尾時會以指數型方式加速。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.RectangleGeometry>   
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>   
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)