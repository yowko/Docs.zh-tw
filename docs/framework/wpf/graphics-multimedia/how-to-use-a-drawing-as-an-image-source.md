---
title: HOW TO：使用繪圖作為影像來源
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097856"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a><span data-ttu-id="b4a22-102">HOW TO：使用繪圖作為影像來源</span><span class="sxs-lookup"><span data-stu-id="b4a22-102">How to: Use a Drawing as an Image Source</span></span>
<span data-ttu-id="b4a22-103">此範例示範如何使用<xref:System.Windows.Media.Drawing>作為<xref:System.Windows.Controls.Image.Source%2A>如<xref:System.Windows.Controls.Image>控制項。</span><span class="sxs-lookup"><span data-stu-id="b4a22-103">This example shows how to use a <xref:System.Windows.Media.Drawing> as the <xref:System.Windows.Controls.Image.Source%2A> for an <xref:System.Windows.Controls.Image> control.</span></span> <span data-ttu-id="b4a22-104">若要顯示<xref:System.Windows.Media.Drawing>與<xref:System.Windows.Controls.Image>控制，請使用<xref:System.Windows.Media.DrawingImage>做為<xref:System.Windows.Controls.Image>控制項的<xref:System.Windows.Controls.Image.Source%2A>並設定<xref:System.Windows.Media.DrawingImage>物件的<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>您想要顯示的繪圖屬性。</span><span class="sxs-lookup"><span data-stu-id="b4a22-104">To display a <xref:System.Windows.Media.Drawing> with an <xref:System.Windows.Controls.Image> control, use a <xref:System.Windows.Media.DrawingImage> as the <xref:System.Windows.Controls.Image> control's <xref:System.Windows.Controls.Image.Source%2A> and set the <xref:System.Windows.Media.DrawingImage> object's <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> property to the drawing you want to display.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4a22-105">範例</span><span class="sxs-lookup"><span data-stu-id="b4a22-105">Example</span></span>  
 <span data-ttu-id="b4a22-106">下列範例會使用<xref:System.Windows.Media.DrawingImage>並<xref:System.Windows.Controls.Image>控制項來顯示<xref:System.Windows.Media.GeometryDrawing>。</span><span class="sxs-lookup"><span data-stu-id="b4a22-106">The following example uses a <xref:System.Windows.Media.DrawingImage> and an <xref:System.Windows.Controls.Image> control to display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="b4a22-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b4a22-107">This example produces the following output:</span></span>  
  
 <span data-ttu-id="b4a22-108">![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="b4a22-108">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
<span data-ttu-id="b4a22-109">DrawingImage</span><span class="sxs-lookup"><span data-stu-id="b4a22-109">A DrawingImage</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b4a22-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4a22-110">See also</span></span>

- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="b4a22-111">使用 ImageDrawing 繪製影像</span><span class="sxs-lookup"><span data-stu-id="b4a22-111">Draw an Image Using ImageDrawing</span></span>](how-to-draw-an-image-using-imagedrawing.md)
- [<span data-ttu-id="b4a22-112">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="b4a22-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="b4a22-113">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="b4a22-113">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="b4a22-114">PresentationOptions:Freeze 屬性</span><span class="sxs-lookup"><span data-stu-id="b4a22-114">PresentationOptions:Freeze Attribute</span></span>](../advanced/presentationoptions-freeze-attribute.md)
