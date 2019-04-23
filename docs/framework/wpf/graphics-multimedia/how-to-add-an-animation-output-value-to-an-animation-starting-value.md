---
title: HOW TO：將動畫輸出值加到動畫啟動值
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102605"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="e7efc-102">HOW TO：將動畫輸出值加到動畫啟動值</span><span class="sxs-lookup"><span data-stu-id="e7efc-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="e7efc-103">此範例示範如何將動畫輸出值加入至動畫的起始值。</span><span class="sxs-lookup"><span data-stu-id="e7efc-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7efc-104">範例</span><span class="sxs-lookup"><span data-stu-id="e7efc-104">Example</span></span>  
 <span data-ttu-id="e7efc-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>屬性會指定是否要加入至動畫的屬性的起始值 （基底值） 的動畫的輸出值。</span><span class="sxs-lookup"><span data-stu-id="e7efc-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="e7efc-106">您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>具有最基本的動畫和大部分的主要畫面格動畫屬性。</span><span class="sxs-lookup"><span data-stu-id="e7efc-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="e7efc-107">如需詳細資訊，請參閱 <<c0> [ 動畫概觀](animation-overview.md)並[主要畫面格動畫概觀](key-frame-animations-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e7efc-107">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="e7efc-108">下列範例示範使用的效果<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>具有屬性<xref:System.Windows.Media.Animation.DoubleAnimation>並使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>屬性與<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。</span><span class="sxs-lookup"><span data-stu-id="e7efc-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e7efc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7efc-109">See also</span></span>

- [<span data-ttu-id="e7efc-110">在重複循環期間累加動畫值</span><span class="sxs-lookup"><span data-stu-id="e7efc-110">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="e7efc-111">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e7efc-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e7efc-112">主要畫面格動畫概觀</span><span class="sxs-lookup"><span data-stu-id="e7efc-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="e7efc-113">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="e7efc-113">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
