---
title: "操作說明：設定 TileBrush 的水平和垂直對齊"
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
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dcbf4715c80f72178295c0b6abdc1272a055a8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a><span data-ttu-id="e56e1-102">操作說明：設定 TileBrush 的水平和垂直對齊</span><span class="sxs-lookup"><span data-stu-id="e56e1-102">How to: Set the Horizontal and Vertical Alignment of a TileBrush</span></span>
<span data-ttu-id="e56e1-103">本範例示範如何控制並排顯示中內容的水平和垂直對齊。</span><span class="sxs-lookup"><span data-stu-id="e56e1-103">This example shows how to control the horizontal and vertical alignment of content in a tile.</span></span> <span data-ttu-id="e56e1-104">若要控制的水平和垂直對齊方式<xref:System.Windows.Media.TileBrush>，使用其<xref:System.Windows.Media.TileBrush.AlignmentX%2A>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e56e1-104">To control the horizontal and vertical alignment of a <xref:System.Windows.Media.TileBrush>, use its <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties.</span></span>  
  
 <span data-ttu-id="e56e1-105"><xref:System.Windows.Media.TileBrush.AlignmentX%2A>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性<xref:System.Windows.Media.TileBrush>用其中一種下列情況為真時：</span><span class="sxs-lookup"><span data-stu-id="e56e1-105">The <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties of a <xref:System.Windows.Media.TileBrush> are used when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="e56e1-106"><xref:System.Windows.Media.TileBrush.Stretch%2A>屬性是<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>和<xref:System.Windows.Media.TileBrush.Viewbox%2A>和<xref:System.Windows.Media.TileBrush.Viewport%2A>有不同的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="e56e1-106">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property is <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill> and the <xref:System.Windows.Media.TileBrush.Viewbox%2A> and <xref:System.Windows.Media.TileBrush.Viewport%2A> have different aspect ratios.</span></span>  
  
