---
title: HOW TO：使用繪圖繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010076"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="e0e9c-102">HOW TO：使用繪圖繪製區域</span><span class="sxs-lookup"><span data-stu-id="e0e9c-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="e0e9c-103">此範例顯示如何使用繪圖繪製區域。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="e0e9c-104">若要繪製含有繪圖區域，您使用<xref:System.Windows.Media.DrawingBrush>和一或多個<xref:System.Windows.Media.Drawing>物件。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="e0e9c-105">下列範例會使用<xref:System.Windows.Media.DrawingBrush>來繪製具有兩個橢圓形繪圖的物件。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e9c-106">範例</span><span class="sxs-lookup"><span data-stu-id="e0e9c-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="e0e9c-107">下圖顯示範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="e0e9c-108">![DrawingBrush 的輸出](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="e0e9c-108">![Output from a DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="e0e9c-109">(圖案的中心是白色的如中所述的理由[控制複合圖案的填色](how-to-control-the-fill-of-a-composite-shape.md)。)</span><span class="sxs-lookup"><span data-stu-id="e0e9c-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="e0e9c-110">藉由設定<xref:System.Windows.Media.DrawingBrush>物件的<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性，您可以建立重複的圖樣。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="e0e9c-111">下列範例繪製的物件具有從兩個橢圓形繪圖建立的圖樣。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="e0e9c-112">下圖顯示並排<xref:System.Windows.Media.DrawingBrush>輸出。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="e0e9c-113">![DrawingBrush 的並排顯示輸出](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="e0e9c-113">![Tiled output from a DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="e0e9c-114">如需有關繪圖筆刷的詳細資訊，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="e0e9c-115">如需詳細資訊<xref:System.Windows.Media.Drawing>物件，請參閱[繪圖物件概觀](drawing-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e9c-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](drawing-objects-overview.md).</span></span>
