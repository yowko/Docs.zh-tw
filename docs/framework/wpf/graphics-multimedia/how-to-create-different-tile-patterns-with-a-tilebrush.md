---
title: HOW TO：使用 TileBrush 建立不同的拼貼模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227401"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="4c40e-102">HOW TO：使用 TileBrush 建立不同的拼貼模式</span><span class="sxs-lookup"><span data-stu-id="4c40e-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="4c40e-103">此範例示範如何使用<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.TileBrush>建立模式。</span><span class="sxs-lookup"><span data-stu-id="4c40e-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="4c40e-104"><xref:System.Windows.Media.TileBrush.TileMode%2A>屬性可讓您指定了內容<xref:System.Windows.Media.TileBrush>重複，也就是，並排顯示以填滿輸出區域。</span><span class="sxs-lookup"><span data-stu-id="4c40e-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="4c40e-105">若要建立的模式，您設定<xref:System.Windows.Media.TileBrush.TileMode%2A>要<xref:System.Windows.Media.TileMode.Tile>， <xref:System.Windows.Media.TileMode.FlipX>， <xref:System.Windows.Media.TileMode.FlipY>，或<xref:System.Windows.Media.TileMode.FlipXY>。</span><span class="sxs-lookup"><span data-stu-id="4c40e-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="4c40e-106">您也必須設定<xref:System.Windows.Media.TileBrush.Viewport%2A>的<xref:System.Windows.Media.TileBrush>，讓它小於您所繪製; 區域，否則為單一並排顯示已產生，而不論其<xref:System.Windows.Media.TileBrush.TileMode%2A>您所使用的設定。</span><span class="sxs-lookup"><span data-stu-id="4c40e-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c40e-107">範例</span><span class="sxs-lookup"><span data-stu-id="4c40e-107">Example</span></span>  
 <span data-ttu-id="4c40e-108">下列範例會建立五<xref:System.Windows.Media.DrawingBrush>物件，並讓他們每個不同<xref:System.Windows.Media.TileBrush.TileMode%2A>設定，並使用它們來繪製五個矩形。</span><span class="sxs-lookup"><span data-stu-id="4c40e-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="4c40e-109">雖然此範例使用<xref:System.Windows.Media.DrawingBrush>類別來示範<xref:System.Windows.Media.TileBrush.TileMode%2A>行為，<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性適用於所有的相同<xref:System.Windows.Media.TileBrush>物件，也就是如<xref:System.Windows.Media.ImageBrush>， <xref:System.Windows.Media.VisualBrush>，和<xref:System.Windows.Media.DrawingBrush>。</span><span class="sxs-lookup"><span data-stu-id="4c40e-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="4c40e-110">下圖顯示的是這個範例產生的輸出。</span><span class="sxs-lookup"><span data-stu-id="4c40e-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="4c40e-111">![TileBrush 並排顯示範例輸出](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="4c40e-111">![TileBrush tiling example output](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="4c40e-112">在建立時 TileMode 屬性的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="4c40e-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4c40e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c40e-113">See also</span></span>

- [<span data-ttu-id="4c40e-114">設定 TileBrush 的拼貼大小</span><span class="sxs-lookup"><span data-stu-id="4c40e-114">Set the Tile Size for a TileBrush</span></span>](how-to-set-the-tile-size-for-a-tilebrush.md)
- [<span data-ttu-id="4c40e-115">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="4c40e-115">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
