---
title: "如何：使用 PointAnimation 建立物件位置的動畫 | Microsoft Docs"
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
  - "動畫, PointAnimation"
  - "類別, PointAnimation"
  - "圖形 [WPF], 動畫"
  - "PointAnimation 類別"
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 PointAnimation 建立物件位置的動畫
本範例說明如何使用 <xref:System.Windows.Media.Animation.PointAnimation> 類別，沿著 <xref:System.Windows.Shapes.Path> 將物件顯示為動畫。  
  
## 範例  
 下列範例會在畫面上將橢圓形沿著 <xref:System.Windows.Shapes.Path> 從某一點移動至另一點。  範例會使用 <xref:System.Windows.Media.Animation.PointAnimation> 讓 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性產生變動，藉由改變 <xref:System.Windows.Media.EllipseGeometry> 的位置以顯示動畫。  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.PointAnimation>   
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.EllipseGeometry>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)