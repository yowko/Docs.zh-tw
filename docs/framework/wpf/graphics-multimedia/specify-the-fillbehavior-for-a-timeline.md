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
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="92e0d-102">如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior</span><span class="sxs-lookup"><span data-stu-id="92e0d-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="92e0d-103">這個範例示範如何指定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為非作用中<xref:System.Windows.Media.Animation.Timeline>動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="92e0d-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92e0d-104">範例</span><span class="sxs-lookup"><span data-stu-id="92e0d-104">Example</span></span>  
 <span data-ttu-id="92e0d-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>決定時發生的事情動畫屬性的值不會有動畫效果，也就是當<xref:System.Windows.Media.Animation.Timeline>非使用中，但其父代<xref:System.Windows.Media.Animation.Timeline>內或保留期。</span><span class="sxs-lookup"><span data-stu-id="92e0d-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="92e0d-106">動畫的屬性保持在其結尾的例如值之後動畫結束，或它不會還原回動畫開始之前的值嗎？</span><span class="sxs-lookup"><span data-stu-id="92e0d-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="92e0d-107">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>以動畫方式顯示<xref:System.Windows.FrameworkElement.Width%2A>兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="92e0d-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="92e0d-108">每個矩形會使用不同<xref:System.Windows.Media.Animation.Timeline>物件。</span><span class="sxs-lookup"><span data-stu-id="92e0d-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="92e0d-109">一個<xref:System.Windows.Media.Animation.Timeline>具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>設為<xref:System.Windows.Media.Animation.FillBehavior.Stop>，因而導致還原回其非動畫矩形的寬度值時<xref:System.Windows.Media.Animation.Timeline>結束。</span><span class="sxs-lookup"><span data-stu-id="92e0d-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="92e0d-110">其他<xref:System.Windows.Media.Animation.Timeline>具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，因而導致維持在其結束寬度值時<xref:System.Windows.Media.Animation.Timeline>結束。</span><span class="sxs-lookup"><span data-stu-id="92e0d-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="92e0d-111">如需完整範例，請參閱[動畫範例圖庫](http://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="92e0d-111">For the complete sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e0d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92e0d-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="92e0d-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="92e0d-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="92e0d-114">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="92e0d-114">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="92e0d-115">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="92e0d-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
