---
title: 如何：繪製矩形
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452931"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="d1bb8-102">如何：繪製矩形</span><span class="sxs-lookup"><span data-stu-id="d1bb8-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="d1bb8-103">這個範例會示範如何使用 <xref:System.Windows.Shapes.Rectangle> 元素繪製矩形。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="d1bb8-104">若要繪製矩形，請建立 <xref:System.Windows.Shapes.Rectangle> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="d1bb8-105">若要在矩形內繪製，請設定其 <xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="d1bb8-106">若要為矩形提供外框，請使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 並 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="d1bb8-107">若要提供矩形圓角，請指定選擇性的 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>，並 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="d1bb8-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> 和 <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> 屬性會設定橢圓形的 X 軸和 y 軸半徑，用來舍入矩形的圓角。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="d1bb8-109">在下列範例中，會在 <xref:System.Windows.Controls.Canvas>中繪製兩個 <xref:System.Windows.Shapes.Rectangle> 元素。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="d1bb8-110">第一個矩形具有 <xref:System.Windows.Media.Brushes.Blue%2A> 內部。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="d1bb8-111">第二個矩形具有 <xref:System.Windows.Media.Brushes.Blue%2A> 內部、<xref:System.Windows.Media.Brushes.Black%2A> 外框和圓角。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bb8-112">範例</span><span class="sxs-lookup"><span data-stu-id="d1bb8-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="d1bb8-113">雖然此範例使用包含矩形的 <xref:System.Windows.Controls.Canvas>，但您可以使用矩形元素（以及所有其他圖形元素）搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="d1bb8-114">事實上，矩形特別適合用來提供部分 <xref:System.Windows.Controls.Grid> 面板的背景。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="d1bb8-115">如需範例，請參閱[資料表總覽](../advanced/table-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="d1bb8-116">這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="d1bb8-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bb8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1bb8-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="d1bb8-118">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="d1bb8-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="d1bb8-119">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="d1bb8-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="d1bb8-120">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="d1bb8-120">Table Overview</span></span>](../advanced/table-overview.md)
