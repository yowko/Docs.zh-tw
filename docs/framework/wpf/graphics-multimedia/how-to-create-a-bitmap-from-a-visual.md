---
title: HOW TO：從視覺物件建立點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189871"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="7595f-102">HOW TO：從視覺物件建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="7595f-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="7595f-103">此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="7595f-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="7595f-104">A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。</span><span class="sxs-lookup"><span data-stu-id="7595f-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="7595f-105"><xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="7595f-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7595f-106">範例</span><span class="sxs-lookup"><span data-stu-id="7595f-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="7595f-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7595f-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="7595f-108">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="7595f-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="7595f-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="7595f-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="7595f-110">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="7595f-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
