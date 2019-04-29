---
title: HOW TO：建立漸層停駐點位置或色彩的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: eeaea4732855155bf711912644f2f5b3f5a4f8d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651359"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="7a063-102">HOW TO：建立漸層停駐點位置或色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="7a063-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="7a063-103">此範例示範如何建立動畫<xref:System.Windows.Media.GradientStop.Color%2A>並<xref:System.Windows.Media.GradientStop.Offset%2A>的<xref:System.Windows.Media.GradientStop>物件。</span><span class="sxs-lookup"><span data-stu-id="7a063-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a063-104">範例</span><span class="sxs-lookup"><span data-stu-id="7a063-104">Example</span></span>  
 <span data-ttu-id="7a063-105">下列範例以動畫顯示在三個漸層停駐<xref:System.Windows.Media.LinearGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="7a063-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="7a063-106">此範例使用三個動畫，其中每一個以動畫顯示不同的漸層停駐：</span><span class="sxs-lookup"><span data-stu-id="7a063-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="7a063-107">第一次的動畫<xref:System.Windows.Media.Animation.DoubleAnimation>，以動畫顯示的第一個漸層停駐<xref:System.Windows.Media.GradientStop.Offset%2A>從 0.0 到 1.0，然後再回到 0.0。</span><span class="sxs-lookup"><span data-stu-id="7a063-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="7a063-108">如此一來，第一個色彩在左側能漸層停駐會轉移至矩形右側，然後再設回左側。</span><span class="sxs-lookup"><span data-stu-id="7a063-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="7a063-109">將第二個動畫<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示第二個漸層停駐<xref:System.Windows.Media.GradientStop.Color%2A>從<xref:System.Windows.Media.Colors.Purple%2A>來<xref:System.Windows.Media.Colors.Yellow%2A>，然後再回到<xref:System.Windows.Media.Colors.Purple%2A>。</span><span class="sxs-lookup"><span data-stu-id="7a063-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="7a063-110">如此一來，在漸層的中間色彩從變更為紫色為黃色，再回到紫色。</span><span class="sxs-lookup"><span data-stu-id="7a063-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="7a063-111">第三個的動畫，另一個<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫顯示的第三個漸層停駐的不透明度<xref:System.Windows.Media.GradientStop.Color%2A>-1，然後重新開機。</span><span class="sxs-lookup"><span data-stu-id="7a063-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="7a063-112">如此一來，漸層中的第三個色彩或淡出，然後再次不透明。</span><span class="sxs-lookup"><span data-stu-id="7a063-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="7a063-113">雖然此範例會使用<xref:System.Windows.Media.LinearGradientBrush>，會以動畫顯示相同的程序<xref:System.Windows.Media.GradientStop>物件內<xref:System.Windows.Media.RadialGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="7a063-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="7a063-114">如需其他範例，請參閱 <<c0> [ 筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="7a063-114">For additional examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a063-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a063-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="7a063-116">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="7a063-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="7a063-117">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="7a063-117">Storyboards Overview</span></span>](storyboards-overview.md)
