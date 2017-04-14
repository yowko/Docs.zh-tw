---
title: "如何：重複動畫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, 重複"
  - "時刻表的 RepeatBehavior 屬性"
  - "重複動畫"
  - "時刻表 RepeatBehavior 屬性"
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：重複動畫
本範例說明如何使用 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性，以控制動畫的重複行為。  
  
## 範例  
 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性可控制動畫重複其持續時間的次數。  藉由使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，您可以指定 <xref:System.Windows.Media.Animation.Timeline> 重複特定次數 \(反覆計數\) 或在指定的一段時間內重複。  不論是哪種情況，動畫都會從頭到尾不斷重複執行，直到達到所要求的計數或持續時間。  
  
 根據預設，時刻表的重複計數為 1.0，這表示播放一次且不再重複。  不過，如果將 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性設為 <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時刻表就會無限次重複。  
  
 下列範例顯示如何使用 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> 屬性控制動畫的重複行為。  此範例會將五個矩形的 <xref:System.Windows.FrameworkElement.Width%2A> 屬性顯示為動畫，每個矩形都使用不同類型的重複行為。  
  
 [!code-xml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 如需完整範例，請參閱[動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970) \(英文\)。  
  
## 請參閱  
 [在重複循環期間累加動畫值](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)   
 [指定時刻表是否會自動反轉](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)