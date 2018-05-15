---
title: 如何：重複動畫
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: b2281805b62d6d4e639524d9a0959b392006d003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="1c857-102">如何：重複動畫</span><span class="sxs-lookup"><span data-stu-id="1c857-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="1c857-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>為了控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="1c857-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c857-104">範例</span><span class="sxs-lookup"><span data-stu-id="1c857-104">Example</span></span>  
 <span data-ttu-id="1c857-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>控制動畫重複其簡單的持續時間的次數。</span><span class="sxs-lookup"><span data-stu-id="1c857-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="1c857-106">使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，您可以指定<xref:System.Windows.Media.Animation.Timeline>會針對特定的次數重複 （反覆項目計數） 或指定的時間週期。</span><span class="sxs-lookup"><span data-stu-id="1c857-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="1c857-107">在任一情況下，動畫會經歷最多需要以便填滿，要求的計數或持續期間的開始-結束執行。</span><span class="sxs-lookup"><span data-stu-id="1c857-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="1c857-108">根據預設，時間軸會擁有為 1.0 表示播放一次且不重複的重複計數。</span><span class="sxs-lookup"><span data-stu-id="1c857-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="1c857-109">不過，如果您設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>至<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間軸會無限期地重複。</span><span class="sxs-lookup"><span data-stu-id="1c857-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="1c857-110">下列範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，即可控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="1c857-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="1c857-111">此範例以動畫方式顯示<xref:System.Windows.FrameworkElement.Width%2A>屬性具有使用不同類型的重複行為每個矩形的五個矩形。</span><span class="sxs-lookup"><span data-stu-id="1c857-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="1c857-112">如需完整範例，請參閱[動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)。</span><span class="sxs-lookup"><span data-stu-id="1c857-112">For the complete sample, see [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c857-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c857-113">See Also</span></span>  
 [<span data-ttu-id="1c857-114">在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="1c857-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="1c857-115">指定時刻表是否會自動反轉</span><span class="sxs-lookup"><span data-stu-id="1c857-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [<span data-ttu-id="1c857-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="1c857-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [<span data-ttu-id="1c857-117">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="1c857-117">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="1c857-118">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="1c857-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="1c857-119">動畫計時行為範例</span><span class="sxs-lookup"><span data-stu-id="1c857-119">Animation Timing Behavior Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159970)
