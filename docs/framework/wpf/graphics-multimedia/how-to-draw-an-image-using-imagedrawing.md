---
title: "如何：使用 ImageDrawing 繪製影像"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d292617ef18bea32396327fd1b0a1d08d35ee16f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a><span data-ttu-id="69654-102">如何：使用 ImageDrawing 繪製影像</span><span class="sxs-lookup"><span data-stu-id="69654-102">How to: Draw an Image Using ImageDrawing</span></span>
<span data-ttu-id="69654-103">這個範例示範如何使用<xref:System.Windows.Media.ImageDrawing>繪製影像。</span><span class="sxs-lookup"><span data-stu-id="69654-103">This example shows how to use an <xref:System.Windows.Media.ImageDrawing> to draw an image.</span></span> <span data-ttu-id="69654-104"><xref:System.Windows.Media.ImageDrawing>可讓您顯示<xref:System.Windows.Media.ImageSource>與<xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.DrawingImage>，或<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="69654-104">An <xref:System.Windows.Media.ImageDrawing> enables you display an <xref:System.Windows.Media.ImageSource> with a <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, or <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="69654-105">若要繪製影像，您建立<xref:System.Windows.Media.ImageDrawing>並設定其<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="69654-105">To draw an image, you create an <xref:System.Windows.Media.ImageDrawing> and set its <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> and <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="69654-106"><xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>屬性指定的影像繪製，而<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性指定的位置和每個影像的大小。</span><span class="sxs-lookup"><span data-stu-id="69654-106">The <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> property specifies the image to draw, and the <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> property specifies the position and size of each image.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69654-107">範例</span><span class="sxs-lookup"><span data-stu-id="69654-107">Example</span></span>  
 <span data-ttu-id="69654-108">下列範例會建立使用四個複合繪圖<xref:System.Windows.Media.ImageDrawing>物件。</span><span class="sxs-lookup"><span data-stu-id="69654-108">The following example creates a composite drawing using four <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="69654-109">這個範例會產生下列影像：</span><span class="sxs-lookup"><span data-stu-id="69654-109">This example produces the following image:</span></span>  
  
 <span data-ttu-id="69654-110">![數個 DrawingImage 物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span><span class="sxs-lookup"><span data-stu-id="69654-110">![Several DrawingImage objects](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")</span></span>  
<span data-ttu-id="69654-111">四個影像繪圖物件</span><span class="sxs-lookup"><span data-stu-id="69654-111">Four ImageDrawing objects</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 <span data-ttu-id="69654-112">如需範例顯示簡單的方式來顯示影像，而不使用<xref:System.Windows.Media.ImageDrawing>，請參閱[使用影像項目](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)。</span><span class="sxs-lookup"><span data-stu-id="69654-112">For an example showing a simple way to display an image without using <xref:System.Windows.Media.ImageDrawing>, see [Use the Image Element](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69654-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="69654-113">See Also</span></span>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [<span data-ttu-id="69654-114">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="69654-114">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="69654-115">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="69654-115">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="69654-116">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="69654-116">PresentationOptions:Freeze Attribute</span></span>](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
