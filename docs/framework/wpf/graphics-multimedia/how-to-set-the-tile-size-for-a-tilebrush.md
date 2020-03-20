---
title: 操作說明：設定 TileBrush 的並排顯示大小
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186841"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="d0961-102">操作說明：設定 TileBrush 的並排顯示大小</span><span class="sxs-lookup"><span data-stu-id="d0961-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="d0961-103">此示例演示如何設置 的<xref:System.Windows.Media.TileBrush>磁貼大小。</span><span class="sxs-lookup"><span data-stu-id="d0961-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="d0961-104">預設情況下，生成<xref:System.Windows.Media.TileBrush>一個完全填充要繪製的區域的磁貼。</span><span class="sxs-lookup"><span data-stu-id="d0961-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="d0961-105">可以通過設置 和<xref:System.Windows.Media.TileBrush.Viewport%2A><xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性來重寫此行為。</span><span class="sxs-lookup"><span data-stu-id="d0961-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="d0961-106">屬性<xref:System.Windows.Media.TileBrush.Viewport%2A>指定 的<xref:System.Windows.Media.TileBrush>磁貼大小。</span><span class="sxs-lookup"><span data-stu-id="d0961-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="d0961-107">預設情況下，<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值與要繪製的區域的大小相關。</span><span class="sxs-lookup"><span data-stu-id="d0961-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="d0961-108">要使<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性指定絕對磁貼大小，請將<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性設置為<xref:System.Windows.Media.BrushMappingMode.Absolute>。</span><span class="sxs-lookup"><span data-stu-id="d0961-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="d0961-109">範例</span><span class="sxs-lookup"><span data-stu-id="d0961-109">Example</span></span>

<span data-ttu-id="d0961-110">下面的示例使用<xref:System.Windows.Media.ImageBrush>、 的類型<xref:System.Windows.Media.TileBrush>，使用切片繪製矩形。</span><span class="sxs-lookup"><span data-stu-id="d0961-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="d0961-111">該示例將每個磁貼按輸出區域（矩形）的 50% 設置為 50%。</span><span class="sxs-lookup"><span data-stu-id="d0961-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="d0961-112">因此，矩形會以影像的四個投影繪製。</span><span class="sxs-lookup"><span data-stu-id="d0961-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="d0961-113">下圖顯示了示例生成的輸出：</span><span class="sxs-lookup"><span data-stu-id="d0961-113">The following illustration shows the output that the example produces:</span></span>

![一個矩形，有四個櫻桃，用影像筆刷演示平鋪。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="d0961-115">下一個示例創建<xref:System.Windows.Media.ImageBrush>一個<xref:System.Windows.Media.TileBrush.Viewport%2A> `0,0,25,25` ，設置<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>其<xref:System.Windows.Media.BrushMappingMode.Absolute>和 其 到 ，並使用它來繪製另一個矩形。</span><span class="sxs-lookup"><span data-stu-id="d0961-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="d0961-116">因此，筆刷會產生寬度為 25 個像素，且高度為 25 個像素的並排顯示。</span><span class="sxs-lookup"><span data-stu-id="d0961-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="d0961-117">下圖顯示了示例生成的輸出：</span><span class="sxs-lookup"><span data-stu-id="d0961-117">The following illustration shows the output that the example produces:</span></span>

![一個長方形，有四十八個櫻桃，展示一個瓷磚刷與視口。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="d0961-119">上述範例是某個完整範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="d0961-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="d0961-120">有關完整示例，請參閱[影像筆刷示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)。</span><span class="sxs-lookup"><span data-stu-id="d0961-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="d0961-121">儘管此示例使用 類<xref:System.Windows.Media.ImageBrush>，<xref:System.Windows.Media.TileBrush.Viewport%2A>但 和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>屬性對於其他<xref:System.Windows.Media.TileBrush>物件（即 和<xref:System.Windows.Media.DrawingBrush>） 的行為相同。 <xref:System.Windows.Media.VisualBrush></span><span class="sxs-lookup"><span data-stu-id="d0961-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="d0961-122">有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件的詳細資訊，請參閱[使用圖像、繪圖和視覺物件進行繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="d0961-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0961-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0961-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="d0961-124">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="d0961-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="d0961-125">使用 TileBrush 建立不同的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="d0961-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
