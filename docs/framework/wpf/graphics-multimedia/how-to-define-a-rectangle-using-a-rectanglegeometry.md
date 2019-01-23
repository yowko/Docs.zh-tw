---
title: HOW TO：使用 RectangleGeometry 定義矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 9c57f1536065af0bca1f3752179547daa502c066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511638"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="7c1ca-102">HOW TO：使用 RectangleGeometry 定義矩形</span><span class="sxs-lookup"><span data-stu-id="7c1ca-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="7c1ca-103">此範例說明如何使用<xref:System.Windows.Media.RectangleGeometry>來描述矩形的類別。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c1ca-104">範例</span><span class="sxs-lookup"><span data-stu-id="7c1ca-104">Example</span></span>  
 <span data-ttu-id="7c1ca-105">下列範例示範如何建立和轉譯<xref:System.Windows.Media.RectangleGeometry>。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="7c1ca-106">所定義的相對位置和維度的矩形<xref:System.Windows.Rect>結構。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="7c1ca-107">相對的位置`50,50`以及高度和寬度都`25`建立正方形。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="7c1ca-108">用於繪製的矩形內部<xref:System.Windows.Media.Brushes.LemonChiffon%2A>筆刷和其外框使用繪製<xref:System.Windows.Media.Brushes.Black%2A>筆觸粗細是`1`。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="7c1ca-109">![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="7c1ca-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="7c1ca-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="7c1ca-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="7c1ca-111">雖然此範例中使用<xref:System.Windows.Shapes.Path>項目來呈現<xref:System.Windows.Media.RectangleGeometry>，有許多其他使用方式<xref:System.Windows.Media.RectangleGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="7c1ca-112">例如，<xref:System.Windows.Media.RectangleGeometry>可用來指定<xref:System.Windows.UIElement.Clip%2A>的<xref:System.Windows.UIElement>或<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>的<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="7c1ca-113">其他簡單幾何類別包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="7c1ca-114">這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="7c1ca-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1ca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c1ca-115">See also</span></span>
- [<span data-ttu-id="7c1ca-116">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="7c1ca-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="7c1ca-117">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="7c1ca-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="7c1ca-118">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="7c1ca-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
