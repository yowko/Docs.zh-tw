---
title: Easing 函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354501"
---
# <a name="easing-functions"></a><span data-ttu-id="3e2d4-102">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="3e2d4-102">Easing Functions</span></span>
<span data-ttu-id="3e2d4-103">Easing 函式可讓您將自訂的數學公式套用至動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="3e2d4-104">例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="3e2d4-105">您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="3e2d4-106">除了建立您自己自訂的 easing 函式，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>，您可以使用其中一個執行階段所提供的數個 easing 函式來建立常見效果。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="3e2d4-107"><xref:System.Windows.Media.Animation.BackEase>：會開始指定的路徑顯示動畫之前稍微撤回動畫的動作。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="3e2d4-108"><xref:System.Windows.Media.Animation.BounceEase>：建立彈跳效果。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="3e2d4-109"><xref:System.Windows.Media.Animation.CircleEase>：用來建立加速和/或減速使用循環函式的動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="3e2d4-110"><xref:System.Windows.Media.Animation.CubicEase>：來建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="3e2d4-111"><xref:System.Windows.Media.Animation.ElasticEase>：建立類似彈簧來回擺動直到來回的動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="3e2d4-112"><xref:System.Windows.Media.Animation.ExponentialEase>：用來建立加速和/或減速使用指數公式的動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="3e2d4-113"><xref:System.Windows.Media.Animation.PowerEase>：來建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>p</sup>其中 p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="3e2d4-114"><xref:System.Windows.Media.Animation.QuadraticEase>：來建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>2</sup>。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="3e2d4-115"><xref:System.Windows.Media.Animation.QuarticEase>：來建立加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>4</sup>。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="3e2d4-116"><xref:System.Windows.Media.Animation.QuinticEase>：建立可加速和/或減速使用公式的動畫*f*(*t*) = *t*<sup>5</sup>。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="3e2d4-117"><xref:System.Windows.Media.Animation.SineEase>：用來建立加速和/或減速使用正弦公式的動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="3e2d4-118">若要套用至動畫的 easing 函式，使用`EasingFunction`動畫的屬性會指定要套用至動畫的 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="3e2d4-119">下列範例會套用<xref:System.Windows.Media.Animation.BounceEase>easing 函式以<xref:System.Windows.Media.Animation.DoubleAnimation>建立彈跳效果。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="3e2d4-120">在上述範例中，easing 函式套用至 From/To/By 動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="3e2d4-121">您也可以將這些 easing 函式套用至主要畫面格動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="3e2d4-122">下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="3e2d4-123">您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>屬性來改變 easing 函式的運作方式，也就是變更動畫插入的方式。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="3e2d4-124">有三個可能的值，您可以為<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="3e2d4-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="3e2d4-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>：插補會遵循相關聯的 easing 函式的數學公式。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="3e2d4-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>：插補會遵循 100%插補減去輸出相關聯的 easing 函式的公式。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="3e2d4-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>：內插補點會使用<xref:System.Windows.Media.Animation.EasingMode.EaseIn>動畫的前半和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>的後半部。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="3e2d4-128">下圖示範不同的值<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>何處*f*(*x*) 代表動畫進度並*t*代表時間。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="3e2d4-129">![BackEase EasingMode 圖形。](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="3e2d4-130">![BounceEase EasingMode 圖形。](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="3e2d4-131">![CircleEase EasingMode 圖形。](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="3e2d4-132">![CubicEase EasingMode 圖形。](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="3e2d4-133">![包含不同加/減速模式圖形的 ElasticEase。](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="3e2d4-134">![不同加/減速模式的 ExponentialEase 圖形。](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="3e2d4-135">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="3e2d4-136">![包含不同加/減速模式圖形的 QuadraticEase。](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="3e2d4-137">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="3e2d4-138">![包含不同加/減速模式圖形的 QuinticEase。](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="3e2d4-139">![使用不同 EasingMode 值的 SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="3e2d4-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e2d4-140">您可以使用<xref:System.Windows.Media.Animation.PowerEase>來建立相同的行為<xref:System.Windows.Media.Animation.CubicEase>， <xref:System.Windows.Media.Animation.QuadraticEase>， <xref:System.Windows.Media.Animation.QuarticEase>，並<xref:System.Windows.Media.Animation.QuinticEase>使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="3e2d4-141">例如，如果您想要<xref:System.Windows.Media.Animation.PowerEase>來替代<xref:System.Windows.Media.Animation.CubicEase>，指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>3 的值。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="3e2d4-142">除了使用包含在執行階段的 easing 函式，您可以建立您自己自訂的 easing 函式，藉由繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="3e2d4-143">下列範例將示範如何建立簡單的自訂 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="3e2d4-144">您可以新增您自己的 easing 函式藉由覆寫的運作方式的數學邏輯<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3e2d4-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
