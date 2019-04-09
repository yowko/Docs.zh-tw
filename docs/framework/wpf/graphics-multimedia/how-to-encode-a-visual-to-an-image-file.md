---
title: HOW TO：將視覺物件編碼為影像檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 872c19af0cfcf4fc980643c37e9a6028457c03b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096780"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a><span data-ttu-id="96208-102">HOW TO：將視覺物件編碼為影像檔</span><span class="sxs-lookup"><span data-stu-id="96208-102">How to: Encode a Visual to an Image File</span></span>
<span data-ttu-id="96208-103">此範例示範如何編碼<xref:System.Windows.Media.Visual>映像檔使用的物件<xref:System.Windows.Media.Imaging.RenderTargetBitmap>和<xref:System.Windows.Media.Imaging.PngBitmapEncoder>。</span><span class="sxs-lookup"><span data-stu-id="96208-103">This example demonstrates how to encode a <xref:System.Windows.Media.Visual> object into an image file using a <xref:System.Windows.Media.Imaging.RenderTargetBitmap> and a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96208-104">範例</span><span class="sxs-lookup"><span data-stu-id="96208-104">Example</span></span>  
 <span data-ttu-id="96208-105"><xref:System.Windows.Media.DrawingVisual>會使用建立<xref:System.Windows.Media.Imaging.BitmapImage>並<xref:System.Windows.Media.FormattedText>轉譯成<xref:System.Windows.Media.Imaging.RenderTargetBitmap>。</span><span class="sxs-lookup"><span data-stu-id="96208-105">The <xref:System.Windows.Media.DrawingVisual> is created using a <xref:System.Windows.Media.Imaging.BitmapImage> and <xref:System.Windows.Media.FormattedText> which is rendered to a <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.</span></span> <span data-ttu-id="96208-106">繪製的點陣圖接著用來建立<xref:System.Windows.Media.Imaging.BitmapFrame>已新增到<xref:System.Windows.Media.Imaging.PngBitmapEncoder>來建立新的[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="96208-106">The rendered bitmap is then used to create a <xref:System.Windows.Media.Imaging.BitmapFrame> which is added to the <xref:System.Windows.Media.Imaging.PngBitmapEncoder> to create a new [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] file.</span></span>  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 <span data-ttu-id="96208-107">A<xref:System.Windows.Media.Imaging.PngBitmapEncoder>已用於此範例中，但任何衍生<xref:System.Windows.Media.Imaging.BitmapEncoder>物件可能已用來建立映像檔。</span><span class="sxs-lookup"><span data-stu-id="96208-107">A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> was used in this example but any of the derived <xref:System.Windows.Media.Imaging.BitmapEncoder> objects could have been used to create the image file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96208-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96208-108">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="96208-109">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="96208-109">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="96208-110">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="96208-110">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="96208-111">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="96208-111">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
