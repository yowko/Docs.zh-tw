---
title: "如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b6617bdaa14f405e54af1709f0cf985911c56ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior
這個範例示範如何指定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為非作用中<xref:System.Windows.Media.Animation.Timeline>動畫屬性。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>決定時發生的事情動畫屬性的值不會有動畫效果，也就是當<xref:System.Windows.Media.Animation.Timeline>非使用中，但其父代<xref:System.Windows.Media.Animation.Timeline>內或保留期。 動畫的屬性保持在其結尾的例如值之後動畫結束，或它不會還原回動畫開始之前的值嗎？  
  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示<xref:System.Windows.FrameworkElement.Width%2A>兩個矩形。 每個矩形會使用不同<xref:System.Windows.Media.Animation.Timeline>物件。  
  
 一個<xref:System.Windows.Media.Animation.Timeline>具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>設為<xref:System.Windows.Media.Animation.FillBehavior.Stop>，因而導致還原回其非動畫矩形的寬度值時<xref:System.Windows.Media.Animation.Timeline>結束。 其他<xref:System.Windows.Media.Animation.Timeline>具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，因而導致維持在其結束寬度值時<xref:System.Windows.Media.Animation.Timeline>結束。  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 如需完整範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [動畫和計時](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
