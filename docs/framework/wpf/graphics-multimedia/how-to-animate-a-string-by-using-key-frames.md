---
title: "使用主要畫面格建立字串的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的字串"
  - "主要畫面格, 建立字串的動畫"
  - "字串, 使用主要畫面格建立動畫"
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 使用主要畫面格建立字串的動畫
本範例說明如何使用主要畫面格將字串顯示為動畫，本範例的字串是 <xref:System.Windows.Controls.Button> 控制項的 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> 類別將 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性顯示為動畫。  
  
 這個範例的所有主要畫面格都使用 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> 類別的執行個體，因為使用主要畫面格建立的字串動畫只能使用不連續的主要畫面格。  不連續的主要畫面格 \(例如 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>\) 會在值之間建立突然的跳躍點，也就是說，動畫的變更快速且明顯。  
  
 [!code-xml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.ContentControl.Content%2A>   
 <xref:System.Windows.Controls.Button>   
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)