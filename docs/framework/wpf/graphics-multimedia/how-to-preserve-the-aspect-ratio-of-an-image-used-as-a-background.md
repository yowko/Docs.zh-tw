---
title: 操作說明：維持當做背景之影像的外觀比例
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186023"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a><span data-ttu-id="0a511-102">操作說明：維持當做背景之影像的外觀比例</span><span class="sxs-lookup"><span data-stu-id="0a511-102">How to: Preserve the Aspect Ratio of an Image Used as a Background</span></span>
<span data-ttu-id="0a511-103">此示例演示如何使用<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.ImageBrush>來保留圖像的縱橫比。</span><span class="sxs-lookup"><span data-stu-id="0a511-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of an <xref:System.Windows.Media.ImageBrush> in order to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="0a511-104">預設情況下，當您使用<xref:System.Windows.Media.ImageBrush>繪製區域時，其內容會拉伸以完全填充輸出區域。</span><span class="sxs-lookup"><span data-stu-id="0a511-104">By default, when you use an <xref:System.Windows.Media.ImageBrush> to paint an area, its content stretches to completely fill the output area.</span></span> <span data-ttu-id="0a511-105">當輸出區域和影像的外觀比例不相同時，影像就會因為自動縮放而扭曲。</span><span class="sxs-lookup"><span data-stu-id="0a511-105">When the output area and the image have different aspect ratios, the image is distorted by this stretching.</span></span>  
  
 <span data-ttu-id="0a511-106">要<xref:System.Windows.Media.ImageBrush>保留其圖像的縱橫比，將<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設置為<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="0a511-106">To make an <xref:System.Windows.Media.ImageBrush> preserve the aspect ratio of its image, set the <xref:System.Windows.Media.TileBrush.Stretch%2A> property to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a511-107">範例</span><span class="sxs-lookup"><span data-stu-id="0a511-107">Example</span></span>  
 <span data-ttu-id="0a511-108">下面的示例使用兩<xref:System.Windows.Media.ImageBrush>個物件繪製兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="0a511-108">The following example uses two <xref:System.Windows.Media.ImageBrush> objects to paint two rectangles.</span></span> <span data-ttu-id="0a511-109">每個矩形是 300 乘 150 像素且各包含一個 300 乘 300 像素的影像。</span><span class="sxs-lookup"><span data-stu-id="0a511-109">Each rectangle is 300 by 150 pixels and each contains a 300 by 300 pixel image.</span></span> <span data-ttu-id="0a511-110">第<xref:System.Windows.Media.TileBrush.Stretch%2A>一個畫筆的屬性設置為<xref:System.Windows.Media.Stretch.Uniform>，第二個畫筆<xref:System.Windows.Media.TileBrush.Stretch%2A>的屬性設置為<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="0a511-110">The <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the first brush is set to <xref:System.Windows.Media.Stretch.Uniform>, and the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of the second brush is set to <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <span data-ttu-id="0a511-111">下圖顯示了第一<xref:System.Windows.Media.TileBrush.Stretch%2A>個畫筆的輸出，該畫筆的設置為<xref:System.Windows.Media.Stretch.Uniform>。</span><span class="sxs-lookup"><span data-stu-id="0a511-111">The following illustration shows the output of the first brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.Uniform>.</span></span>  
  
 <span data-ttu-id="0a511-112">![Stretch 屬性設定為 Uniform 的 ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span><span class="sxs-lookup"><span data-stu-id="0a511-112">![ImageBrush with Uniform stretching](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")</span></span>  
  
 <span data-ttu-id="0a511-113">下圖顯示了第二個<xref:System.Windows.Media.TileBrush.Stretch%2A>畫筆的輸出，其設置為<xref:System.Windows.Media.Stretch.UniformToFill>。</span><span class="sxs-lookup"><span data-stu-id="0a511-113">The next illustration shows the output of the second brush, which has a <xref:System.Windows.Media.TileBrush.Stretch%2A> setting of <xref:System.Windows.Media.Stretch.UniformToFill>.</span></span>  
  
 <span data-ttu-id="0a511-114">![Stretch 屬性設定為 UniformToFill 的 ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span><span class="sxs-lookup"><span data-stu-id="0a511-114">![ImageBrush with UniformToFill stretching](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")</span></span>  
  
 <span data-ttu-id="0a511-115">請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性對於其他<xref:System.Windows.Media.TileBrush>物件（即 和 ）<xref:System.Windows.Media.DrawingBrush>的事務相同。 <xref:System.Windows.Media.VisualBrush></span><span class="sxs-lookup"><span data-stu-id="0a511-115">Note that the <xref:System.Windows.Media.TileBrush.Stretch%2A> property behaves identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="0a511-116">有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件的詳細資訊，請參閱[使用圖像、繪圖和視覺物件進行繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="0a511-116">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="0a511-117">另請注意，儘管<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性似乎指定<xref:System.Windows.Media.TileBrush>內容如何拉伸以適合其輸出區域，但它實際上指定<xref:System.Windows.Media.TileBrush>內容如何拉伸以填充其基本磁貼。</span><span class="sxs-lookup"><span data-stu-id="0a511-117">Note also that, although the <xref:System.Windows.Media.TileBrush.Stretch%2A> property appears to specify how the <xref:System.Windows.Media.TileBrush> content stretches to fit its output area, it actually specifies how the <xref:System.Windows.Media.TileBrush> content stretches to fill its base tile.</span></span> <span data-ttu-id="0a511-118">如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush>。</span><span class="sxs-lookup"><span data-stu-id="0a511-118">For more information, see <xref:System.Windows.Media.TileBrush>.</span></span>  
  
 <span data-ttu-id="0a511-119">此代碼示例是為類提供的較大示例的<xref:System.Windows.Media.ImageBrush>一部分。</span><span class="sxs-lookup"><span data-stu-id="0a511-119">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="0a511-120">有關完整示例，請參閱[影像筆刷示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)。</span><span class="sxs-lookup"><span data-stu-id="0a511-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a511-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a511-121">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="0a511-122">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="0a511-122">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
