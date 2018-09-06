---
title: 如何：建立三次方貝茲曲線
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 2dd9dfa7f15ce00261c87f316079c25a7aa52532
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032078"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="c51fa-102">如何：建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="c51fa-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="c51fa-103">此範例示範如何建立三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="c51fa-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="c51fa-104">若要建立三次方貝茲曲線，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.BezierSegment>類別。</span><span class="sxs-lookup"><span data-stu-id="c51fa-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="c51fa-105">若要顯示產生的幾何，請使用<xref:System.Windows.Shapes.Path>項目，或使用它來搭配<xref:System.Windows.Media.GeometryDrawing>或<xref:System.Windows.Media.DrawingContext>。</span><span class="sxs-lookup"><span data-stu-id="c51fa-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="c51fa-106">在下列範例中，三次方貝茲曲線會繪製從 （10，100） 到 （300，100）。</span><span class="sxs-lookup"><span data-stu-id="c51fa-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="c51fa-107">曲線具有的控點 （100，0） 和 （200，200）。</span><span class="sxs-lookup"><span data-stu-id="c51fa-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c51fa-108">範例</span><span class="sxs-lookup"><span data-stu-id="c51fa-108">Example</span></span>  
 <span data-ttu-id="c51fa-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="c51fa-109">[xaml]</span></span>  
  
 <span data-ttu-id="c51fa-110">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以使用縮寫的標記語法來描述路徑。</span><span class="sxs-lookup"><span data-stu-id="c51fa-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="c51fa-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="c51fa-111">[xaml]</span></span>  
  
 <span data-ttu-id="c51fa-112">在  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您也可以繪製使用 object 標記之三次方貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="c51fa-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="c51fa-113">下列範例相當於先前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="c51fa-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="c51fa-114">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="c51fa-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51fa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c51fa-115">See Also</span></span>  
 [<span data-ttu-id="c51fa-116">建立橢圓形弧線</span><span class="sxs-lookup"><span data-stu-id="c51fa-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="c51fa-117">在 PathGeometry 中建立 LineSegment</span><span class="sxs-lookup"><span data-stu-id="c51fa-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [<span data-ttu-id="c51fa-118">建立三次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="c51fa-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [<span data-ttu-id="c51fa-119">建立二次方貝茲曲線</span><span class="sxs-lookup"><span data-stu-id="c51fa-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
