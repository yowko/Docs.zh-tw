---
title: 操作說明：使用 AnimationClock 建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: b8c64586d0dc5dc2e565fe4cb002e0f9cd4109af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558728"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="1a8f9-102">操作說明：使用 AnimationClock 建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="1a8f9-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="1a8f9-103">這個範例示範如何使用<xref:System.Windows.Media.Animation.Clock>以動畫方式顯示屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="1a8f9-104">有三種方式可以動畫顯示相依性屬性︰</span><span class="sxs-lookup"><span data-stu-id="1a8f9-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="1a8f9-105">建立<xref:System.Windows.Media.Animation.AnimationTimeline>和其關聯屬性使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="1a8f9-106">使用物件的<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法，以套用單一<xref:System.Windows.Media.Animation.AnimationTimeline>至目標屬性。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="1a8f9-107">建立<xref:System.Windows.Media.Animation.AnimationClock>從<xref:System.Windows.Media.Animation.AnimationTimeline>並將它套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="1a8f9-108"><xref:System.Windows.Media.Animation.Storyboard> 物件和<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法可讓您建立屬性動畫沒有直接建立與散發時鐘 (如需範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)和[屬性而不建立動畫使用分鏡腳本](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md));建立和自動為您散發的時鐘。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a8f9-109">範例</span><span class="sxs-lookup"><span data-stu-id="1a8f9-109">Example</span></span>  
 <span data-ttu-id="1a8f9-110">下列範例示範如何建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用到兩個類似的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="1a8f9-111">如需範例示範如何以互動方式控制<xref:System.Windows.Media.Animation.Clock>啟動之後，請參閱[以互動方式控制時鐘](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)。</span><span class="sxs-lookup"><span data-stu-id="1a8f9-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a8f9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a8f9-112">See Also</span></span>  
 [<span data-ttu-id="1a8f9-113">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="1a8f9-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="1a8f9-114">不使用分鏡腳本而建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="1a8f9-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="1a8f9-115">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="1a8f9-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
