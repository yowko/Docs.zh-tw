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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186492"
---
# <a name="easing-functions"></a><span data-ttu-id="8adda-102">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="8adda-102">Easing Functions</span></span>
<span data-ttu-id="8adda-103">Easing 函式可讓您將自訂的數學公式套用至動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="8adda-104">例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。</span><span class="sxs-lookup"><span data-stu-id="8adda-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="8adda-105">您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。</span><span class="sxs-lookup"><span data-stu-id="8adda-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="8adda-106">除了通過繼承創建自己的自訂緩動函數外<xref:System.Windows.Media.Animation.EasingFunctionBase>，您還可以使用運行時提供的幾個緩動函數之一來創建常見效果。</span><span class="sxs-lookup"><span data-stu-id="8adda-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="8adda-107"><xref:System.Windows.Media.Animation.BackEase>：在動畫開始在指示的路徑中設置動畫之前稍微縮回動畫的運動。</span><span class="sxs-lookup"><span data-stu-id="8adda-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="8adda-108"><xref:System.Windows.Media.Animation.BounceEase>：創建彈跳效果。</span><span class="sxs-lookup"><span data-stu-id="8adda-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="8adda-109"><xref:System.Windows.Media.Animation.CircleEase>：創建使用圓形函數加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="8adda-110"><xref:System.Windows.Media.Animation.CubicEase>： 創建使用公式*f*（*t*） = *t*<sup>3</sup>加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="8adda-111"><xref:System.Windows.Media.Animation.ElasticEase>：創建類似于彈簧來回擺動的動畫，直到它開始休息。</span><span class="sxs-lookup"><span data-stu-id="8adda-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="8adda-112"><xref:System.Windows.Media.Animation.ExponentialEase>：創建使用指數公式加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="8adda-113"><xref:System.Windows.Media.Animation.PowerEase>： 創建使用公式*f*（*t*） = *t*<sup>p</sup>的公式加速和/或減速的動畫<xref:System.Windows.Media.Animation.PowerEase.Power%2A>，其中 p 等於屬性。</span><span class="sxs-lookup"><span data-stu-id="8adda-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="8adda-114"><xref:System.Windows.Media.Animation.QuadraticEase>： 創建使用公式*f*（*t*） = *t*<sup>2</sup>加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="8adda-115"><xref:System.Windows.Media.Animation.QuarticEase>： 創建使用公式*f*（*t*） = *t*<sup>4</sup>加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="8adda-116"><xref:System.Windows.Media.Animation.QuinticEase>： 創建使用公式*f*（*t*） = *t*<sup>5</sup>加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="8adda-117"><xref:System.Windows.Media.Animation.SineEase>：創建使用子項公式加速和/或減速的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="8adda-118">要將緩動函數應用於動畫，請使用動畫`EasingFunction`的屬性指定要應用於動畫的緩動函數。</span><span class="sxs-lookup"><span data-stu-id="8adda-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="8adda-119">下面的示例將<xref:System.Windows.Media.Animation.BounceEase>緩動函數應用於<xref:System.Windows.Media.Animation.DoubleAnimation>創建彈跳效果。</span><span class="sxs-lookup"><span data-stu-id="8adda-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="8adda-120">在上述範例中，easing 函式套用至 From/To/By 動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="8adda-121">您也可以將這些 easing 函式套用至主要畫面格動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="8adda-122">下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。</span><span class="sxs-lookup"><span data-stu-id="8adda-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="8adda-123">可以使用 屬性<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>更改緩動函數的特性，即更改動畫插值的方式。</span><span class="sxs-lookup"><span data-stu-id="8adda-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="8adda-124">您可以為<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>：</span><span class="sxs-lookup"><span data-stu-id="8adda-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="8adda-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>：插值遵循與緩動函數關聯的數學公式。</span><span class="sxs-lookup"><span data-stu-id="8adda-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="8adda-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>：插值遵循 100% 插值減去與緩動函數關聯的公式的輸出。</span><span class="sxs-lookup"><span data-stu-id="8adda-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="8adda-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>：插值用於<xref:System.Windows.Media.Animation.EasingMode.EaseIn>動畫的上半部分和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>下半場。</span><span class="sxs-lookup"><span data-stu-id="8adda-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="8adda-128">下圖顯示了*f*（*x* <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> ） 表示動畫進度和*t*表示時間的不同值。</span><span class="sxs-lookup"><span data-stu-id="8adda-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="8adda-129">![BackEase EasingMode 圖形。](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="8adda-130">![BounceEase EasingMode 圖形。](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="8adda-131">![CircleEase EasingMode 圖形。](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="8adda-132">![CubicEase EasingMode 圖形。](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="8adda-133">![包含不同加/減速模式圖形的 ElasticEase。](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="8adda-134">![不同加/減速模式的 ExponentialEase 圖形。](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="8adda-135">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="8adda-136">![具有不同緩動模式的圖形的二次緩動](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="8adda-137">![包含不同加/減速模式圖形的 QuarticEase。](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="8adda-138">![包含不同加/減速模式圖形的 QuinticEase。](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="8adda-139">![使用不同 EasingMode 值的 SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8adda-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8adda-140">可以使用 創建<xref:System.Windows.Media.Animation.PowerEase>與<xref:System.Windows.Media.Animation.CubicEase><xref:System.Windows.Media.Animation.QuadraticEase><xref:System.Windows.Media.Animation.QuarticEase>、 和<xref:System.Windows.Media.Animation.QuinticEase>以及 使用 屬性<xref:System.Windows.Media.Animation.PowerEase.Power%2A>相同的行為。</span><span class="sxs-lookup"><span data-stu-id="8adda-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="8adda-141">例如，如果要使用<xref:System.Windows.Media.Animation.PowerEase>替換<xref:System.Windows.Media.Animation.CubicEase>，請指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值 3。</span><span class="sxs-lookup"><span data-stu-id="8adda-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="8adda-142">除了使用運行時中包含的緩動函數外，還可以通過繼承 來<xref:System.Windows.Media.Animation.EasingFunctionBase>創建自己的自訂緩動函數。</span><span class="sxs-lookup"><span data-stu-id="8adda-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="8adda-143">下列範例將示範如何建立簡單的自訂 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="8adda-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="8adda-144">您可以添加您自己的數學邏輯，用於緩動函數如何通過重寫<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法來運行。</span><span class="sxs-lookup"><span data-stu-id="8adda-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
