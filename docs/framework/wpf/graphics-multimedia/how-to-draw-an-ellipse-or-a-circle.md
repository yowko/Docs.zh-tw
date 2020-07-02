---
title: 如何：繪製橢圓形或圓形
description: 瞭解如何在 Windows Presentation Foundation （WPF）中，使用外框粗細和內部色彩的選項繪製橢圓形或圓形。
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853558"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="51cbe-103">如何：繪製橢圓形或圓形</span><span class="sxs-lookup"><span data-stu-id="51cbe-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="51cbe-104">這個範例示範如何使用元素繪製橢圓形和圓形 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="51cbe-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="51cbe-105">若要繪製橢圓形，請建立 <xref:System.Windows.Shapes.Ellipse> 元素，並指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 。</span><span class="sxs-lookup"><span data-stu-id="51cbe-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="51cbe-106">使用其 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性來指定 <xref:System.Windows.Media.Brush> 用來繪製橢圓形內部的。</span><span class="sxs-lookup"><span data-stu-id="51cbe-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="51cbe-107">使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 屬性來指定 <xref:System.Windows.Media.Brush> 用來繪製橢圓形外框的。</span><span class="sxs-lookup"><span data-stu-id="51cbe-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="51cbe-108"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性會指定橢圓形外框的粗細。</span><span class="sxs-lookup"><span data-stu-id="51cbe-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="51cbe-109">若要繪製圓形，請讓 <xref:System.Windows.FrameworkElement.Width%2A> 元素的和彼此 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> 相等。</span><span class="sxs-lookup"><span data-stu-id="51cbe-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="51cbe-110">下列範例會在中繪製四個 <xref:System.Windows.Shapes.Ellipse> 元素 <xref:System.Windows.Controls.Canvas> 。</span><span class="sxs-lookup"><span data-stu-id="51cbe-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cbe-111">範例</span><span class="sxs-lookup"><span data-stu-id="51cbe-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="51cbe-112">雖然此範例使用 <xref:System.Windows.Controls.Canvas> 來包含省略號，但是您可以使用橢圓形元素（以及所有其他圖形元素）搭配任何 <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> 支援非文字內容的或。</span><span class="sxs-lookup"><span data-stu-id="51cbe-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="51cbe-113">這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="51cbe-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51cbe-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51cbe-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="51cbe-115">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="51cbe-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
