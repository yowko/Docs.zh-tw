---
title: HOW TO：在重複循環期間累加動畫值
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 4b739883322751e2df86e13bfd07249abdb10a08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146012"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="aae81-102">HOW TO：在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="aae81-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="aae81-103">此範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>累加動畫值，在重複循環的屬性。</span><span class="sxs-lookup"><span data-stu-id="aae81-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae81-104">範例</span><span class="sxs-lookup"><span data-stu-id="aae81-104">Example</span></span>  
 <span data-ttu-id="aae81-105">使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>累積在重複循環的基底值的動畫的屬性。</span><span class="sxs-lookup"><span data-stu-id="aae81-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="aae81-106">比方說，如果您將設定重複 9 次的動畫 (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = 「 9 倍 」)，並設定要以動畫顯示介於 10 到 15 之間的屬性 (從 = 10 到 = 15)，屬性以動畫顯示從 10 到 15 之間在第一個週期中，從 15 到 20，第二個週期從 20 到 25 期間第三個週期，依此類推。</span><span class="sxs-lookup"><span data-stu-id="aae81-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="aae81-107">因此，每個動畫循環會使用從先前的動畫循環結束的動畫值，做為其基底值。</span><span class="sxs-lookup"><span data-stu-id="aae81-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="aae81-108">您可以使用`IsCumulative`具有最基本的動畫和大部分的主要畫面格動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="aae81-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="aae81-109">如需詳細資訊，請參閱 <<c0> [ 動畫概觀](animation-overview.md)並[主要畫面格動畫概觀](key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="aae81-109">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="aae81-110">下列範例會示範此行為，以動畫顯示四個矩形的寬度。</span><span class="sxs-lookup"><span data-stu-id="aae81-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="aae81-111">範例：</span><span class="sxs-lookup"><span data-stu-id="aae81-111">The example:</span></span>  
  
-   <span data-ttu-id="aae81-112">以動畫顯示的第一個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>，並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="aae81-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="aae81-113">以動畫顯示第二個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>，並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性的預設值為`false`。</span><span class="sxs-lookup"><span data-stu-id="aae81-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="aae81-114">以動畫顯示的第三個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>，並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="aae81-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="aae81-115">以動畫顯示最後一個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>，並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="aae81-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="aae81-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aae81-116">See also</span></span>

- [<span data-ttu-id="aae81-117">將動畫輸出值加入至動畫啟動值</span><span class="sxs-lookup"><span data-stu-id="aae81-117">Add an Animation Output Value to an Animation Starting Value</span></span>](how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="aae81-118">重複動畫</span><span class="sxs-lookup"><span data-stu-id="aae81-118">Repeat an Animation</span></span>](how-to-repeat-an-animation.md)
- [<span data-ttu-id="aae81-119">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="aae81-119">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="aae81-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="aae81-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="aae81-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="aae81-121">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
