---
title: 如何：重複動畫
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141544"
---
# <a name="how-to-repeat-an-animation"></a>如何：重複動畫
此示例演示如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>來控制動畫的重複行為。  
  
## <a name="example"></a>範例  
 控制項<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>的屬性工作表示動畫重複其簡單持續時間的次數。 通過使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，可以指定<xref:System.Windows.Media.Animation.Timeline>重複一定次數（反覆運算計數）或指定時間段。 在這兩種情況下，動畫都會經歷它所需的相同多個開始到端運行，以填充請求的計數或持續時間。  
  
 預設情況下，時間表的重複計數為 1.0，這意味著它們播放一次，不重複。 但是，如果將 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>設置為<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間表將無限期重複。  
  
 下面的示例演示如何使用 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>來控制動畫的重複行為。 該示例使用不同類型的重複<xref:System.Windows.FrameworkElement.Width%2A>行為為每個矩形為五個矩形的屬性設置動畫。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 有關完整示例，請參閱[動畫計時行為示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)。  
  
## <a name="see-also"></a>另請參閱

- [在重複循環期間累加動畫值](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [指定時刻表是否會自動反轉](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [動畫和計時 HOW TO 主題](animation-and-timing-how-to-topics.md)
- [動畫概觀](animation-overview.md)
- [動畫計時行為範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
