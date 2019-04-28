---
title: HOW TO：沿著路徑建立物件的動畫 (雙精度浮點數動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 54f345bbe6b513e3593cbf45ba190d4a44228424
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010107"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="84e30-102">HOW TO：沿著路徑建立物件的動畫 (雙精度浮點數動畫)</span><span class="sxs-lookup"><span data-stu-id="84e30-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="84e30-103">此範例示範如何使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>類別以沿著所定義的路徑移動物件<xref:System.Windows.Media.PathGeometry>。</span><span class="sxs-lookup"><span data-stu-id="84e30-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e30-104">範例</span><span class="sxs-lookup"><span data-stu-id="84e30-104">Example</span></span>  
 <span data-ttu-id="84e30-105">下列範例會使用兩個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>物件來沿著幾何路徑移動矩形：</span><span class="sxs-lookup"><span data-stu-id="84e30-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="84e30-106">第一個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.TranslateTransform.X%2A>的<xref:System.Windows.Media.TranslateTransform>套用到矩形。</span><span class="sxs-lookup"><span data-stu-id="84e30-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="84e30-107">它會使矩形沿著路徑水平移動。</span><span class="sxs-lookup"><span data-stu-id="84e30-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="84e30-108">第二個<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>繪製<xref:System.Windows.Media.TranslateTransform.Y%2A>的<xref:System.Windows.Media.TranslateTransform>套用到矩形。</span><span class="sxs-lookup"><span data-stu-id="84e30-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="84e30-109">它會使矩形沿著路徑垂直移動。</span><span class="sxs-lookup"><span data-stu-id="84e30-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="84e30-110">如需完整的範例，請參閱[路徑動畫範例](https://go.microsoft.com/fwlink/?LinkID=160028)。</span><span class="sxs-lookup"><span data-stu-id="84e30-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="84e30-111">使用幾何路徑移動物件的另一種方式是使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>物件。</span><span class="sxs-lookup"><span data-stu-id="84e30-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="84e30-112">如需範例，請參閱[以動畫顯示物件沿著路徑動畫 （矩陣動畫）](how-to-animate-an-object-along-a-path-matrix-animation.md)。</span><span class="sxs-lookup"><span data-stu-id="84e30-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e30-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84e30-113">See also</span></span>

- [<span data-ttu-id="84e30-114">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="84e30-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="84e30-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="84e30-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
