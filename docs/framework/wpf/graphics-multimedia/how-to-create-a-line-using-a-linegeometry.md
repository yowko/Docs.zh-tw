---
title: HOW TO：使用 LineGeometry 建立線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: fbf44f627ede0fe3bdf7e629728a1e3b858fd30e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690562"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="e5563-102">HOW TO：使用 LineGeometry 建立線條</span><span class="sxs-lookup"><span data-stu-id="e5563-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="e5563-103">此範例示範如何使用<xref:System.Windows.Media.LineGeometry>類別來描述一條線。</span><span class="sxs-lookup"><span data-stu-id="e5563-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="e5563-104">A<xref:System.Windows.Media.LineGeometry>由其開始和結束點定義。</span><span class="sxs-lookup"><span data-stu-id="e5563-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5563-105">範例</span><span class="sxs-lookup"><span data-stu-id="e5563-105">Example</span></span>  
 <span data-ttu-id="e5563-106">下列範例示範如何建立和轉譯<xref:System.Windows.Media.LineGeometry>。</span><span class="sxs-lookup"><span data-stu-id="e5563-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="e5563-107">A<xref:System.Windows.Shapes.Path>元素用來轉譯線條。</span><span class="sxs-lookup"><span data-stu-id="e5563-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="e5563-108">由於線條沒有任何區域中，<xref:System.Windows.Shapes.Path>物件的<xref:System.Windows.Shapes.Shape.Fill%2A>未指定改用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>就會使用屬性。</span><span class="sxs-lookup"><span data-stu-id="e5563-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="e5563-109">![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="e5563-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="e5563-110">從 (10,20) 繪製到 (100,130) 的 LineGeometry</span><span class="sxs-lookup"><span data-stu-id="e5563-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="e5563-111">其他簡單幾何類別包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="e5563-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="e5563-112">這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="e5563-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="e5563-113">如需詳細資訊，請參閱 <<c0> [ 幾何概觀](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e5563-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5563-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5563-114">See also</span></span>
- [<span data-ttu-id="e5563-115">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="e5563-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="e5563-116">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="e5563-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="e5563-117">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="e5563-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
