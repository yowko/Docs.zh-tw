---
title: "如何：建立漸層停駐點位置或色彩的動畫 | Microsoft Docs"
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
  - "動畫, GradientStop 物件的色彩"
  - "動畫, GradientStop 物件的位置"
  - "色彩, 動畫"
  - "GradientStop 物件, 建立色彩動畫"
  - "GradientStop 物件, 建立位置動畫"
  - "位置, 動畫"
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：建立漸層停駐點位置或色彩的動畫
本範例示範如何建立 <xref:System.Windows.Media.GradientStop> 物件之 <xref:System.Windows.Media.GradientStop.Color%2A> 和 <xref:System.Windows.Media.GradientStop.Offset%2A> 的動畫。  
  
## 範例  
 下列範例會建立 <xref:System.Windows.Media.LinearGradientBrush> 內三個漸層停駐點的動畫。  範例中使用三個動畫，分別製造不同漸層停駐點的動畫效果：  
  
-   第一個動畫是 <xref:System.Windows.Media.Animation.DoubleAnimation>，它會讓第一個停駐點的 <xref:System.Windows.Media.GradientStop.Offset%2A> 產生從 0.0 移到 1.0 然後再移回 0.0 的動畫效果。  因此，漸層中的第一個色彩會從矩形的左邊移到右邊，然後再移回左邊。  
  
-   第二個動畫是 <xref:System.Windows.Media.Animation.ColorAnimation>，它會讓第二個漸層停駐點的 <xref:System.Windows.Media.GradientStop.Color%2A> 產生從 <xref:System.Windows.Media.Colors.Purple%2A> 變成 <xref:System.Windows.Media.Colors.Yellow%2A> 然後再變回 <xref:System.Windows.Media.Colors.Purple%2A> 的動畫效果。  因此，漸層中的中間色彩會從紫色變成黃色，然後再變回紫色。  
  
-   第三個動畫是 <xref:System.Windows.Media.Animation.ColorAnimation>，它會讓第三個漸層停駐點的 <xref:System.Windows.Media.GradientStop.Color%2A> 產生不透明度 \-1 然後再回復的動畫效果。  因此，漸層中第三個色彩會淡出然後再還原成不透明。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 雖然這個範例使用的是 <xref:System.Windows.Media.LinearGradientBrush>，但是程序與建立 <xref:System.Windows.Media.RadialGradientBrush> 內 <xref:System.Windows.Media.GradientStop> 物件的動畫相同。  
  
 如需其他範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.GradientStop>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)