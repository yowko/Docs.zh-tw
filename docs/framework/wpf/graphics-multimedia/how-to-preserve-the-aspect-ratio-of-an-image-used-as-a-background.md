---
title: HOW TO：保留當做背景之影像的外觀比例
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: df5632aa3d3c7dbc2442cabe1f4db7a850a1bd54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353942"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="19677-102">HOW TO：保留當做背景之影像的外觀比例</span><span class="sxs-lookup"><span data-stu-id="19677-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="19677-103">此範例示範如何使用<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.ImageBrush>以維持影像的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="19677-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="19677-104">根據預設，當您使用<xref:System.Windows.Media.ImageBrush>繪製區域，其內容自動縮放以完全填滿輸出區域。</span><span class="sxs-lookup"><span data-stu-id="19677-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="19677-105">當輸出區域和影像的外觀比例不相同時，影像就會因為自動縮放而扭曲。</span><span class="sxs-lookup"><span data-stu-id="19677-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="19677-106">若要讓<xref:System.Windows.Media.ImageBrush>保留長寬比的映像，請將<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="19677-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19677-107">範例</span><span class="sxs-lookup"><span data-stu-id="19677-107">Example</span></span>  
 <span data-ttu-id="19677-108">下列範例會使用兩個<xref:System.Windows.Media.ImageBrush>物件來繪製兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="19677-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="19677-109">每個矩形是 300 乘 150 像素且各包含一個 300 乘 300 像素的影像。</span><span class="sxs-lookup"><span data-stu-id="19677-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="19677-110"><xref:System.Windows.Media.TileBrush.Stretch%2A>的第一個筆刷屬性設定為<xref:System.Windows.Media.Stretch.Uniform>，而<xref:System.Windows.Media.TileBrush.Stretch%2A>的第二個筆刷屬性設定為<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="19677-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="19677-111">下圖顯示具有的第一個筆刷的輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>。</span><span class="sxs-lookup"><span data-stu-id="19677-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="19677-112">![Stretch 屬性設定為 Uniform 的 ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="19677-112">![ImageBrush with Uniform stretching](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="19677-113">下圖顯示具有的第二個筆刷的輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="19677-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="19677-114">![Stretch 屬性設定為 UniformToFill 的 ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="19677-114">![ImageBrush with UniformToFill stretching](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="19677-115">請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性，其行為完全相同的另<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。</span><span class="sxs-lookup"><span data-stu-id="19677-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="19677-116">如需詳細資訊<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="19677-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="19677-117">另請注意，雖然<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性會顯示以指定如何<xref:System.Windows.Media.TileBrush>內容自動縮放以符合其輸出區域，它實際上是指定如何<xref:System.Windows.Media.TileBrush>兩端之間自動縮放以填滿其基底的並排顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="19677-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="19677-118">如需詳細資訊，請參閱<xref:System.Windows.Media.TileBrush>。</span><span class="sxs-lookup"><span data-stu-id="19677-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="19677-119">此程式碼範例是針對所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="19677-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="19677-120">如需完整的範例，請參閱[ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)。</span><span class="sxs-lookup"><span data-stu-id="19677-120">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19677-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19677-121">See also</span></span>
- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="19677-122">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="19677-122">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
