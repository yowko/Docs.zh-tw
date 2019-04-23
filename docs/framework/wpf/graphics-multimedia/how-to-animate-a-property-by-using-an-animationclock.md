---
title: HOW TO：使用 AnimationClock 建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 4fa9efc593461d26eabaee5e2f62c1a17da1b543
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201360"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="c591a-102">HOW TO：使用 AnimationClock 建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="c591a-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="c591a-103">此範例示範如何使用<xref:System.Windows.Media.Animation.Clock>以動畫顯示屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="c591a-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="c591a-104">有三種方式可以動畫顯示相依性屬性︰</span><span class="sxs-lookup"><span data-stu-id="c591a-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="c591a-105">建立<xref:System.Windows.Media.Animation.AnimationTimeline>和其關聯該屬性使用<xref:System.Windows.Media.Animation.Storyboard>。</span><span class="sxs-lookup"><span data-stu-id="c591a-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="c591a-106">使用物件的<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法來套用單一<xref:System.Windows.Media.Animation.AnimationTimeline>至目標屬性。</span><span class="sxs-lookup"><span data-stu-id="c591a-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="c591a-107">建立<xref:System.Windows.Media.Animation.AnimationClock>從<xref:System.Windows.Media.Animation.AnimationTimeline>並將它套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="c591a-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="c591a-108"><xref:System.Windows.Media.Animation.Storyboard> 物件和<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法可讓您以動畫顯示屬性，而不需要直接建立和散發時鐘 (如需範例，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)和[屬性而不需要建立動畫使用分鏡腳本](how-to-animate-a-property-without-using-a-storyboard.md));建立時鐘，並為您自動散發。</span><span class="sxs-lookup"><span data-stu-id="c591a-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c591a-109">範例</span><span class="sxs-lookup"><span data-stu-id="c591a-109">Example</span></span>  
 <span data-ttu-id="c591a-110">下列範例示範如何建立<xref:System.Windows.Media.Animation.AnimationClock>並將它套用至兩個類似的屬性。</span><span class="sxs-lookup"><span data-stu-id="c591a-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="c591a-111">如需範例，示範如何以互動方式控制<xref:System.Windows.Media.Animation.Clock>啟動之後，請參閱[以互動方式控制時鐘](how-to-interactively-control-a-clock.md)。</span><span class="sxs-lookup"><span data-stu-id="c591a-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c591a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c591a-112">See also</span></span>

- [<span data-ttu-id="c591a-113">使用分鏡腳本建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="c591a-113">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="c591a-114">不使用分鏡腳本而建立屬性的動畫</span><span class="sxs-lookup"><span data-stu-id="c591a-114">Animate a Property Without Using a Storyboard</span></span>](how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="c591a-115">屬性動畫技術概觀</span><span class="sxs-lookup"><span data-stu-id="c591a-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
