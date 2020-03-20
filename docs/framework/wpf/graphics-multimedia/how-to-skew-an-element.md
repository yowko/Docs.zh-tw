---
title: 操作說明：扭曲元素
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 370ac28b07427345b52822133b5414b45d4462eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187654"
---
# <a name="how-to-skew-an-element"></a>操作說明：扭曲元素
此示例演示如何使用<xref:System.Windows.Media.SkewTransform>傾斜元素。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 一<xref:System.Windows.Media.SkewTransform>個典型的用途是類比二維物件中的三維深度。  
  
 使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>和<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性指定 的中心<xref:System.Windows.Media.SkewTransform>點。  
  
 使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定 X 軸和 y 軸的傾斜角度，並沿這些軸傾斜當前坐標系。  
  
 要預測偏斜變換的效果，請考慮傾斜<xref:System.Windows.Media.SkewTransform.AngleX%2A>X 軸值相對於原始坐標系。 因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>30，y 軸通過原點旋轉 30 度，並將該原點以 x- 30 度表示值。 同樣，30 的 y<xref:System.Windows.Media.SkewTransform.AngleY%2A>值從原點偏斜 30 度。 請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。  
  
 下面的示例將 45 度的水準偏斜從中心<xref:System.Windows.Shapes.Rectangle>點 （0，0） 應用於 a。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 下面的示例將 45 度的水準偏斜從中心<xref:System.Windows.Shapes.Rectangle>點 （25，25） 應用於 a。  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 下面的示例將 45 度的垂直傾斜從中心點<xref:System.Windows.Shapes.Rectangle>（25，25） 應用於 a。  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 下圖顯示本範例所使用的不同扭曲。  
  
 ![SkewTransform 範例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
三個 SkewTransform 範例的示意圖  
  
 如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [轉換概觀](transforms-overview.md)
- [如何使用主題](transformations-how-to-topics.md)
