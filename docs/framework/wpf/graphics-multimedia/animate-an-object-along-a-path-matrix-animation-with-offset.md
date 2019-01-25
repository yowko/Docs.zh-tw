---
title: HOW TO：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: e5e619de8b90737136559db134a131fdc1833fb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640091"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="c8c05-102">HOW TO：沿著路徑建立物件的動畫 (具有位移累加的矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="c8c05-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="c8c05-103">此範例示範如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>類別以沿著路徑建立物件和動畫的累積其位移值，因為它會重複。</span><span class="sxs-lookup"><span data-stu-id="c8c05-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8c05-104">範例</span><span class="sxs-lookup"><span data-stu-id="c8c05-104">Example</span></span>  
 <span data-ttu-id="c8c05-105">下列範例會使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>來以動畫顯示的物件<xref:System.Windows.Media.MatrixTransform.Matrix%2A>屬性<xref:System.Windows.Media.MatrixTransform>套用至按鈕。</span><span class="sxs-lookup"><span data-stu-id="c8c05-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="c8c05-106">如此一來，按鈕會沿著曲線路徑移動。</span><span class="sxs-lookup"><span data-stu-id="c8c05-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="c8c05-107">此外，此範例設定<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>屬性設`true`，這會造成動畫重複時累加動畫矩陣的位移。</span><span class="sxs-lookup"><span data-stu-id="c8c05-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="c8c05-108">因為位移會一直累積，所以按鈕會在動畫重複時逐漸橫越螢幕移動，而不是重設為起始位置。</span><span class="sxs-lookup"><span data-stu-id="c8c05-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="c8c05-109">請注意，雖然<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A>屬性導致位移的值隨著重複而累積，但它不會累積旋轉值。</span><span class="sxs-lookup"><span data-stu-id="c8c05-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="c8c05-110">若要讓累積旋轉值，設定動畫的<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>並<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A>屬性，以`true`。</span><span class="sxs-lookup"><span data-stu-id="c8c05-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="c8c05-111">如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="c8c05-111">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="c8c05-112">如需示範如何以動畫顯示範例<xref:System.Windows.Media.Matrix>沿著不含位移累加的路徑值，請參閱[建立動畫物件沿著路徑動畫 （矩陣動畫）](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c05-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c05-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8c05-113">See also</span></span>
- [<span data-ttu-id="c8c05-114">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="c8c05-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="c8c05-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="c8c05-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
