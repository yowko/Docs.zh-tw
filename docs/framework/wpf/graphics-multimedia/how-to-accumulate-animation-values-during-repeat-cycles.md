---
title: "如何：在重複循環期間累加動畫值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="006b6-102">如何：在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="006b6-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="006b6-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性重複循環累加動畫值。</span><span class="sxs-lookup"><span data-stu-id="006b6-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="006b6-104">範例</span><span class="sxs-lookup"><span data-stu-id="006b6-104">Example</span></span>  
 <span data-ttu-id="006b6-105">使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>累積重複循環基底值的動畫的屬性。</span><span class="sxs-lookup"><span data-stu-id="006b6-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="006b6-106">比方說，如果您設定重複 9 次動畫 (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ="9 x")，並設定要繪製介於 10 到 15 之間的屬性 (從 = 10 到 = 15)，屬性以動畫方式顯示從 10 到 15 在第一個週期中，從 15 到 20 的第二個週期從 20 到 25 期間第三個週期，依此類推。</span><span class="sxs-lookup"><span data-stu-id="006b6-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="006b6-107">因此，每次的動畫循環使用先前的動畫循環結束動畫值做為其基底值。</span><span class="sxs-lookup"><span data-stu-id="006b6-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="006b6-108">您可以使用`IsCumulative`具有最基本的動畫和大部分的主要畫面格動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="006b6-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="006b6-109">如需詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="006b6-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="006b6-110">下列範例會顯示動畫四個矩形的寬度，以這種行為。</span><span class="sxs-lookup"><span data-stu-id="006b6-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="006b6-111">範例：</span><span class="sxs-lookup"><span data-stu-id="006b6-111">The example:</span></span>  
  
-   <span data-ttu-id="006b6-112">以動畫方式顯示與第一個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="006b6-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="006b6-113">以動畫方式顯示與第二個矩形<xref:System.Windows.Media.Animation.DoubleAnimation>並設定<xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A>屬性的預設值為`false`。</span><span class="sxs-lookup"><span data-stu-id="006b6-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="006b6-114">以動畫顯示具有的第三個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="006b6-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="006b6-115">以動畫顯示具有的最後一個矩形<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>並設定<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="006b6-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="006b6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="006b6-116">See Also</span></span>  
 [<span data-ttu-id="006b6-117">將動畫輸出值加入至動畫啟動值</span><span class="sxs-lookup"><span data-stu-id="006b6-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="006b6-118">重複動畫</span><span class="sxs-lookup"><span data-stu-id="006b6-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="006b6-119">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="006b6-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="006b6-120">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="006b6-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="006b6-121">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="006b6-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
