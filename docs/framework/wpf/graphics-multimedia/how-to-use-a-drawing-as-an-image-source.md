---
title: HOW TO：使用繪圖作為影像來源
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: d4b91a6495e1c54400d5fbfe43b6311d908565a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097856"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>HOW TO：使用繪圖作為影像來源
此範例示範如何使用<xref:System.Windows.Media.Drawing>作為<xref:System.Windows.Controls.Image.Source%2A>如<xref:System.Windows.Controls.Image>控制項。 若要顯示<xref:System.Windows.Media.Drawing>與<xref:System.Windows.Controls.Image>控制，請使用<xref:System.Windows.Media.DrawingImage>做為<xref:System.Windows.Controls.Image>控制項的<xref:System.Windows.Controls.Image.Source%2A>並設定<xref:System.Windows.Media.DrawingImage>物件的<xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType>您想要顯示的繪圖屬性。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.DrawingImage>並<xref:System.Windows.Controls.Image>控制項來顯示<xref:System.Windows.Media.GeometryDrawing>。 這個範例會產生下列輸出：  
  
 ![兩個橢圓形的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable.Freeze%2A>
- [使用 ImageDrawing 繪製影像](how-to-draw-an-image-using-imagedrawing.md)
- [繪圖物件概觀](drawing-objects-overview.md)
- [Freezable 物件概觀](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze 屬性](../advanced/presentationoptions-freeze-attribute.md)
