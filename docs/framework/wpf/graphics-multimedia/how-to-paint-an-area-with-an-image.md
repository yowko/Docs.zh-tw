---
title: HOW TO：使用影像繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 2b88982e7a8d196c31869dc74aac636d78f68386
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207808"
---
# <a name="how-to-paint-an-area-with-an-image"></a>HOW TO：使用影像繪製區域
此範例示範如何使用<xref:System.Windows.Media.ImageBrush>類別來使用影像繪製區域。 <xref:System.Windows.Media.ImageBrush>會顯示單一的映像，以指定其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性。  
  
## <a name="example"></a>範例  
 下列範例繪製<xref:System.Windows.Controls.Control.Background%2A>的按鈕，以使用<xref:System.Windows.Media.ImageBrush>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 根據預設，<xref:System.Windows.Media.ImageBrush>會自動縮放其影像來填滿您所繪製的區域。 在上一個範例中，已自動縮放影像來填滿按鈕，且可能造成影像扭曲。 您可以設定來控制此行為<xref:System.Windows.Media.TileBrush.Stretch%2A>的屬性<xref:System.Windows.Media.TileBrush>要<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>，這樣會使筆刷維持影像的外觀比例。  
  
 如果您設定<xref:System.Windows.Media.TileBrush.Viewport%2A>並<xref:System.Windows.Media.TileBrush.TileMode%2A>的屬性<xref:System.Windows.Media.ImageBrush>，您可以建立重複的圖樣。 下列範例使用從影像建立的圖樣來繪製按鈕。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 如需詳細資訊<xref:System.Windows.Media.ImageBrush>類別，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
 此程式碼範例是針對所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。 如需完整的範例，請參閱[ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)。  
  
## <a name="see-also"></a>另請參閱

- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
