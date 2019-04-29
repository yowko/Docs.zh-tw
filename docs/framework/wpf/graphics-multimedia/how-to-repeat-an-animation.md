---
title: HOW TO：重複動畫
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: a80f72b0e67c13890d4befcbd5ab7c4a92a93fe7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942086"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="e0bf7-102">HOW TO：重複動畫</span><span class="sxs-lookup"><span data-stu-id="e0bf7-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="e0bf7-103">此範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>以控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bf7-104">範例</span><span class="sxs-lookup"><span data-stu-id="e0bf7-104">Example</span></span>  
 <span data-ttu-id="e0bf7-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性<xref:System.Windows.Media.Animation.Timeline>控制動畫重複其簡單持續時間的次數。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="e0bf7-106">藉由使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，您可以指定<xref:System.Windows.Media.Animation.Timeline>重複特定次數 （反覆項目計數） 或一段指定的時間。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="e0bf7-107">在任一情況下，動畫會經歷多個需要以填滿要求的計數或持續時間的開始-結束執行。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="e0bf7-108">根據預設，時間軸的重複計數為 1.0，這表示它們播放一次，且不重複。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="e0bf7-109">不過，如果您設定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的屬性<xref:System.Windows.Media.Animation.Timeline>到<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，時間軸會無限期地重複。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="e0bf7-110">下列範例示範如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>屬性，即可控制動畫的重複行為。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="e0bf7-111">此範例<xref:System.Windows.FrameworkElement.Width%2A>屬性使用不同類型的重複行為每個矩形的五個矩形。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="e0bf7-112">如需完整的範例，請參閱[動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)。</span><span class="sxs-lookup"><span data-stu-id="e0bf7-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bf7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0bf7-113">See also</span></span>

- [<span data-ttu-id="e0bf7-114">在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="e0bf7-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="e0bf7-115">指定時刻表是否會自動反轉</span><span class="sxs-lookup"><span data-stu-id="e0bf7-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="e0bf7-116">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="e0bf7-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="e0bf7-117">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e0bf7-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e0bf7-118">動畫計時行為範例</span><span class="sxs-lookup"><span data-stu-id="e0bf7-118">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
