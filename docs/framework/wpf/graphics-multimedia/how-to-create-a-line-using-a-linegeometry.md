---
title: HOW TO：使用 LineGeometry 建立線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 6d5d0b413f940a2c7f70e05135ff070c1fe5ba21
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374657"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="546d2-102">HOW TO：使用 LineGeometry 建立線條</span><span class="sxs-lookup"><span data-stu-id="546d2-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="546d2-103">此範例示範如何使用<xref:System.Windows.Media.LineGeometry>類別來描述一條線。</span><span class="sxs-lookup"><span data-stu-id="546d2-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="546d2-104">A<xref:System.Windows.Media.LineGeometry>由其開始和結束點定義。</span><span class="sxs-lookup"><span data-stu-id="546d2-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="546d2-105">範例</span><span class="sxs-lookup"><span data-stu-id="546d2-105">Example</span></span>  
 <span data-ttu-id="546d2-106">下列範例示範如何建立和轉譯<xref:System.Windows.Media.LineGeometry>。</span><span class="sxs-lookup"><span data-stu-id="546d2-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="546d2-107">A<xref:System.Windows.Shapes.Path>元素用來轉譯線條。</span><span class="sxs-lookup"><span data-stu-id="546d2-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="546d2-108">由於線條沒有任何區域中，<xref:System.Windows.Shapes.Path>物件的<xref:System.Windows.Shapes.Shape.Fill%2A>未指定改用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>就會使用屬性。</span><span class="sxs-lookup"><span data-stu-id="546d2-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="546d2-109">![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="546d2-109">![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="546d2-110">從 (10,20) 繪製到 (100,130) 的 LineGeometry</span><span class="sxs-lookup"><span data-stu-id="546d2-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="546d2-111">其他簡單幾何類別包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="546d2-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="546d2-112">這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="546d2-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="546d2-113">如需詳細資訊，請參閱 <<c0> [ 幾何概觀](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="546d2-113">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546d2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="546d2-114">See also</span></span>
- [<span data-ttu-id="546d2-115">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="546d2-115">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="546d2-116">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="546d2-116">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="546d2-117">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="546d2-117">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
