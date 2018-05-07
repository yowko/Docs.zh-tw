---
title: 如何：從 Visual 建立點陣圖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 4735474d00712598cb5e41fad289e8f568d83a48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>如何：從 Visual 建立點陣圖
這個範例示範如何建立可從點陣圖<xref:System.Windows.Media.Visual>。 A<xref:System.Windows.Media.DrawingVisual>以呈現<xref:System.Windows.Media.FormattedText>。 <xref:System.Windows.Media.Visual>接著會轉譯成<xref:System.Windows.Media.Imaging.RenderTargetBitmap>建立指定文字的點陣圖。  
  
## <a name="example"></a>範例  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.DrawingContext>  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [使用 DrawingVisual 物件](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
