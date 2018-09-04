---
title: 如何：繪製矩形
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 5f65bd11976817fe3f4d3e5d016f820a249769c3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506150"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="97034-102">如何：繪製矩形</span><span class="sxs-lookup"><span data-stu-id="97034-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="97034-103">此範例示範如何藉由繪製矩形<xref:System.Windows.Shapes.Rectangle>項目。</span><span class="sxs-lookup"><span data-stu-id="97034-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="97034-104">若要繪製矩形，建立<xref:System.Windows.Shapes.Rectangle>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="97034-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="97034-105">若要繪製的矩形內部，請將其<xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="97034-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="97034-106">若要讓矩形外框，使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="97034-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="97034-107">提供給矩形的圓角中，指定選擇性<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="97034-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="97034-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>設定 x 軸和 y 軸半徑，用來將矩形的圓角的省略符號的屬性。</span><span class="sxs-lookup"><span data-stu-id="97034-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="97034-109">在下列範例中，兩個<xref:System.Windows.Shapes.Rectangle>項目會繪製<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="97034-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="97034-110">第一個矩形具有<xref:System.Windows.Media.Brushes.Blue%2A>內部。</span><span class="sxs-lookup"><span data-stu-id="97034-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="97034-111">第二個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部，<xref:System.Windows.Media.Brushes.Black%2A>大綱和圓的角。</span><span class="sxs-lookup"><span data-stu-id="97034-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97034-112">範例</span><span class="sxs-lookup"><span data-stu-id="97034-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="97034-113">雖然此範例會使用<xref:System.Windows.Controls.Canvas>要包含的矩形，您可以使用矩形元素 （和其他圖形元素） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="97034-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="97034-114">事實上，矩形會特別有用的部分位置提供背景<xref:System.Windows.Controls.Grid>面板。</span><span class="sxs-lookup"><span data-stu-id="97034-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="97034-115">如需範例，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="97034-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="97034-116">這個範例屬於較大型的範例;如需完整的範例，請參閱[圖形元素範例](https://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="97034-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97034-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97034-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="97034-118">圖形元素範例</span><span class="sxs-lookup"><span data-stu-id="97034-118">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="97034-119">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="97034-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="97034-120">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="97034-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
