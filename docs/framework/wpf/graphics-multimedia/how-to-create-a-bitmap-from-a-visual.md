---
title: HOW TO：從 Visual 建立點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: dbbf7691508e5e5ddf3ed3af768f757ee0c3f20c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705442"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="54735-102">HOW TO：從 Visual 建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="54735-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="54735-103">此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="54735-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="54735-104">A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。</span><span class="sxs-lookup"><span data-stu-id="54735-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="54735-105"><xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="54735-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54735-106">範例</span><span class="sxs-lookup"><span data-stu-id="54735-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="54735-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54735-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="54735-108">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="54735-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
- [<span data-ttu-id="54735-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="54735-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="54735-110">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="54735-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
