---
title: 操作說明：沿著路徑建立物件的動畫 (點動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452892"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="db115-102">操作說明：沿著路徑建立物件的動畫 (點動畫)</span><span class="sxs-lookup"><span data-stu-id="db115-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="db115-103">這個範例示範如何使用 <xref:System.Windows.Media.Animation.PointAnimationUsingPath> 物件，沿著彎曲的路徑建立 <xref:System.Windows.Point> 的動畫。</span><span class="sxs-lookup"><span data-stu-id="db115-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db115-104">範例</span><span class="sxs-lookup"><span data-stu-id="db115-104">Example</span></span>  
 <span data-ttu-id="db115-105">下列範例會沿著 <xref:System.Windows.Media.PathGeometry>所定義的路徑移動 <xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="db115-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="db115-106">橢圓形幾何的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性（採用 <xref:System.Windows.Point> 值）會指定其位置;若要移動橢圓形幾何，您可以建立其 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="db115-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="db115-107">這個範例會使用 <xref:System.Windows.Media.Animation.PointAnimationUsingPath>，以動畫顯示 <xref:System.Windows.Media.EllipseGeometry> 物件的 <xref:System.Windows.Media.EllipseGeometry.Center%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="db115-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="db115-108">如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。</span><span class="sxs-lookup"><span data-stu-id="db115-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="db115-109">上述範例的程式碼版本使用 <xref:System.Windows.Media.Animation.Storyboard> 來建立 <xref:System.Windows.Media.EllipseGeometry>的動畫，即使只套用了一個動畫也一樣。</span><span class="sxs-lookup"><span data-stu-id="db115-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="db115-110"><xref:System.Windows.Media.Animation.Storyboard> 通常是套用多個動畫的最簡單方式，因為這些動畫可以透過相同的 <xref:System.Windows.Media.Animation.Storyboard>來控制。</span><span class="sxs-lookup"><span data-stu-id="db115-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="db115-111">不過，使用程式碼時，將單一動畫套用至屬性的更簡單方法是使用 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="db115-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="db115-112">如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。</span><span class="sxs-lookup"><span data-stu-id="db115-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db115-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db115-113">See also</span></span>

- [<span data-ttu-id="db115-114">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="db115-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="db115-115">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="db115-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="db115-116">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="db115-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
