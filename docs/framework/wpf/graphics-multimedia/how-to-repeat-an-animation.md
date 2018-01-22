---
title: "如何：重複動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03ee84463bc6ce76d209d3c9fbb0455fedd9ca1a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-repeat-an-animation"></a>如何：重複動畫
這個範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>為了控制動畫的重複行為。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>控制動畫重複其簡單的持續時間的次數。 使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，您可以指定<xref:System.Windows.Media.Animation.Timeline>會針對特定的次數重複 （反覆項目計數） 或指定的時間週期。 在任一情況下，動畫會經歷最多需要以便填滿，要求的計數或持續期間的開始-結束執行。  
  
 根據預設，時間軸會擁有為 1.0 表示播放一次且不重複的重複計數。 不過，如果您設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>至<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間軸會無限期地重複。  
  
 下列範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，即可控制動畫的重複行為。 此範例以動畫方式顯示<xref:System.Windows.FrameworkElement.Width%2A>屬性具有使用不同類型的重複行為每個矩形的五個矩形。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 如需完整範例，請參閱[動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)。  
  
## <a name="see-also"></a>請參閱  
 [在重複循環期間累加動畫值](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [指定時刻表是否會自動反轉](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [動畫和計時](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)
