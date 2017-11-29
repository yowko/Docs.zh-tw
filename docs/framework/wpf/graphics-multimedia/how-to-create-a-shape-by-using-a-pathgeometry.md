---
title: "如何：使用 PathGeometry 建立圖案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31f77f0921bb018317834077f70e4623c47a4f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="9622f-102">如何：使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="9622f-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="9622f-103">這個範例示範如何建立使用圖形<xref:System.Windows.Media.PathGeometry>類別。</span><span class="sxs-lookup"><span data-stu-id="9622f-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="9622f-104"><xref:System.Windows.Media.PathGeometry>物件會組成一或多個<xref:System.Windows.Media.PathFigure>物件; 每一個<xref:System.Windows.Media.PathFigure>代表不同的 「 圖 」 或圖形。</span><span class="sxs-lookup"><span data-stu-id="9622f-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="9622f-105">每個<xref:System.Windows.Media.PathFigure>本身組成一或多個<xref:System.Windows.Media.PathSegment>物件，分別代表連接圖或形狀圖的一部分。</span><span class="sxs-lookup"><span data-stu-id="9622f-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="9622f-106">區段類型包括<xref:System.Windows.Media.LineSegment>， <xref:System.Windows.Media.ArcSegment>，和<xref:System.Windows.Media.BezierSegment>。</span><span class="sxs-lookup"><span data-stu-id="9622f-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9622f-107">範例</span><span class="sxs-lookup"><span data-stu-id="9622f-107">Example</span></span>  
 <span data-ttu-id="9622f-108">下列範例會使用<xref:System.Windows.Media.PathGeometry>，以建立三角形。</span><span class="sxs-lookup"><span data-stu-id="9622f-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="9622f-109"><xref:System.Windows.Media.PathGeometry>使用顯示<xref:System.Windows.Shapes.Path>項目。</span><span class="sxs-lookup"><span data-stu-id="9622f-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="9622f-110">下圖顯示上一個範例中所建立的圖案。</span><span class="sxs-lookup"><span data-stu-id="9622f-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="9622f-111">![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="9622f-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="9622f-112">PathGeometry 以建立三角形</span><span class="sxs-lookup"><span data-stu-id="9622f-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="9622f-113">前一個範例，示範如何建立簡單的圖形，三角形。</span><span class="sxs-lookup"><span data-stu-id="9622f-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="9622f-114">A<xref:System.Windows.Media.PathGeometry>也可用來建立更複雜的圖形，包括弧形和曲線。</span><span class="sxs-lookup"><span data-stu-id="9622f-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="9622f-115">如需範例，請參閱[建立橢圓形弧線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)，[建立三次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)，和[建立二次方貝茲曲線](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)。</span><span class="sxs-lookup"><span data-stu-id="9622f-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="9622f-116">這個範例屬於較大型的範例；如需完整範例，請參閱[幾何範例](http://go.microsoft.com/fwlink/?LinkID=159989)。</span><span class="sxs-lookup"><span data-stu-id="9622f-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9622f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9622f-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="9622f-118">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="9622f-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="9622f-119">幾何範例</span><span class="sxs-lookup"><span data-stu-id="9622f-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)
