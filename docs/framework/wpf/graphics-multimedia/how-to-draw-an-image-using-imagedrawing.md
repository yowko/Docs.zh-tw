---
title: HOW TO：使用 ImageDrawing 繪製影像
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 9a9a7ee32104e44997e6eaada09edaac2b1d610e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355586"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="08394-102">HOW TO：使用 ImageDrawing 繪製影像</span><span class="sxs-lookup"><span data-stu-id="08394-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="08394-103">此範例示範如何使用<xref:System.Windows.Media.ImageDrawing>繪製影像。</span><span class="sxs-lookup"><span data-stu-id="08394-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="08394-104"><xref:System.Windows.Media.ImageDrawing>可讓您顯示<xref:System.Windows.Media.ImageSource>具有<xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.DrawingImage>，或<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="08394-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="08394-105">若要繪製影像，您建立<xref:System.Windows.Media.ImageDrawing>並將其<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="08394-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="08394-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>屬性會指定要繪製，影像和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性指定的位置與每個影像的大小。</span><span class="sxs-lookup"><span data-stu-id="08394-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08394-107">範例</span><span class="sxs-lookup"><span data-stu-id="08394-107">Example</span></span>  
 <span data-ttu-id="08394-108">下列範例會建立複合圖形使用四個<xref:System.Windows.Media.ImageDrawing>物件。</span><span class="sxs-lookup"><span data-stu-id="08394-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="08394-109">此範例會產生下列映像：</span><span class="sxs-lookup"><span data-stu-id="08394-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="08394-110">![數個 DrawingImage 物件](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="08394-110">![Several DrawingImage objects](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="08394-111">四個 ImageDrawing 物件</span><span class="sxs-lookup"><span data-stu-id="08394-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="08394-112">如需示範簡單的方式來顯示影像，而不需使用範例<xref:System.Windows.Media.ImageDrawing>，請參閱 <<c2> [ 使用 Image 元素](../controls/how-to-use-the-image-element.md)。</span><span class="sxs-lookup"><span data-stu-id="08394-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08394-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08394-113">See also</span></span>
- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [<span data-ttu-id="08394-114">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="08394-114">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="08394-115">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="08394-115">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="08394-116">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="08394-116">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