-   <span data-ttu-id="e56e1-107"><xref:System.Windows.Media.TileBrush.Stretch%2A>屬性是<xref:System.Windows.Media.Stretch.None>和<xref:System.Windows.Media.TileBrush.Viewbox%2A>和<xref:System.Windows.Media.TileBrush.Viewport%2A>大小不同。</span><span class="sxs-lookup"><span data-stu-id="e56e1-107">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property is <xref:System.Windows.Media.Stretch.None> and the <xref:System.Windows.Media.TileBrush.Viewbox%2A> and <xref:System.Windows.Media.TileBrush.Viewport%2A> are different sizes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56e1-108">範例</span><span class="sxs-lookup"><span data-stu-id="e56e1-108">Example</span></span>  
 <span data-ttu-id="e56e1-109">下列範例將對齊的內容<xref:System.Windows.Media.DrawingBrush>，這是一種<xref:System.Windows.Media.TileBrush>，其磚的左上角。</span><span class="sxs-lookup"><span data-stu-id="e56e1-109">The following example aligns the content of a <xref:System.Windows.Media.DrawingBrush>, which is a type of <xref:System.Windows.Media.TileBrush>, to the upper-left corner of its tile.</span></span> <span data-ttu-id="e56e1-110">若要對齊的內容中，範例會設定<xref:System.Windows.Media.TileBrush.AlignmentX%2A>屬性<xref:System.Windows.Media.DrawingBrush>至<xref:System.Windows.Media.AlignmentX.Left>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性<xref:System.Windows.Media.AlignmentY.Top>。</span><span class="sxs-lookup"><span data-stu-id="e56e1-110">To align the content, the example sets the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property of the <xref:System.Windows.Media.DrawingBrush> to <xref:System.Windows.Media.AlignmentX.Left> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Top>.</span></span> <span data-ttu-id="e56e1-111">此範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="e56e1-111">This example produces the following output.</span></span>  
  
 <span data-ttu-id="e56e1-112">![TileBrush top &#45; 靠左的對齊](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")</span><span class="sxs-lookup"><span data-stu-id="e56e1-112">![A TileBrush with top&#45;left alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")</span></span>  
<span data-ttu-id="e56e1-113">內容對齊左上角的 TileBrush</span><span class="sxs-lookup"><span data-stu-id="e56e1-113">TileBrush with content aligned to the upper-left corner</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a><span data-ttu-id="e56e1-114">範例</span><span class="sxs-lookup"><span data-stu-id="e56e1-114">Example</span></span>  
 <span data-ttu-id="e56e1-115">下一個範例將對齊的內容<xref:System.Windows.Media.DrawingBrush>藉由設定其磚的右下角<xref:System.Windows.Media.TileBrush.AlignmentX%2A>屬性<xref:System.Windows.Media.AlignmentX.Right>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性<xref:System.Windows.Media.AlignmentY.Bottom>。</span><span class="sxs-lookup"><span data-stu-id="e56e1-115">The next example aligns the content of a <xref:System.Windows.Media.DrawingBrush> to the lower-right corner of its tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Right> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Bottom>.</span></span> <span data-ttu-id="e56e1-116">這個範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="e56e1-116">The example produces the following output.</span></span>  
  
 <span data-ttu-id="e56e1-117">![TileBrush 底部 &#45; 向右對齊](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")</span><span class="sxs-lookup"><span data-stu-id="e56e1-117">![A TileBrush with bottom&#45;right alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")</span></span>  
<span data-ttu-id="e56e1-118">內容對齊右下角的 TileBrush</span><span class="sxs-lookup"><span data-stu-id="e56e1-118">TileBrush with content aligned to the lower-right corner</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a><span data-ttu-id="e56e1-119">範例</span><span class="sxs-lookup"><span data-stu-id="e56e1-119">Example</span></span>  
 <span data-ttu-id="e56e1-120">下一個範例將對齊的內容<xref:System.Windows.Media.DrawingBrush>藉由設定其磚的左上角<xref:System.Windows.Media.TileBrush.AlignmentX%2A>屬性<xref:System.Windows.Media.AlignmentX.Left>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性<xref:System.Windows.Media.AlignmentY.Top>。</span><span class="sxs-lookup"><span data-stu-id="e56e1-120">The next example aligns the content of a <xref:System.Windows.Media.DrawingBrush> to the upper-left corner of its tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Left> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Top>.</span></span> <span data-ttu-id="e56e1-121">它也會設定<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.TileMode%2A>的<xref:System.Windows.Media.DrawingBrush>產生並排顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e56e1-121">It also sets the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> of the <xref:System.Windows.Media.DrawingBrush> to produce a tile pattern.</span></span> <span data-ttu-id="e56e1-122">這個範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="e56e1-122">The example produces the following output.</span></span>  
  
 <span data-ttu-id="e56e1-123">![Top &#45;的並排顯示的 TileBrush; 靠左的對齊](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")</span><span class="sxs-lookup"><span data-stu-id="e56e1-123">![A tiled TileBrush with top&#45;left alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")</span></span>  
<span data-ttu-id="e56e1-124">內容對齊基底並排中左上角的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="e56e1-124">Tile pattern with content aligned to upper-left in base tile</span></span>  
  
 <span data-ttu-id="e56e1-125">上圖將其中一個基底並排醒目提示，讓您能了解其內容的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="e56e1-125">The illustration highlights abase tile so that you can see how its content is aligned.</span></span> <span data-ttu-id="e56e1-126">請注意，<xref:System.Windows.Media.TileBrush.AlignmentX%2A>設定沒有任何作用，因為內容<xref:System.Windows.Media.DrawingBrush>完全填滿基底的並排顯示水平。</span><span class="sxs-lookup"><span data-stu-id="e56e1-126">Notice that the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> setting has no effect because the content of the <xref:System.Windows.Media.DrawingBrush> completely fills the base tile horizontally.</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a><span data-ttu-id="e56e1-127">範例</span><span class="sxs-lookup"><span data-stu-id="e56e1-127">Example</span></span>  
 <span data-ttu-id="e56e1-128">最後一個範例將對齊的並排顯示內容<xref:System.Windows.Media.DrawingBrush>藉由設定其基底磚右下<xref:System.Windows.Media.TileBrush.AlignmentX%2A>屬性<xref:System.Windows.Media.AlignmentX.Right>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>屬性<xref:System.Windows.Media.AlignmentY.Bottom>。</span><span class="sxs-lookup"><span data-stu-id="e56e1-128">The final example aligns the content of a tiled <xref:System.Windows.Media.DrawingBrush> to the lower-right of its base tile by setting the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> property to <xref:System.Windows.Media.AlignmentX.Right> and the <xref:System.Windows.Media.TileBrush.AlignmentY%2A> property to <xref:System.Windows.Media.AlignmentY.Bottom>.</span></span> <span data-ttu-id="e56e1-129">這個範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="e56e1-129">The example produces the following output.</span></span>  
  
 <span data-ttu-id="e56e1-130">![並排顯示 TileBrush 顯示加上下方 &#45; 向右對齊](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")</span><span class="sxs-lookup"><span data-stu-id="e56e1-130">![A tiled TileBrush with bottom&#45;right alignment](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")</span></span>  
<span data-ttu-id="e56e1-131">內容對齊基底並排中右下角的並排顯示模式</span><span class="sxs-lookup"><span data-stu-id="e56e1-131">Tile pattern with content aligned to lower-right in base tile</span></span>  
  
 <span data-ttu-id="e56e1-132">同樣地，<xref:System.Windows.Media.TileBrush.AlignmentX%2A>設定沒有任何作用，因為內容<xref:System.Windows.Media.DrawingBrush>完全填滿基底的並排顯示水平。</span><span class="sxs-lookup"><span data-stu-id="e56e1-132">Again, the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> setting has no effect because the content of the <xref:System.Windows.Media.DrawingBrush> completely fills the base tile horizontally.</span></span>  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 <span data-ttu-id="e56e1-133">範例會使用<xref:System.Windows.Media.DrawingBrush>物件來示範如何<xref:System.Windows.Media.TileBrush.AlignmentX%2A>和<xref:System.Windows.Media.TileBrush.AlignmentY%2A>可用屬性。</span><span class="sxs-lookup"><span data-stu-id="e56e1-133">The examples use <xref:System.Windows.Media.DrawingBrush> objects to demonstrate how the <xref:System.Windows.Media.TileBrush.AlignmentX%2A> and <xref:System.Windows.Media.TileBrush.AlignmentY%2A> properties are used.</span></span> <span data-ttu-id="e56e1-134">這些屬性的行為即會相同拼貼筆刷： <xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.ImageBrush>，和<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="e56e1-134">These properties behave identically for all the tile brushes: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="e56e1-135">如需拼貼筆刷的詳細資訊，請參閱[使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="e56e1-135">For more information about tile brushes, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56e1-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="e56e1-136">See Also</span></span>  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="e56e1-137">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="e56e1-137">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
