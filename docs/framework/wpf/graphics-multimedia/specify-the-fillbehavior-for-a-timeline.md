---
title: 如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141169"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior
此示例演示如何<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為動畫屬性的非活動<xref:System.Windows.Media.Animation.Timeline>指定 。  
  
## <a name="example"></a>範例  
 屬性<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A><xref:System.Windows.Media.Animation.Timeline>確定動畫屬性未進行動畫處理時（即 非活動但其父<xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.Timeline>屬性在其活動或保留期間內）的值會發生什麼情況。 例如，動畫屬性在動畫結束後是否保持其結束值，還是恢復到動畫啟動前的值？  
  
 下面的示例使用 為<xref:System.Windows.Media.Animation.DoubleAnimation>兩<xref:System.Windows.FrameworkElement.Width%2A>個矩形設置動畫。 每個矩形使用不同的<xref:System.Windows.Media.Animation.Timeline>物件。  
  
 一<xref:System.Windows.Media.Animation.Timeline>個設置為<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的 有<xref:System.Windows.Media.Animation.FillBehavior.Stop>一個 ，這將導致矩形的寬度在<xref:System.Windows.Media.Animation.Timeline>結束時恢復到其非動畫值。 另<xref:System.Windows.Media.Animation.Timeline>一個具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>， 這將導致寬度在<xref:System.Windows.Media.Animation.Timeline>結束時保持其結束值。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 有關完整示例，請參閱[動畫示例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [動畫概觀](animation-overview.md)
- [動畫和計時 HOW TO 主題](animation-and-timing-how-to-topics.md)
