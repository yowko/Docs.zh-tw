---
title: 操作說明：沿著路徑建立物件的動畫 (矩陣動畫)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452905"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="9f692-102">操作說明：沿著路徑建立物件的動畫 (矩陣動畫)</span><span class="sxs-lookup"><span data-stu-id="9f692-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="9f692-103">這個範例示範如何使用 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 類別，沿著 <xref:System.Windows.Media.PathGeometry>所定義的路徑建立物件的動畫。</span><span class="sxs-lookup"><span data-stu-id="9f692-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f692-104">範例</span><span class="sxs-lookup"><span data-stu-id="9f692-104">Example</span></span>  
 <span data-ttu-id="9f692-105">下列範例會執行下列動作，沿著路徑以動畫顯示的物件︰</span><span class="sxs-lookup"><span data-stu-id="9f692-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="9f692-106">將 <xref:System.Windows.Media.MatrixTransform> 套用至物件，以便移動。</span><span class="sxs-lookup"><span data-stu-id="9f692-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="9f692-107">使用 <xref:System.Windows.Media.PathGeometry>定義路徑。</span><span class="sxs-lookup"><span data-stu-id="9f692-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="9f692-108">建立 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>，並使用它以動畫顯示 <xref:System.Windows.Media.MatrixTransform>的 <xref:System.Windows.Media.Matrix> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9f692-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="9f692-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> 會採用 <xref:System.Windows.Media.PathGeometry>，並使用它來產生 <xref:System.Windows.Media.Matrix> 值。</span><span class="sxs-lookup"><span data-stu-id="9f692-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="9f692-110">如需完整範例，請參閱[路徑動畫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)。</span><span class="sxs-lookup"><span data-stu-id="9f692-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="9f692-111">如需幾何路徑的詳細資訊，請參閱[幾何總覽](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f692-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f692-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f692-112">See also</span></span>

- [<span data-ttu-id="9f692-113">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="9f692-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9f692-114">路徑動畫範例</span><span class="sxs-lookup"><span data-stu-id="9f692-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="9f692-115">路徑動畫操作說明主題</span><span class="sxs-lookup"><span data-stu-id="9f692-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
