---
title: "如何：在重複循環期間累加動畫值 | Microsoft Docs"
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
  - "在重複循環期間累加動畫值"
  - "動畫, 在重複循環期間累加值"
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：在重複循環期間累加動畫值
本範例說明如何使用 <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> 屬性在重複循環期間累加動畫值。  
  
## 範例  
 使用 <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> 屬性在重複循環期間累加動畫的基底值。  例如，假設您設定動畫重複 9 次 \(<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> \= "9x"\) 並設定屬性在 10 與 15 之間顯示動畫 \(From \= 10 To \= 15\)，那麼屬性在第一次循環期間會在 10 到 15 之間顯示動畫、第二次循環期間在 15 到 20 之間顯示動畫，第三次循環在 20 到 25 之間顯示動畫，以此類推。  因此，每次動畫循環會使用前次動畫循環的結束動畫值做為基底值。  
  
 `IsCumulative` 屬性可以用於大多數基本動畫和多數的主要畫面格動畫。  如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
 下列範例會將四個矩形的寬度顯示為動畫，以示範這個行為。  這個範例會：  
  
-   使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 將第一個矩形顯示為動畫，並將 <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> 屬性設為 `true`。  
  
-   使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 將第二個矩形顯示為動畫，並將 <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> 屬性設為 `false` 的預設值。  
  
-   使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 將第三個矩形顯示為動畫，並將 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> 屬性設為 `true`。  
  
-   使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> 將最後一個矩形顯示為動畫，並將 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> 屬性設為 `false`。  
  
 [!code-xml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## 請參閱  
 [將動畫輸出值加入至動畫啟動值](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)   
 [重複動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)