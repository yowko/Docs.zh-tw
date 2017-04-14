---
title: "如何：使用主要畫面格建立色彩的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的色彩"
  - "色彩, 使用主要畫面格建立動畫"
  - "主要畫面格, 建立色彩動畫"
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用主要畫面格建立色彩的動畫
本範例說明如何使用主要畫面格，將 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 顯示為動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格。  
  
1.  在前兩秒，使用 <xref:System.Windows.Media.Animation.LinearColorKeyFrame> 類別的執行個體，逐漸將色彩從綠色變成紅色。  線性的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.LinearColorKeyFrame>\) 會在兩個值之間建立平滑的線性轉換。  
  
2.  在後半秒結尾，使用 <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> 類別的執行個體，快速將色彩從紅色變成黃色。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>\) 會在值之間建立突然的變化，也就是說，這部分動畫的色彩變更快速而且明顯。  
  
3.  在最後兩秒，使用 <xref:System.Windows.Media.Animation.SplineColorKeyFrame> 類別的執行個體再次變更色彩，這次是從黃色變回綠色。  [曲線](GTMT)主要畫面格 \(例如 <xref:System.Windows.Media.Animation.SplineColorKeyFrame>\) 會根據 <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個範例中，色彩一開始會緩慢變更，當接近時間區段結尾時會以指數型方式加速。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>   
 <xref:System.Windows.Media.SolidColorBrush>   
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)