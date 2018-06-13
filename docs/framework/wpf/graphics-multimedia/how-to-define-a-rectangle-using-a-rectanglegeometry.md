---
title: 如何：使用 RectangleGeometry 定義矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 5d2ec6aec1eea8528ea6b43f72f4820b8bc19a37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560419"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="8ddf4-102">如何：使用 RectangleGeometry 定義矩形</span><span class="sxs-lookup"><span data-stu-id="8ddf4-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="8ddf4-103">這個範例說明如何使用<xref:System.Windows.Media.RectangleGeometry>來描述矩形的類別。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ddf4-104">範例</span><span class="sxs-lookup"><span data-stu-id="8ddf4-104">Example</span></span>  
 <span data-ttu-id="8ddf4-105">下列範例示範如何建立及呈現<xref:System.Windows.Media.RectangleGeometry>。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="8ddf4-106">所定義的相對位置和矩形的維度<xref:System.Windows.Rect>結構。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="8ddf4-107">相對的位置是`50,50`和高度和寬度都`25`建立正方形。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="8ddf4-108">矩形的內部繪製與<xref:System.Windows.Media.Brushes.LemonChiffon%2A>筆刷和控制項外框繪製與<xref:System.Windows.Media.Brushes.Black%2A>筆觸的粗細`1`。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="8ddf4-109">![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="8ddf4-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="8ddf4-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="8ddf4-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="8ddf4-111">雖然這個範例使用<xref:System.Windows.Shapes.Path>項目來呈現<xref:System.Windows.Media.RectangleGeometry>，有許多其他的方式使用<xref:System.Windows.Media.RectangleGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="8ddf4-112">例如，<xref:System.Windows.Media.RectangleGeometry>可以用來指定<xref:System.Windows.UIElement.Clip%2A>的<xref:System.Windows.UIElement>或<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>的<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="8ddf4-113">其他簡單的幾何類別包含<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="8ddf4-114">這些幾何，以及更複雜的也可以建立使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。</span><span class="sxs-lookup"><span data-stu-id="8ddf4-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddf4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ddf4-115">See Also</span></span>  
 [<span data-ttu-id="8ddf4-116">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="8ddf4-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="8ddf4-117">建立複合圖案</span><span class="sxs-lookup"><span data-stu-id="8ddf4-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="8ddf4-118">使用 PathGeometry 建立圖案</span><span class="sxs-lookup"><span data-stu-id="8ddf4-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
