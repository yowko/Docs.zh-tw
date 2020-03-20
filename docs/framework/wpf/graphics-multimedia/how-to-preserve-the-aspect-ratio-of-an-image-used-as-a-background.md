---
title: 操作說明：維持當做背景之影像的外觀比例
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186023"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>操作說明：維持當做背景之影像的外觀比例
此示例演示如何使用<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.ImageBrush>來保留圖像的縱橫比。  
  
 預設情況下，當您使用<xref:System.Windows.Media.ImageBrush>繪製區域時，其內容會拉伸以完全填充輸出區域。 當輸出區域和影像的外觀比例不相同時，影像就會因為自動縮放而扭曲。  
  
 要<xref:System.Windows.Media.ImageBrush>保留其圖像的縱橫比，將<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設置為<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
## <a name="example"></a>範例  
 下面的示例使用兩<xref:System.Windows.Media.ImageBrush>個物件繪製兩個矩形。 每個矩形是 300 乘 150 像素且各包含一個 300 乘 300 像素的影像。 第<xref:System.Windows.Media.TileBrush.Stretch%2A>一個畫筆的屬性設置為<xref:System.Windows.Media.Stretch.Uniform>，第二個畫筆<xref:System.Windows.Media.TileBrush.Stretch%2A>的屬性設置為<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 下圖顯示了第一<xref:System.Windows.Media.TileBrush.Stretch%2A>個畫筆的輸出，該畫筆的設置為<xref:System.Windows.Media.Stretch.Uniform>。  
  
 ![Stretch 屬性設定為 Uniform 的 ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 下圖顯示了第二個<xref:System.Windows.Media.TileBrush.Stretch%2A>畫筆的輸出，其設置為<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 ![Stretch 屬性設定為 UniformToFill 的 ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性對於其他<xref:System.Windows.Media.TileBrush>物件（即 和 ）<xref:System.Windows.Media.DrawingBrush>的事務相同。 <xref:System.Windows.Media.VisualBrush> 有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件的詳細資訊，請參閱[使用圖像、繪圖和視覺物件進行繪製](painting-with-images-drawings-and-visuals.md)。  
  
 另請注意，儘管<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性似乎指定<xref:System.Windows.Media.TileBrush>內容如何拉伸以適合其輸出區域，但它實際上指定<xref:System.Windows.Media.TileBrush>內容如何拉伸以填充其基本磁貼。 如需詳細資訊，請參閱 <xref:System.Windows.Media.TileBrush>。  
  
 此代碼示例是為類提供的較大示例的<xref:System.Windows.Media.ImageBrush>一部分。 有關完整示例，請參閱[影像筆刷示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.TileBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
