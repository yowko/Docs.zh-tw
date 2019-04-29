---
title: HOW TO：轉換筆刷
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: a83f3b1c046e94faa8816e8c310f438b4711048a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769368"
---
# <a name="how-to-transform-a-brush"></a>HOW TO：轉換筆刷
此範例示範如何轉換<xref:System.Windows.Media.Brush>物件使用其兩個轉換屬性：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>。  
  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>若要旋轉的內容<xref:System.Windows.Media.ImageBrush>旋轉 45 度。  
  
 如下圖所示<xref:System.Windows.Media.ImageBrush>而不需要<xref:System.Windows.Media.RotateTransform>，使用<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，且<xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.Media.Brush.Transform%2A>屬性。  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>範例  
 第一個範例會套用<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>的屬性<xref:System.Windows.Media.RotateTransform>物件都設為 0.5，這是此內容的中心點的相對座標。 如此一來，<xref:System.Windows.Media.ImageBrush>旋轉中心的內容。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 第二個範例也適用於<xref:System.Windows.Media.RotateTransform>要<xref:System.Windows.Media.ImageBrush>; 不過，此範例會使用<xref:System.Windows.Media.Brush.Transform%2A>屬性而非<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性。  
  
 若要旋轉筆刷的中心，此範例會設定<xref:System.Windows.Media.RotateTransform.CenterX%2A>並<xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性的<xref:System.Windows.Media.RotateTransform>為絕對座標的物件。 由於筆刷會繪製大小為 175 x 90 像素的矩形，矩形的中心點將會是 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 如需說明如何<xref:System.Windows.Media.Brush.RelativeTransform%2A>並<xref:System.Windows.Media.Brush.Transform%2A>屬性運作，請參閱[筆刷轉換概觀](brush-transformation-overview.md)。  
  
 如需完整的範例，請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [筆刷轉換概觀](brush-transformation-overview.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [轉換概觀](transforms-overview.md)
