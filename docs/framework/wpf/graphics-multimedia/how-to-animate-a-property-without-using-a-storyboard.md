---
title: "如何：不使用腳本而建立屬性的動畫 | Microsoft Docs"
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
  - "動畫, 非腳本 (本機)"
  - "本機動畫"
  - "非腳本動畫"
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：不使用腳本而建立屬性的動畫
本範例說明如何在不使用 <xref:System.Windows.Media.Animation.Storyboard> 的情況下，將動畫套用到屬性的一種方式。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 無法使用這個功能。  如需在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中將屬性顯示為動畫的詳細資訊，請參閱 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。  
  
 若要將本機動畫套用到屬性，請使用 <xref:System.Windows.UIElement.BeginAnimation%2A> 方法。  這個方法接受兩個參數：一是 <xref:System.Windows.DependencyProperty>，用來指定要顯示為動畫的屬性，另一是要套用到該屬性的動畫。  
  
## 範例  
 下列範例顯示如何將 <xref:System.Windows.Controls.Button> 的寬度和背景色彩顯示為動畫。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <xref:System.Windows.Media.Animation> 命名空間有各種動畫類別，可用來將不同型別的屬性顯示為動畫。  如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  如需[相依性屬性](GTMT) \(這些範例中顯示之屬性的型別\) 及其功能的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
 另外還有其他方式可以在不使用 <xref:System.Windows.Media.Animation.Storyboard> 物件的情況下顯示動畫；如需詳細資訊，請參閱[建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.AnimationTimeline>   
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Animation.Storyboard>   
 [建立屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)