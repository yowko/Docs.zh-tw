---
title: 作法：將視覺物件編碼為影像檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545287"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="3b109-102">作法：將視覺物件編碼為影像檔</span><span class="sxs-lookup"><span data-stu-id="3b109-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="3b109-103">這個範例示範如何<xref:System.Windows.Media.Visual> <xref:System.Windows.Media.Imaging.RenderTargetBitmap>使用和, <xref:System.Windows.Media.Imaging.PngBitmapEncoder>將物件編碼成影像檔案。</span><span class="sxs-lookup"><span data-stu-id="3b109-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b109-104">範例</span><span class="sxs-lookup"><span data-stu-id="3b109-104">Example</span></span>  
 <span data-ttu-id="3b109-105">是使用所<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立<xref:System.Windows.Media.FormattedText> , 且會轉譯為。 <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.DrawingVisual></span><span class="sxs-lookup"><span data-stu-id="3b109-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="3b109-106">然後, 呈現的點陣圖會用來建立<xref:System.Windows.Media.Imaging.BitmapFrame> , 並將其新增<xref:System.Windows.Media.Imaging.PngBitmapEncoder>至, 以建立新的可移植網狀圖形 (PNG) 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b109-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new Portable Network Graphics (PNG) file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="3b109-107">在<xref:System.Windows.Media.Imaging.PngBitmapEncoder>此範例中使用了, 但任何衍生<xref:System.Windows.Media.Imaging.BitmapEncoder>的物件都可能已用來建立影像檔案。</span><span class="sxs-lookup"><span data-stu-id="3b109-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b109-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b109-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="3b109-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="3b109-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="3b109-110">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="3b109-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="3b109-111">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="3b109-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
