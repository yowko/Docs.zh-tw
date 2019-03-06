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
# <a name="how-to-create-a-bitmap-from-a-visual"></a>HOW TO：從 Visual 建立點陣圖
此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。 A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。 <xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。  
  
## <a name="example"></a>範例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.DrawingContext>
- [影像處理概觀](imaging-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [使用 DrawingVisual 物件](using-drawingvisual-objects.md)
