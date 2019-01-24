---
title: HOW TO：繪製橢圓形或圓形
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: 7aac743b0cd2119107e48493b3ee9563b81b391d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689113"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="94808-102">HOW TO：繪製橢圓形或圓形</span><span class="sxs-lookup"><span data-stu-id="94808-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="94808-103">此範例示範如何使用繪製橢圓形和圓形<xref:System.Windows.Shapes.Ellipse>項目。</span><span class="sxs-lookup"><span data-stu-id="94808-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="94808-104">若要繪製橢圓形，建立<xref:System.Windows.Shapes.Ellipse>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="94808-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="94808-105">使用其<xref:System.Windows.Shapes.Shape.Fill%2A>屬性來指定<xref:System.Windows.Media.Brush>，用來繪製橢圓形內部。</span><span class="sxs-lookup"><span data-stu-id="94808-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="94808-106">使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>屬性來指定<xref:System.Windows.Media.Brush>，用來繪製外框的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="94808-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="94808-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性指定的橢圓形外框粗細。</span><span class="sxs-lookup"><span data-stu-id="94808-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="94808-108">若要繪製圓形，請<xref:System.Windows.FrameworkElement.Width%2A>並<xref:System.Windows.FrameworkElement.Height%2A>的<xref:System.Windows.Shapes.Ellipse>彼此相等的項目。</span><span class="sxs-lookup"><span data-stu-id="94808-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="94808-109">下列範例會繪製四<xref:System.Windows.Shapes.Ellipse>內的項目<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="94808-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94808-110">範例</span><span class="sxs-lookup"><span data-stu-id="94808-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="94808-111">雖然此範例會使用<xref:System.Windows.Controls.Canvas>包含省略符號，您可以使用 ellipse 項目 （和其他圖形元素） 的任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="94808-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="94808-112">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="94808-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94808-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94808-113">See also</span></span>
- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="94808-114">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="94808-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
