---
title: HOW TO：使用 ImageDrawing 繪製影像
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100154"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>HOW TO：使用 ImageDrawing 繪製影像
此範例示範如何使用<xref:System.Windows.Media.ImageDrawing>繪製影像。 <xref:System.Windows.Media.ImageDrawing>可讓您顯示<xref:System.Windows.Media.ImageSource>具有<xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.DrawingImage>，或<xref:System.Windows.Media.Visual>。 若要繪製影像，您建立<xref:System.Windows.Media.ImageDrawing>並將其<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>屬性會指定要繪製，影像和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>屬性指定的位置與每個影像的大小。  
  
## <a name="example"></a>範例  
 下列範例會建立複合圖形使用四個<xref:System.Windows.Media.ImageDrawing>物件。 此範例會產生下列映像：  
  
 ![數個 DrawingImage 物件](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
四個 ImageDrawing 物件  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 如需示範簡單的方式來顯示影像，而不需使用範例<xref:System.Windows.Media.ImageDrawing>，請參閱 <<c2> [ 使用 Image 元素](../controls/how-to-use-the-image-element.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [繪圖物件概觀](drawing-objects-overview.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze 屬性](../advanced/presentationoptions-freeze-attribute.md)
