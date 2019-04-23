---
title: HOW TO：使用聚合線條元素繪製聚合線條
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 4f55ecc206be0ef4947923047e796c36131c70ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114842"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="bca3f-102">HOW TO：使用聚合線條元素繪製聚合線條</span><span class="sxs-lookup"><span data-stu-id="bca3f-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="bca3f-103">此範例示範如何繪製聚合線，也就是一系列連接的直線，使用<xref:System.Windows.Shapes.Polyline>項目。</span><span class="sxs-lookup"><span data-stu-id="bca3f-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="bca3f-104">若要繪製聚合線，請建立<xref:System.Windows.Shapes.Polyline>項目，並使用其<xref:System.Windows.Shapes.Polyline.Points%2A>屬性來指定圖形的頂點。</span><span class="sxs-lookup"><span data-stu-id="bca3f-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="bca3f-105">最後，使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>來描述聚合線條的屬性說明，因為沒有筆觸線條是不可見。</span><span class="sxs-lookup"><span data-stu-id="bca3f-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bca3f-106">因為<xref:System.Windows.Shapes.Polyline>項目不是封閉的形狀，<xref:System.Windows.Shapes.Shape.Fill%2A>屬性有任何作用，即使您刻意關閉圖形外框。</span><span class="sxs-lookup"><span data-stu-id="bca3f-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="bca3f-107">若要建立一個封閉的形狀，與<xref:System.Windows.Shapes.Shape.Fill%2A>，使用<xref:System.Windows.Shapes.Polygon>項目。</span><span class="sxs-lookup"><span data-stu-id="bca3f-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="bca3f-108">下列範例會繪製兩個<xref:System.Windows.Shapes.Polyline>內的項目<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="bca3f-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca3f-109">範例</span><span class="sxs-lookup"><span data-stu-id="bca3f-109">Example</span></span>  
 <span data-ttu-id="bca3f-110">在  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，有效的語法，點是以逗號分隔的 x 和 y 座標組的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="bca3f-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="bca3f-111">雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含多線條，您可以使用 polyline 項目 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="bca3f-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="bca3f-112">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="bca3f-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca3f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca3f-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="bca3f-114">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="bca3f-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="bca3f-115">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="bca3f-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
