---
title: "如何：使用 Polyline 項目繪製聚合線"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fa8cafdaf7856e95129f648da1d4b4ccb2f54eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="1259b-102">如何：使用 Polyline 項目繪製聚合線</span><span class="sxs-lookup"><span data-stu-id="1259b-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="1259b-103">此範例顯示如何畫聚合線條，這是使用一系列連接的直線<xref:System.Windows.Shapes.Polyline>項目。</span><span class="sxs-lookup"><span data-stu-id="1259b-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="1259b-104">若要繪製的聚合線條，請建立<xref:System.Windows.Shapes.Polyline>項目，並使用其<xref:System.Windows.Shapes.Polyline.Points%2A>屬性可指定圖形頂點。</span><span class="sxs-lookup"><span data-stu-id="1259b-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="1259b-105">最後，使用<xref:System.Windows.Shapes.Shape.Stroke%2A>和<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>來描述聚合線條的內容大綱，因為沒有筆觸線條是不可見。</span><span class="sxs-lookup"><span data-stu-id="1259b-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1259b-106">因為<xref:System.Windows.Shapes.Polyline>元素不是封閉的圖形，<xref:System.Windows.Shapes.Shape.Fill%2A>屬性有任何作用，即使您刻意關閉圖形外框。</span><span class="sxs-lookup"><span data-stu-id="1259b-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="1259b-107">若要建立具有封閉的圖形<xref:System.Windows.Shapes.Shape.Fill%2A>，使用<xref:System.Windows.Shapes.Polygon>項目。</span><span class="sxs-lookup"><span data-stu-id="1259b-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="1259b-108">下列範例會繪製兩個<xref:System.Windows.Shapes.Polyline>內的項目<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="1259b-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1259b-109">範例</span><span class="sxs-lookup"><span data-stu-id="1259b-109">Example</span></span>  
 <span data-ttu-id="1259b-110">在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，點的有效語法是以空格分隔清單的逗號分隔 x 和 y 座標組。</span><span class="sxs-lookup"><span data-stu-id="1259b-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="1259b-111">雖然這個範例會使用<xref:System.Windows.Controls.Canvas>包含聚合線條，您可以使用聚合線條元素 （和其他所有圖形項目） 與任何<xref:System.Windows.Controls.Panel>或<xref:System.Windows.Controls.Control>支援非文字內容。</span><span class="sxs-lookup"><span data-stu-id="1259b-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="1259b-112">這個範例是較大範例的一部分如需完整範例，請參閱[圖形項目範例](http://go.microsoft.com/fwlink/?LinkID=160037)。</span><span class="sxs-lookup"><span data-stu-id="1259b-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1259b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1259b-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="1259b-114">圖形項目範例</span><span class="sxs-lookup"><span data-stu-id="1259b-114">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="1259b-115">WPF 中圖案和基本繪圖概觀</span><span class="sxs-lookup"><span data-stu-id="1259b-115">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
