---
title: HOW TO：將動畫輸出值加入至動畫啟動值
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 820e03064d331e852a224e1f989685d7a77983db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603023"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="dfb51-102">HOW TO：將動畫輸出值加入至動畫啟動值</span><span class="sxs-lookup"><span data-stu-id="dfb51-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="dfb51-103">此範例示範如何將動畫輸出值加入至動畫的起始值。</span><span class="sxs-lookup"><span data-stu-id="dfb51-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfb51-104">範例</span><span class="sxs-lookup"><span data-stu-id="dfb51-104">Example</span></span>  
 <span data-ttu-id="dfb51-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>屬性會指定是否要加入至動畫的屬性的起始值 （基底值） 的動畫的輸出值。</span><span class="sxs-lookup"><span data-stu-id="dfb51-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="dfb51-106">您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>具有最基本的動畫和大部分的主要畫面格動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="dfb51-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="dfb51-107">如需詳細資訊，請參閱 <<c0> [ 動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)並[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="dfb51-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="dfb51-108">下列範例示範使用的效果<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>具有屬性<xref:System.Windows.Media.Animation.DoubleAnimation>並使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>屬性與<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。</span><span class="sxs-lookup"><span data-stu-id="dfb51-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="dfb51-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfb51-109">See also</span></span>
- [<span data-ttu-id="dfb51-110">在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="dfb51-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="dfb51-111">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="dfb51-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="dfb51-112">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="dfb51-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="dfb51-113">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="dfb51-113">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="dfb51-114">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="dfb51-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
