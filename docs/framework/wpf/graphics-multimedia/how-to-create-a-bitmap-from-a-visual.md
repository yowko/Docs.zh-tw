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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910256"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="0ebba-102">HOW TO：從視覺物件建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="0ebba-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="0ebba-103">此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="0ebba-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="0ebba-104">A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。</span><span class="sxs-lookup"><span data-stu-id="0ebba-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="0ebba-105"><xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="0ebba-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ebba-106">範例</span><span class="sxs-lookup"><span data-stu-id="0ebba-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="0ebba-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ebba-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="0ebba-108">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="0ebba-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="0ebba-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="0ebba-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="0ebba-110">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="0ebba-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
