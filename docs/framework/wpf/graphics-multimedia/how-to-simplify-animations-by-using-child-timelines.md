---
title: "如何：使用子時刻表簡化動畫 | Microsoft Docs"
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
  - "動畫, 使用子時刻表簡化"
  - "子時刻表"
  - "使用子時刻表簡化動畫"
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：使用子時刻表簡化動畫
本範例會顯示如何使用子 <xref:System.Windows.Media.Animation.ParallelTimeline> 物件來簡化動畫。  <xref:System.Windows.Media.Animation.Storyboard> 是一種 <xref:System.Windows.Media.Animation.Timeline>，可以提供特定時限所包含的目標資訊。  使用 <xref:System.Windows.Media.Animation.Storyboard> 以提供時間表目標資訊，包含物件和屬性資訊。  
  
 若要開始動畫，請先使用一或多個 <xref:System.Windows.Media.Animation.ParallelTimeline> 物件，做為 <xref:System.Windows.Media.Animation.Storyboard> 的巢狀子項目。  這些 <xref:System.Windows.Media.Animation.ParallelTimeline> 物件可包含其他動畫，因此，可以較佳方法將時間序列封裝在複雜動畫中。  例如，如果您在相同 <xref:System.Windows.Media.Animation.Storyboard> 中設計 <xref:System.Windows.Controls.TextBlock> 的動畫和數個圖案，您可以將 <xref:System.Windows.Controls.TextBlock> 的動畫和圖案、將每個項目放入個別的 <xref:System.Windows.Media.Animation.ParallelTimeline>。  因為每個 <xref:System.Windows.Media.Animation.ParallelTimeline> 都有專屬的 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>，且 <xref:System.Windows.Media.Animation.ParallelTimeline> 的所有子項目會與 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 產生關聯，即可以較佳方式封裝時間。  
  
 下列範例會從相同 <xref:System.Windows.Media.Animation.Storyboard> 加入兩段文字 \(<xref:System.Windows.Controls.TextBlock> 物件\) 的動畫。  <xref:System.Windows.Media.Animation.ParallelTimeline> 封裝其中一個 <xref:System.Windows.Controls.TextBlock> 物件的動畫。  
  
 **效能提示：** 雖然您可以彼此之間的巢狀化 <xref:System.Windows.Media.Animation.Storyboard> 時間表，<xref:System.Windows.Media.Animation.ParallelTimeline> 會更適用於進行巢狀化，因為他們需要的負荷較少   \(<xref:System.Windows.Media.Animation.Storyboard> 類別繼承自 <xref:System.Windows.Media.Animation.ParallelTimeline> 類別\)。  
  
## 範例  
 [!code-xml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [指定腳本動畫之間的傳遞行為](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)