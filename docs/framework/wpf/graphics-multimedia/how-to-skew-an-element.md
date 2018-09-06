---
title: 如何：傾斜項目
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: f828e4d4e59fa5ed31f81f3e83570a25add19e01
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734899"
---
# <a name="how-to-skew-an-element"></a>如何：傾斜項目
此範例示範如何使用<xref:System.Windows.Media.SkewTransform>來扭曲元素。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 一般用途<xref:System.Windows.Media.SkewTransform>會模擬[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]深度[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]物件。  
  
 使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>並<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。  
  
 使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度，以及目前座標系統沿著這些軸的扭曲。  
  
 若要預測扭曲轉換的效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲 x 軸值相對於原始座標系統。 因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度穿過原點，x-從該原點 30 度的值扭曲。 同樣地， <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 個圖形的 y 值扭曲 30 度，從原始伺服器。 請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。  
  
 下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (0，0)。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 下列範例會套用至 45 度的水平扭曲<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 下列範例會以 45 度的垂直扭曲套用<xref:System.Windows.Shapes.Rectangle>從中心點 (25，25)。  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 下圖顯示本範例所使用的不同扭曲。  
  
 ![SkewTransform 範例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
三個 SkewTransform 範例的示意圖  
  
 如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
