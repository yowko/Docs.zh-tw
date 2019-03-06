---
title: HOW TO：使用 PathGeometry 建立圖案
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: ce84f2509116207afa200ddf83dcdc1f8101da13
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356199"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="9561d-102">HOW TO：使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="9561d-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="9561d-103">此範例示範如何使用建立圖形<xref:System.Windows.Media.PathGeometry>類別。</span><span class="sxs-lookup"><span data-stu-id="9561d-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="9561d-104"><xref:System.Windows.Media.PathGeometry> 物件會組成一或多個<xref:System.Windows.Media.PathFigure>物件; 每個<xref:System.Windows.Media.PathFigure>代表不同的 「 圖形 」 或圖案。</span><span class="sxs-lookup"><span data-stu-id="9561d-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="9561d-105">每個<xref:System.Windows.Media.PathFigure>本身由一或多個<xref:System.Windows.Media.PathSegment>物件，每個均代表圖形或圖案的已連接的部分。</span><span class="sxs-lookup"><span data-stu-id="9561d-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="9561d-106">線段類型包括<xref:System.Windows.Media.LineSegment>， <xref:System.Windows.Media.ArcSegment>，和<xref:System.Windows.Media.BezierSegment>。</span><span class="sxs-lookup"><span data-stu-id="9561d-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9561d-107">範例</span><span class="sxs-lookup"><span data-stu-id="9561d-107">Example</span></span>  
 <span data-ttu-id="9561d-108">下列範例會使用<xref:System.Windows.Media.PathGeometry>，以建立三角形。</span><span class="sxs-lookup"><span data-stu-id="9561d-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="9561d-109"><xref:System.Windows.Media.PathGeometry>會顯示使用<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="9561d-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="9561d-110">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="9561d-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="9561d-111">![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="9561d-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="9561d-112">使用 PathGeometry 建立三角形</span><span class="sxs-lookup"><span data-stu-id="9561d-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="9561d-113">前一個範例，示範如何建立簡單的圖形，三角形。</span><span class="sxs-lookup"><span data-stu-id="9561d-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="9561d-114">A<xref:System.Windows.Media.PathGeometry>也可用來建立更複雜的圖形，包括弧線和曲線。</span><span class="sxs-lookup"><span data-stu-id="9561d-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="9561d-115">如需範例，請參閱[建立橢圓形弧線](how-to-create-an-elliptical-arc.md)，[建立三次方貝茲曲線](how-to-create-a-cubic-bezier-curve.md)，並[建立二次方貝茲曲線](how-to-create-a-quadratic-bezier-curve.md)。</span><span class="sxs-lookup"><span data-stu-id="9561d-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="9561d-116">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](https://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="9561d-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9561d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9561d-117">See also</span></span>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="9561d-118">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="9561d-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="9561d-119">幾何範例</span><span class="sxs-lookup"><span data-stu-id="9561d-119">Geometries Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159989)
