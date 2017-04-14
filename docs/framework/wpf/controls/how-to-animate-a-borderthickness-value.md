---
title: "如何：建立 BorderThickness 值的動畫 | Microsoft Docs"
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
  - "動畫, 框線粗細變更"
  - "框線粗細, 建立變更的動畫"
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：建立 BorderThickness 值的動畫
本範例說明如何使用 <xref:System.Windows.Media.Animation.ThicknessAnimation> 類別，將框線粗細的變化顯示為動畫。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.ThicknessAnimation>，將框線的粗細顯示為動畫。  此範例使用 <xref:System.Windows.Controls.Border> 的 <xref:System.Windows.Controls.Border.BorderThickness%2A> 屬性。  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 如需完整範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.ThicknessAnimation>   
 <xref:System.Windows.Controls.Border.BorderThickness%2A>   
 <xref:System.Windows.Controls.Border>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [使用主要畫面格建立框線粗細的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)