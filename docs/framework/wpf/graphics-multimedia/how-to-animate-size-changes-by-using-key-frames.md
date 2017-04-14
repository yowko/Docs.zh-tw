---
title: "如何：使用主要畫面格建立大小變更的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的大小變更"
  - "主要畫面格, 建立大小變更的動畫"
  - "大小變更, 使用主要畫面格建立動畫"
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用主要畫面格建立大小變更的動畫
本範例說明如何使用主要畫面格建立大小變更的動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Media.ArcSegment> 的 <xref:System.Windows.Media.ArcSegment.Size%2A> 屬性顯示為動畫。  這個動畫以下列方式使用三個主要畫面格。  
  
1.  在動畫的前半秒，使用 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> 類別的執行個體，逐漸增加弧形的大小。  線性的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>\) 會在兩個值之間建立平滑的線性轉換。  
  
2.  在後半秒結尾，使用 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> 類別的執行個體，突然增加弧形的大小。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>\) 會在值之間建立突然的跳躍點，也就是說，大小會突然變更而且很明顯。  
  
3.  在最後兩秒，使用 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> 類別的執行個體，增加弧形的大小。  [曲線](GTMT)主要畫面格 \(例如 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>\) 會根據 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> 屬性的值建立值之間的可變轉換。  在這個範例中，弧形一開始會緩慢增加大小，接著當接近時間區段結尾時會呈指數增加。  
  
 [!code-xml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.ArcSegment.Size%2A>   
 <xref:System.Windows.Media.ArcSegment>   
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)