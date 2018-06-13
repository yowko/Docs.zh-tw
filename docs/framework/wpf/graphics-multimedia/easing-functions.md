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
ms.openlocfilehash: 3ce7c1824dc53c154ba1091ea62c1b8950b757c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557559"
---
# <a name="easing-functions"></a><span data-ttu-id="0bac0-102">Easing 函式</span><span class="sxs-lookup"><span data-stu-id="0bac0-102">Easing Functions</span></span>
<span data-ttu-id="0bac0-103">Easing 函式可讓您將自訂的數學公式套用至動畫。</span><span class="sxs-lookup"><span data-stu-id="0bac0-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="0bac0-104">例如，您可能想要物件實際表現出反彈或像是在彈簧上一樣。</span><span class="sxs-lookup"><span data-stu-id="0bac0-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="0bac0-105">您可以使用主要畫面格或甚至 From/To/By 動畫來模擬這些效果，但所需的工作量可能很大，而且和使用數學公式相比，動畫會較不精確。</span><span class="sxs-lookup"><span data-stu-id="0bac0-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="0bac0-106">除了繼承以建立您自己自訂的 easing 函式從<xref:System.Windows.Media.Animation.EasingFunctionBase>，您可以使用其中一個執行階段提供的幾個 easing 函式來建立通用的效果。</span><span class="sxs-lookup"><span data-stu-id="0bac0-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="0bac0-107"><xref:System.Windows.Media.Animation.BackEase>： 會撤銷動畫的動畫看的起來稍有後，才開始以動畫方式顯示在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="0bac0-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="0bac0-108"><xref:System.Windows.Media.Animation.BounceEase>： 建立彈跳的效果。</span><span class="sxs-lookup"><span data-stu-id="0bac0-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="0bac0-109"><xref:System.Windows.Media.Animation.CircleEase>： 建立的動畫加速或減速使用循環函式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="0bac0-110"><xref:System.Windows.Media.Animation.CubicEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="0bac0-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="0bac0-111"><xref:System.Windows.Media.Animation.ElasticEase>： 建立類似 spring，直到到達貼齊來回擺動的動畫。</span><span class="sxs-lookup"><span data-stu-id="0bac0-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="0bac0-112"><xref:System.Windows.Media.Animation.ExponentialEase>： 建立的動畫加速或減速使用指數的公式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="0bac0-113"><xref:System.Windows.Media.Animation.PowerEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>p</sup> p 等於<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0bac0-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="0bac0-114"><xref:System.Windows.Media.Animation.QuadraticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>2</sup>。</span><span class="sxs-lookup"><span data-stu-id="0bac0-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="0bac0-115"><xref:System.Windows.Media.Animation.QuarticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>4</sup>。</span><span class="sxs-lookup"><span data-stu-id="0bac0-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="0bac0-116"><xref:System.Windows.Media.Animation.QuinticEase>： 建立的動畫加速或減速使用公式*f*(*t*) = *t*<sup>5</sup>。</span><span class="sxs-lookup"><span data-stu-id="0bac0-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="0bac0-117"><xref:System.Windows.Media.Animation.SineEase>： 建立的動畫加速或減速使用正弦的公式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="0bac0-118">您可以使用下列範例來探索這些 easing 函式的行為。</span><span class="sxs-lookup"><span data-stu-id="0bac0-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="0bac0-119">執行這個範例</span><span class="sxs-lookup"><span data-stu-id="0bac0-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="0bac0-120">若要套用至動畫的 easing 函式，使用`EasingFunction`動畫屬性指定要套用至動畫的 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="0bac0-121">下列範例會套用<xref:System.Windows.Media.Animation.BounceEase>easing 函式可<xref:System.Windows.Media.Animation.DoubleAnimation>建立彈跳的效果。</span><span class="sxs-lookup"><span data-stu-id="0bac0-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="0bac0-122">執行這個範例</span><span class="sxs-lookup"><span data-stu-id="0bac0-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="0bac0-123">在上述範例中，easing 函式套用至 From/To/By 動畫。</span><span class="sxs-lookup"><span data-stu-id="0bac0-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="0bac0-124">您也可以將這些 easing 函式套用至主要畫面格動畫。</span><span class="sxs-lookup"><span data-stu-id="0bac0-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="0bac0-125">下列範例示範如何使用主要畫面格搭配其相關聯的 easing 函式，來建立收縮向上，減慢，然後向下展開 (如同下降)，然後不斷彈跳直到停止的動畫。</span><span class="sxs-lookup"><span data-stu-id="0bac0-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="0bac0-126">執行這個範例</span><span class="sxs-lookup"><span data-stu-id="0bac0-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="0bac0-127">您可以使用<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>改變 easing 函式的行為，亦即，屬性變更動畫的插補。</span><span class="sxs-lookup"><span data-stu-id="0bac0-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="0bac0-128">有三個可能的值，您可以提供<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="0bac0-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="0bac0-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>： 插補遵循 easing 函式相關聯的數學公式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="0bac0-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>： 插補如下輸出減去 easing 函式相關聯的公式的 100%插補。</span><span class="sxs-lookup"><span data-stu-id="0bac0-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="0bac0-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>： 使用插補<xref:System.Windows.Media.Animation.EasingMode.EaseIn>前半的動畫和<xref:System.Windows.Media.Animation.EasingMode.EaseOut>第二個半。</span><span class="sxs-lookup"><span data-stu-id="0bac0-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="0bac0-132">下列圖表示範不同的值<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>其中*f*(*x*) 表示的動畫進度和*t*代表時間。</span><span class="sxs-lookup"><span data-stu-id="0bac0-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="0bac0-133">![BackEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="0bac0-134">![BounceEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="0bac0-135">![CircleEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="0bac0-136">![CubicEase EasingMode 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="0bac0-137">![包含不同加/減速模式圖形的 ElasticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="0bac0-138">![不同加/減速模式的 ExponentialEase 圖形。](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="0bac0-139">![包含不同加/減速模式圖形的 QuarticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="0bac0-140">![包含不同加/減速模式圖形的 QuadraticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="0bac0-141">![包含不同加/減速模式圖形的 QuarticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="0bac0-142">![包含不同加/減速模式圖形的 QuinticEase。](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="0bac0-143">![使用不同 EasingMode 值的 SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0bac0-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bac0-144">您可以使用<xref:System.Windows.Media.Animation.PowerEase>建立相同的行為<xref:System.Windows.Media.Animation.CubicEase>， <xref:System.Windows.Media.Animation.QuadraticEase>， <xref:System.Windows.Media.Animation.QuarticEase>，和<xref:System.Windows.Media.Animation.QuinticEase>使用<xref:System.Windows.Media.Animation.PowerEase.Power%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0bac0-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="0bac0-145">例如，如果您想要使用<xref:System.Windows.Media.Animation.PowerEase>替換<xref:System.Windows.Media.Animation.CubicEase>，指定<xref:System.Windows.Media.Animation.PowerEase.Power%2A>值為 3。</span><span class="sxs-lookup"><span data-stu-id="0bac0-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="0bac0-146">除了使用加/減速函數包含在執行階段中，您可以建立您自己自訂的加/減速函數透過繼承自<xref:System.Windows.Media.Animation.EasingFunctionBase>。</span><span class="sxs-lookup"><span data-stu-id="0bac0-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="0bac0-147">下列範例將示範如何建立簡單的自訂 easing 函式。</span><span class="sxs-lookup"><span data-stu-id="0bac0-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="0bac0-148">您可以加入您自己的 easing 函式藉由覆寫的操作方式的數學邏輯<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0bac0-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="0bac0-149">執行這個範例</span><span class="sxs-lookup"><span data-stu-id="0bac0-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
