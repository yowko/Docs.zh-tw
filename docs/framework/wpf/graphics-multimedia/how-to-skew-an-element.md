---
title: "操作說明：扭曲元素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9da10e4eb6cf045c6c4936b76f847f21ea1495e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-skew-an-element"></a>操作說明：扭曲元素
這個範例示範如何使用<xref:System.Windows.Media.SkewTransform>扭曲項目。 扭曲也稱為傾斜，這種轉換會以非一致的方式延伸座標空間。 一般用途之一<xref:System.Windows.Media.SkewTransform>是模擬[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]深度[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]物件。  
  
 使用<xref:System.Windows.Media.SkewTransform.CenterX%2A>和<xref:System.Windows.Media.SkewTransform.CenterY%2A>屬性，以指定中心點的<xref:System.Windows.Media.SkewTransform>。  
  
 使用<xref:System.Windows.Media.SkewTransform.AngleX%2A>和<xref:System.Windows.Media.SkewTransform.AngleY%2A>屬性指定的 x 軸和 y 軸扭曲角度以及扭曲目前座標系統沿著這些座標軸。  
  
 若要預測的傾斜轉換效果，請考慮，<xref:System.Windows.Media.SkewTransform.AngleX%2A>扭曲相對於原始座標系統的 x 軸值。 因此，對於<xref:System.Windows.Media.SkewTransform.AngleX%2A>是 30，y 軸旋轉 30 度透過原點，扭曲 x-30 度從該來源的值。 同樣地，<xref:System.Windows.Media.SkewTransform.AngleY%2A>為 30 從原點 30 度扭曲圖形的 y 值。 請注意，這和將座標系統的 X 軸或 Y 軸平移 (移動) 30 度的效果不同。  
  
 下列範例會套用至 45 度的水平傾斜<xref:System.Windows.Shapes.Rectangle>從中心點為 (0，0)。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 下列範例會套用至 45 度的水平傾斜<xref:System.Windows.Shapes.Rectangle>從中心點的 (25,25)。  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 下列範例會套用至 45 度的垂直傾斜<xref:System.Windows.Shapes.Rectangle>從中心點的 (25,25)。  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 下圖顯示本範例所使用的不同扭曲。  
  
 ![SkewTransform 範例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
三個 SkewTransform 範例的示意圖  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
