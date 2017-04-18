---
title: "如何：對文字套用動畫 | Microsoft Docs"
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
  - "動畫, 文字"
  - "印刷樣式, 動畫"
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：對文字套用動畫
動畫可以改變應用程式中文字的顯示及外觀。  下列範例會使用不同類型的動畫來影響 <xref:System.Windows.Controls.TextBlock> 控制項中的文字顯示。  
  
## 範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 顯示文字區塊寬度的動畫。  在 10 秒期間內，寬度值從文字區塊寬度變更為 0，然後回復寬度值並繼續播放。  這種類型的動畫會建立擦拭效果。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 顯示文字區塊不透明度的動畫。  在 5 秒期間內，不透明值會從 1.0 漸變成 0，然後回復不透明值並繼續播放。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 下圖顯示在 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 所定義的 5 秒間隔內，<xref:System.Windows.Controls.TextBlock> 控制項的不透明值從 `1.00` 漸變成 `0.00` 的效果。  
  
 ![不透明度從 1.00 變更為 0.00 的文字](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
從 1.00 漸變成 0.00 的文字不透明效果  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.ColorAnimation> 顯示文字區塊前景色彩的動畫。  在 5 秒期間內，前景色彩會從一個色彩漸變成第二個色彩，然後回復色彩值並繼續播放。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 旋轉文字區塊。  在 20 秒期間內，文字區塊會完整轉一圈，然後繼續重複旋轉。  
  
 [!code-xml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)