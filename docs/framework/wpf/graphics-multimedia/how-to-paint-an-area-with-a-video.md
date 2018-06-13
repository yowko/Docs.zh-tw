---
title: 如何：繪製含有視訊的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: d2ca0f8b70abf6e895ea275d2a47eb4a6dd4bfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560773"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="f7263-102">如何：繪製含有視訊的區域</span><span class="sxs-lookup"><span data-stu-id="f7263-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="f7263-103">這個範例示範如何使用媒體繪製區域。</span><span class="sxs-lookup"><span data-stu-id="f7263-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="f7263-104">若要使用媒體繪製區域的一種方式為使用<xref:System.Windows.Controls.MediaElement>搭配<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="f7263-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="f7263-105">使用<xref:System.Windows.Controls.MediaElement>載入並播放媒體，然後用它來設定<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="f7263-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="f7263-106">然後您可以使用<xref:System.Windows.Media.VisualBrush>繪製區域載入的媒體。</span><span class="sxs-lookup"><span data-stu-id="f7263-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7263-107">範例</span><span class="sxs-lookup"><span data-stu-id="f7263-107">Example</span></span>  
 <span data-ttu-id="f7263-108">下列範例會使用<xref:System.Windows.Controls.MediaElement>和<xref:System.Windows.Media.VisualBrush>來繪製<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>與視訊控制。</span><span class="sxs-lookup"><span data-stu-id="f7263-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="f7263-109">此範例會設定<xref:System.Windows.Controls.MediaElement.IsMuted%2A>屬性<xref:System.Windows.Controls.MediaElement>至`true`，讓它會產生任何聲音。</span><span class="sxs-lookup"><span data-stu-id="f7263-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="f7263-110">範例</span><span class="sxs-lookup"><span data-stu-id="f7263-110">Example</span></span>  
 <span data-ttu-id="f7263-111">因為<xref:System.Windows.Media.VisualBrush>繼承自<xref:System.Windows.Media.TileBrush>類別，它會提供數個並排顯示模式。</span><span class="sxs-lookup"><span data-stu-id="f7263-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="f7263-112">藉由設定<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.VisualBrush>至<xref:System.Windows.Media.TileMode.Tile>和設定其<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值小於您所繪製的區域，您可以建立的並排顯示的模式。</span><span class="sxs-lookup"><span data-stu-id="f7263-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="f7263-113">下列範例等同於上述範例中，不同處在於<xref:System.Windows.Media.VisualBrush>視訊從產生的模式。</span><span class="sxs-lookup"><span data-stu-id="f7263-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="f7263-114">如需如何將內容檔案，例如媒體檔案新增至您的應用程式，請參閱[WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="f7263-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="f7263-115">當您新增的媒體檔案時，您必須將它加入做為內容檔案，而非資源檔。</span><span class="sxs-lookup"><span data-stu-id="f7263-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7263-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7263-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="f7263-117">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="f7263-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="f7263-118">TileBrush 概觀</span><span class="sxs-lookup"><span data-stu-id="f7263-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="f7263-119">多媒體概觀</span><span class="sxs-lookup"><span data-stu-id="f7263-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
