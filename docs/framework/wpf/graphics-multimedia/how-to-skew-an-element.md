---
title: HOW TO：扭曲元素
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: cf770a284238826852e788e27f3b3f329ed0269f
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664090"
---
# <a name="how-to-skew-an-element"></a>作法：扭曲元素
此範例示範如何使用<xref:System.Windows.Media.SkewTransform>來扭曲元素。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 典型的用途之一<xref:System.Windows.Media.SkewTransform>會模擬 3d 2d 物件中的深度。  
  
 使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>並<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。  
  
 使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度，以及目前座標系統沿著這些軸的扭曲。  
  
 若要預測扭曲轉換的效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲 x 軸值相對於原始座標系統。 因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度穿過原點，x-從該原點 30 度的值扭曲。 同樣地， <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 個圖形的 y 值扭曲 30 度，從原始伺服器。 請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。  
  
 下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (0，0)。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 下列範例會以 45 度的垂直扭曲套用<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 下圖顯示本範例所使用的不同扭曲。  
  
 ![SkewTransform 範例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
三個 SkewTransform 範例的示意圖  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [轉換概觀](transforms-overview.md)
- [HOW-TO 主題](transformations-how-to-topics.md)
