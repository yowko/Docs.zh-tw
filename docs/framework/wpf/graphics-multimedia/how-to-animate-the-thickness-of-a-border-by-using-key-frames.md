---
title: "如何：使用主要畫面格建立框線粗細的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格建立框線粗細"
  - "框線粗細, 使用主要畫面格建立動畫"
  - "主要畫面格, 建立框線粗細的動畫"
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用主要畫面格建立框線粗細的動畫
本範例說明如何將 <xref:System.Windows.Controls.Border> 的 <xref:System.Windows.Controls.Control.BorderThickness%2A> 屬性顯示為動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Controls.Border> 的 <xref:System.Windows.Controls.Control.BorderThickness%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格。  
  
1.  在前半秒內，使用 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> 類別的執行個體，逐漸將框線加粗。  範例是使用 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>，在兩個值之間建立平滑的線性遞增。  
  
2.  在後半秒結尾，使用 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> 類別的執行個體，突然將框線加粗。  不連續的主要畫面格 \(例如衍生自 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> 的主要畫面格\) 會在值之間建立突然的跳躍點 \(亦即動畫的動作會變得不穩定\)。  
  
3.  在最後兩秒內，使用 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> 類別的執行個體，使框線變細。  [Spline](GTMT) 主要畫面格 \(例如衍生自 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> 的主要畫面格\) 會根據 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個主要畫面格中，動畫一開始很緩慢，接著當接近時間區段結尾時會以等比級數的速度加速。  
  
 [!code-xml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [建立 BorderThickness 值的動畫](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)