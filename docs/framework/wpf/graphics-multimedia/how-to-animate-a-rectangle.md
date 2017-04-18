---
title: "如何：建立矩形動畫 | Microsoft Docs"
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
  - "動畫, 矩形"
  - "矩形, 動畫"
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：建立矩形動畫
本範例說明如何建立以動畫顯示矩形大小及位置的變更。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.RectAnimation> 類別的執行個體，讓 <xref:System.Windows.Media.RectangleGeometry> 之 <xref:System.Windows.Media.RectangleGeometry.Rect%2A> 屬性產生矩形大小和位置的變動以顯示動畫。  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.RectAnimation>   
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>   
 <xref:System.Windows.Media.RectangleGeometry>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)