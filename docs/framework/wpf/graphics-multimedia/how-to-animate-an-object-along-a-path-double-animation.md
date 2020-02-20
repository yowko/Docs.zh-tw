---
title: 操作說明：沿著路徑建立物件的動畫 (Double 動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452853"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="4354f-102">操作說明：沿著路徑建立物件的動畫 (Double 動畫)</span><span class="sxs-lookup"><span data-stu-id="4354f-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="4354f-103">這個範例示範如何使用 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 類別，沿著 <xref:System.Windows.Media.PathGeometry>所定義的路徑移動物件。</span><span class="sxs-lookup"><span data-stu-id="4354f-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4354f-104">範例</span><span class="sxs-lookup"><span data-stu-id="4354f-104">Example</span></span>  
 <span data-ttu-id="4354f-105">下列範例會使用兩個 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 物件，沿著幾何路徑移動矩形：</span><span class="sxs-lookup"><span data-stu-id="4354f-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="4354f-106">第一個 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 會繪製套用至矩形之 <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> 的動畫。</span><span class="sxs-lookup"><span data-stu-id="4354f-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="4354f-107">它會使矩形沿著路徑水平移動。</span><span class="sxs-lookup"><span data-stu-id="4354f-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="4354f-108">第二個 <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> 會繪製套用至矩形之 <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.Y%2A> 的動畫。</span><span class="sxs-lookup"><span data-stu-id="4354f-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="4354f-109">它會使矩形沿著路徑垂直移動。</span><span class="sxs-lookup"><span data-stu-id="4354f-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="4354f-110">如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。</span><span class="sxs-lookup"><span data-stu-id="4354f-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="4354f-111">使用幾何路徑移動物件的另一種方式是使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 物件。</span><span class="sxs-lookup"><span data-stu-id="4354f-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="4354f-112">如需範例，請參閱[沿著路徑建立物件的動畫（矩陣動畫）](how-to-animate-an-object-along-a-path-matrix-animation.md)。</span><span class="sxs-lookup"><span data-stu-id="4354f-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4354f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4354f-113">See also</span></span>

- [<span data-ttu-id="4354f-114">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="4354f-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4354f-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="4354f-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
