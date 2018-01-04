---
title: "操作說明：設定 TileBrush 的並排顯示大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e9b746fe66635054dbd35463f727d28a8abd3d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="93161-102">操作說明：設定 TileBrush 的並排顯示大小</span><span class="sxs-lookup"><span data-stu-id="93161-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="93161-103">這個範例示範如何設定的磚大小<xref:System.Windows.Media.TileBrush>。</span><span class="sxs-lookup"><span data-stu-id="93161-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="93161-104">根據預設，<xref:System.Windows.Media.TileBrush>會產生單一的磚，完全填滿您所繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="93161-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="93161-105">您可以藉由設定覆寫這個行為<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="93161-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="93161-106"><xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定的圖格大小<xref:System.Windows.Media.TileBrush>。</span><span class="sxs-lookup"><span data-stu-id="93161-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="93161-107">根據預設，值<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性是相對於所繪製的區域大小。</span><span class="sxs-lookup"><span data-stu-id="93161-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="93161-108">若要讓<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定為絕對的圖格的大小，設定<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性<xref:System.Windows.Media.BrushMappingMode.Absolute>。</span><span class="sxs-lookup"><span data-stu-id="93161-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93161-109">範例</span><span class="sxs-lookup"><span data-stu-id="93161-109">Example</span></span>  
 <span data-ttu-id="93161-110">下列範例會使用<xref:System.Windows.Media.ImageBrush>，一種<xref:System.Windows.Media.TileBrush>，若要繪製的圖格的矩形。</span><span class="sxs-lookup"><span data-stu-id="93161-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="93161-111">這個範例會將每個並排顯示設為輸出區域 (即矩形) 的 50% x 50%。</span><span class="sxs-lookup"><span data-stu-id="93161-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="93161-112">因此，矩形會以影像的四個投影繪製。</span><span class="sxs-lookup"><span data-stu-id="93161-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="93161-113">下圖顯示範例所產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="93161-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="93161-114">![使用影像筆刷進行並排顯示的範例](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="93161-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="93161-115">下一個範例會建立<xref:System.Windows.Media.ImageBrush>，設定其<xref:System.Windows.Media.TileBrush.Viewport%2A>至`0,0,25,25`及其<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>至<xref:System.Windows.Media.BrushMappingMode.Absolute>，並用來繪製另一個矩形。</span><span class="sxs-lookup"><span data-stu-id="93161-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="93161-116">因此，筆刷會產生寬度為 25 個像素，且高度為 25 個像素的並排顯示。</span><span class="sxs-lookup"><span data-stu-id="93161-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="93161-117">下圖顯示範例所產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="93161-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="93161-118">![檢視區為 0,0,0.25,0.25 的並排顯示 TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="93161-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="93161-119">上述範例是某個完整範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="93161-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="93161-120">如需完整範例，請參閱[ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)。</span><span class="sxs-lookup"><span data-stu-id="93161-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="93161-121">雖然這個範例會使用<xref:System.Windows.Media.ImageBrush>類別，<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性的行為即會相同其他<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="93161-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="93161-122">如需有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="93161-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93161-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="93161-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="93161-124">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="93161-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="93161-125">使用 TileBrush 建立不同的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="93161-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
