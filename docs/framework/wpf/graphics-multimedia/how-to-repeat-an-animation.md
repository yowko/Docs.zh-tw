---
title: HOW TO：重複動畫
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 213fca0796840ae87035be4f474cfdf4648460a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609638"
---
# <a name="how-to-repeat-an-animation"></a>HOW TO：重複動畫
此範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>以控制動畫的重複行為。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>控制動畫重複其簡單持續時間的次數。 藉由使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，您可以指定<xref:System.Windows.Media.Animation.Timeline>重複特定次數 （反覆項目計數） 或一段指定的時間。 在任一情況下，動畫會經歷多個需要以填滿要求的計數或持續時間的開始-結束執行。  
  
 根據預設，時間軸的重複計數為 1.0，這表示它們播放一次，且不重複。 不過，如果您設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的屬性<xref:System.Windows.Media.Animation.Timeline>到<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間軸會無限期地重複。  
  
 下列範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，即可控制動畫的重複行為。 此範例<xref:System.Windows.FrameworkElement.Width%2A>屬性使用不同類型的重複行為每個矩形的五個矩形。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 如需完整的範例，請參閱[動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)。  
  
## <a name="see-also"></a>另請參閱
- [在重複循環期間累加動畫值](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [指定時刻表是否會自動反轉](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
- [動畫和計時](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)
