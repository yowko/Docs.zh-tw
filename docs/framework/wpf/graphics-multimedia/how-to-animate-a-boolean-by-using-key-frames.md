---
title: "如何：使用主要畫面格建立布林值的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的布林值"
  - "布林值, 使用主要畫面格建立動畫"
  - "主要畫面格, 建立布林值的動畫"
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用主要畫面格建立布林值的動畫
本範例說明如何使用主要畫面格建立 <xref:System.Windows.Controls.Button> 控制項布林屬性值的動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.UIElement.IsEnabled%2A> 屬性顯示為動畫。  這個範例中的所有主要畫面格都使用 <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> 類別的執行個體。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame>\) 會在值之間建立突然的跳躍點 \(亦即動畫的動作會變得不穩定\)。  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>   
 <xref:System.Windows.UIElement.IsEnabled%2A>   
 <xref:System.Windows.Controls.Button>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)