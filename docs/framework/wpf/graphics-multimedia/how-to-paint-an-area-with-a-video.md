---
title: HOW TO：繪製含有視訊的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: 0756a9e87840648b55ecad4b3f1ce6e0e5452eb7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363289"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="27b88-102">HOW TO：繪製含有視訊的區域</span><span class="sxs-lookup"><span data-stu-id="27b88-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="27b88-103">此範例示範如何使用媒體繪製區域。</span><span class="sxs-lookup"><span data-stu-id="27b88-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="27b88-104">若要使用媒體繪製區域的一個方式是使用<xref:System.Windows.Controls.MediaElement>搭配<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="27b88-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="27b88-105">使用 <xref:System.Windows.Controls.MediaElement>載入及播放媒體，並接著使用它來設定<xref:System.Windows.Media.VisualBrush.Visual%2A>屬性<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="27b88-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="27b88-106">您可以接著使用<xref:System.Windows.Media.VisualBrush>來繪製區域載入的媒體。</span><span class="sxs-lookup"><span data-stu-id="27b88-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27b88-107">範例</span><span class="sxs-lookup"><span data-stu-id="27b88-107">Example</span></span>  
 <span data-ttu-id="27b88-108">下列範例會使用<xref:System.Windows.Controls.MediaElement>並<xref:System.Windows.Media.VisualBrush>繪製<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>與 video 搭配運作的控制項。</span><span class="sxs-lookup"><span data-stu-id="27b88-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="27b88-109">此範例會設定<xref:System.Windows.Controls.MediaElement.IsMuted%2A>的屬性<xref:System.Windows.Controls.MediaElement>到`true`以便所不產生的任何聲音。</span><span class="sxs-lookup"><span data-stu-id="27b88-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="27b88-110">範例</span><span class="sxs-lookup"><span data-stu-id="27b88-110">Example</span></span>  
 <span data-ttu-id="27b88-111">因為<xref:System.Windows.Media.VisualBrush>繼承自<xref:System.Windows.Media.TileBrush>類別，它會提供數個並排顯示模式。</span><span class="sxs-lookup"><span data-stu-id="27b88-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="27b88-112">藉由設定<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.VisualBrush>要<xref:System.Windows.Media.TileMode.Tile>並且將其<xref:System.Windows.Media.TileBrush.Viewport%2A>屬性的值小於您所繪製的區域，您可以建立並排顯示的圖樣。</span><span class="sxs-lookup"><span data-stu-id="27b88-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="27b88-113">下列範例等同於上述範例中，不同之處在於<xref:System.Windows.Media.VisualBrush>會產生從視訊的模式。</span><span class="sxs-lookup"><span data-stu-id="27b88-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="27b88-114">如需如何將內容檔案，例如媒體檔案新增至您的應用程式，請參閱[WPF 應用程式資源、 內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)。</span><span class="sxs-lookup"><span data-stu-id="27b88-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="27b88-115">當您新增的媒體檔案時，您必須將它新增為內容檔案，而非資源檔。</span><span class="sxs-lookup"><span data-stu-id="27b88-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b88-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27b88-116">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="27b88-117">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="27b88-117">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="27b88-118">TileBrush 概觀</span><span class="sxs-lookup"><span data-stu-id="27b88-118">TileBrush Overview</span></span>](tilebrush-overview.md)
- [<span data-ttu-id="27b88-119">多媒體概觀</span><span class="sxs-lookup"><span data-stu-id="27b88-119">Multimedia Overview</span></span>](multimedia-overview.md)
