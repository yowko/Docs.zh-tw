---
title: "如何：設定動畫的持續時間 | Microsoft Docs"
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
  - "動畫, 持續期間"
  - "動畫持續期間"
  - "時刻表, description"
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：設定動畫的持續時間
<xref:System.Windows.Media.Animation.Timeline> 代表一段時間，而這段時間的長度是由時間表的 <xref:System.Windows.Duration> 所決定。  當 <xref:System.Windows.Media.Animation.Timeline> 過了持續期間後，就會停止播放。  如果 <xref:System.Windows.Media.Animation.Timeline> 子時間表，子時間表也會停止播放。  動畫的 <xref:System.Windows.Duration> 會指定動畫從開始值轉換到結束值要用多少時間。  
  
 您可以將 <xref:System.Windows.Duration> 指定為特定有限時間或是特殊值 \(<xref:System.Windows.Duration.Automatic%2A> 或 <xref:System.Windows.Duration.Forever%2A>\)。  動畫的持續時間須為時間值，因為動畫必須永遠有定義的有限長度，否則動畫就不知道如何在其目標值之間轉換。  容器時間表 \(<xref:System.Windows.Media.Animation.TimelineGroup> 物件，例如 <xref:System.Windows.Media.Animation.Storyboard> 和 <xref:System.Windows.Media.Animation.ParallelTimeline>\) 的預設持續時間為 <xref:System.Windows.Duration.Automatic%2A>，這表示它們會在最後一個子系停止播放時自動結束。  
  
 在下列範例中，<xref:System.Windows.Shapes.Rectangle> 的寬度、高度和填滿色彩會顯示為動畫。  持續時間會在動畫和容器時間表上設定，所產生的動畫效果包括控制動畫的顯示速度以及使用容器時間表的持續時間覆寫子時間表的持續時間。  
  
## 範例  
 [!code-xml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Duration>   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)