---
title: "如何：建立漸層停駐點位置或色彩的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968d285d8a3345da9810f0ba4797bf8b2e33d36e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="9e07e-102">如何：建立漸層停駐點位置或色彩的動畫</span><span class="sxs-lookup"><span data-stu-id="9e07e-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="9e07e-103">此範例示範如何以動畫方式顯示<xref:System.Windows.Media.GradientStop.Color%2A>和<xref:System.Windows.Media.GradientStop.Offset%2A>的<xref:System.Windows.Media.GradientStop>物件。</span><span class="sxs-lookup"><span data-stu-id="9e07e-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e07e-104">範例</span><span class="sxs-lookup"><span data-stu-id="9e07e-104">Example</span></span>  
 <span data-ttu-id="9e07e-105">下列範例以動畫方式顯示在三個漸層停駐<xref:System.Windows.Media.LinearGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="9e07e-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="9e07e-106">此範例會使用三個動畫，其中每個不同的漸層停駐以動畫方式顯示：</span><span class="sxs-lookup"><span data-stu-id="9e07e-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="9e07e-107">第一次的動畫， <xref:System.Windows.Media.Animation.DoubleAnimation>，以動畫方式顯示第一個漸層停駐<xref:System.Windows.Media.GradientStop.Offset%2A>是介於 0.0 到 1.0 之間，然後再回到 0.0。</span><span class="sxs-lookup"><span data-stu-id="9e07e-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="9e07e-108">如此一來，第一個色彩在右側，即矩形的漸層從左邊算起排班中，然後再變回左側。</span><span class="sxs-lookup"><span data-stu-id="9e07e-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="9e07e-109">第二個動畫<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫方式顯示第二個漸層停駐<xref:System.Windows.Media.GradientStop.Color%2A>從<xref:System.Windows.Media.Colors.Purple%2A>至<xref:System.Windows.Media.Colors.Yellow%2A>然後再設回<xref:System.Windows.Media.Colors.Purple%2A>。</span><span class="sxs-lookup"><span data-stu-id="9e07e-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="9e07e-110">如此一來，漸層中間色彩從變更紫色顯示為黃色，並返回紫色。</span><span class="sxs-lookup"><span data-stu-id="9e07e-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="9e07e-111">第三個動畫，另一個<xref:System.Windows.Media.Animation.ColorAnimation>，以動畫方式顯示的第三個漸層停駐的不透明度<xref:System.Windows.Media.GradientStop.Color%2A>-1，然後重新開機。</span><span class="sxs-lookup"><span data-stu-id="9e07e-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="9e07e-112">如此一來，第三個的色彩漸層中消失，再變成 不透明。</span><span class="sxs-lookup"><span data-stu-id="9e07e-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="9e07e-113">雖然這個範例會使用<xref:System.Windows.Media.LinearGradientBrush>，處理程序是相同的動畫<xref:System.Windows.Media.GradientStop>物件內<xref:System.Windows.Media.RadialGradientBrush>。</span><span class="sxs-lookup"><span data-stu-id="9e07e-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="9e07e-114">如需其他範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973)。</span><span class="sxs-lookup"><span data-stu-id="9e07e-114">For additional examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e07e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e07e-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="9e07e-116">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="9e07e-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9e07e-117">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="9e07e-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
