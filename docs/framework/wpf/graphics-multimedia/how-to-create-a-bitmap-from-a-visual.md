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
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362860"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="dd0b3-102">HOW TO：從 Visual 建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="dd0b3-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="dd0b3-103">此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="dd0b3-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="dd0b3-104">A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。</span><span class="sxs-lookup"><span data-stu-id="dd0b3-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="dd0b3-105"><xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="dd0b3-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd0b3-106">範例</span><span class="sxs-lookup"><span data-stu-id="dd0b3-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="dd0b3-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd0b3-107">See also</span></span>
- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="dd0b3-108">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="dd0b3-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="dd0b3-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="dd0b3-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="dd0b3-110">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="dd0b3-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
