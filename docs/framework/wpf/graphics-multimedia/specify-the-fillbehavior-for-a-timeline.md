---
title: HOW TO：針對已達到作用時段結尾的時間表指定 FillBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 9f03c5b8d4585c32e0a9f119649dd15a23523033
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091109"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>HOW TO：針對已達到作用時段結尾的時間表指定 FillBehavior
此範例示範如何指定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為非作用中<xref:System.Windows.Media.Animation.Timeline>動畫的屬性。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>判斷發生什麼事的動畫的屬性值時不在動畫，也就是當<xref:System.Windows.Media.Animation.Timeline>為非使用中，但其父代<xref:System.Windows.Media.Animation.Timeline>內作用，或保留期。 例如，動畫的屬性維持不在其結尾後動畫結束，或它的值還原成之前啟動動畫值？  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>來以動畫顯示<xref:System.Windows.FrameworkElement.Width%2A>的兩個矩形。 每個矩形會使用不同<xref:System.Windows.Media.Animation.Timeline>物件。  
  
 一個<xref:System.Windows.Media.Animation.Timeline>已經<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>會設<xref:System.Windows.Media.Animation.FillBehavior.Stop>，這樣會使還原回其非動畫矩形的寬度值<xref:System.Windows.Media.Animation.Timeline>結束。 另<xref:System.Windows.Media.Animation.Timeline>已經<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，這會保留在其結尾寬度值<xref:System.Windows.Media.Animation.Timeline>結束。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 如需完整的範例，請參閱[動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [動畫概觀](animation-overview.md)
- [動畫和計時 HOW TO 主題](animation-and-timing-how-to-topics.md)
