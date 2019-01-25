---
title: HOW TO：建立 GeometryDrawing
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: c3312802b4a623afc10b620dbe2159d2c52a41a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646223"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="99247-102">HOW TO：建立 GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="99247-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="99247-103">此範例示範如何建立並顯示<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="99247-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="99247-104">A<xref:System.Windows.Media.GeometryDrawing>可讓您建立與填滿外框的圖形建立關聯<xref:System.Windows.Media.Pen>並<xref:System.Windows.Media.Brush>使用<xref:System.Windows.Media.Geometry>。</span><span class="sxs-lookup"><span data-stu-id="99247-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="99247-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A>描述圖形的結構<xref:System.Windows.Media.GeometryDrawing.Brush%2A>描述圖案的填滿，而<xref:System.Windows.Media.GeometryDrawing.Pen%2A>說明圖形外框。</span><span class="sxs-lookup"><span data-stu-id="99247-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99247-106">範例</span><span class="sxs-lookup"><span data-stu-id="99247-106">Example</span></span>  
 <span data-ttu-id="99247-107">下列範例會使用<xref:System.Windows.Media.GeometryDrawing>來轉譯圖形。</span><span class="sxs-lookup"><span data-stu-id="99247-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="99247-108">所描述的圖形<xref:System.Windows.Media.GeometryGroup>並將兩個<xref:System.Windows.Media.EllipseGeometry>物件。</span><span class="sxs-lookup"><span data-stu-id="99247-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="99247-109">用於繪製圖形的內部<xref:System.Windows.Media.LinearGradientBrush>，以繪製其外框<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>。</span><span class="sxs-lookup"><span data-stu-id="99247-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="99247-110"><xref:System.Windows.Media.GeometryDrawing>會使用顯示<xref:System.Windows.Media.ImageDrawing>和<xref:System.Windows.Controls.Image>項目。</span><span class="sxs-lookup"><span data-stu-id="99247-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="99247-111">下圖顯示產生<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="99247-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="99247-112">![兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="99247-112">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="99247-113">若要建立更複雜的繪圖，您可以將多個繪圖物件合併成單一複合繪圖使用<xref:System.Windows.Media.DrawingGroup>。</span><span class="sxs-lookup"><span data-stu-id="99247-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99247-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99247-114">See also</span></span>
- <xref:System.Windows.Media.DrawingGroup>
- [<span data-ttu-id="99247-115">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="99247-115">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="99247-116">幾何概觀</span><span class="sxs-lookup"><span data-stu-id="99247-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="99247-117">建立複合圖形</span><span class="sxs-lookup"><span data-stu-id="99247-117">Create a Composite Drawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
