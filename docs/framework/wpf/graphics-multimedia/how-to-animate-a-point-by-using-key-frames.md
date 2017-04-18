---
title: "如何：使用主要畫面格建立點的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的數"
  - "主要畫面格, 建立數的動畫"
  - "點, 使用主要畫面格建立動畫"
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用主要畫面格建立點的動畫
本範例說明如何使用 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> 類別，將 <xref:System.Windows.Point> 顯示為動畫。  
  
## 範例  
 下列範例會沿著三角形路徑移動一個橢圓形。  此範例使用 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> 類別，將 <xref:System.Windows.Media.EllipseGeometry> 的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格。  
  
1.  在前半秒，使用 <xref:System.Windows.Media.Animation.LinearPointKeyFrame> 類別的執行個體，從起始位置沿著路徑以穩定速率移動橢圓形。  線性的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.LinearPointKeyFrame>\) 會在兩個值之間建立平滑的線性插補 \(Linear Interpolation\)。  
  
2.  在後半秒結尾，使用 <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> 類別的執行個體，突然將橢圓形沿著路徑移動至下一個位置。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscretePointKeyFrame>\) 會在值之間建立突然的跳躍點。  
  
3.  在最後兩秒時，使用 <xref:System.Windows.Media.Animation.SplinePointKeyFrame> 類別的執行個體，將橢圓形移回至起始位置。  [曲線](GTMT)主要畫面格 \(例如 <xref:System.Windows.Media.Animation.SplinePointKeyFrame>\) 會根據 <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個範例中，動畫一開始會緩慢進行，當接近時間區段結尾時會以指數型方式加速。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
 為了保持與其他動畫範例的一致性，這個範例的程式碼版本是使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來套用 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。  不過，在程式碼中套用單一動畫時，使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法會比使用 <xref:System.Windows.Media.Animation.Storyboard> 更簡單。  如需範例，請參閱 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.EllipseGeometry>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)