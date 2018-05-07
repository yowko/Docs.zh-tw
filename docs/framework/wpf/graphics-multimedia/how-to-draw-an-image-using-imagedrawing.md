---
title: 如何：使用 ImageDrawing 繪製影像
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 2c7771f841fb3b600d4790eb4d484b0a09c45dd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>如何：使用 ImageDrawing 繪製影像
這個範例示範如何使用<xref:System.Windows.Media.ImageDrawing>繪製影像。 <xref:System.Windows.Media.ImageDrawing>可讓您顯示<xref:System.Windows.Media.ImageSource>與<xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.DrawingImage>，或<xref:System.Windows.Media.Visual>。 若要繪製影像，您建立<xref:System.Windows.Media.ImageDrawing>並設定其<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>屬性指定的影像繪製，而<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性指定的位置和每個影像的大小。  
  
## <a name="example"></a>範例  
 下列範例會建立使用四個複合繪圖<xref:System.Windows.Media.ImageDrawing>物件。 這個範例會產生下列影像：  
  
 ![數個 DrawingImage 物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
四個影像繪圖物件  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 如需範例顯示簡單的方式來顯示影像，而不使用<xref:System.Windows.Media.ImageDrawing>，請參閱[使用影像項目](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
