---
title: "如何：繪製矩形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c163897af27c9b34c8cd87a3b197047f86d21ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="fd305-102">如何：繪製矩形</span><span class="sxs-lookup"><span data-stu-id="fd305-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="fd305-103">這個範例示範如何使用繪製矩形<xref:System.Windows.Shapes.Rectangle>項目。</span><span class="sxs-lookup"><span data-stu-id="fd305-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="fd305-104">若要繪製矩形，建立<xref:System.Windows.Shapes.Rectangle>項目，並指定其<xref:System.Windows.FrameworkElement.Width%2A>和<xref:System.Windows.FrameworkElement.Height%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd305-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="fd305-105">若要繪製的矩形內部，將其<xref:System.Windows.Shapes.Shape.Fill%2A>。</span><span class="sxs-lookup"><span data-stu-id="fd305-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="fd305-106">若要讓矩形外框，使用其<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fd305-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="fd305-107">若要將矩形的圓角中，指定選擇性<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="fd305-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="fd305-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A>和<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>設定 x 軸和 y 軸半徑，用來決定矩形的圓橢圓形的屬性。</span><span class="sxs-lookup"><span data-stu-id="fd305-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="fd305-109">在下列範例中，兩個<xref:System.Windows.Shapes.Rectangle>項目會繪製<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="fd305-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="fd305-110">第一個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部。</span><span class="sxs-lookup"><span data-stu-id="fd305-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="fd305-111">第二個矩形<xref:System.Windows.Media.Brushes.Blue%2A>內部，<xref:System.Windows.Media.Brushes.Black%2A>大綱，以及圓的角。</span><span class="sxs-lookup"><span data-stu-id="fd305-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd305-112">範例</span><span class="sxs-lookup"><span data-stu-id="fd305-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="fd305-113">雖然這個範例會使用<xref:System.Windows.Controls.Canvas>包含矩形，您可以使用矩形項目 （以及所有其他圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="fd305-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="fd305-114">事實上，矩形會特別有用的部分提供背景<xref:System.Windows.Controls.Grid>面板。</span><span class="sxs-lookup"><span data-stu-id="fd305-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="fd305-115">如需範例，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fd305-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="fd305-116">這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="fd305-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd305-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd305-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="fd305-118">圖形項目範例</span><span class="sxs-lookup"><span data-stu-id="fd305-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="fd305-119">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="fd305-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="fd305-120">資料表概觀</span><span class="sxs-lookup"><span data-stu-id="fd305-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
