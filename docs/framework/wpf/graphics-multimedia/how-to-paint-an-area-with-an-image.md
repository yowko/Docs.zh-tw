---
title: 操作說明：使用影像繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186058"
---
# <a name="how-to-paint-an-area-with-an-image"></a>操作說明：使用影像繪製區域
此示例演示如何使用 類<xref:System.Windows.Media.ImageBrush>使用圖像繪製區域。 顯示<xref:System.Windows.Media.ImageBrush>由其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>屬性指定的單個圖像。  
  
## <a name="example"></a>範例  
 下面的示例<xref:System.Windows.Controls.Control.Background%2A>使用 繪製按鈕的 。 <xref:System.Windows.Media.ImageBrush>  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 預設情況下，拉伸<xref:System.Windows.Media.ImageBrush>其圖像以完全填充要繪製的區域。 在上一個範例中，已自動縮放影像來填滿按鈕，且可能造成影像扭曲。 可以通過<xref:System.Windows.Media.TileBrush.Stretch%2A>設置<xref:System.Windows.Media.TileBrush>的 屬性 來<xref:System.Windows.Media.Stretch.Uniform>控制此行為<xref:System.Windows.Media.Stretch.UniformToFill>，這將導致畫筆保留圖像的縱橫比。  
  
 如果設置 的<xref:System.Windows.Media.TileBrush.Viewport%2A><xref:System.Windows.Media.TileBrush.TileMode%2A>和 屬性<xref:System.Windows.Media.ImageBrush>，則可以創建重複模式。 下列範例使用從影像建立的圖樣來繪製按鈕。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 有關該類的詳細資訊，<xref:System.Windows.Media.ImageBrush>請參閱[使用圖像、繪圖和視覺物件進行繪畫](painting-with-images-drawings-and-visuals.md)。  
  
 此代碼示例是為類提供的較大示例的<xref:System.Windows.Media.ImageBrush>一部分。 有關完整示例，請參閱[影像筆刷示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)。  
  
## <a name="see-also"></a>另請參閱

- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
