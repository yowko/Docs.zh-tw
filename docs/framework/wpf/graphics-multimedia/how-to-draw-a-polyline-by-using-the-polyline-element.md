---
title: 作法：使用聚合線條元素繪製聚合線條
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934966"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="1ea9b-102">作法：使用聚合線條元素繪製聚合線條</span><span class="sxs-lookup"><span data-stu-id="1ea9b-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="1ea9b-103">這個範例示範如何使用<xref:System.Windows.Shapes.Polyline>專案, 繪製一系列連接線條的折線。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="1ea9b-104">若要繪製一條折線, <xref:System.Windows.Shapes.Polyline>請建立一個專案<xref:System.Windows.Shapes.Polyline.Points%2A> , 並使用其屬性來指定圖形頂點。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="1ea9b-105">最後, 使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性來描述聚合線條外框, 因為不會顯示沒有筆觸的線條。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ea9b-106">因為專案不是封閉圖形<xref:System.Windows.Shapes.Shape.Fill%2A> , 所以即使您故意關閉圖形大綱, 屬性也不會有任何作用。 <xref:System.Windows.Shapes.Polyline></span><span class="sxs-lookup"><span data-stu-id="1ea9b-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="1ea9b-107">若要使用來建立已關閉<xref:System.Windows.Shapes.Shape.Fill%2A>的圖形, <xref:System.Windows.Shapes.Polygon>請使用元素。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="1ea9b-108">下列範例會在<xref:System.Windows.Shapes.Polyline> <xref:System.Windows.Controls.Canvas>內繪製兩個元素。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ea9b-109">範例</span><span class="sxs-lookup"><span data-stu-id="1ea9b-109">Example</span></span>  
 <span data-ttu-id="1ea9b-110">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中, 點的有效語法是以空格分隔的逗號分隔 x 和 y 座標配對清單。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="1ea9b-111">雖然此範例使用<xref:System.Windows.Controls.Canvas>來包含多線條, 但您可以使用折線元素 (以及所有其他圖形元素) 搭配任何<xref:System.Windows.Controls.Panel>支援非<xref:System.Windows.Controls.Control>文字內容的或。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="1ea9b-112">這個範例是較大範例的一部分;如需完整範例, 請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="1ea9b-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea9b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea9b-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="1ea9b-114">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="1ea9b-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="1ea9b-115">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="1ea9b-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
