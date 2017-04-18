---
title: "如何：使用主要畫面格建立雙精度浮點數的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格建立雙精度浮點數"
  - "雙核心, 使用主要畫面格建立動畫"
  - "主要畫面格, 建立雙精度浮點數的動畫"
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用主要畫面格建立雙精度浮點數的動畫
本範例說明如何使用主要畫面格建立屬性值 \(這個屬性會採用 <xref:System.Double>\) 的動畫。  
  
## 範例  
 下列範例會在畫面上移動矩形。  此範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 類別，將套用至 <xref:System.Windows.Shapes.Rectangle> 之 <xref:System.Windows.Media.TranslateTransform> 的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格，會無限重複：  
  
1.  在前三秒內，使用 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> 類別的執行個體，從起始位置沿著路徑以穩定速率將矩形移動至 500 位置。  線性的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>\) 會在兩個值之間建立平滑的線性轉換。  
  
2.  在第四秒結束時，使用 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> 類別的執行個體，突然將矩形移動至下一個位置。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>\) 會在值之間建立突然的跳躍點。  在這個範例中，矩形是在起始位置，接著會突然出現在 500 位置。  
  
3.  在最後兩秒時，使用 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> 類別的執行個體，將矩形移回至起始位置。  [曲線](GTMT)主要畫面格 \(例如 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>\) 會根據 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個範例中，矩形一開始會緩慢移動，接著當接近時間區段結尾時會以指數型方式加速。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
 為了保持與其他動畫範例的一致性，這個範例的程式碼版本是使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來套用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。  或者，在程式碼中套用單一動畫時，使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法會比使用 <xref:System.Windows.Media.Animation.Storyboard> 更簡單。  如需範例，請參閱 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Shapes.Rectangle>   
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)