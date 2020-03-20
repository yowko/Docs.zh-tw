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
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="63bf4-102">如何：針對已達到使用中週期結尾的時刻表指定 FillBehavior</span><span class="sxs-lookup"><span data-stu-id="63bf4-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="63bf4-103">此示例演示如何<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>為動畫屬性的非活動<xref:System.Windows.Media.Animation.Timeline>指定 。</span><span class="sxs-lookup"><span data-stu-id="63bf4-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63bf4-104">範例</span><span class="sxs-lookup"><span data-stu-id="63bf4-104">Example</span></span>  
 <span data-ttu-id="63bf4-105">屬性<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A><xref:System.Windows.Media.Animation.Timeline>確定動畫屬性未進行動畫處理時（即 非活動但其父<xref:System.Windows.Media.Animation.Timeline><xref:System.Windows.Media.Animation.Timeline>屬性在其活動或保留期間內）的值會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="63bf4-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="63bf4-106">例如，動畫屬性在動畫結束後是否保持其結束值，還是恢復到動畫啟動前的值？</span><span class="sxs-lookup"><span data-stu-id="63bf4-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="63bf4-107">下面的示例使用 為<xref:System.Windows.Media.Animation.DoubleAnimation>兩<xref:System.Windows.FrameworkElement.Width%2A>個矩形設置動畫。</span><span class="sxs-lookup"><span data-stu-id="63bf4-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="63bf4-108">每個矩形使用不同的<xref:System.Windows.Media.Animation.Timeline>物件。</span><span class="sxs-lookup"><span data-stu-id="63bf4-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="63bf4-109">一<xref:System.Windows.Media.Animation.Timeline>個設置為<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的 有<xref:System.Windows.Media.Animation.FillBehavior.Stop>一個 ，這將導致矩形的寬度在<xref:System.Windows.Media.Animation.Timeline>結束時恢復到其非動畫值。</span><span class="sxs-lookup"><span data-stu-id="63bf4-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="63bf4-110">另<xref:System.Windows.Media.Animation.Timeline>一個具有<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>， 這將導致寬度在<xref:System.Windows.Media.Animation.Timeline>結束時保持其結束值。</span><span class="sxs-lookup"><span data-stu-id="63bf4-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="63bf4-111">有關完整示例，請參閱[動畫示例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。</span><span class="sxs-lookup"><span data-stu-id="63bf4-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bf4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63bf4-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="63bf4-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="63bf4-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="63bf4-114">動畫和計時 HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="63bf4-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
