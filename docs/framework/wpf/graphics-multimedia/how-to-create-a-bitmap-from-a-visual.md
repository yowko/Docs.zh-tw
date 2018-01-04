---
title: "如何：從 Visual 建立點陣圖"
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
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db3ad547072f1d9162ede5c45144aa30e809c50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="a0c85-102">如何：從 Visual 建立點陣圖</span><span class="sxs-lookup"><span data-stu-id="a0c85-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="a0c85-103">這個範例示範如何建立可從點陣圖<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="a0c85-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="a0c85-104">A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。</span><span class="sxs-lookup"><span data-stu-id="a0c85-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="a0c85-105"><xref:System.Windows.Media.Visual>接著會轉譯成<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="a0c85-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c85-106">範例</span><span class="sxs-lookup"><span data-stu-id="a0c85-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="a0c85-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c85-107">See Also</span></span>  
 <xref:System.Windows.Media.DrawingContext>  
 [<span data-ttu-id="a0c85-108">影像處理概觀</span><span class="sxs-lookup"><span data-stu-id="a0c85-108">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [<span data-ttu-id="a0c85-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="a0c85-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="a0c85-110">使用 DrawingVisual 物件</span><span class="sxs-lookup"><span data-stu-id="a0c85-110">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
