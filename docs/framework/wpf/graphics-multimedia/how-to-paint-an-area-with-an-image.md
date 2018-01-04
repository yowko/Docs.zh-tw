---
title: "操作說明：使用影像繪製區域"
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
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e346990696301d27ea329ea4255258562b353c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-an-image"></a><span data-ttu-id="d3872-102">操作說明：使用影像繪製區域</span><span class="sxs-lookup"><span data-stu-id="d3872-102">How to: Paint an Area with an Image</span></span>
<span data-ttu-id="d3872-103">這個範例示範如何使用<xref:System.Windows.Media.ImageBrush>類別，以使用影像繪製區域。</span><span class="sxs-lookup"><span data-stu-id="d3872-103">This example shows how to use the <xref:System.Windows.Media.ImageBrush> class to paint an area with an image.</span></span> <span data-ttu-id="d3872-104"><xref:System.Windows.Media.ImageBrush>會顯示所指定的單一映像及其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d3872-104">An <xref:System.Windows.Media.ImageBrush> displays a single image, which is specified by its <xref:System.Windows.Media.ImageBrush.ImageSource%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3872-105">範例</span><span class="sxs-lookup"><span data-stu-id="d3872-105">Example</span></span>  
 <span data-ttu-id="d3872-106">下列範例繪製<xref:System.Windows.Controls.Control.Background%2A>按鈕所使用的<xref:System.Windows.Media.ImageBrush>。</span><span class="sxs-lookup"><span data-stu-id="d3872-106">The following example paints the <xref:System.Windows.Controls.Control.Background%2A> of a button by using an <xref:System.Windows.Media.ImageBrush>.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 <span data-ttu-id="d3872-107">根據預設，<xref:System.Windows.Media.ImageBrush>自動縮放它的映像完全填滿您所繪製的區域。</span><span class="sxs-lookup"><span data-stu-id="d3872-107">By default, an <xref:System.Windows.Media.ImageBrush> stretches its image to completely fill the area that you are painting.</span></span> <span data-ttu-id="d3872-108">在上一個範例中，已自動縮放影像來填滿按鈕，且可能造成影像扭曲。</span><span class="sxs-lookup"><span data-stu-id="d3872-108">In the preceding example, the image is stretched to fill the button, possibly distorting the image.</span></span> <span data-ttu-id="d3872-109">您可以設定來控制此行為<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.TileBrush>至<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>，因而導致保留外觀比例的影像筆刷。</span><span class="sxs-lookup"><span data-stu-id="d3872-109">You can control this behavior by setting the <xref:System.Windows.Media.TileBrush.Stretch%2A> property of <xref:System.Windows.Media.TileBrush> to <xref:System.Windows.Media.Stretch.Uniform> or <xref:System.Windows.Media.Stretch.UniformToFill>, which causes the brush to preserve the aspect ratio of the image.</span></span>  
  
 <span data-ttu-id="d3872-110">如果您設定<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.TileMode%2A>屬性<xref:System.Windows.Media.ImageBrush>，您可以建立重複的圖樣。</span><span class="sxs-lookup"><span data-stu-id="d3872-110">If you set the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties of an <xref:System.Windows.Media.ImageBrush>, you can create a repeating pattern.</span></span> <span data-ttu-id="d3872-111">下列範例使用從影像建立的圖樣來繪製按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3872-111">The following example paints a button by using a pattern that is created from an image.</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <span data-ttu-id="d3872-112">如需有關<xref:System.Windows.Media.ImageBrush>類別，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="d3872-112">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
 <span data-ttu-id="d3872-113">這個程式碼範例是所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="d3872-113">This code example is part of a larger example that is provided for the <xref:System.Windows.Media.ImageBrush> class.</span></span> <span data-ttu-id="d3872-114">如需完整範例，請參閱[ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)。</span><span class="sxs-lookup"><span data-stu-id="d3872-114">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3872-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3872-115">See Also</span></span>  
 [<span data-ttu-id="d3872-116">使用影像、繪圖和視覺效果繪製</span><span class="sxs-lookup"><span data-stu-id="d3872-116">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
