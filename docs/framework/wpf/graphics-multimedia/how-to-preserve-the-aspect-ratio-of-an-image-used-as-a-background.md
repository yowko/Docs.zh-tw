---
title: HOW TO：保留作為背景之影像的外觀比例
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 4ae6f1242548038bcd54b7218783e5063fa67872
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083241"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>HOW TO：保留作為背景之影像的外觀比例
此範例示範如何使用<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性<xref:System.Windows.Media.ImageBrush>以維持影像的外觀比例。  
  
 根據預設，當您使用<xref:System.Windows.Media.ImageBrush>繪製區域，其內容自動縮放以完全填滿輸出區域。 當輸出區域和影像的外觀比例不相同時，影像就會因為自動縮放而扭曲。  
  
 若要讓<xref:System.Windows.Media.ImageBrush>保留長寬比的映像，請將<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性設<xref:System.Windows.Media.Stretch.Uniform>或<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
## <a name="example"></a>範例  
 下列範例會使用兩個<xref:System.Windows.Media.ImageBrush>物件來繪製兩個矩形。 每個矩形是 300 乘 150 像素且各包含一個 300 乘 300 像素的影像。 <xref:System.Windows.Media.TileBrush.Stretch%2A>的第一個筆刷屬性設定為<xref:System.Windows.Media.Stretch.Uniform>，而<xref:System.Windows.Media.TileBrush.Stretch%2A>的第二個筆刷屬性設定為<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 下圖顯示具有的第一個筆刷的輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>。  
  
 ![Stretch 屬性設定為 Uniform 的 ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 下圖顯示具有的第二個筆刷的輸出<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>。  
  
 ![Stretch 屬性設定為 UniformToFill 的 ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 請注意，<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性，其行為完全相同的另<xref:System.Windows.Media.TileBrush>物件，也就是針對<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 如需詳細資訊<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>物件，請參閱[使用影像、 繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)。  
  
 另請注意，雖然<xref:System.Windows.Media.TileBrush.Stretch%2A>屬性會顯示以指定如何<xref:System.Windows.Media.TileBrush>內容自動縮放以符合其輸出區域，它實際上是指定如何<xref:System.Windows.Media.TileBrush>兩端之間自動縮放以填滿其基底的並排顯示的內容。 如需詳細資訊，請參閱<xref:System.Windows.Media.TileBrush>。  
  
 此程式碼範例是針對所提供之較大範例的一部分<xref:System.Windows.Media.ImageBrush>類別。 如需完整的範例，請參閱[ImageBrush 範例](https://go.microsoft.com/fwlink/?LinkID=160005)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.TileBrush>
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
