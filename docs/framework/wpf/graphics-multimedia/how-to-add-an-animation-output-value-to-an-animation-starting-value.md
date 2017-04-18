---
title: "如何：將動畫輸出值加入至動畫啟動值 | Microsoft Docs"
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
  - "動畫"
  - "IsAdditive 屬性"
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：將動畫輸出值加入至動畫啟動值
本範例說明如何將動畫輸出值加入至動畫起始值。  
  
## 範例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> 屬性會指定您是否要將動畫的輸出值加到動畫屬性的起始值 \(基底值\)。  <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> 屬性可以用於大多數基本動畫和多數的主要畫面格動畫。  如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例顯示 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=fullName> 屬性和 <xref:System.Windows.Media.Animation.DoubleAnimation> 一起使用，以及 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=fullName> 屬性和 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 一起使用時，所呈現出來的效果。  
  
 [!code-xml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## 請參閱  
 [在重複循環期間累加動畫值](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)