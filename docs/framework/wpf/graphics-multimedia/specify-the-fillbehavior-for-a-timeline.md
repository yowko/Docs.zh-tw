---
title: "如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior | Microsoft Docs"
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
  - "非使用中時刻表的 FillBehavior 屬性"
  - "時刻表, FillBehavior 屬性"
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior
這個範例說明如何為動畫屬性的非現用 <xref:System.Windows.Media.Animation.Timeline> 指定 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>。  
  
## 範例  
 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 屬性會判斷當動畫屬性沒有建立動畫時，屬性的值會產生什麼變化，也就是說，當 <xref:System.Windows.Media.Animation.Timeline> 為非作用中而它的父代 <xref:System.Windows.Media.Animation.Timeline> 卻是在作用中或保留期間。  例如，動畫屬性在動畫結束後，是否仍保留結尾值，還是回復動畫開始前的值？  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 以建立兩個矩形的 <xref:System.Windows.FrameworkElement.Width%2A> 動畫。  每一個矩形都會使用不同的 <xref:System.Windows.Media.Animation.Timeline> 物件。  
  
 其中一個 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 設定為 <xref:System.Windows.Media.Animation.FillBehavior>，會在 <xref:System.Windows.Media.Animation.Timeline> 停止時，使矩形的寬度回復成非動畫值。  另一個 <xref:System.Windows.Media.Animation.Timeline> 的 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 則是設定為 <xref:System.Windows.Media.Animation.FillBehavior>，會在 <xref:System.Windows.Media.Animation.Timeline> 結束時，令寬度保留結束值。  
  
 [!code-xml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 如需完整範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Media.Animation.DoubleAnimation>   
 <xref:System.Windows.FrameworkElement.Width%2A>   
 <xref:System.Windows.Media.Animation.Timeline>   
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 <xref:System.Windows.Media.Animation.FillBehavior>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/zh-tw/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)