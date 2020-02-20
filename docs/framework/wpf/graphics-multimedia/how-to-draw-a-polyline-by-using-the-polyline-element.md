---
title: 如何：使用 Polyline 項目繪製聚合線
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452957"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="a517d-102">如何：使用 Polyline 項目繪製聚合線</span><span class="sxs-lookup"><span data-stu-id="a517d-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="a517d-103">這個範例會示範如何使用 <xref:System.Windows.Shapes.Polyline> 元素繪製一系列連接線條的「折線」。</span><span class="sxs-lookup"><span data-stu-id="a517d-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="a517d-104">若要繪製一個折線，請建立一個 <xref:System.Windows.Shapes.Polyline> 專案，並使用其 <xref:System.Windows.Shapes.Polyline.Points%2A> 屬性來指定圖形頂點。</span><span class="sxs-lookup"><span data-stu-id="a517d-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="a517d-105">最後，使用 [<xref:System.Windows.Shapes.Shape.Stroke%2A>] 和 [<xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性] 來描述 [折線外框]，因為不會顯示沒有筆觸的線條。</span><span class="sxs-lookup"><span data-stu-id="a517d-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a517d-106">因為 <xref:System.Windows.Shapes.Polyline> 元素不是封閉圖形，所以即使您故意關閉圖形大綱，<xref:System.Windows.Shapes.Shape.Fill%2A> 屬性也沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="a517d-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="a517d-107">若要建立具有 <xref:System.Windows.Shapes.Shape.Fill%2A>的封閉圖形，請使用 <xref:System.Windows.Shapes.Polygon> 元素。</span><span class="sxs-lookup"><span data-stu-id="a517d-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="a517d-108">下列範例會在 <xref:System.Windows.Controls.Canvas>內繪製兩個 <xref:System.Windows.Shapes.Polyline> 元素。</span><span class="sxs-lookup"><span data-stu-id="a517d-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a517d-109">範例</span><span class="sxs-lookup"><span data-stu-id="a517d-109">Example</span></span>  
 <span data-ttu-id="a517d-110">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，點的有效語法是以空格分隔的逗號分隔 x 和 y 座標配對清單。</span><span class="sxs-lookup"><span data-stu-id="a517d-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="a517d-111">雖然此範例會使用 <xref:System.Windows.Controls.Canvas> 來包含多線條，但您可以搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>，使用折線元素（以及所有其他圖形元素）。</span><span class="sxs-lookup"><span data-stu-id="a517d-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="a517d-112">這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="a517d-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a517d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a517d-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="a517d-114">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="a517d-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="a517d-115">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="a517d-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
