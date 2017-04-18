---
title: "如何：使用主要畫面格建立物件的動畫 | Microsoft Docs"
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
  - "動畫, 使用主要畫面格的物件"
  - "主要畫面格, 建立物件的動畫"
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用主要畫面格建立物件的動畫
本範例說明如何使用主要畫面格建立物件的動畫，本範例的物件是 <xref:System.Windows.Controls.Page> 控制項的 <xref:System.Windows.Controls.Page.Background%2A> 屬性。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 類別，以動畫方式顯示 <xref:System.Windows.Controls.Page> 控制項之 <xref:System.Windows.Controls.Page.Background%2A> 屬性的色彩變更。  範例動畫會定期變更為不同的背景筆刷。  本動畫使用 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 類別以建立三個不同的主要畫面格。  這個動畫以下列方式使用主要畫面格：  
  
1.  在第一秒結束時，以動畫方式呈現 <xref:System.Windows.Media.LinearGradientBrush> 類別的執行個體。  範例的這一部分會將線形漸層套用至背景色彩，色彩就會由黃色轉換為橘色再轉換為紅色。  
  
2.  在下一秒結束時，以動畫方式呈現 <xref:System.Windows.Media.RadialGradientBrush> 類別的執行個體。  範例的這一部分會將放射狀漸層套用至背景色彩，色彩就會由白色轉換為藍色再轉換為黑色。  
  
3.  在第三秒結束時，以動畫方式呈現 <xref:System.Windows.Media.DrawingBrush> 類別的執行個體。  範例的這一部分會將棋盤式樣式套用至背景。  
  
4.  動畫又再開始並且不斷重複。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 是您唯一能搭配 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 類別使用的主要畫面格。  像是 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 這類的主要畫面格會忽然變更值，也就是說，本範例中的色彩會忽然改變。  
  
 [!code-xml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 如需完整範例，請參閱 [KeyFrame 動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.Page.Background%2A>   
 <xref:System.Windows.Controls.Page>   
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>   
 <xref:System.Windows.Media.LinearGradientBrush>   
 <xref:System.Windows.Media.RadialGradientBrush>   
 <xref:System.Windows.Media.DrawingBrush>   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [主要畫面格 HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)