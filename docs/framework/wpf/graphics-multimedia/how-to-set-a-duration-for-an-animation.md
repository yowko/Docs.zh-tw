---
title: HOW TO：設定動畫的持續時間
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: 7a2edbd953f648d5555e5dc50469211a6da066de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497927"
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="fb9f3-102">HOW TO：設定動畫的持續時間</span><span class="sxs-lookup"><span data-stu-id="fb9f3-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="fb9f3-103">A<xref:System.Windows.Media.Animation.Timeline>代表一段時間和該區段的長度由時間軸的<xref:System.Windows.Duration>。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="fb9f3-104">當<xref:System.Windows.Media.Animation.Timeline>結束其持續時間，它就會停止播放。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="fb9f3-105">如果<xref:System.Windows.Media.Animation.Timeline>有子時間軸，它們也會停止播放。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="fb9f3-106">如果動畫，<xref:System.Windows.Duration>指定花多少時間動畫轉換從其起始值到結束值。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="fb9f3-107">您可以指定<xref:System.Windows.Duration>與特定、 有限的時間或特殊值<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="fb9f3-108">動畫的持續時間必須一律是時間值，因為動畫必須永遠有已定義的有限的長度，否則動畫就不會知道如何在其目標值之間轉換。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="fb9f3-109">容器時間軸 (<xref:System.Windows.Media.Animation.TimelineGroup>物件)，例如<xref:System.Windows.Media.Animation.Storyboard>並<xref:System.Windows.Media.Animation.ParallelTimeline>的預設持續時間<xref:System.Windows.Duration.Automatic%2A>，這表示它們會自動結束時其最後一個子項目停止播放。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="fb9f3-110">在下列的範例、 寬度、 高度和填滿色彩的<xref:System.Windows.Shapes.Rectangle>以動畫顯示。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="fb9f3-111">持續時間會設定導致包括控制動畫的認知的速度，並覆寫子時間軸與容器時間軸的持續時間的持續時間的動畫效果的動畫和容器時間軸上。</span><span class="sxs-lookup"><span data-stu-id="fb9f3-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb9f3-112">範例</span><span class="sxs-lookup"><span data-stu-id="fb9f3-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fb9f3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb9f3-113">See also</span></span>
- <xref:System.Windows.Duration>
- [<span data-ttu-id="fb9f3-114">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="fb9f3-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
