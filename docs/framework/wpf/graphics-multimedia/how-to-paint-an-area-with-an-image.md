---
title: HOW TO：使用影像繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 2b88982e7a8d196c31869dc74aac636d78f68386
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207808"
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="7696c-102">HOW TO：使用影像繪製區域</span><span class="sxs-lookup"><span data-stu-id="7696c-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="7696c-103">此範例示範如何使用<xref:System.Windows.Media.ImageBrush>類別來使用影像繪製區域。</span><span class="sxs-lookup"><span data-stu-id="7696c-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="7696c-104"><xref:System.Windows.Media.ImageBrush>會顯示單一的映像，以指定其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7696c-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7696c-105">範例</span><span class="sxs-lookup"><span data-stu-id="7696c-105">Example</span></span>  
 <span data-ttu-id="7696c-106">下列範例繪製<xref:System.Windows.Controls.Control.Background%2A>的按鈕，以使用<xref:System.Windows.Media.ImageBrush>。</span><span class="sxs-lookup"><span data-stu-id="7696c-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="7696c-107">根據預設，<xref:System.Windows.Media.ImageBrush>會自動縮放其影像來填滿您所繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="7696c-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="7696c-108">在上一個範例中，已自動縮放影像來填滿按鈕，且可能造成影像扭曲。</span><span class="sxs-lookup"><span data-stu-id="7696c-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="7696c-109">您可以設定來控制此行為<xref:System.Windows.Media.TileBrush.Stretch%2A>的屬性<xref:System.Windows.Media.TileBrush>要<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>，這樣會使筆刷維持影像的外觀比例。</span><span class="sxs-lookup"><span data-stu-id="7696c-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="7696c-110">如果您設定<xref:System.Windows.Media.TileBrush.Viewport%2A>並<xref:System.Windows.Media.TileBrush.TileMode%2A>的屬性<xref:System.Windows.Media.ImageBrush>，您可以建立重複的圖樣。</span><span class="sxs-lookup"><span data-stu-id="7696c-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="7696c-111">下列範例使用從影像建立的圖樣來繪製按鈕。</span><span class="sxs-lookup"><span data-stu-id="7696c-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="7696c-112">如需詳細資訊<xref:System.Windows.Media.ImageBrush>類別，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="7696c-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="7696c-113">此程式碼範例是針對所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="7696c-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="7696c-114">如需完整的範例，請參閱[ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)。</span><span class="sxs-lookup"><span data-stu-id="7696c-114">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7696c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7696c-115">See also</span></span>

- [<span data-ttu-id="7696c-116">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="7696c-116">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
