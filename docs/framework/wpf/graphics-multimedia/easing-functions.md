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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965738"
---
# <a name="easing-functions"></a><span data-ttu-id="e87aa-102">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="e87aa-102">Easing Functions</span></span>
<span data-ttu-id="e87aa-103">Easing 函式可讓您將自訂的數學公式套用至動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="e87aa-104">例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。</span><span class="sxs-lookup"><span data-stu-id="e87aa-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="e87aa-105">您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。</span><span class="sxs-lookup"><span data-stu-id="e87aa-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="e87aa-106">除了藉由繼承<xref:System.Windows.Media.Animation.EasingFunctionBase>來建立自己的自訂緩動函式之外, 您還可以使用執行時間所提供的數個緩動函式之一來建立常見的效果。</span><span class="sxs-lookup"><span data-stu-id="e87aa-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="e87aa-107"><xref:System.Windows.Media.Animation.BackEase>：先撤銷動畫的動作, 再開始在指定的路徑中建立動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="e87aa-108"><xref:System.Windows.Media.Animation.BounceEase>：建立跳動的效果。</span><span class="sxs-lookup"><span data-stu-id="e87aa-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="e87aa-109"><xref:System.Windows.Media.Animation.CircleEase>：使用迴圈函式建立加速和 (或) 減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="e87aa-110"><xref:System.Windows.Media.Animation.CubicEase>：使用公式*f*(*t*) = *t*<sup>3</sup>, 建立加速及/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="e87aa-111"><xref:System.Windows.Media.Animation.ElasticEase>：建立類似彈簧的動畫, 直到進入 rest 為止。</span><span class="sxs-lookup"><span data-stu-id="e87aa-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="e87aa-112"><xref:System.Windows.Media.Animation.ExponentialEase>：建立使用指數公式加速和 (或) 減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="e87aa-113"><xref:System.Windows.Media.Animation.PowerEase>：使用公式*f*(*t*) = *t*<sup>p</sup> (其中 p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性), 建立加速及/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="e87aa-114"><xref:System.Windows.Media.Animation.QuadraticEase>：使用公式*f*(*t*) = *t*<sup>2</sup>, 建立加速及/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="e87aa-115"><xref:System.Windows.Media.Animation.QuarticEase>：使用公式*f*(*t*) = *t*<sup>4</sup>, 建立加速及/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="e87aa-116"><xref:System.Windows.Media.Animation.QuinticEase>：使用公式*f*(*t*) = *t*<sup>5</sup>來建立加速及/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="e87aa-117"><xref:System.Windows.Media.Animation.SineEase>：建立使用正弦公式加速和 (或) 減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="e87aa-118">若要將緩動函式套用至動畫, `EasingFunction`請使用動畫的屬性, 指定要套用至動畫的緩時函數。</span><span class="sxs-lookup"><span data-stu-id="e87aa-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="e87aa-119">下列範例會將<xref:System.Windows.Media.Animation.BounceEase>緩動函式套用<xref:System.Windows.Media.Animation.DoubleAnimation>至, 以建立跳動效果。</span><span class="sxs-lookup"><span data-stu-id="e87aa-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="e87aa-120">在上述範例中，easing 函式套用至 From/To/By 動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="e87aa-121">您也可以將這些 easing 函式套用至主要畫面格動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="e87aa-122">下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。</span><span class="sxs-lookup"><span data-stu-id="e87aa-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="e87aa-123">您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>屬性來改變緩動函式的行為, 也就是變更動畫的插補方式。</span><span class="sxs-lookup"><span data-stu-id="e87aa-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="e87aa-124">有三個可能的值可供<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>您指定:</span><span class="sxs-lookup"><span data-stu-id="e87aa-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="e87aa-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>：插補會遵循與緩動函數相關聯的數學公式。</span><span class="sxs-lookup"><span data-stu-id="e87aa-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="e87aa-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>：插補會遵循 100% 插補, 減去與緩動函數相關聯的公式輸出。</span><span class="sxs-lookup"><span data-stu-id="e87aa-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="e87aa-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>：插補<xref:System.Windows.Media.Animation.EasingMode.EaseIn>會在動畫的前半部和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半部使用。</span><span class="sxs-lookup"><span data-stu-id="e87aa-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="e87aa-128">下列<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>圖表示範不同的值, 其中*f*(*x*) 代表動畫進度, 而*t*代表時間。</span><span class="sxs-lookup"><span data-stu-id="e87aa-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="e87aa-129">![BackEase EasingMode 圖形。](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="e87aa-130">![BounceEase EasingMode 圖形。](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="e87aa-131">![CircleEase EasingMode 圖形。](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="e87aa-132">![CubicEase EasingMode 圖形。](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="e87aa-133">![包含不同加/減速模式圖形的 ElasticEase。](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="e87aa-134">![不同加/減速模式的 ExponentialEase 圖形。](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="e87aa-135">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="e87aa-136">![包含不同加/減速模式圖形的 QuadraticEase。](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="e87aa-137">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="e87aa-138">![包含不同加/減速模式圖形的 QuinticEase。](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="e87aa-139">![使用不同 EasingMode 值的 SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="e87aa-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e87aa-140">您可以使用<xref:System.Windows.Media.Animation.PowerEase>來建立與<xref:System.Windows.Media.Animation.CubicEase>、、 <xref:System.Windows.Media.Animation.QuarticEase>和<xref:System.Windows.Media.Animation.QuinticEase>相同<xref:System.Windows.Media.Animation.QuadraticEase>的行為, 方法是使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e87aa-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="e87aa-141">例如, 如果您想要使用<xref:System.Windows.Media.Animation.PowerEase>替代的<xref:System.Windows.Media.Animation.CubicEase>, 請指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值3。</span><span class="sxs-lookup"><span data-stu-id="e87aa-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="e87aa-142">除了使用執行時間中包含的緩動函式之外, 您還可以藉由繼承<xref:System.Windows.Media.Animation.EasingFunctionBase>來建立自己的自訂緩動函數。</span><span class="sxs-lookup"><span data-stu-id="e87aa-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="e87aa-143">下列範例將示範如何建立簡單的自訂 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="e87aa-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="e87aa-144">您可以藉由覆寫<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法來新增您自己的數學邏輯, 以瞭解緩時函數的行為方式。</span><span class="sxs-lookup"><span data-stu-id="e87aa-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
