---
title: 操作說明：維持當做背景之影像的外觀比例
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>操作說明：維持當做背景之影像的外觀比例
這個範例示範如何使用<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.ImageBrush>以維持外觀比例的影像。  
  
 根據預設，當您使用<xref:System.Windows.Media.ImageBrush>繪製區域，其內容自動縮放以完全填滿輸出區域。 當輸出區域和影像的外觀比例不相同時，影像就會因為自動縮放而扭曲。  
  
 讓<xref:System.Windows.Media.ImageBrush>保留其影像的外觀比例，設定<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
## <a name="example"></a>範例  
 下列範例會使用兩個<xref:System.Windows.Media.ImageBrush>來繪製兩個矩形的物件。 每個矩形是 300 乘 150 像素且各包含一個 300 乘 300 像素的影像。 <xref:System.Windows.Media.TileBrush.Stretch%2A>第一筆刷屬性設定為<xref:System.Windows.Media.Stretch.Uniform>，而<xref:System.Windows.Media.TileBrush.Stretch%2A>的第二筆刷屬性設定為<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 下圖顯示具有的第一筆刷輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>。  
  
 ![Stretch 屬性設定為 Uniform 的 ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 下圖顯示具有的第二筆刷的輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 ![Stretch 屬性設定為 UniformToFill 的 ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性運作方式完全相同的其他<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 如需有關<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件，請參閱[使用映像、 繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)。  
  
 此外，請注意，雖然<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性會顯示以指定如何<xref:System.Windows.Media.TileBrush>內容自動縮放以符合其輸出區域中，它確實會指定如何<xref:System.Windows.Media.TileBrush>兩端之間自動縮放以填滿其基底的並排顯示的內容。 如需詳細資訊，請參閱<xref:System.Windows.Media.TileBrush>。  
  
 這個程式碼範例是所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。 如需完整範例，請參閱[ImageBrush 範例](http://go.microsoft.com/fwlink/?LinkID=160005)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.TileBrush>  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
