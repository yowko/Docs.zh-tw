---
title: HOW TO：針對已達到作用時段結尾的時間表指定 FillBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 9f03c5b8d4585c32e0a9f119649dd15a23523033
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091109"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="7e551-102">HOW TO：針對已達到作用時段結尾的時間表指定 FillBehavior</span><span class="sxs-lookup"><span data-stu-id="7e551-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="7e551-103">此範例示範如何指定<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為非作用中<xref:System.Windows.Media.Animation.Timeline>動畫的屬性。</span><span class="sxs-lookup"><span data-stu-id="7e551-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e551-104">範例</span><span class="sxs-lookup"><span data-stu-id="7e551-104">Example</span></span>  
 <span data-ttu-id="7e551-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>判斷發生什麼事的動畫的屬性值時不在動畫，也就是當<xref:System.Windows.Media.Animation.Timeline>為非使用中，但其父代<xref:System.Windows.Media.Animation.Timeline>內作用，或保留期。</span><span class="sxs-lookup"><span data-stu-id="7e551-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="7e551-106">例如，動畫的屬性維持不在其結尾後動畫結束，或它的值還原成之前啟動動畫值？</span><span class="sxs-lookup"><span data-stu-id="7e551-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="7e551-107">下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>來以動畫顯示<xref:System.Windows.FrameworkElement.Width%2A>的兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="7e551-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="7e551-108">每個矩形會使用不同<xref:System.Windows.Media.Animation.Timeline>物件。</span><span class="sxs-lookup"><span data-stu-id="7e551-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="7e551-109">一個<xref:System.Windows.Media.Animation.Timeline>已經<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>會設<xref:System.Windows.Media.Animation.FillBehavior.Stop>，這樣會使還原回其非動畫矩形的寬度值<xref:System.Windows.Media.Animation.Timeline>結束。</span><span class="sxs-lookup"><span data-stu-id="7e551-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="7e551-110">另<xref:System.Windows.Media.Animation.Timeline>已經<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，這會保留在其結尾寬度值<xref:System.Windows.Media.Animation.Timeline>結束。</span><span class="sxs-lookup"><span data-stu-id="7e551-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="7e551-111">如需完整的範例，請參閱[動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。</span><span class="sxs-lookup"><span data-stu-id="7e551-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e551-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e551-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="7e551-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="7e551-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="7e551-114">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="7e551-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
