---
title: 如何：繪製線條
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452944"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="f915b-102">如何：繪製線條</span><span class="sxs-lookup"><span data-stu-id="f915b-102">How to: Draw a Line</span></span>
<span data-ttu-id="f915b-103">這個範例會示範如何使用 <xref:System.Windows.Shapes.Line> 元素繪製線條。</span><span class="sxs-lookup"><span data-stu-id="f915b-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="f915b-104">若要繪製線條，請建立 <xref:System.Windows.Shapes.Line> 元素。</span><span class="sxs-lookup"><span data-stu-id="f915b-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="f915b-105">使用其 <xref:System.Windows.Shapes.Line.X1%2A> 和 <xref:System.Windows.Shapes.Line.Y1%2A> 屬性來設定其起始點;和會使用其 <xref:System.Windows.Shapes.Line.X2%2A> 和 <xref:System.Windows.Shapes.Line.Y2%2A> 屬性來設定其結束點。</span><span class="sxs-lookup"><span data-stu-id="f915b-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="f915b-106">最後，設定它的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>，因為不會隱藏沒有筆觸的線條。</span><span class="sxs-lookup"><span data-stu-id="f915b-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="f915b-107">設定線條的 <xref:System.Windows.Shapes.Shape.Fill%2A> 專案不會有任何作用，因為線條沒有內部。</span><span class="sxs-lookup"><span data-stu-id="f915b-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="f915b-108">下列範例會在 <xref:System.Windows.Controls.Canvas> 元素內繪製三行。</span><span class="sxs-lookup"><span data-stu-id="f915b-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f915b-109">範例</span><span class="sxs-lookup"><span data-stu-id="f915b-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="f915b-110">這個範例是較大範例的一部分;如需完整範例，請參閱[圖形元素範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="f915b-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f915b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f915b-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="f915b-112">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="f915b-112">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
