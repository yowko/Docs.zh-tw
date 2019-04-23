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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189871"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>HOW TO：從視覺物件建立點陣圖
此範例示範如何建立從點陣圖<xref:System.Windows.Media.Visual>。 A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。 <xref:System.Windows.Media.Visual>接著會轉譯為<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。  
  
## <a name="example"></a>範例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.DrawingContext>
- [影像處理概觀](imaging-overview.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [使用 DrawingVisual 物件](using-drawingvisual-objects.md)
