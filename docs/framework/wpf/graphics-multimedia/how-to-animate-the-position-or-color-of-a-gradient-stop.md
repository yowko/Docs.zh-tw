---
title: 如何：建立漸層停駐點位置或色彩的動畫
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
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452840"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="44b3c-102">如何：建立漸層停駐點位置或色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="44b3c-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="44b3c-103">這個範例示範如何以動畫顯示 <xref:System.Windows.Media.GradientStop> 物件的 <xref:System.Windows.Media.GradientStop.Color%2A> 和 <xref:System.Windows.Media.GradientStop.Offset%2A>。</span><span class="sxs-lookup"><span data-stu-id="44b3c-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b3c-104">範例</span><span class="sxs-lookup"><span data-stu-id="44b3c-104">Example</span></span>  
 <span data-ttu-id="44b3c-105">下列範例會在 <xref:System.Windows.Media.LinearGradientBrush>內繪製三個漸層停駐的動畫。</span><span class="sxs-lookup"><span data-stu-id="44b3c-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="44b3c-106">此範例使用三個動畫，其中每一個都會以動畫呈現不同的漸層停駐點：</span><span class="sxs-lookup"><span data-stu-id="44b3c-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="44b3c-107">第一個動畫是 <xref:System.Windows.Media.Animation.DoubleAnimation>，會將第一個漸層停駐的 <xref:System.Windows.Media.GradientStop.Offset%2A> 從0.0 到1.0，然後回到0.0。</span><span class="sxs-lookup"><span data-stu-id="44b3c-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="44b3c-108">因此，漸層中的第一個色彩會從左邊到矩形的右邊，然後回到左側。</span><span class="sxs-lookup"><span data-stu-id="44b3c-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="44b3c-109">第二個動畫（<xref:System.Windows.Media.Animation.ColorAnimation>）會將第二個漸層停駐的 <xref:System.Windows.Media.GradientStop.Color%2A> 從 <xref:System.Windows.Media.Colors.Purple%2A> 繪製到 <xref:System.Windows.Media.Colors.Yellow%2A>，然後再回到 <xref:System.Windows.Media.Colors.Purple%2A>。</span><span class="sxs-lookup"><span data-stu-id="44b3c-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="44b3c-110">如此一來，漸層中的中間色彩就會從紫色變更為黃色，再改回紫色。</span><span class="sxs-lookup"><span data-stu-id="44b3c-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="44b3c-111">第三個動畫，另一個 <xref:System.Windows.Media.Animation.ColorAnimation>，會將第三個漸層停駐 <xref:System.Windows.Media.GradientStop.Color%2A> 點的不透明度繪製到-1，然後返回。</span><span class="sxs-lookup"><span data-stu-id="44b3c-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="44b3c-112">因此，漸層中的第三個色彩會淡開，然後再次變成不透明。</span><span class="sxs-lookup"><span data-stu-id="44b3c-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="44b3c-113">雖然此範例使用 <xref:System.Windows.Media.LinearGradientBrush>，但在 <xref:System.Windows.Media.RadialGradientBrush>內建立 <xref:System.Windows.Media.GradientStop> 物件動畫的程式是相同的。</span><span class="sxs-lookup"><span data-stu-id="44b3c-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="44b3c-114">如需其他範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。</span><span class="sxs-lookup"><span data-stu-id="44b3c-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b3c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44b3c-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="44b3c-116">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="44b3c-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="44b3c-117">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="44b3c-117">Storyboards Overview</span></span>](storyboards-overview.md)
