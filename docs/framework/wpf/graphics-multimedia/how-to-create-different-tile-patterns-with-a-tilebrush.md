---
title: "如何：使用 TileBrush 建立不同的並排顯示模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646ce5142875c95c0b1ca19643790f73f7eb83e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="7ea5c-102">如何：使用 TileBrush 建立不同的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="7ea5c-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="7ea5c-103">這個範例示範如何使用<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.TileBrush>建立模式。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="7ea5c-104"><xref:System.Windows.Media.TileBrush.TileMode%2A>屬性可讓您指定如何內容的<xref:System.Windows.Media.TileBrush>重複，也就是，並排顯示，以填滿輸出區域。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="7ea5c-105">若要建立的模式，您將設定<xref:System.Windows.Media.TileBrush.TileMode%2A>至<xref:System.Windows.Media.TileMode.Tile>， <xref:System.Windows.Media.TileMode.FlipX>， <xref:System.Windows.Media.TileMode.FlipY>，或<xref:System.Windows.Media.TileMode.FlipXY>。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="7ea5c-106">您也必須設定<xref:System.Windows.Media.TileBrush.Viewport%2A>的<xref:System.Windows.Media.TileBrush>使其小於您所繪製; 區域否則單一磚就是產生，而不論其<xref:System.Windows.Media.TileBrush.TileMode%2A>您使用的設定。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ea5c-107">範例</span><span class="sxs-lookup"><span data-stu-id="7ea5c-107">Example</span></span>  
 <span data-ttu-id="7ea5c-108">下列範例會建立五個<xref:System.Windows.Media.DrawingBrush>物件資訊，請提供每個不同<xref:System.Windows.Media.TileBrush.TileMode%2A>設定，然後使用它們來繪製五個矩形。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="7ea5c-109">雖然這個範例會使用<xref:System.Windows.Media.DrawingBrush>類別來示範<xref:System.Windows.Media.TileBrush.TileMode%2A>行為，<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性即會相同適用於所有<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.VisualBrush>，和<xref:System.Windows.Media.DrawingBrush>。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="7ea5c-110">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="7ea5c-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="7ea5c-111">![TileBrush 並排顯示範例輸出](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="7ea5c-111">![TileBrush tiling example output](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="7ea5c-112">利用 TileMode 屬性建立的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="7ea5c-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="7ea5c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ea5c-113">See Also</span></span>  
 [<span data-ttu-id="7ea5c-114">設定 TileBrush 的並排顯示大小</span><span class="sxs-lookup"><span data-stu-id="7ea5c-114">Set the Tile Size for a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [<span data-ttu-id="7ea5c-115">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="7ea5c-115">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
