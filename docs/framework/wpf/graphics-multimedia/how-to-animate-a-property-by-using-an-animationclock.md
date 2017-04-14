---
title: "如何：使用 AnimationClock 建立屬性的動畫 | Microsoft Docs"
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
  - "動畫, 屬性, 使用 AnimationClocks"
  - "AnimationClocks"
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 AnimationClock 建立屬性的動畫
本範例顯示如何使用 <xref:System.Windows.Media.Animation.Clock> 物件建立屬性的動畫。  
  
 有三種方式可以建立[相依性屬性](GTMT)的動畫：  
  
-   建立 <xref:System.Windows.Media.Animation.AnimationTimeline>，並使用 <xref:System.Windows.Media.Animation.Storyboard> 讓其與該屬性建立關聯。  
  
-   使用物件的 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法以套用單一 <xref:System.Windows.Media.Animation.AnimationTimeline> 至目標屬性。  
  
-   從 <xref:System.Windows.Media.Animation.AnimationTimeline> 建立 <xref:System.Windows.Media.Animation.AnimationClock>，並套用至屬性。  
  
 <xref:System.Windows.Media.Animation.Storyboard> 物件和 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法可以讓您建立屬性的動畫，不需直接建立和散發時鐘 \(如需範例，請參閱 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)和 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)\)。時鐘會自動建立和散發。  
  
## 範例  
 下列範例顯示如何建立 <xref:System.Windows.Media.Animation.AnimationClock> 並將其套用至兩個類似的屬性。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 如需顯示如何在啟動 <xref:System.Windows.Media.Animation.Clock> 後以互動方式控制時鐘的範例，請參閱 [以互動方式控制時鐘](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)。  
  
## 請參閱  
 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [不使用腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)