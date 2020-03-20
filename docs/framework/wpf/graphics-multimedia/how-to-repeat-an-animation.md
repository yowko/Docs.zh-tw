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
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="4fd57-102">如何：重複動畫</span><span class="sxs-lookup"><span data-stu-id="4fd57-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="4fd57-103">此示例演示如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>來控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="4fd57-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fd57-104">範例</span><span class="sxs-lookup"><span data-stu-id="4fd57-104">Example</span></span>  
 <span data-ttu-id="4fd57-105">控制項<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>的屬性工作表示動畫重複其簡單持續時間的次數。</span><span class="sxs-lookup"><span data-stu-id="4fd57-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="4fd57-106">通過使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，可以指定<xref:System.Windows.Media.Animation.Timeline>重複一定次數（反覆運算計數）或指定時間段。</span><span class="sxs-lookup"><span data-stu-id="4fd57-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="4fd57-107">在這兩種情況下，動畫都會經歷它所需的相同多個開始到端運行，以填充請求的計數或持續時間。</span><span class="sxs-lookup"><span data-stu-id="4fd57-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="4fd57-108">預設情況下，時間表的重複計數為 1.0，這意味著它們播放一次，不重複。</span><span class="sxs-lookup"><span data-stu-id="4fd57-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="4fd57-109">但是，如果將 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A><xref:System.Windows.Media.Animation.Timeline>設置為<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間表將無限期重複。</span><span class="sxs-lookup"><span data-stu-id="4fd57-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="4fd57-110">下面的示例演示如何使用 屬性<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>來控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="4fd57-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="4fd57-111">該示例使用不同類型的重複<xref:System.Windows.FrameworkElement.Width%2A>行為為每個矩形為五個矩形的屬性設置動畫。</span><span class="sxs-lookup"><span data-stu-id="4fd57-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="4fd57-112">有關完整示例，請參閱[動畫計時行為示例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)。</span><span class="sxs-lookup"><span data-stu-id="4fd57-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd57-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fd57-113">See also</span></span>

- [<span data-ttu-id="4fd57-114">在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="4fd57-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="4fd57-115">指定時刻表是否會自動反轉</span><span class="sxs-lookup"><span data-stu-id="4fd57-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="4fd57-116">動畫和計時 HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="4fd57-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="4fd57-117">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="4fd57-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4fd57-118">動畫計時行為範例</span><span class="sxs-lookup"><span data-stu-id="4fd57-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
