---
title: 如何：繪製橢圓形或圓形
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452918"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="ae46d-102">如何：繪製橢圓形或圓形</span><span class="sxs-lookup"><span data-stu-id="ae46d-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="ae46d-103">這個範例示範如何使用 <xref:System.Windows.Shapes.Ellipse> 元素繪製橢圓形和圓形。</span><span class="sxs-lookup"><span data-stu-id="ae46d-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="ae46d-104">若要繪製橢圓形，請建立 <xref:System.Windows.Shapes.Ellipse> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="ae46d-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="ae46d-105">使用其 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性來指定用來繪製橢圓形內部的 <xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="ae46d-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="ae46d-106">使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性來指定用來繪製橢圓形外框的 <xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="ae46d-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="ae46d-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> 屬性會指定橢圓形外框的粗細。</span><span class="sxs-lookup"><span data-stu-id="ae46d-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="ae46d-108">若要繪製圓形，請將 <xref:System.Windows.Shapes.Ellipse> 元素的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 相等。</span><span class="sxs-lookup"><span data-stu-id="ae46d-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="ae46d-109">下列範例會在 <xref:System.Windows.Controls.Canvas>中繪製四個 <xref:System.Windows.Shapes.Ellipse> 元素。</span><span class="sxs-lookup"><span data-stu-id="ae46d-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae46d-110">範例</span><span class="sxs-lookup"><span data-stu-id="ae46d-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="ae46d-111">雖然此範例使用 <xref:System.Windows.Controls.Canvas> 來包含省略號，但是您可以使用橢圓形元素（以及所有其他圖形元素）搭配任何支援非文字內容的 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.Control>。</span><span class="sxs-lookup"><span data-stu-id="ae46d-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="ae46d-112">這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="ae46d-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae46d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae46d-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="ae46d-114">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="ae46d-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
